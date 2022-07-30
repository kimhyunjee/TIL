## **Query Parameter**

당신이 웹 개발자라면, 가장 간단한 방법인 GET 메소드를 사용해서 데이터를 전송하는 방법을 배웠을 것이다.소셜 서비스를 만든다고 가정해보자. 사용자 목록을 관리해야 하고, 모든 사용자는 사용자 페이지가 있어야 할 것이다.

그리고 각각의 사용자를 위한 페이지를 만들려면 페이지 마다 식별된 파라미터 경로가 필요한데,다음과 같은 get 파라미터를 사용할 수 있을 것이다.

`/users?**id**=123  # 아이디가 123인 사용자를 가져온다.`

그럼 서버로부터 id 변수를 얻을 수 있다. 이것이 Query String이 동작하는 방식이다.

만약 어떤 **resource를 식별**하고 싶으면 **Path Variable**을 사용하고,**정렬이나 필터링**을 한다면 **Query Parameter**를 사용하는 것이 Best Practice이다.

`/users  # 사용자 목록을 가져온다.
/users?occupation=programer  # 프로그래머인 사용자 목록을 가져온다.
/users/123  # 아이디가 123인 사용자를 가져온다.`

출처 : https://ryan-han.com/post/translated/pathvariable_queryparam/
