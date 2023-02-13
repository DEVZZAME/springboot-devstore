# 이커머스 쇼핑몰(Dev Store)

## 프로젝트 개요

| Front-end | HTML5, CSS3, Javascript, Thymeleaf |
| --- | --- |
| Back-end | Spring Boot, Spring Data JPA, Spring Security, JUnit5 |
| Database | MySQL |
| Deployment | AWS EC2, AWS RDS |
| 개발 기간 | 2022.01.11 ~ 2022.03.02 (약 7주) |
| 참여 인원 | 1인 개발 |
| 담당 구현 파트 | - 프로젝트 개발환경 구축, 설계 참여
- 로그인, 회원가입, 소셜 로그인 구현
- 해더(홈, 태그 및 계정 검색, 돋보기, 마이페이지)
- 메인 피드 페이지(구독 대상 게시물 노출, 페이징)
- 마이 페이지(프로필 및 내정보 변경, 게시물 업로드, 로그아웃, 구독 관리)
- 돋보기 페이지(Likes 기준 노출, 상대 페이지 링크)
- GitHub 레포지토리 전체 관리 |

## 프로젝트 소개

- 길지 않은 시간동안 쿠팡, 아마존과 같은 이커머스 플랫폼들은 급속도로 성장해왔습니다. 이에 따라 우리의 실생활에서 상당히 긍정적인 영향을 주고 있으며, 이커머스 플랫폼들이 갑자기 사라진다면 굉장히 불편할 것이라고 예상합니다. 하나의 이커머스 서비스가 생기기 위해서 어떤 기능들이 포함되어야 할까 고민하다 직접 이를 구현해 본 프로젝트입니다.

## 개발 중 이슈와 해결

| 문제점 | 해결책 |
| --- | --- |
| Servlet과 JSP를 사용했을 때, View에서 Java 코드를 직접 사용해 비즈니스 로직을 구현하니 코드도 복잡해지고 다소 무거워지는 문제점이 생겼었음. | Spring 에서 공식적으로 지원하는 Thymeleaf 를 사용하기로 함. 물론 Servlet를 제외시키고 JSP만 사용하는 Model1 방식이 있긴 했지만, Thymeleaf는 기본적으로 HTML 코드로 작성되어 브라우저가 불필요하거나 인식하지 못하는 부분을 건너뛰고 읽기 때문에 개발하면서 굉장히 편리했음. |
| Java 는 OOP에 맞춰 프로그래밍을 해야 한다고 알고 있었지만, 인터페이스와 상속을 제외하고는 정확히 어떻게 객체지향적으로 프로그래밍을 할 지 고민이 많았음. | Java 프로그래밍을 하면서 관계형 데이터베이스를 사용하면, 테이블에는 상속이 없기 때문에 OOP가 지켜지지 않는 문제점이 있었는데, JPA를 사용하면서 해당 문제점이 해결 되었음. 더불어 반복적인 CRUD 쿼리를 작성하지 않아도 되니 생산성이 향상되는 결과까지 가져옴. |

# Spring Boot(API Server)

### JSP(MAP)에서 Data Request → JSON으로 Response

> 
> 
- config : project configurations 관리
- domain : DB에서 Table과 Mapping
- handler : custom exception message 관리, aop를 이용해 validation
- service : business logic 처리
- util : 공통응답을 위한 util 기능 관리
- web
    - dto : 일반적인 request/response dto와 공통응답을 위한 dto를 관리
    - api : data를 응답할 controller를 관리

# JPA+QLRM(ORM)

### 반복적인 CRUD 작성과 쿼리 작성을 자동화

> 
> 
- JPA : 반복적인 CRUD 작업을 대체해 간단히 DB에서 데이터를 조회
- QLRM : JPA Native Query 결과값을 Entity가 아닌 특정 DTO로 매핑

### 의존성

- Sring Boot DevTools
- Lombok
- Spring Data JPA
- MariaDB Driver
- Spring Security
- Spring Web
- oauth2-client

# Views

- **회원가입 및 메인**

  <p align="center"><img src="https://github.com/DEVZZAME/zzameshop/blob/master/01.gif?raw=true"/></p>





- **상품 관리** 

<p align="center"><img src="https://github.com/DEVZZAME/zzameshop/blob/master/02.gif?raw=true"/></p>





- **상품 등록**

<p align="center"><img src="https://github.com/DEVZZAME/zzameshop/blob/master/03.gif?raw=true"/></p>





- **장바구니 및 로그아웃**

<p align="center"><img src="https://github.com/DEVZZAME/zzameshop/blob/master/04.gif?raw=true"/></p>
