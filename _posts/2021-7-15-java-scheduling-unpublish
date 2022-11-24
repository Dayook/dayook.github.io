---
layout: post
title: "[java] @Scheduled 어노테이션 활용한 자바 스케쥴링 "
---


#### 1. 스케쥴링 기능 설정

어노테이션, xml 두 가지 방법중 하나를 선택해서 쓸 수 있다.

1.어노테이션

```java
@Configuration
@EnableScheduling
public class Spring config{
  ...
}
```

2.xml

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns:task="http://www.springframework.org/schema/task"
	xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
	http://www.springframework.org/schema/task http://www.springframework.org/schema/task/spring-task.xsd">

	<task:annotation-driven/>
```

#### 2. 스케쥴링 시간 설정

1. fixedDelay

```java
// 밀리초 단위로 설정 - 1000ms=1s마다 실행됨
@Scheduled(fixedDelay = 1000)
public void scheduleFixedDelayTask() {
    System.out.println(
      "Fixed delay task - " + System.currentTimeMillis() / 1000);
}
```

fixed delay는 이전 실행의 종료시간과 다음 실행의 시작시간 간격을 설정한다. 다음 실행 이전에 이전 실행이 반드시 완료되어야 하는 경우 쓰임.

2 . FixedRate + Async

```java
@EnableAsync
public class ScheduledFixedRateExample {
    @Async
    @Scheduled(fixedRate = 1000)
    public void scheduleFixedRateTaskAsync() throws InterruptedException {
        System.out.println(
          "Fixed rate task async - " + System.currentTimeMillis() / 1000);
        Thread.sleep(2000);
    }

}
```

사건들을 병렬로 실행하고 싶은 경우, @Async 어노테이션을 덧붙이고 Fixed Rate를 사용한다.

3 . Cron 표현을 사용한 스케줄링

```java
@Scheduled(cron = "0 15 10 15 * ?" /*, zone="Europe/Paris"*/) // 매달 15일, 10시 15분에 실행
public void scheduleTaskUsingCronExpression() {

    long now = System.currentTimeMillis() / 1000;
    System.out.println(
      "schedule tasks using cron jobs - " + now);
}

```

이 때 스프링은 서버의 로컬 타임을 표준시간으로 사용하는데, zone 속성을 추가해준다면 표준 시간대 역시 바꿔줄 수 있다. cron은 컴퓨터 운영체제의 시간 기반 잡 스케쥴러(출처:[wikipedia](https://ko.wikipedia.org/wiki/Cron))인데 왼쪽부터 순서대로 초, 분, 시, 일, 월, 요일을 의미하며 \*는 모든 값을, ?은 해당 항목을 사용하지 않음을 뜻한다.

[Cron Maker - 크론 표현식 생성 사이트 ](http://www.cronmaker.com/;jsessionid=node0hax1d8ad4ecxfpum15o8l3jp1417306.node0?0)

4 . XML을 사용한 스케쥴링

```xml
<task:scheduled-tasks>
	<task:scheduled ref="printStars" method="stars" fixed-delay="3000"/>
	</task:scheduled-tasks>
```

```java
@Component("printStars")
public class PrintStars {

	public void stars() {
		System.out.println("* Exectuted Printing Stars... ");
	}
}
```

참고자료

- [The @Scheduled Annotation in Spring](https://www.baeldung.com/spring-scheduled-tasks#parameterizing-the-schedule)
- [Spring Scheduler Example Using Xml Configuration](https://www.technicalkeeda.com/spring-tutorials/spring-scheduler-example-using-xml-configuration)
