# 데이터베이스 설계

## 데이터베이스 설계 순서

1\) 논리 데이터베이스 모델(ERD) 설계

2\) 상관 모델링 작성

3\) 테이블 정의서 작성

## 1. 논리 데이터베이스 모델(ERD) 설계

#### : 현실 세계를 관찰, 분석하여 개념적 모델 (ERD)를 만드는 과정으로, '데이터 모델링' 이라고도 합니다.

![26개 엔터티 중 일부](<../../../.gitbook/assets/image (31) (1).png>)

####

* 사용 tool : DA#
* 표기법 : Barker 표기법

&#x20;  → **현재 DAP 시험의 표기법으로 채택**되어 사용중이기에 Barker 표기법으로 설계했습니다.

* 총 엔터티 : 26개



#### 화면 속 엔티 설명(왼쪽 상단 '의뢰 정보'부터)

1\) '의뢰 정보'는 '회원'인 사용자와 해결사 모두의 정보를 포함하며, 각각의 회원은 여러 '의뢰 정보'를 가질 수 있기 때문에 회원 : 의뢰 정보 = 1 : 다 관계로 만들었습니다.&#x20;

속성인 '의뢰 상태'는 크게 5가지 상태로 구분했으며, 실질적으로 이용자 혹은 청소 해결사에게 일어날 수 있는 상황에 따라 범주화 해, 만들었습니다.

2\) 의뢰 상태가 '완료'일 때에 한 해, 의뢰 첨부파일을 등록하며, 여러 사진을 등록할 수 있기 때문에 '의뢰 정보' : '의뢰 첨부파일' = 1 : 다 관계로 만들었습니다.

3\) '의뢰 정보'는 여러 종류의 '의뢰 간접비'를 가질 수 있으므로(ex. 부가세, 중개비 등) 역시 1 : 다 관계로 만들었습니다.

4\) 하나의 의뢰는 상태가 지속적으로 바뀌므로 '의뢰 정보'와 '의뢰 상태 관리'의 관계는 1:다 관계로 설정했습입니다.



아직 미숙했기 때문에 여러 차례에 걸쳐 모델링 작업을 새롭게 진행했었습니다.

가장 어려웠던 부분은 유도 속성을 적게 정의하는 것이었습니다. 데이터의 정합성을 유지하기 위해 최대한 적게 정의해야 했습니다. 하지만 유도 속성과 기본 속성을 구분하는 것도 익숙지 않아 팀원들 간에 의견이 달랐고, 시간이 많이 소요됐던 부분입니다.   &#x20;

변화 과정 및 전체 ERD는 아래의 링크에서 확인하실 수 있습니다.

{% embed url="https://www.notion.so/ERD-c3cbe4f6f0e5442bbbdfd85707ac2144" %}

## 2. 상관 모델링 작성

: DB를 구축하기 위해, 행위들 간의 상관 관계를 분석하는 방법을 상관 모델링이라고 합니다.

![](<../../../.gitbook/assets/image (6).png>)

C : Create

R : Read

U : Update

D : Delete

로 단위 프로세스가 엔티티 타입에 어떤 행위(C,R,U,D)를 하는지 표기하는 것입니다.



**'의뢰 관리' 상관 모델링 설명 예시**

* 사용자 의뢰 등록 행위 시 : 의뢰 정보, 의뢰 상태, 의뢰 변경 내역 엔티티에 create됨
* 해결사 의뢰 매칭 행위 시 : 의뢰 상태 엔티티는 update, 의뢰 변경 내역 엔티티는 create 됨



전체 상관 모델링은 아래의 링크에서 확인하실 수 있습니다.

{% embed url="https://www.notion.so/48ee6a7175bc42ad9d7b0a9afeddd7ed" %}

## 3. 테이블 정의서 작성

: 각 테이블의 컬럼명, 컬럼ID, 데이터타입, 길이 등 모든 조건을 상세히 정하는 작업입니다.

![](<../../../.gitbook/assets/image (44) (1).png>)

테이블 정의서 작성 후, 팀원들 모두 검토하며 더블 체크했습니다.&#x20;

이렇게 모든 테이블의 상세 정보를 지정 후, 그대로 DB를 구축했습니다.



자세한 내용은 아래의 링크에서 확인하실 수 있습니다.

{% embed url="https://www.notion.so/9232ecc91f104f0ea9172463f4d72f5f" %}

설계 과정은 예측하여 작성한 것이었고, 저희는 배우는 과정이다 보니 구현 중에도 수정하는 경우가 여러 번 있었습니다.&#x20;

수정을 최소화하기 위해 최대한 꼼꼼하게 설계하는 것이 중요하다는 점을 느꼈습니다.

