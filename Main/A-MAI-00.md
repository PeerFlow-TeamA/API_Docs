# 게시판 메인화면 불러오기

## 공통 정보

<!-- 요청 시 URL 입니다. Root url에 대해서는 제외하고 서술합니다. -->
URL(endpoint): /v1?category={category}&sort={sort}&page={page}&size={size}

<!-- 요청 시 method 입니다. HTTP method를 기준으로 합니다. -->
method: GET

<!-- 요청 시 기능명세 코드 입니다. API가 활용되는 페이지를 기준으로 합니다. -->
기능명세 코드: A-MAI-00

## 요청시 데이터

<!-- 요청시에 Path Parameter, Request Parameter, 혹은 Query Parameter가 필요한 지에 대해 체크합니다. -->
<!-- 만약 해당되는 데이터가 없다면 표를 비워주세요. 제목을 포함한 항목을 지우시면 됩니다.-->
Path Parameter : <input type="checkbox" value="Path Parameter" checked>

Request Body : <input type="checkbox" value="Request Body">

Query Parameter : <input type="checkbox" value="Query Parameter">

### Path Parameter

<!-- 요청 시 데이터에 대해 명시하는 테이블입니다. -->
<!-- Key, Data-Type, Description, Condition 순으로 작성해주세요. -->
<!-- Key는 요청 시 데이터의 Key를,
    Data-Type은 요청 시 데이터의 Data-Type을,
    Description은 요청 시 데이터의 설명을,
    Condition은 요청 시 데이터의 조건을 명시해주세요. -->
| Key | Data-Type | Description | Condition |
| --- | --- | --- | --- |
| category | string | 글의 카테고리 | ft_irc, minishell, minirt 셋 중 하나로 할 것 |
| sort | string | 정렬 기준 | lastest, views, recommends 셋 중 하나 |
| page | int | 페이지의 사이즈 |
| size | int | 페이지의 인덱스 | 


#### 예시

<img width="50%" src="../static/images/A-MAI-00-00.png">

```json
// 아래는 요청할 때의 Path Parameter 데이터 예시입니다.
{
    "category" : "minishell",
    "sort" : "views",
    "page" : 0,
    "size" : 10
}

// 아래는 요청할 때의 Request Body 데이터 예시입니다.
{
    // 없음
}

// 아래는 요청할 때의 Query Parameter 데이터 예시입니다.
{
    // 없음
}
```

***

## 응답시 데이터

### 성공

#### 요청시 게시글이 있는 경우

```json
// 아래는 성공시 응답 데이터 예시입니다.
// 아래의 요청시 Path parameter는 위의 요청시 데이터 예시를 참고해주세요.
// 요청시 Path parameter에 따라 응답 데이터가 달라집니다.

STATUS CODE: 200 OK

{
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
    "totalElements": 1,
    "totalPages": 1,
    "size": 10,
    "number": 0,
    "sort": {
        "empty": true,
        "sorted": false,
        "unsorted": true
    },
    "first": true,
    "numberOfElements": 1,
    "empty": false
}
```

#### 요청시 게시글이 없는 경우

```json
// 아래는 성공시 응답 데이터 예시입니다.
// 아래의 요청시 Path parameter는 위의 요청시 데이터 예시를 참고해주세요.
// 요청시 Path parameter에 따라 응답 데이터가 달라집니다.

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

#### 존재하지 않는 카테고리를 요청한 경우
<!-- 실패시에는 어떻게 해서 실패한 코드인지 반드시 실패 사유를 적어주세요. -->

```json
// 응답시 HTTP Status Code는 아래와 같습니다.
STATUS CODE: 400 BAD REQUEST

// 아래는 응답시 전달될 데이터 예시입니다.
{
    "message" : "category not correct - category must be one of [ft_irc, minishell, minirt]"
}
```
