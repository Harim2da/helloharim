---
description: 담당 파트 중 일부분의 화면, 코드를 설명합니다.
---

# 이하림 구현 화면 및 코드

## 구현 화면 및 코드

### 1) 관리자의 의뢰 리스트 검색 조회 (상세 조회 포함)&#x20;

![](<../../../.gitbook/assets/image (27).png>)

![](<../../../.gitbook/assets/image (48) (1).png>)

* **View (JSP)**

1. 효율적인 코드 정리를 위해 jsp include 지시자 태그를 활용했습니다.  다른 jsp 파일에 nav bar를 작성하고 이를 불러오는 방식을 사용했습니다.
2. form 태그를 사용해 관리자가 입력한 검색어를 get 방식으로 전달해, 검색 기능 중, 주로 사용할 기능을 select 방식으로 선택할 수 있게 설정했습니다.

![](<../../../.gitbook/assets/image (12) (1).png>)

* **Model**

1. view에서 입력한 검색어 및 검색 조건을 hashMap에 담아 전달했습니다.
2. DB에서 조회한 결과 값은 여러 개의 DTO를 포함하므로, ArrayList 자료형으로 return했습니다.

![](<../../../.gitbook/assets/image (29) (1).png>)

* **SQL**

1. 같은 table을 공유하는 사용자 정보와 청소 해결사 정보는, 스칼라 서브쿼리를 통해 조회했습니다.
2. Mybatis 동적 SQL을 활용하여 검색 시, 효율적으로 쿼리문을 작성했습니다.



**의뢰 리스트 상세 조회**

![](<../../../.gitbook/assets/image (5) (1).png>)

![](<../../../.gitbook/assets/image (26) (1).png>)

* **View (JSP)**

1. ArrayList의 값을 화면에 구현하기 위해, JSTL Core tag 중 forEach 태그 사용했습니다.
2. 조회해온 ArrayList의 개수를 모르기 때문에 varStatus를 활용해 구분했습니다. 이는 forEach를 통해 생성한 버튼의 위치 확인 및 의뢰를 세부 조회 할 때 사용했습니다.
3. '자세히' 버튼을 선택했을 때, varStatus 확인 후 해당 의뢰번호를 찾아, servlet으로 전달하도록 했습니다.



### 2) 관리자의 정산 자동 계산 및 정산 대기 등록

![](<../../../.gitbook/assets/image (7) (1).png>)

* **Controller & Service**

![](<../../../.gitbook/assets/image (1).png>)

1\) Controller에서는 정산하고자 하는 기간에 맞는, 미정산 리스트 호출합니다.

2\) DB에서 조건에 맞는 데이터를 select 한 뒤, service에서 세율을 계산 후 다시 controller로 return 합니다.

* **View**

![](<../../../.gitbook/assets/image (8) (1).png>)

1\) view에서 관리자는 정산할 항목을 클릭하고, checked 된 항목을 다시 전송해 저장합니다.

* **Service**

![](<../../../.gitbook/assets/image (22) (1) (1).png>)

1\) view에서 전달 받은 값을 기반으로 service에서는 hashMap에 담에 DB에 insert하는 것으로 프로세스는 종료됩니다.
