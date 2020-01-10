[설계] 데이터 모델링의 주요 개념
===================================
## 3.1 개요
- 논리적 DB 설계 : 현실세계의 업무를 분석, 이를 약속된 표기법을 이용하여 개념적 모델(ERD)로 표현하는 과정
- 데이터 모델링에서는 약속된 개념들로 현실세계를 표현한다. (엔티티,속성,관계 등...)
- 데이터 모델링의 최종 산출물은 ERD이다.
- 데이터베이스와 모델링 용어의 대비표
> |DB 용어| 용어 |
> |------|---|
> |테이블(table)|엔티티(entity)|
> |컬럼(column),열|속성(attribute)|
> |튜플(tuple),행(row)|인스턴스(instance)|
> |기본키(primary key)|주식별자(primary identifier)|
> |외래키(foreign key)|외래식별자(foreign identifier)|

## 3.2 엔티티
### 3.2.1 엔티티의 정의
- 엔티티(entity) : 업무의 관심 대상이 되는 정보를 갖고 있거나, 그에 대한 정보를 관리할 필요가 있는 유형, 무형의 사물(개체)
- 인스턴스(instance) : 엔티티내부 속성들
- 표
> |논리적 설계단계|물리적 설계단계|객체지향 개발|
> |---|---|---| 
> |엔티티|테이블|클래스|
> |인스턴스|튜플|객체|

### 3.2.2 엔티티의 분류
- 엔티티는 특성에 따라 분류 할 수 있다.
1. 유형 엔티티 : 물리적인 형태가 있고 쉽게 엔티티임을 알 수 있다.  
  ex) 고객, 사원, 상품,거래처, 학생, 교수, ...
2. 무형 엔티티 : 물리적인 형태가 없고 개념적으로 존재하는 엔티티이다.  
  ex) 생산, 계획, 부서조직, 색상별선호도, ...
3. 문서 엔티티 : 업무 절차상에서 사용되는 문서나 장부, 전표에 대한 엔티티이다.
  ex) 거래명세서, 입출금전표, 주문서, 금전출납부, ...
4. 이력 엔티티 : 업무상 반복적으로 이루어지는 행위나 사건의 내용을 일자별, 시간별로 저장하기 위한 엔티티이다.
  ex) 입고이력, 출고이력 , ...
5. 코드 엔티티 : 무형 엔티티의 일종으로 각종 코드를 관리하기 위한 엔티티이다.
  ex) 국가코드, 색상코드, 직급분류코드, 상태코드, ... 
  
### 3.2.3 엔티티의 성질
- 엔티티인지 아닌지 결정 기준에서는 성질을 만족하는지 확인한다.
1. 업무의 필요성
> 업무의 관심대상이 되는 사물이어야 한다. 업무의 관심 대상이 아니거나 업무 절차상에서 사용되지 않는다면 엔티티로 표현할 필요가 없다.
2. 두개 이상의 인스턴스 소유
> 두 개 이상의 인스턴스를 가져야 엔티티에 의미가 있다.
3. 속성의 소유
> 열, 컬럼에 해당되는 속성을 가지지 않는다면 업무분석을 제대로 하지 못했거나, 속성으로 분류해야할 것을 엔티티로 분류한 것이다.

## 3.3 속성
- 엔티티에서 관리해야 할 최소 단위의 정보 항목을 말하며 엔티티는 하나 이상의 속성을 포함한다.
- 엔티티 특성에 따른 구분
> 기본 속성 (basicattribute) : 업무 분석 과정에서 업무의 관심 대상으로 분류된 정보 항목들로 전체 속성들 중에서 가장 많은 비중을 차지한다.
> 유도 속성(derived attribute) : 다른 속성의 값들로부터 유도될 수 있는 속성
> 설계 속성 : 실제로 존재 하지 않지만 설계를 보다 효과적으로 할 수 있기 위해서, 혹은 나중에 정보 시스템이 운영될 때의 필요성 때문에 강제적으로
  만들어주는 속성
