# 게시글 (질문) 작성하기

## 공통 정보

<!-- 요청 시 URL 입니다. Root url에 대해서는 제외하고 서술합니다. -->
URL(endpoint): /v1/question

<!-- 요청 시 method 입니다. HTTP method를 기준으로 합니다. -->
method: POST

<!-- 요청 시 기능명세 코드 입니다. API가 활용되는 페이지를 기준으로 합니다. -->
기능명세 코드: B-WRI-00

## 요청시 데이터

<!-- 요청시에 Path Variable, Request Parameter, 혹은 Query Parameter가 필요한 지에 대해 체크합니다. -->
<!-- 만약 해당되는 데이터가 없다면 표를 비워주세요. 제목을 포함한 항목을 지우시면 됩니다.-->
Path Variable : <input type="checkbox" value="Path Variable">

Request Body : <input type="checkbox" value="Request Body" checked>

Query Parameter : <input type="checkbox" value="Query Parameter">

### Request Body 

<!-- 요청 시 데이터에 대해 명시하는 테이블입니다. -->
<!-- Key, Data-Type, Description, Condition 순으로 작성해주세요. -->
<!-- Key는 요청 시 데이터의 Key를,
    Data-Type은 요청 시 데이터의 Data-Type을,
    Description은 요청 시 데이터의 설명을,
    Condition은 요청 시 데이터의 조건을 명시해주세요. -->
| Key | Data-Type | Description | Condition |
| --- | --- | --- | --- |
| title | string | 질문의 제목 | |
| nickname | string | 작성자의 nickname | |
| password | string | 작성자임을 판별할 수 있는 password | |
| category | string | 질문의 카테고리 | |
| content | string | 질문의 내용 | |
| createdAt | string | 질문이 작성된 시간 | 질문이 작성되어 작성 버튼을 누른 시점을 기준으로 할 것 |

### 예시

```json
// 아래는 요청할 때의 Path Variable 데이터 예시입니다.
{
    // 없음
}

// 아래는 요청할 때의 Request Body 데이터 예시입니다.
{
	"title": "미니쉘 우웩",
	"nickname": "san", 
	"password": "1111aaaa", 
	"category": "minishell",
	"content": "미니쉘 어떻게 시작해야하나요?",
	"createdAt": "2023-06-29T15:02:59"
}

// 아래는 요청할 때의 Query Parameter 데이터 예시입니다.
{
    // 없음
}
```

***

## 응답시 데이터

### 성공

```json
// 아래의 응답에 대한 요청은 위의 요청시 데이터 예시를 참고해주세요.
// 요청시 Path Variable와 Request Body에 따라 응답 데이터가 달라집니다.

// 응답시 HTTP Status Code는 아래와 같습니다.
STATUS CODE: 201 CREATED

// 아래는 응답시 전달될 데이터 예시입니다.
{
    "message" : "question created successfully",
}
```

### 실패

#### 잘못된 Category로 요청을 보낼 경우
<!-- 실패시에는 어떻게 해서 실패한 코드인지 반드시 실패 사유를 적어주세요. -->

```json
// 응답시 HTTP Status Code는 아래와 같습니다.
STATUS CODE: 400 BAD REQUEST

// 아래는 응답시 전달될 데이터 예시입니다.
{
    "message" : "category is invalid - category must be one of [ft_irc, minishell, minirt]",
}
```
<!-- 실패 사유가 여러가지 존재하여서 2개 이상의 실패 응답을 정의할 때에는 복수의 ### [실패사유] 탭을 만들어 주세요.-->