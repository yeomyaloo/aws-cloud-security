# aws-cloud-security
AWS 클라우드 환경에서의 보안 요소를 고려한 구축 방법에 대한 레포지토리 입니다.
  
## IAM Service
1. `IAM (Identity and Access Managenment)`
    1. 사용자 계정관리 개별 IAM계정을 만들어 사용자별로 AWS 보안 자격 증명을 부여
![image](https://github.com/user-attachments/assets/e2eb5389-094f-4c8c-b7b3-79d23d55224d)
- AWS는 계정별로 사용 가능한 권한이 다르다.
- 기본적으로 ROOT 계정이 제일 최상단 권한을 가진 계정이다. 그러나 이 계정을 이용해선 인프라 구성을 하지 않는다.(진짜로 안 해요)
- IAM 서비스 계정을 만든 뒤 해당 계정의 역할(Role)이나 정책(Policy)를 주어서 권한을 제한하는 식으로 진행한다.
  - 예를 들면 S3 사용 시 해당 S3 사용 권한을 따로 부여하는 식으로 진행한다. 
### 그룹별 최소 권한 확인
![image](https://github.com/user-attachments/assets/389a4fd8-7795-4d35-9474-361542c2a58c)
- Dev / Network Group 등에 Admin 권한을 부여하지 않도록 한다.
- IAM Full 권한은 운영자만 가질 수 있도록 한다.
    - 예를 들면 엔지니어링 과정 중에 사용한 IAM 계정을 난 사용했지만 ADMIN 계정은 아니었다.
- IAM Service 사용 시 그룹을 만들거나 하는 등의 작업을 할수 있다.
- 이때 권한을 부여하거나 할때 그룹별로 부여하는 게 가장 관리하기 효과적이다.
- 하나씩 권한이나 정책 부여를 하면 계정당 이를 관리해야해서 귀찮아진다.
### 3. AWS 계정은 AWS 자원 격리 공간이다.
- IAM 계정을 사용해야 서비스, 자원 등을 사용할 수 있다.

### 4. Role VS Policy
- IAM Role: 임시 자격 증명
- User Policy 부여: 상시 적용 ~> 결과적으로 보안에 매우 취약
- 권한 부여와 관련해서 만료 기간 차이가 있음을 제대로 파악하자 

### 5. 여러개의 정책 부여?
- 여러개의 정책을 부여하는 경우엔 교집합으로 적용된다.
- `최소 권한`이 부여 됨을 알수 있다.

## NACL VS Security group

## ALB VS NLB

## SSH

## SSL / TLS 

## ACM 

## Role vs policy



## WAF
### WAF란?
- 기존 방화벽(*FW = FireWall)의 웹 특화 버전인 Web firewall WAF는 웹 애플리케이션 또는 API에 대한 악의적인 요청을 필터링합니다.
- 또한 트래픽 발생 지점에 대한 가시성을 높이고 Layer 7 배포된 서비스 거부(DDoS) 공격을 완화하여 애플리케이션 가용성을 확보하고 규정 준수 지시를 더욱 효과적으로 적용할 수 있습니다
```
웹 애플리케이션 방화벽은 봇, 삽입, 애플리케이션 계층 서비스 거부(DoS)를 비롯한 악의적 공격과 원치 않는 인터넷 트래픽으로부터 웹 애플리케이션을 보호할 수 있도록 지원합니다.
WAF를 사용하면 IP 주소, HTTP 헤더, HTTP 본문, URI 문자열, 교차 사이트 스크립팅 (XSS), SQL 삽입 및 기타 OWASP 정의 취약성을 비롯한 인터넷 위협을 방지하기 위한 규칙을 수립하고 관리할 수 있습니다.
웹 애플리케이션 방화벽은 웹 연결 애플리케이션을 보호하고 규정 준수와 분석을 위한 액세스 로그를 수집하기 위해 배포됩니다.
```
### WAF 설정 방법(아키텍처 편)


### WAF와 ALB(부제: 7L ALB 장비와 함께..) 

### 정책 
---------------
- 클라우드 엔지니어 기술 면접 준비

    
## Cloud

### **클라우드란?**

• 클라우드 컴퓨팅 또는 클라우드 서비스를 줄인 말
• 클라우드 컴퓨팅(cloud computing)
    ◦ 인터넷 기반 컴퓨팅의 일종으로 정보를 자신의 컴퓨터가 아닌 인터넷에 연결된 다른 컴퓨터로 처리하는 **기술**
• 개인 사용자를 위한 클라우드
    ◦ 내가 내 돈으로 직접 컴퓨터를 사지 않고, 서비스로 제공 받는 것
• 기업을 위한 클라우드
    ◦ 기업이 물리적인 컴퓨터(서버)를 사지 않고, 소비스로 제공 받는 것

### **클라우드의 장점?**

• 가격 (가격보다는 탄력성과 안정성이 중요)
• 탄력성과 확장성
    ◦ 서비스 규모에 맞게 IT 인프라를 확장/축소할 수 있는가?
• 안정성
    ◦ 다운타임/유지보수시간을 최소화하고 서비스가 정상적으로 유지되는가?
• 내구도
    ◦ 오류 및 사고발생 시점에 데이터가 안전하게 저장되는가?
****

### **왜 클라우드를 사용할까요?**

• 외부에서 본인이 만든 서비스에 접근하려면 24시간 작동하는 서버가 필수
    ◦ 집에 PC를 24시간 구동시키거나
    ◦ 호스팅 서비스를 이용하거나(Cafe24, 코리아 호스팅)
    ◦ 클라우드 서비스를 이용할 수 있음(AWS, AZURE, GCP)
• 비용은 집이나 호스팅 서비스를 이용하는 것이 저렴하지만 특정 시간에만 트래픽이 몰린다면 유동적으로 사양을 늘릴 수 있는 **클라우드**가 유리
• 인터넷(클라우드)을 통해 서버, 스토리지, DB, 네트워크, 소프트웨어, 모니터링 등의 컴퓨팅 서비스를 제공하는 것
• 클라우드의 형태
    ◦ IaaS(Infrastructure as a Service)
        ▪ 기존 물리 장비를 미들웨어와 함꼐 묶어둔 추상화 서비스
        ▪ 가상머신, 스토리지, 네트워크, 운영체제 등의 IT 인프라를 대여해주는 서비스
        ▪ ex. AWS 사용 시
            • 컴퓨팅: EC2
            • 스토리지: EBS
            • 네트워크: VPC
    ◦ PaaS(Platform as a Service)
        ▪ IaaS에서 한 번 더 추상화한 서비스
        ▪ 많은 기능이 자동화
        ▪ ex. AWS의 Beanstalk, Heroku
    ◦ SaaS(Software as a Service)
        ▪ 소프트웨어 서비스
        ▪ 구글 드라이브, 드랍박스, 와탭
**클라우드 서비스 제공업체**
• AWS
• Google
• Azure
• Pivotal, Heroku, Digital Ocean, …
• 네이버, NHN Enter, …
• KT, …

## **AWS**
### AWS 주요 서비스들
- 계정관리: IAM
- 컴퓨팅: EC2, Lambda, ECS
- 네트워크: VPC, Route53, CloudFront
- 저장: S3
- 데이터베이스: RDS
- 모니터링: CloudWatch, CloudTrail
- 기타: SNS, SES, SQS, CloudFormation

### AWS IAM
- 인증 관련 기능 제공 서비스
- AWS에서 제공하는 서비스의 접근 방식과 권한 관리
- 역할
  - AWS 서비스에만 할당할 수 있는 권한
  - EC2, CodeDeploy, SQS 등
- 사용자
  - AWS 서비스 외에 사용할 수 있는 권한
  - 로컬 PC, IDC 서버 등

### AWS EC2
- Elastic Compute Cloud
- AWS에서 제공하는 성능, 용량 등을 유동적으로 사용할 수 있는 서버

### AWS RDS
- AWS에서 지원하는 클라우드 기반 관계형 데이터베이스
- 하드웨어 프로비저닝, 데이터베이스 설정, 패치 및 백업과 같이 잦은 운영 작업을 자동화하여 개발자가 개발에 집중할 수 있게 지원하는 서비스
- 조정 가능한 용량을 지원하여 예상치 못한 양의 데이터가 쌓여도 비용 추가로 서비스 이용 가능

### Amazon S3
- Simple Storage Service
- 객체 저장소(Object Storage): 파일 단위로 저장
- 99.999999999% 내구성
- 높은 가용성
- 저장 용량에 제한이 없어서 무제한으로 저장 가능
- SSD 서비스(EBS) 보다 저렴
- 주로 비즈니스용, 앱개발용으로 사용됨
- 가용성: 서비스가 항상 사용 가능한지 나타내는 지표
- 내구성: 데이터가 안전하게 저장되는지를 나타내는 지표
- AWS의 스토리지 서비스
  - EBS: EC2와 연결해서 사용하는 SSD 같은 서비스
  - S3: 드롭박스처럼 파일 업로드 / 다운로드가 가능한 인터넷 저장 서비스
### AWS Route 53
- AWS 에서 제공해 주는 DNS 서비스
- 저렴하고 100% 가용성을 보장해 준다.
### AWS SQS
- Simple Queue Service
- 마이크로 서비스와 분산 시스템, 그리고 서버리스 애플리케이션을 쉽게 분리하고 확장할 수 있는 ‘완전관리형 메시지 대기열 서비스’
- 높은 확장성과 신뢰성을 가진 큐를 제공하는 서비스
- micro service 간에 메시지들을 안정적으로 저장 및 전달
- SQS에서 메시지는 삭제명령으로 삭제 될 때까지 큐 안에서 유지
- 한 번 전달된 메시지는 일정 시간동안 다시 처리되지 않도록 구성
  - 작업메시지들을 저장해 놓는 작업 대기열의 큐로 사용될 수 있음
  - ⚠️ 일반 Queue의 경우에는 고가용성의 보장을 위한 구조로 인해 하나의 메시지가 동시에 여러 번 호출될 수도 있음

## MSA(Micro Service Architecture)**
- 애플리케이션을 작은 서비스로 나누어 개발하는 아키텍처 스타일
- 개별 서비스를 독립된 프로세스로 실행하고 각 서비스가 REST API나 메시징을 이용해서 통신하는 구조
- 각 BOUNDED CONTEXT를 MSA로 구현하면 자연스럽게 컨텍스트 별로 모델이 분리되면서 별도의 프로세스로 마이크로 서비스마다 프로젝트가 생성되며 이를 독립적으로 배포하고 모니터링하고 확장할 수 있음

### MSA의 장점은 무엇인가? 기존 방식에 비해 어떤 Benefit을 가져올 수 있는가? 이에 따른 단점이나 리스크가 있는가?
#### 장점
• 배포
    ◦ 서비스별 개별 배포가 가능(배포 시 전체 서비스의 중단이 없음)
    ◦ 특정 서비스의 요구사항만을 반영하여, 빠르게 배포 가능
• 확장
    ◦ 특정 서비스에 대한 확장성(scale-out)이 유리
    ◦ 클라우드 기반 서비스 사용에 적합
• 장애
    ◦ 일부 장애가 전체 서비스로 확장될 가능성이 적음
    ◦ 부분적으로 발생하는 장애에 대한 격리가 수월함
• 그 외
    ◦ 새로운 기술을 적용하기 유연함(전체 서비스가 아닌 특정 서비스만 별도의 기술 또는 언어로 구현 가능)
    ◦ 각각의 서비스에 대한 구조 파악 및 분석이 모놀리식 구조에 비해 쉬움
#### 단점
- 설계의 어려움
  - Monolithic에 비해 상대적으로 많이 복잡함
  - 서비스가 모두 분산되어 있기 때문에 개발자는 내부 시스템의 통신을 어떻게 가져가야 할지 정해야 함
  - 통신의 장애와 서버의 부하 등이 있을 경우 어떻게 transaction을 유지할지 결정하고 구현해야 함
- 성능
  - 서비스 간 호출 시 API를 사용하므로, 통신 비용이나 Latency에 대해 이슈가 존재
- 테스트/데이터 트랜잭션
  - MSA에서는 비즈니스에 대한 DB를 가지고 있는 서비스도 각기 다르고, 서비스의 연결을 위해서는 통신이 포함되기 때문에 트랜잭션을 유지하는게 어려움
  - 통합 테스트가 어려움
  - 개발 환경과 실제 운영환경을 동일하게 가져가는 것이 쉽지 않음
- 데이터 관리
  - 데이터가 여러 서비스에 분산되어 있어 조회하기 어려움
  - 데이터를 관리하기 어려움

## Load Balancer
- 서버에 가해지는 부하(=로드)를 분산(=밸런싱)해주는 장치 또는 기술을 통칭
- 클라이언트와 서버풀(Server Pool, 분산 네트워크를 구성하는 서버들의 그룹) 사이에 위치하며, 한 대의 서버로 부하가 집중되지 않도록 트래픽을 관리해 각각의 서버가 최적의 퍼포먼스를 보일 수 있도록 함
### Scale-up / Scale-out
- 증가한 트래픽에 대처하기 위해 인프라를 업그레이드 하는 방법
### Scale-up
- 스케일 업(Scale-up)은 기존의 서버를 보다 높은 사양으로 업그레이드하는 것
  - ex. 하드웨어 - 성능이나 용량 증강을 목적으로 하나의 서버에 디스크를 추가하거나 CPU나 메모리를 업그레이드시키는 것
  - ex. 소프트웨어 - AWS의 EC2 인스턴스 사양을 micro에서 small, small에서 medium 등으로 높이는 것으로 생각
- 하나의 서버의 능력을 증강하기 때문에 수직 스케일링(vertical scaling)이라고도 함
### Scale-out
- 스케일 아웃(Scale-out)은 장비를 추가해서 확장하는 방식
- 기존 서버만으로 용량이나 성능의 한계에 도달했을 때, 비슷한 사양의 서버를 추가로 연결해 처리할 수 있는 데이터 용량이 증가할 뿐만 아니라 기존 서버의 부하를 분담해 성능 향상의 효과를 기대할 수 있음
- 서버를 추가로 확장하기 때문에 수평 스케일링(horizontal scaling)이라고도 불림
- 클라우드 서비스에서는 자원 사용량을 모니터링하여 자동으로 서버를 증설(Scale Out)하는 Auto Scaling 기능도 있음

## 로드 밸런싱 알고리즘
### 라운드로빈 방식(Round Robin Method)
- 서버에 들어온 요청을 순서대로 돌아가며 배정하는 방식
- 클라이언트 요청을 순서대로 분배하기 때문에 여러 대의 서버가 동일한 스펙을 갖고 있음
- 서버와 세션이 오래 지속되지 않는 경우에 활용하기 적합
### 가중 라운드로빈 방식(Weighted Round Robin Method)
- 각각의 서버마다 가중치를 매기고 가중치가 높은 서버에 클라이언트 요청을 우선적으로 배분
- 주로 서버의 트래픽 처리 능력이 상이한 경우 사용되는 부하 분산 방식
### IP 해시 방식(IP Hash Method)
- 클라이언트의 IP 주소를 틍정 서버로 매핑하여 요청을 처리하는 방식
- 사용자가 항상 동일한 서버로 연결되는 것을 보장
### 최소 연결 방식(Least Connection Method)**
- 요청이 들어온 시점에 가장 적은 연결 상태를 보이는 서버에 우선적으로 트래픽 배분
- 자주 세션이 길어지거나 서버에 분배된 트래픽들이 일정하지 않은 경우에 적합한 방식
### 최소 리스폰타임(Least Response Time Method)
- 서버의 현재 연결 상태와 응답시간(Response Time, 서버에 요청 보내고 최초 응답 받을 때까지 소요되는 시간)을 모두 고려하여 트래픽 배분
- 가장 적은 연결 상태와 가장 짧은 응답시간을 보이는 서버에 우선적으로 로드를 배분하는 방식

## L4, L7 로드밸런서
- 부하 분산에 가장 많이 활용되는 로드밸런서
- L4 로드밸런서부터 포트(port)정보를 바탕으로 로드를 분산하는 것이 가능
- 한 대의 서버에 각기 다른 포트 번호를 부여하여 다수의 서버 프로그램을 운영하는 경우라면 최소 L4 이상
- L4, L7
  - OSI Layers 각각의 계층을 의미(이건 알아야 됨)
    - L1 : 물리 (피지컬) 계층
    - L2 : 데이터링크 계층
    - L3 : 네트워크 계층
    - L4 : 전송 (트랜스포트) 계층
    - L5 : 세션 계층
    - L6 : 표현 (프레젠테이션) 계층
    - L7 : 응용 (애플리케이션) 계층
  - 낮은 계층일 수록 물리/반대로 높은 계층일수록 논리적
  - 상위 계층에서 사용되는 장비는 하위 계층의 장비가 갖고있는 기능을 모두 가지고 있음, 상위로 갈수록 정교한 로드밸런싱 가능
![image](https://github.com/user-attachments/assets/af18936e-c92a-4c56-8fcf-c8fe74ff504e)
![image](https://github.com/user-attachments/assets/ca58a890-876c-4838-ba7a-360a1521110d)


### L4 로드밸런서
- 네트워크 계층(IP/IPX)이나 트랜스포트 계층(TCP/UDP)의 정보를 바탕으로 로드를 분산
- IP주소나 포트번호, MAC주소, 전송 프로토콜에 따라 트래픽을 나누는 것이 가능
- 장점
  - 데이터 안을 들여다보지 않고 패킷 레벨에서만 로드를 분산 => 속도가 빠르고 효용이 높음
  - 데이터의 내용을 복호화할 필요가 없기 때문에 안전
  - L7보다 저렴
- 단점
  - 패킷의 내용을 살펴볼 수 없기 떄문에 섬세한 라우팅 불가능
  - 사용자의 IP가 수시로 바뀌는 경우라면 연속적인 서비스를 제공하기 어려움
**L7 로드밸런서**
- 애플리케이션 계층(HTTP, FTP, SMTP)에서 로드를 분산하기 때문에 HTTP헤더, 쿠키 등과 같은 사용자의 요청을 기준으로 특정 서버에 트래픽을 분산하는 것이 가능
- 패킷의 내용을 확인하고 그 내용에 따라 로드를 특정 서버에 분배하는 것이 가능
- URL에 따라 부하를 분산시키거나, HTTP 헤더의 쿠키값에 따라 부하를 분산하는 등 클라이언트의 요청을 보다 세분화해 서버에 전달할 수 있음
- 장점
  - 상위 계층에서 로들르 분산하기 떄문에 훨씬 더 섬세한 라우팅 가능
  - 캐싱 기능 제공
  - 비정상적인 트래픽을 사전에 필터링할 수 있어 서비스 안정성이 높음
  - 특정한 패턴을 지닌 바이러스를 감지해 네트워크 보호할 수 있음
  - DoS/DDos와 같은 비정상적인 트래픽 필터링할 수 있어 네트워크 보안 분야에서도 활용
- 단점
  - 패킷 내용 복호화 해야해서 비용 비쌈
  - 클라이언트가 로드밸런서와 인증서 공유 -> 공격자가 로드밸런서 통해서 클라이언트 데이터에 접근할 위험

## Proxy
- 프록시 서버: 클라이언트가 자신을 통해 다른 네트워크 서비스에 간접적으로 접속할 수 있게 해주는 컴퓨터 시스템이나 응용 시스템
- 서버 & 클라이언트 사이의 중계기로서 대리로 통신을 수행하는 것
- 프록시 서버를 사용하면 보안, 성능, 안정성 향상 가능
- Forward Proxy Server / Reverse Proxy Server
### Forward Proxy
- 클라이언트 앞에 놓여있음
- 클라이언트가 인터넷 웹 서버를 요청을 보내면 그 요청을 프록시 서버가 가로챔 -> 해당 요청을 웹 서버에 다시 보내고 그 응답을 다시 클라이언트에 전달
- 정부, 학교, 기업 등과 같은 기관에서 제한적인 인터넷 사용을 위해 방화벽 사용하는 등 방문하고자 하는 웹 사이트에 직접적으로 방문하는 것을 방지
- 기관에 속한 유저가 특정 컨텐츠에 접근하는 것을 방지하는데 사용
- 유저의 정체를 숨겨줌 -> IP 주소를 역추적해도 프록시 서버만 보임
### Reverse Proxy
- 웹 서버 앞에 놓여있음
- 로드 밸런싱에 사용 -> 대량 트래픽으로 특정 서버가 과부화 되지 않도록
- 본래 서버의 IP 주소 노출되지 않아 DDos 공격을 막는 등 보안에 좋음
- CDN과 같은 리버스 프록시 서버가 공격의 타겟이 될 수는 있음
- 캐시데이터를 저장할 수 있음 => 성능상의 이점
- SSL 암호화에 좋음
  - 들어오는 요청을 모두 복호화, 나가는 응답을 암호화 => 안전한 통신 가능

## 컨테이너
Virtual Machine vs Container
Virtual Machine(VM)**
- Server -> Hypervisor -> Guest OS
- OS를 각각 설치하기 때문에 리소스 낭비가 있습니다.
### Container
- 어플리케이션을 구동하는 환경을 격리한 Space
- Server -> Docker Engine -> Container
- VM에 비해 오버헤드가 적습니다.
### 컨테이너를 사용하면 얻을 수 있는 장점?
- Guest OS가 따로 없는 형태라서 경량화 되어 있고(가볍고) 또 어떤 환경에서도 동일하게 사용 가능하다 VM의 경우엔 하이퍼바이저 위에 Guest OS가 또 따로 있기 때문에 다른 곳에서도 해당 환경과 동일하게 구성해야 동작한다는 문제가 있다.(도커는 이 문제를 해결하기 위해 나옴)
- Environment Disparit
- 기능별로 모듈화를 할 수 있어 MSA를 구축할 수 있습니다.
- 언어와 프레임워크 상관없이 동일한 프로세스를 가질 수 있습니다.
- VM 대비 컨테이너 생성이 쉽고 빠릅니다.
- 컨테이너 이미지를 이용한 배포, 롤백이 간단합니다.
- 특정 클라우드 벤더(AWS, GCP…)에 종속적이지 않습니다. (멀티 클라우드도 가능)
### 컨테이너를 위한 운영 환경에는 어떠한 것들이 있는가? 가장 많이 사용되는 것은 무엇인가?
- MSA를 구축하면서 한 번에 여러 개의 컨테이너를 관리할 필요가 생깁니다
- 어느 서버가 비어있는지 어떻게 알 수 있을까?
- 배포와 롤백은 어떻게 할 수 있을까?
- Service Discovery, Monitoring을 어떻게 할 수 있을까?
- Kubernetes!

## 쿠버네티스 Kubernetes
쿠버네티스가 가장 선호되는 이유가 무엇이라고 생각하는가?
- 컨테이너를 쉽고 빠르게 배포/확장하고, 관리를 자동화하는 오케스트레이션 툴입니다.
- 많은 수의 컨테이너를 협조적으로 연동시키기 위한 통합 시스템, 이 컨테이너를 다루기 위한, API 및 명령행 도구(kubectl) 등이 함께 제공됩니다.
- 컨테이너의 운영체제 같은 것
- Google의 주도로 개발, CNCF가 관리합니다. 컨테이너 오케스트레이션의 사실상 표준(de facto)입니다.
- 컨테이너를 이용해 애플리케이션을 개발합니다.
- 도커 호스트를 관리합니다.
- 서버 리소스의 여유를 고려해서 컨테이너를 배치합니다.
- 스케일링
- 여러 개의 컨테이너 그룹에 대한 로드 밸런싱을 지원합니다.

## Fault-tolerant(무정지) 시스템으로 가기 위해 필요한 방법에 대한 생각을 말해주세요.**
- 기본적으로 서버는 물리적/소프트웨어적으로 이중화(Server/DB)
- 다운 타임이 발생하지 않도록 두 대 이상의 서버를 서비스
- 비용 절감을 위해 배포할 때에만 새롭게 서비스를 띄우고, 배포가 완료된 후에는 기존 서버는 shut-down
### 무정지 배포 방법 Rolling
- 로드 밸런서에서 서버를 빼고, 배포하고 다시 넣는 작업이 각 서버마다 이루어지도록 함
- 단점
  - 배포할 서버가 너무 많다면, n대 단위로 배포하기도 하는데 배포가 모두 끝나기 전까지 클라이언트 중 누구는 이전 서비스를 제공 받고 누구는 신규 서비스를 제공 받게 되는 문제가 발생
  - 1대에 배포하는 것보다 최소 2배 이상 느립니다.
### 무정지 배포 방법 Canary
- 소수의 유저(혹은 사내)만 사용하는 환경(Canary 환경)에 신규 버전을 배포하고 문제가 없다고 판단됐을 때 다른 모든 서버에 배포
### 무정지 배포 방법 Blue/Green
- 실제로 서비스 중인 환경(Blue)과 새롭게 배포할 환경(Green)을 세트로 준비해서 배포하는 형식
- 새롭게 배포할 환경에만 배포하면 되기 때문에 배포 속도가 매우 빠르며, 언제나 Green 환경이 실행 중이기 때문에 만약 잘못된 버전으로 배포 했을 경우 신속하게 롤백이 가능합
- 단점
  - Green 환경이 항상 실행 중이어야 하기 때문에 비용이 많이 발생

## CI/CD
CI/CD가 무엇인가요? 왜 CI/CD가 장점이 될까요?**어떤 CI/CD를 써봤는지 툴을 설명하고 그 툴의 장단점을 설명
### CI
- 지속적 통합 continuous integration
- 코드 버전 관리를 하는 VCS 시스템에 push가 되면 테스트와 빌드가 수행되어 안정적인 배포파일을 만드는 과정
- 개발자가 작업한 코드를 자동으로 테스트 하고 테스트에 통과하면 코드를 통합하여 저장
### CD
- 지속적 배포 continuous delivery or continuous deployment
- 빌드 결과를 자동으로 운영 서버에 배포까지 되는 과정을 CD
- 푸시가 될 때마다 코드를 병합하고, 테스트 코드와 빌드를 수행하면서 자동으로 코드가 통합되어 더는 수동으로 코드를 통합할 필요가 없어져 개발에만 신경을 쓸 수 있음
- 작업한 코드 및 변경사항들을 테스트를 거쳐 리포지토리로 업그레이드 되고 실 서비스 배포로 릴리즈 까지 자동화 하는 것

## DevOps
- 애플리케이션 개발-운영 간의 협업 프로세스를 자동화하는 것 -> 결과적으로 애플리케이션의 개발과 개선속도를 빠르게 함
- DevOps는 애플리케이션과 서비스를 빠른 속도로 제공할 수 있도록 조직의 역량을 향상시키는 문화와 방식이며 자동화, 측정, 공유를 수행하고 이 모든 것들을 축적해나가는 것
- DevOps를 수행하면, 기존의 개발 및 인프라 관리 프로세스를 사용하는 조직보다 제품을 더 빠르게 혁신하고 개선할 수 있음 => 고객 친화적이고, 시장에 효과적으로 대응할 수 있는 유연성을 얻을 수 있음[←](https://suhyunsim.github.io/2022-12-24/Tips-For-System-Design-Interview)[→](https://suhyunsim.github.io/2022-10-16/%EA%B8%80%EB%98%90%ED%9B%84%EA%B8%B0)[Top](https://suhyunsim.github.io/2022-12-08/%EC%9D%B8%ED%94%84%EB%9D%BC-%ED%81%B4%EB%9D%BC%EC%9A%B0%EB%93%9C-%EB%A9%B4%EC%A0%91%EC%A7%88%EB%AC%B8#)

