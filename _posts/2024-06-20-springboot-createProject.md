---
title: Javascript - 호이스팅
categories:
- Javascript
feature_image: "https://picsum.photos/2560/600?image=872"
---

인텔리제이 통합개발환경으로 스프링부트 프로젝트 생성하는 법!

인텔리제이는 유료버전과 무료버전(community)이 있는데 무료버전을 사용할 경우 스프링 프로젝트를 직접 생성할 수는 없고 https://start.spring.io/ 라는 사이트에서 생성할 수 있습니다.

![](https://velog.velcdn.com/images/chjw147/post/80265e4f-29b5-4d6a-97ad-2019f7309ecc/image.png)


[Project] 이 옵션에서는 프로젝트 빌드시 어떤 빌드툴을 사용할 것인지 정해야합니다.

> **빌드란?**
빌드는 소스코드 파일을 실행 파일로 변환하거나 소프트웨어 배포를 위해 다른 형태로 변환하는 과정을 말합니다.
+ **컴파일** : 소스코드를 컴파일하여 바이트코드나 기계어 코드로 변환.
+ **패키징** : 컴파일된 코드를 JAR, WAR, EAR 등의 아카이브 파일로 묶음.
+ **의존성관리**: 프로젝트에서 사용하는 외부 라이브러리와 그 버전을 관리.
+ **테스트**: 단위 테스트, 통합 테스트 등을 실행하여 코드의 품질을 검증.
+ **배포**: 빌드된 아티팩트를 다양한 환경(로컬, 스테이징, 프로덕션)에 배포.
+ **빌드 관리 도구**: Maven과 Gradle

>**Maven** VS **Gradle** VS **Kotlin**
예전에는 Maven을 많이 사용했지만 요즘에는 더 작성하기 쉽고 속도도 빠른 Gradle을 사용하는 것을 추천합니다.

>**Maven**
**<특징>**
**빌드 도구**: Maven은 Apache에서 제공하는 빌드 자동화 도구로, Java 프로젝트를 중심으로 사용됩니다.
**프로젝트 객체 모델(POM)**: 프로젝트의 빌드 프로세스와 종속성을 관리하기 위해 XML 파일(POM.xml)을 사용합니다.
**의존성 관리**: 중앙 저장소를 통해 라이브러리와 플러그인을 쉽게 관리하고 사용할 수 있습니다.
**생명 주기(Lifecycle)**: 빌드 프로세스를 표준화하기 위해 일련의 단계로 구성된 빌드 생명 주기를 제공합니다.
**<장점>**
**광범위한 도입**: 많은 Java 프로젝트에서 표준으로 사용되며, 커뮤니티와 문서가 풍부합니다.
**<단점>**
**복잡성**: POM.xml이 복잡해질 수 있으며, XML의 가독성이 떨어질 수 있습니다.
**유연성 부족**: 생명 주기와 플러그인이 고정되어 있어 커스터마이징이 어렵습니다.
**속도**: Gradle에 비해 빌드 속도가 느립니다.

>**Gradle**
**<특징>**
**빌드 도구**: Gradle은 유연하고 강력한 빌드 도구로, JVM 언어뿐만 아니라 다른 언어 프로젝트에도 사용될 수 있습니다.
**Groovy와 Kotlin DSL**: 빌드 스크립트를 작성하기 위해 Groovy와 Kotlin DSL을 지원합니다.
**의존성 관리**: Maven과 유사하게 중앙 저장소를 통해 라이브러리와 플러그인을 관리합니다.
**태스크(Task) 기반**: 빌드 과정을 태스크 단위로 나누어 관리합니다.
**<장점>**
**유연성**: Groovy와 Kotlin DSL을 사용하여 빌드 스크립트를 더욱 유연하게 작성할 수 있습니다.
**범용성**: 자바외에 C, C++등 다른언어에서도 사용가능합니다.
**성능**: 인크리멘탈 빌드와 캐시 기능으로 빌드 속도가 빠릅니다.(Maven에 비해 최소 2배에서 빌드 캐시를 사용하는 대규모 빌드의 경우 100배까지 차이가 납니다.)
**유연한 구성**: 사용자 정의가 용이하며, 다양한 플러그인과 확장을 지원합니다.
**<단점>**
**학습 곡선**: Groovy나 Kotlin DSL을 익히는 데 시간이 걸릴 수 있습니다.
**초기 설정 복잡성**: 처음 설정할 때 복잡할 수 있으며, 설정 파일이 많아질 수 있습니다.
**의존성 해결 문제**: 가끔 의존성 충돌 문제를 해결하는 데 어려움이 있을 수 있습니다.


>**Kotlin**
**<특징>**
**프로그래밍 언어**: Kotlin은 JetBrains에서 개발한 현대적인 다목적 프로그래밍 언어로, JVM에서 실행됩니다.
**상호 운용성**: Java와 100% 상호 운용이 가능하며, 기존 Java 코드를 쉽게 사용할 수 있습니다.
**간결성**: 코드가 간결하고, Null 안전성과 같은 다양한 언어적 기능을 제공합니다.
**확장 함수**: 클래스의 기능을 확장할 수 있는 기능을 제공합니다.
**<장점>**
**간결성**: 불필요한 코드 작성을 줄여주어 생산성을 높입니다.
**Null 안전성**: NullPointerException을 방지하는 기능을 제공하여 코드 안정성을 높입니다.
**Java 호환성**: 기존 Java 라이브러리와 프레임워크를 쉽게 사용할 수 있습니다.
**커뮤니티 지원**: Android 개발에서 표준 언어로 채택되어 강력한 커뮤니티 지원을 받습니다.
**<단점>**
**학습 곡선**: Java 개발자에게는 새로운 문법과 개념을 익히는 데 시간이 걸릴 수 있습니다.
**컴파일 속도**: 일부 경우에 컴파일 속도가 Java보다 느릴 수 있습니다.
도구 체인 성숙도: 도구 체인이 Java에 비해 아직 성숙하지 않을 수 있습니다(예: 디버깅 도구).
**Gradle 5.0 부터 지원**
**Java 8 부터 가능**

![](https://velog.velcdn.com/images/chjw147/post/bedbf7c5-98d0-49c0-af53-73217adbe2bf/image.png)

여러사람이 협업하는 프로젝트에서 위와 같은 통일성은 코드의 유지보수를 용이하게 합니다.


---

툴의 특징들을 살펴보면 결국 의존성 관리가 빌드툴의 핵심기능처럼 보입니다.

그렇다면 왜 **의존성 관리**가 중요한가?
>
+ **자동 업데이트**: 최신 버전의 라이브러리를 쉽게 사용할 수 있도록 도와줍니다. 보안 패치나 새로운 기능을 빠르게 반영할 수 있습니다.
+ **충돌 해결**: 여러 라이브러리 간의 버전 충돌을 관리하여, 호환되지 않는 버전 사용으로 인한 문제를 방지합니다.
+ **일관성 유지**: 프로젝트 팀 전체가 동일한 버전의 라이브러리를 사용하도록 하여, 환경 차이로 인한 문제를 최소화합니다.



---

>
**Groovy란?**
Groovy는 자바 플랫폼에서 동작하는 객체 지향 프로그래밍 언어로, 자바와의 호환성을 유지하면서도 간결하고 유연한 문법을 제공합니다. 스프링 부트(Spring Boot)와 같은 프레임워크와 결합하여 사용할 때 여러 가지 장점을 제공하며, 특정한 경우에는 단점도 있을 수 있습니다.
**<특징>**
**자바와의 호환성**: Groovy는 자바 플랫폼 위에서 동작하기 때문에 자바의 모든 라이브러리와 프레임워크를 사용할 수 있습니다.
자바 코드와 혼합하여 사용할 수 있으며, 기존 자바 코드를 거의 수정 없이 Groovy 코드로 변환할 수 있습니다. (단, 같은 .java 파일에서 사용하는 것이 아니라 따로 Groovy 파일을 자바 프로젝트 안에 넣어 사용할 수 있습니다)
**간결한 문법**: 불필요한 코드 생략이 가능해 코드가 더 간결하고 읽기 쉬워집니다.
예를 들어, 세미콜론(;)을 생략할 수 있으며, getter와 setter 메서드를 자동으로 생성해줍니다.
**스크립트 언어로서의 유연성**: Groovy는 스크립트 언어로서의 특성을 가지므로, 빠르게 프로토타입을 작성하거나 테스트 스크립트를 작성하는 데 유리합니다.
동적 타입을 지원하여 코드를 더 유연하게 작성할 수 있습니다.
**강력한 DSL(Domain Specific Language) 작성 기능**: Groovy는 DSL을 작성하기에 적합한 문법적 특성을 가지고 있습니다. 예를 들어, 빌드 도구인 Gradle이 Groovy를 기반으로 작성되었습니다.
스프링의 Grails 프레임워크도 Groovy를 기반으로 만들어져 있으며, 웹 애플리케이션 개발을 간소화합니다.
**기본 제공 기능들**: 클로저(Closure)를 이용한 함수형 프로그래밍 스타일을 지원합니다.
빌트인 컬렉션 메서드와 스트링 처리 기능 등이 풍부합니다.
**<장점>**
**생산성 향상**: 간결한 문법과 다양한 내장 기능으로 인해 개발 속도가 빨라집니다.
반복적인 코드 작성이 줄어들어 유지보수가 용이합니다.
**자바와의 상호운용성**: 자바 코드와 쉽게 통합될 수 있어 기존 자바 프로젝트에 Groovy를 도입하는 데 어려움이 없습니다.
자바 개발자들이 쉽게 배울 수 있습니다.
**동적 프로그래밍 기능**: 컴파일 타임보다 런타임에 더 많은 유연성을 제공합니다.
동적 메서드 호출, 동적 객체 생성 등을 통해 코드의 유연성을 극대화할 수 있습니다.
**<단점>**
**성능 저하**:동적 타입을 사용함에 따라 런타임에 타입 체크가 이루어지므로, 순수 자바보다 실행 속도가 느릴 수 있습니다.
성능이 중요한 애플리케이션에서는 신중하게 사용해야 합니다.
**에러 검출 어려움**:동적 타이핑으로 인해 컴파일 타임에 잡히지 않는 오류가 발생할 수 있습니다.
큰 프로젝트에서는 정적 타입 언어보다 버그 검출이 어려울 수 있습니다.
**학습 곡선**: 자바 개발자에게는 새로운 문법과 개념(예: 클로저, 동적 프로그래밍 등)을 배우는 데 다소 시간이 걸릴 수 있습니다.
특히, 자바에 익숙한 개발자에게는 문법의 유연성이 처음에는 혼란스러울 수 있습니다.

>
Groovy와 스프링 부트의 결합
결론적으로, Groovy는 자바와의 높은 호환성과 간결한 문법으로 인해 스프링 부트와 같은 프레임워크와 함께 사용할 때 개발 생산성을 크게 높일 수 있는 유용한 도구입니다. 다만, 성능이나 타입 안전성이 중요한 경우에는 신중하게 도입을 고려해야 합니다.


>
GROOVY VS KOTLIN

![](https://velog.velcdn.com/images/chjw147/post/86d9431f-9b42-481f-8623-29df3157dc68/image.png)

결론부터 말하자면 Groovy DSL 과 Kotlin DSL 은 거의 차이가 없다고 볼 수 있습니다. 

+ 빌드 속도의 차이는 거의 없다고 볼 수 있습니다.

+ 빌드 스크립트의 확장자명에 차이가 있습니다.

 Groovy : build.gradle / Kotlin : build.gardle.kts

+ Kotlin DSL 에서 스크립트 작성 시 큰따옴표(")  를 사용하게끔 약간의 제약을 가하는 표현방식을 사용하며 
Groovy DSL 은 큰따옴표(")와 작은따옴표(') 모두 사용 가능하게 하여 표현 방식에서 좀 더 자유롭습니다.



---


**JAR(Java ARchive)**와** WAR(Web Application Archive)**는 자바에서 사용되는 두 가지 주요 아카이브 파일 형식입니다. 각각의 용도와 특징에 대해 자세히 설명드리겠습니다.

**JAR (Java ARchive)**

**정의**
+ JAR 파일은 여러 자바 클래스 파일, 메타데이터, 리소스(이미지, 텍스트 등)를 하나의 파일로 묶은 압축 파일 형식입니다.

**특징**

1. **압축 형식**:

+ ZIP 파일 형식을 기반으로 하며, 압축되어 있어 파일 크기를 줄일 수 있습니다.

2. **구조**:

+ JAR 파일 내부에는 자바 클래스 파일(.class), 메타데이터 파일(META-INF 디렉토리 내의 MANIFEST.MF 파일) 및 기타 리소스 파일이 포함될 수 있습니다.

3. ** 메타데이터**:

+ META-INF/MANIFEST.MF 파일은 JAR 파일의 메타데이터를 포함하며, 실행 가능한 JAR 파일의 경우, 메인 클래스의 경로를 지정할 수 있습니다.
```
Main-Class: com.example.Main
```

4. **용도**:

+ **라이브러리 배포**: 여러 클래스와 리소스를 하나의 파일로 묶어 배포할 때 사용합니다.
+ **실행 가능한 애플리케이션**: JAR 파일 내부에 메인 클래스를 지정하면, JAR 파일을 실행하여 자바 애플리케이션을 실행할 수 있습니다.

사용 예시
+ **라이브러리 배포**: 자바 프로젝트에서 외부 라이브러리를 JAR 파일로 제공받아 사용합니다.
+ **애플리케이션 실행**: 실행 가능한 JAR 파일을 사용하여 자바 애플리케이션을 배포하고 실행합니다.

```bash
java -jar my-application.jar
```

---

**WAR (Web Application Archive)**

**정의**
+ WAR 파일은 웹 애플리케이션을 배포하기 위한 아카이브 파일 형식으로, 웹 애플리케이션의 모든 컴포넌트(서블릿, JSP 파일, HTML 파일, 이미지, 자바 클래스 파일 등)를 하나의 파일로 묶어 제공합니다.

**특징**

1. **압축 형식**:

+ JAR 파일과 마찬가지로 ZIP 파일 형식을 기반으로 합니다.

2. **구조**:

- **WEB-INF 디렉토리**: 웹 애플리케이션의 구성 파일과 클래스 파일이 위치합니다.
  + **WEB-INF/web.xml**: 웹 애플리케이션의 배포 설명자(Deployment Descriptor) 파일로, 서블릿 매핑, 필터 설정 등을 정의합니다.
  + **WEB-INF/classes/**: 애플리케이션의 자바 클래스 파일이 위치합니다.
  + **WEB-INF/lib/**: 애플리케이션에서 사용하는 JAR 파일들이 위치합니다.
- **웹 루트 디렉토리**: JSP, HTML, CSS, JavaScript 파일 등이 위치합니다.

3. **용도**:

+ **웹 애플리케이션 배포**: 서블릿 컨테이너(Tomcat, Jetty 등)에 배포하여 실행할 수 있는 형태로 웹 애플리케이션을 패키징합니다.

사용 예시
웹 애플리케이션 배포: WAR 파일을 서블릿 컨테이너에 배포하여 웹 애플리케이션을 실행합니다.
```bash
cp my-webapp.war /path/to/tomcat/webapps/
```

---


JAR 파일과 WAR 파일의 배포 시점과 용도는 애플리케이션의 성격에 따라 달라집니다. 이 두 가지 아카이브 형식은 각각의 목적과 상황에 맞게 사용됩니다.

**JAR 파일로 배포할 때**

**사용 시기**

1. **독립 실행형 애플리케이션**:

콘솔 애플리케이션, 데스크톱 애플리케이션 또는 백그라운드 서비스와 같이 독립적으로 실행되는 자바 프로그램의 경우 JAR 파일로 배포합니다.
이 경우, JAR 파일에 Main-Class 속성을 설정하여 실행 가능한 애플리케이션을 만들 수 있습니다.

2. **라이브러리 또는 모듈 배포**:

재사용 가능한 자바 라이브러리나 모듈을 배포할 때 JAR 파일을 사용합니다.
예를 들어, 다른 프로젝트에서 사용할 공통 유틸리티 클래스, 데이터 처리 라이브러리 등을 JAR 파일로 배포합니다.

**장점**
**간편성**: 실행 가능한 JAR 파일을 만들면, 명령어 한 줄로 애플리케이션을 실행할 수 있습니다.
**재사용성**: 라이브러리 배포 시 JAR 파일을 사용하면 다른 프로젝트에서 쉽게 의존성을 추가할 수 있습니다.

예시
독립 실행형 애플리케이션:

```bash
java -jar my-application.jar
```

라이브러리 사용:

```xml

<!-- Maven 의존성 예시 -->
<dependency>
    <groupId>com.example</groupId>
    <artifactId>my-library</artifactId>
    <version>1.0.0</version>
</dependency>
```

**WAR 파일로 배포할 때**

**사용 시기**

1. **웹 애플리케이션**:

서블릿, JSP, Spring MVC, Spring Boot 웹 애플리케이션 등 웹 기반 애플리케이션의 경우 WAR 파일로 배포합니다.
WAR 파일은 웹 애플리케이션의 모든 리소스를 포함하고, 서블릿 컨테이너(Tomcat, Jetty 등)에 배포되어 실행됩니다.

2. **웹 서비스**:
RESTful 웹 서비스, SOAP 웹 서비스 등 웹 기반 서비스를 배포할 때도 WAR 파일을 사용합니다.

**장점**
**표준화**: WAR 파일은 Java EE 표준에 맞게 설계되어, 다양한 서블릿 컨테이너와 애플리케이션 서버에서 호환됩니다.
**구성 관리**: 웹 애플리케이션의 모든 리소스와 설정 파일을 포함하므로, 배포와 구성이 용이합니다.

예시
웹 애플리케이션 배포:
```bash
# Tomcat의 webapps 디렉토리에 WAR 파일 복사
cp my-webapp.war /path/to/tomcat/webapps/
```

---

**요약**

**JAR 파일 배포**:
독립 실행형 애플리케이션 또는 라이브러리.
단일 파일로 배포 및 실행 가능.
명령줄에서 실행하거나 다른 프로젝트에서 의존성으로 추가.

**WAR 파일 배포**:
웹 애플리케이션 또는 웹 서비스.
서블릿 컨테이너나 애플리케이션 서버에 배포.
웹 애플리케이션의 구성과 리소스를 포함.

각 파일 형식은 애플리케이션의 성격에 따라 선택하여 사용하면 됩니다. 웹 애플리케이션은 WAR 파일로, 독립 실행형 애플리케이션이나 라이브러리는 JAR 파일로 배포하는 것이 일반적입니다.



참고 사이트
https://blog.naver.com/PostView.naver?blogId=haert2010&logNo=223088418758
[출처] [ Spring / Java ]  Gradle - Groovy  VS  Gradle - Kotlin 의 차이|작성자 또뇽