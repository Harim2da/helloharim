# 데이터베이스 설계

## 데이터베이스 설계 순서

1\) 논리 데이터베이스 모델(ERD) 설계

2\) 상관 모델링 작성

3\) 테이블 정의서 작성

## 1. 논리 데이터베이스 모델(ERD) 설계

#### 먼저, 논리 데이터 모델(ERD)를 작성했습니다.

![](<../../../.gitbook/assets/image (39) (1).png>)

* 사용 tool : DA#
* 표기법 : Barker 표기법

→ **현재 DAP 시험의 표기법으로 채택**되어 사용중이기에 Barker 표기법으로 설계했습니다.

* 총 엔터티 : 55개



#### \*엔터티 설명 (오른쪽 위부터 차례로)

1\) **'업체 기본 정보' 엔터티 **1개에는 여러 개의 '임직원 계정'이 포함됩니다. (ex.한 회사에 여러 명의 직원 有)&#x20;

&#x20;   \-> 1:다 관계

2\) **'업체 기본 정보' 엔터티** 1개는 여러 개의 '직급별 호봉'을 가질 수 있습니다.&#x20;

&#x20;   \-> 역시 1:다 관계

3\) **'직급별 호봉'**은 회사번호(FK)와 '직급별 호봉'을 식별자로 가집니다.

4\)** '직급별 호봉'**은 회사의 정책에 따라 언제든 변경될 수 있고, 변경 이력은 꾸준히 쌓이는 데이터이므로 **'직급별 호봉 변경 이력' 엔터티**와는 1:다 관계입니다. 직급별 호봉 변경 이력 엔터티는 '변경 번호'를 구분자로 갖습니다.

5\) '직급별 호봉'과 '임직원 계정'에서 데이터를 가져와 '직원별 호봉' 엔터티를 구성합니다. 직원의 호봉은 계속 변하는 값이기 때문에 '임직원 직급별 호봉 변경 이력' 엔터티가 필요합니다. 역시 1:다 관계이며 변경할 때마다 이 엔터티에 insert 하도록 만들었습니다.



전체 ERD는 아래의 링크에서 확인하실 수 있습니다.

{% embed url="https://simplistic-snow-ae5.notion.site/ERD-d52a857ca0ad47d4bb75315a7cebee2f" %}

## 2. 상관 모델링 작성

: DB를 구축하기 위해, 행위들 간의 상관 관계를 분석하는 방법을 상관 모델링이라고 합니다.

![](<../../../.gitbook/assets/image (17).png>)

C : Create

R : Read

U : Update

D : Delete

로 단위 프로세스가 엔티티 타입에 어떤 행위(C,R,U,D)를 하는지 표기하는 것입니다.



**'급여 관리' 상관 모델링 설명 예시**

* 연봉 조회 행위 시 : 임직원 계정, 부서, 직급별 호봉, 직원별 호봉, 급여 기준은 read됨
* 연봉설정 수정 행위 시 : 임직원 계정, 부서, 직급별 호봉,  직원별 호봉, 급여 기준은 read & 직원별호봉, 급여기준은 update도 진행 & 임직원 직급별 호봉, 직원별월지급목록은 create



전체 상관 모델링은 아래의 링크에서 확인하실 수 있습니다.

{% embed url="https://simplistic-snow-ae5.notion.site/fbd6e1df6aac41e29cd790b533fa01a5" %}

## 3. 테이블 정의서 작성

: 각 테이블의 컬럼명, 컬럼ID, 데이터타입, 길이 등 모든 조건을 상세히 정하는 작업입니다.

![](<../../../.gitbook/assets/image (17) (1).png>)

테이블 정의서 작성 후, 팀원들 모두 검토하며 더블 체크했습니다.&#x20;

이렇게 모든 테이블의 상세 정보를 지정 후, 그대로 DB를 구축했습니다.



자세한 내용은 아래의 링크에서 확인하실 수 있습니다.

{% embed url="https://simplistic-snow-ae5.notion.site/ebe5f7f4b217403b84c7a10f67efe672" %}

저희는 배우는 과정이다 보니 구현 중에도 수정하는 경우가 여러 번 있었습니다.&#x20;

은행코드를 처음엔 Number로 설정했다가 이후 VARCHAR2로 변경하는 등 소소한 수정을 진행하며 구현했습니다.

수정을 최소화하기 위해 최대한 꼼꼼하게 설계하는 것이 중요하다는 점을 느꼈습니다.