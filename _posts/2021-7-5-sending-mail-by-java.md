---
layout: post
title: "[java] 자바로 메일 보내기"
---

이메일 인증, 비밀번호 찾기, 뉴스레터에 사용되는 이메일 전송. 어떤 방식으로 이뤄지는 걸까? 「자바 웹을 다루는 기술」 28장과 팀프로젝트 코드를 읽으며 정리해보았다.

#### 0. 코드 작성 이전에

1. 메일에 사용할 구글/네이버 계정 SMTP 설정
2. 보안 수준이 낮은 앱 액세스 허용
3. 앱 비밀번호 설정

#### 1. pom.xml에 자바 메일 라이브러리 추가

```xml
  <dependency>
    <groupId>javax.mail</groupId>
    <artifactId>javax.mail-api</artifactId>
    <version>1.5.4</version>
  </dependency>

  <dependency>
		<groupId>com.sun.mail</groupId>
		<artifactId>javax.mail</artifactId>
		<version>1.5.3</version>
	</dependency>
```

#### 2. mail-context.xml

```xml
<bean id="mailSender" class="org.springframework.mail.javamail.JavaMailSenderImpl">
  // 메일 보냈을 때, 실제 수신자에게 메일을 보내는 host 서버에 구글의 SMTP 서버를 설정
  <property name="host" value="smtp.gmail.com" />
  // 구글의 SMTP 메일 서버의 포트는 465 또는 587
  <property name="port" value="587" />
  // 메일 송신에 사용할 계정과 비밀번호를 입력
  <property name="username" value="사용할 메일 주소" />
  <property name="password" value="메일 비밀번호" />
  // 메일 전달 프로토콜 세부 속성 설정
  <property name="javaMailProperties">
    <props>
       <prop key="mail.transport.protocol">smtp</prop>
       <prop key="mail.smtp.auth">true</prop>
       <prop key="mail.smtp.starttls.enable">true</prop>
       <prop key="mail.smtp.socketFactory.class">javax.net.ssl.SSLSocketFactory</prop>
       <prop key="mail.debug">true</prop>
    </props>
  </property>
</bean>
```

이 때, 해당 설정파일을 읽어올 수 있도록 web.xml에서 경로를 지정해주어야 한다.

#### 3. MailController 클래스

```java
@Controller
@EnableAsync
public class MainController {
	@Autowired
	private MailService mailService;

	@RequestMapping(value="/sendMail.do", method = RequestMethod.GET)
	public void sendSimpleMail(HttpServletRequest request, HttpServletResponse response) throws Exception{
		request.setCharacterEncoding("utf-8");
		response.setContentType("text/html;charset=utf-8");
		PrintWriter out = response.getWriter();
		String to = "수신자 메일";
		String subject = "제목 입력";
		String body = "메일 내용 입력";
		mailService.sendMail(to, subject, body);
		out.print("메일 전송");
	}
}


```

#### 4. MailService 클래스

```java
@Service("mailService")
public class MailService {
	@Autowired
	private JavaMailSender mailSender;
	@Autowired
	private SimpleMailMessage preConfiguredMessage;

	@Async
	public void sendMail(String to, String subject, String body) {
		MimeMessage message = mailSender.createMimeMessage();

		try {
			MimeMessageHelper messageHelper = new MimeMessageHelper(message, true, "UTF-8");
			messageHelper.setFrom("보내는 사람 메일주소", "보내는 사람 이름");
			messageHelper.setTo(to); // 수신자 메일
			messageHelper.setSubject(subject); // 메일 제목
			messageHelper.setText(body); // 메일 내용
			mailSender.send(message);
		} catch(Exception e) {
			e.printStackTrace();
		}
	}

```

**✅@Async 애너테이션으로 지정된 메서드는 비동기로 동작한다.**

즉 메일 보내는 작업을 따로 수행하기 때문에 **많은 양의 작업을 요청한 경우에도 작업이 끝날 때까지 기다릴 필요가 없다**. 해당 코드에서는 다수에게 메일을 보내야 하는 때에 유용하게 작동할 것이다.
