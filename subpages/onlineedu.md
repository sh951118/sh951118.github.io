---
layout: default
---

### **Microservice Architecture**

```
참고 문헌 사항 정리
CNCF(Cloud Native Computing Foundation)

 ※ https://landscape.cncf.io/
 - 클라우드 네이티브를 구축하기 위해 상호연관된 서비스를 나타냄.
 - 해당 제품들을 조합해서 사용하면 개발 ~ 모니터링까지 사용 가능.

```
<p><img src="/assets/img/msaImplementList.png" alt="msa" height="400x" width="900px"></p>

>**Cloud Native Architecture**

```
 - 확장 가능한 아키텍처
    -> 시스템의 수평적 확정에 유연
    -> 확장된 서버로 시스템의 부하 분산, 가용성 보장(2가지 / up(하드웨어 스팩을 올림) out(서버를 여러대 놔둠))
    -> 시스템 또는 서비스 애플리케이션 단위의 패키지(컨테이너 기반, 가상의 서버기술이 핵심)
 - 탄력적 아키텍처
    -> 서비스 생성 - 통합 - 배포, 비즈니스 환경 변화에 대응 시간 단축
    -> 분활 된 서비스 구조
    -> 변경된 서비스 요청에 따라 사용자 요청 처리(동적처리)
    -> 무상태 통신 프로토콜 / 서비스의 추가와 삭제 자동 감지
 - 장애 격리(Fault isolation)
    -> 특정 서비스에 오류가 발생해도 다른 서비스에 영향 주지 않음.
```


>**MicroService와 Spring Cloud의 소개**
 - Microservice
 - 지속적인 통합(CI), ex) Jenkins, Team CI, Travis CI
 - 지속적 배포(CD), ex) Pipe line (Continuous Delivery / Continous Deployment)
 - DevOps -> 문제발생시 바로 수정해서 배포하는 과정 (Da, 구현, 테스트, 배포까지 무한 반복해줌) 
 - Containers -> 클라우드 환경에 배포하고 사용하기 위함.

<br/>

>**MicroService의 특징**
 - Challenges
 - RESTful
 - Bounded Context
 - Small Well Chosen Deployable Units
 - Configuration Management
 - Cloud Enabled
 - Dynamic Scale Up And Scale Down
 - CI/CD
 - Visibility(시각화)

```
-  Continuous Delivery -> 수동반영 / Continous Deployment -> 자동반영
-  카나리 배포 / 블루그린 배포 (※사용자가 크게 느끼지 못할 만큼 새 버전 서비스를 배포하여야 함.)
```

<br/>

>**12 Factors**

 1. BASE CODE => 각 MSA에 대한 단위코드, 버전관리 및 형상관리가 목적(코드의 통일적 관리)
 2. DEPENDENCY ISOLATION => 자체 종속성을 가지고 있어서 전체 코드에 영향을 주지않고 수정할 수 있어야 함.
 3. CONFIGURATIONS => 구성정보 즉, 코드의 외부에서 코드 안에 설정되어 있는 설정코드나 시스템 외부에 필요한 작업 관리도구
 4. LINKABLE BACKING SERVICES => 서비스 지원, (캐싱, 메세지, 브로커) 등 MSA가 가져야 할 추가 기능을 상호가능
 5. STAGES OF CREATION => Build, Release, Run(실행환경)을 분리, 배포를 하는 과정까지 엄격하게 분리 해야 함.(ROLLBACK)
 6. STATELESS PROCESSES => MS(MicroService)는 다른 MS와 독립적으로 실행하여야 함. 필요한 자원은 캐시나 DB를 통해서 동기화
 7. PORT BINDING => 각각의 MS는 노출되는 PORT에 각각의 기능이 있어야 함.
 8. CONCURRENCY => 많은 수의 수많은 동일한 프로세스를 복사해서 확장. 하나의 서비스가 동일한 형태로 복사(동시성)
 9. BISPOSABILITY => 인스턴스 자체가 삭제 가능해야 함. 정상종료 가능 및 확장성 기회가 높아야 함.
 10. DEVELPMENT & PRODUCTION PARITY => 개발/생산 단계를 구분해야 함.
 11. LOGS => MS안에서 생성된 로그를 이벤트 스트림으로 처리 / 로그를 출력하는 로직은 어플리케이션이 실행하지 않더라도 실행 되어야 함, 모니터링 도구를 활용
 12. ADMIN PROCESSES FOR EVENTUAL PROCESSES => 운영되고 있는 모든 MS는 어떻게 실행되는지 리소스 파악이 필수(리포팅 및 데이터 분석기술 필요)
 (아래, 3가지 항목 추가)
 13. API first => 어떤 형태로 쓸건지 고민해서 사용
 14. Telemetry => 모든 항목은 시각화
 15. Authentication and authorizaion => 인증관련 부분은 필수가 되어야 함(추가로 어떤 서비스라도 데이터 교환이 가능해야 함.)

<br/>

 >**Monolith vs Microservice**
  - Monolith 방식이란?
    -> 하나의 SW안에서 모든 비즈니스 및 데이터 관련 / 프론트까지 하나의 애플리케이션에서 작동(패키징 및 의존성)
  - Microservice 방식이란?
    -> 서비스를 분리시켜놓은 방식, 유지보수나 변경사항에 유리하고 서비스 전체가 다운되는 현상이 없음.

| Monolith                  | Microservice               |
|:--------------------------|:---------------------------|
| Frontend                  | Frontend - Team            |
| Backend                   | Bckend   - GraphQL, 생산, 배송, 구매 Team|
| DataBase                  | DataBase                   |
| 모두 하나의 팀으로 이루어짐| 여러개의 분할된 팀으로 이루어짐|

<br/>

 >**SOA와 MSA 차이점**

  - SOA - 재사용을 통한 비용 절감<br/>
          공통의 서비스를 ESB에 모아 사업 측면에서 공통 서비스 형식으로 서비스 제공
  - MSA - 서비스간의 결합도를 낮추어 변화에 능동적으로 대응<br/>
          각 독립된 서비스가 노출된 REST API를 사용

```
    RESTful Web Service (최소한 LEVEL2까지 표출)

 - LEVEL0
   - http://server/getPosts -> 기본적인 리소스를 웹 서비스 상태로 URL만 매핑한 형태

 - LEVEL1
   - http://server/accounts/10 -> 웹으로 공개하기 위해 의미있는 리소스 표현한 URL 하지만, 작업의 종류로 http메서드로 사용하지 않음

 - LEVEL2
   - LEVEL1 + HTTP -> get/post/put/delete(CRUD) 등 리소스의 상태까지 표현한 단계  
   
 - LEVEL3
   - LEVEL2 + HATEOAS(헤테오스) -> 데이터를 가지고 그 다음 작업에서 어떠한 엑션을 할 수 있는지 상태 정보를 같이 넘겨줌.
```

 - Response Status
    1. 200 / 300 - 정상 성공 코드
    2. 404 - 클라이언트가 요청한 데이터가 없는 경우
    3. 500 - 서버의 오류사항

 - Use plurals(복수형태의 URI값 사용)
    1. prefer / users to / user
    2. prefer / users / 1 to / user / 1