## 3.4 관계
### 3.4.1 관계의 정의
- 관계(Relationship) : 두 엔티티 사이의 관련성을 나타내는 용어
- 선으로 연결한다.
- 두 엔티티가 관계가 있다는 의미는 상호 공유하는 속성이 있다는 것
### 3.4.2 관계의 카디널리티
- 카디널리티(cardinality)는 두 엔티티간의 관계를 보다 구체적으로 표현하는 방법중 하나
- 각 엔티티에 속해 있는 인스턴스들 간에 수적으로 어떤 관계에 있는지를 나타내는 개념
- 두개의 엔티티 혹은 테이블 간의 카디널리티를 생각할 때는  
  기준이 되는 쪽 엔티티(테이블)의 인스턴스(튜플) 1개가 상대족 엔티티(테이블)의 인스턴스(튜플)  
  몇 개와 관련성을 맺는지를 살펴보면 된다.
- 여러경우의 카디널리티
> 1. 1:1(one-to-one) : 두 엔티티를 하나로 합쳐도 되는데 어떤 이유로 해서 일부러 두 개로 나누어 놓은 경우에 해당한다.
> 2. 1:N(one-to-many)
> 3. M:N(many-to-many) : 두 엔티티가 관련이 있다는 정보를 두 엔티티만으로 표현할 수 없어   
  중간에 다른 엔티티를 필요로 한다. 따라서 1:N 관계로 전환시켜주는 작업을 필요로 한다.
### 3.4.3 관계의 참여도  
- 카디널리티의관점에서도 표현할 수 있지만 **참여도 관점**에서도 표현할 수 있다.
- 참여도에는 필수(mandatory), 선택(optional) 두 가지가 있다.
- 선택관계
> - 기준이 되는 엔티티의 인스턴스와 대응되는 인스턴스가 상대방 엔티티에 있을 수도 있고 없을 수도 있을 때
> - 카디널리티앞에 동그라미로 표시한다.
- 필수관계
> - 어느 한쪽이 존재하면 다른쪽도 반드시 존재해야하는 관계
> - 카디널리티앞에 '|'로 표시한다.
### 3.4.4 부모 엔티티와 자식 엔티티
- 상호 관계가 있는 두 엔티티는 부모-자식의 관계에 잇는 경우가 많다.
- 부모, 자식 여부는 어느 쪽에 정보가 먼저 생성이 되는가에 따라 결정된다.
- 두 엔티티가 부모-자식 관계가 있다면 **일반적**으로 부모 엔티티와 자식 엔티티의 카디널리티는 1:N이고  
  참여도는 부무 쪽이 필수, 바식 쪽이 선택을 나타난다.
- 부모엔티티 자식엔티티 카티널리티, 참여도 그림  
![부모자식관계](https://user-images.githubusercontent.com/58258024/72131632-34c0a800-33c0-11ea-8c06-22a75342ef27.PNG)

## 3.5 주식별자와 외래식별자
- 모델링에서는 '키'라는 용어 대신에 '식별자'라는 용어를 사용한다.  

|모델|관계형 모델|
|---|----------|
|주식별자(Primary identifier)|기본키(primary key)|
|외래식별자(Foreign identifier)|외래키(foreign key)|
|보조식별자|대체키(alternate key)|

- 보조식별자는 중요하지 않다.
- 주식별자와 외래식별자는 엔티티에 포함된 속성들 중에서 선택한다.
- 주식별자
> 엔티티 내에서 인스턴스와 인스턴스를 구별하는 기준
- 외래식별자
> 엔티티와 엔티티를 연결해주는 역할
- 부모 엔티티와 자식 엔티티 관계에서 자식 엔티티의 외래식별자는 부모 엔티티의 주식별자와 연결된다.
## 3.6 ERD 표기법
- ERD(entity-relationship diagram)은 오늘날 데이터 모델링에서 일반적으로 사용하는 도구