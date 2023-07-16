# 게시판 메인화면 불러오기

## 공통 정보

<!-- 요청 시 URL 입니다. Root url에 대해서는 제외하고 서술합니다. -->
URL(endpoint): /v1?category={category}&sort={sort}&page={page}&size={size}

<!-- 요청 시 method 입니다. HTTP method를 기준으로 합니다. -->
method: GET

<!-- 요청 시 기능명세 코드 입니다. API가 활용되는 페이지를 기준으로 합니다. -->
기능명세 코드: A-MAI-00

## 요청시 데이터

<!-- 요청시에 Path Variable, Request Parameter, 혹은 Query Parameter가 필요한 지에 대해 체크합니다. -->
<!-- 만약 해당되는 데이터가 없다면 표를 비워주세요. 제목을 포함한 항목을 지우시면 됩니다.-->
Path Variable : <input type="checkbox" value="Path Variable">

Request Body : <input type="checkbox" value="Request Body">

Query Parameter : <input type="checkbox" value="Query Parameter" check>

### Query Parameter

<!-- 요청 시 데이터에 대해 명시하는 테이블입니다. -->
<!-- Key, Data-Type, Description, Condition 순으로 작성해주세요. -->
<!-- Key는 요청 시 데이터의 Key를,
    Data-Type은 요청 시 데이터의 Data-Type을,
    Description은 요청 시 데이터의 설명을,
    Condition은 요청 시 데이터의 조건을 명시해주세요. -->
| Key | Data-Type | Description | Condition |
| --- | --- | --- | --- |
| category | string | 글의 카테고리 | all, ft_irc, minishell, minirt 넷 중 하나로 할 것 |
| sort | string | 정렬 기준 | lastest, views, recommends 셋 중 하나 |
| page | int | 페이지의 사이즈 |
| size | int | 페이지의 인덱스 |

#### 예시

```json
// 아래는 요청할 때의 Path Variable 데이터 예시입니다.
{
    // 없음
}

// 아래는 요청할 때의 Request Body 데이터 예시입니다.
{
    // 없음
}

// 아래는 요청할 때의 Query Parameter 데이터 예시입니다.
{
    "category" : "minishell",
    "sort" : "views",
    "page" : 0,
    "size" : 10
}
```

***

## 응답시 데이터

### 성공

#### 요청시 게시글이 있는 경우

```json
// 아래는 성공시 응답 데이터 예시입니다.
// 아래의 요청시 Path Variable는 위의 요청시 데이터 예시를 참고해주세요.
// 요청시 Path Variable에 따라 응답 데이터가 달라집니다.

STATUS CODE: 200 OK

{
    // 아래는 게시글의 정보를 담은 데이터입니다.
    "content": [
        {
            "questionId": 1,
            "title": "미니쉘 우웩",
            "answerCount": 1,
            "category": "minishell",
            "recommend": 0,
            "view": 0,
            "nickname": "san",
            "createdAt": "2023-07-04T16:45:48.683522",
            "content": "응 안해"
        }
    ],
    // 아래는 페이징 처리를 위한 데이터입니다.
    "pageable": {
        // 아래는 페이지의 정렬 기준을 나타냅니다.
        "sort": {
            "empty": true, // 정렬할 데이터가 없는지 나타냅니다.
            "sorted": false, // 정렬이 되었는지 나타냅니다.
            "unsorted": true // 정렬이 되지 않았는지 나타냅니다.
        },
        "offset": 0, // 페이지의 시작 인덱스를 나타냅니다.
        "pageNumber": 0, // 페이지의 인덱스를 나타냅니다.
        "pageSize": 10, // 페이지의 사이즈를 나타냅니다.
        "paged": true, // 페이징 처리가 되었는지 나타냅니다.
        "unpaged": false // 페이징 처리가 되지 않았는지 나타냅니다.
    },
    "last": true, // 마지막 페이지인지 나타냅니다.
    "totalElements": 1, // 전체 게시글의 개수를 나타냅니다.
    "totalPages": 1, // 전체 페이지의 개수를 나타냅니다.
    "size": 10, // 페이지의 사이즈를 나타냅니다.
    "number": 0, // 페이지의 인덱스를 나타냅니다.
    // 아래는 페이지의 정렬 기준을 나타냅니다.
    "sort": {
        "empty": true,
        "sorted": false,
        "unsorted": true
    },
    "first": true, // 첫번째 페이지인지 나타냅니다.
    "numberOfElements": 1, // 현재 페이지의 게시글 개수를 나타냅니다.
    "empty": false // 페이지가 비어있는지 나타냅니다.
}
```

#### 요청시 게시글이 없는 경우

```json
// 아래는 성공시 응답 데이터 예시입니다.
// 아래의 요청시 Path Variable는 위의 요청시 데이터 예시를 참고해주세요.
// 요청시 Path Variable에 따라 응답 데이터가 달라집니다.

STATUS CODE: 200 OK

{
    "content": [
    ],
    "pageable": {
        "sort": {
            "empty": true,
            "sorted": false,
            "unsorted": true
        },
        "offset": 0,
        "pageNumber": 0,
        "pageSize": 10,
        "paged": true,
        "unpaged": false
    },
    "last": true,
    "totalElements": 0,
    "totalPages": 0,
    "size": 10,
    "number": 0,
    "sort": {
        "empty": true,
        "sorted": false,
        "unsorted": true
    },
    "first": true,
    "numberOfElements": 0,
    "empty": true
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
    "message" : "category not correct - category must be one of [ft_irc, minishell, minirt]"
}
```
