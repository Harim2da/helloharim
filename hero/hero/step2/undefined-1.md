# 기획 및 화면 설계

## 기획 및 화면 설계 순서

1\) 정책 정의서 작성

2\) Information Architecture(IA) 작성

3\) 메뉴 구조도(사이트맵) 작성

4\) 화면 목록 및 화면 정의서 작성

## 1. 정책 정의서 작성

먼저 각 화면별로 권한 정책을 작성했습니다.

![](<../../../.gitbook/assets/image (43).png>)

담당자별 접근 가능한 기능의 차이는 중요했기 때문에 권한 정책을 최대한 꼼꼼하게 작성했습니다.

user에 따라 조회, 수정, 삭제, 쓰기 권한에 차등을 두고, 이에 맞게 구현할 수 있도록 확정지었습니다.



전체 리스트는 아래의 링크에서 확인하실 수 있습니다.

{% embed url="https://simplistic-snow-ae5.notion.site/6349a157647d46ba8b915ae898add6e5" %}

## 2.  Information Architecture(IA) 작성

: 각 기능별 depth를 구분하며, 구조화하는 작업입니다.

![](<../../../.gitbook/assets/image (7).png>)

depth가 같은 것끼리 범주화 작업을 했고, 그 과정에서 분류가 모호한 것들은 최대한 유사한 것끼리 묶었습니다.

이 때 작성한 구조를 기반으로 다음 단계인 메뉴 구조도를 만들었습니다.



전체 IA는 아래의 링크에서 보실 수 있습니다.

{% embed url="https://simplistic-snow-ae5.notion.site/Information-Architecture-IA-3df61bee1db54186845172e0eb5e27dd" %}

## 3. 메뉴 구조도(사이트맵) 작성

프로그램의 메뉴 구조도를 만들어 전체 구조를 확정 지었습니다.

![](../../../.gitbook/assets/메뉴구조도.png)

이전 단계인 IA를 기반으로 메뉴 구조를 확정 짓고, 어색한 부분이 없는지 점검했습니다.

## 4. 화면 목록 및 화면 정의서 작성

이후 각 화면별 버튼의 기능, 클릭 이벤트 등에 설명을 달아 구현이 용이하게 만들었습니다.



![](<../../../.gitbook/assets/image (13).png>)

![](<../../../.gitbook/assets/image (18) (1).png>)

각 버튼의 event 및 기능을 표기하고, 보여지는 화면을 자세히 작성했습니다.

작성하면서 담당 파트의 기능 로직을 구상해볼 수 있었습니다. 또, 다른 팀원의 화면과 기능을 미리 확인할 수 있어 의사소통이 원활하게 진행될 수 있었습니다.



작성한 모든 화면 정의서를 보시려면 아래의 링크를 클릭하시면 됩니다.

{% embed url="https://simplistic-snow-ae5.notion.site/8b1b2ff8dae548b2be7172f19ba4092f" %}
