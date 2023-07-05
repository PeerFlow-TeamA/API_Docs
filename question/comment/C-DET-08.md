# 특정 질문 글에 쓰여진 모든 댓글 조회하기

## 공통 정보


<!-- 요청 시 URL 입니다. Root url에 대해서는 제외하고 서술합니다. -->
URL(endpoint): /v1/questions/{questionId}/comments?page={page}&size={size}

<!-- 요청 시 method 입니다. HTTP method를 기준으로 합니다. -->
method: GET

<!-- 요청 시 기능명세 코드 입니다. HTTP method를 기준으로 합니다. -->
기능명세 코드: C-DET-08

## 요청시 데이터

<!-- 요청시에 Path Parameter 혹은 Request Parameter가 필요한 지에 대해 체크합니다. -->
<!-- 만약 해당되는 데이터가 없다면 표를 비워주세요. 제목을 포함한 항목을 지우시면 안됩니다.-->
Path Parameter : <input type="checkbox" value="Path Parameter" checked>

Request Body : <input type="checkbox" value="Request Body">

### Path Parameter

<!-- 요청 시 데이터에 대해 명시하는 테이블입니다. -->
<!-- Key, Data-Type, Description, Condition 순으로 작성해주세요. -->
<!-- Key는 요청 시 데이터의 Key를,
    Data-Type은 요청 시 데이터의 Data-Type을,
    Description은 요청 시 데이터의 설명을,
    Condition은 요청 시 데이터의 조건을 명시해주세요. -->
| Key | Data-Type | Description | Condition |
| --- | --- | --- | --- |
| questionId | int | 질문의 id | |
| page | int | 페이지 번호 | |
| size | int | 페이지 사이즈 | |

### 예시

```json
// 아래는 요청할 때의 Path Parameter 데이터 예시입니다.
{
    "questionId": 1,
    "page": 1,
    "size": 10
}

// 아래는 요청할 때의 Request Body 데이터 예시입니다.
{
    // 없음
}
```

***

## 응답시 데이터

### 성공

#### 응답시 조회된 댓글이 있는 경우

```json
// 아래의 응답에 대한 요청은 위의 요청시 데이터 예시를 참고해주세요.
// 요청시 Path Parameter와 Request Body에 따라 응답 데이터가 달라집니다.

// 응답시 HTTP Status Code는 아래와 같습니다.
STATUS CODE: 200 OK

// 아래는 응답시 전달될 데이터 예시입니다.
{
    "content": [
        {
            "nickname": "hyeongki",
            "content": "정말 좋은 질문입니다.",
            "createdAt": "2023-07-04T16:59:59.978898",
            "updatedAt": null,
            "type": "question",
            "questionCommentId": 1
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
        "pageSize": 20,
        "paged": true,
        "unpaged": false
    },
    "last": true,
    "totalElements": 1,
    "totalPages": 1,
    "size": 20,
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


#### 응답시 조회된 댓글이 없는 경우

```json
// 아래의 응답에 대한 요청은 위의 요청시 데이터 예시를 참고해주세요.
// 요청시 Path Parameter와 Request Body에 따라 응답 데이터가 달라집니다.

// 응답시 HTTP Status Code는 아래와 같습니다.
STATUS CODE: 200 OK

// 아래는 응답시 전달될 데이터 예시입니다.
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
        "pageSize": 20,
        "paged": true,
        "unpaged": false
    },
    "last": true,
    "totalElements": 0,
    "totalPages": 0,
    "size": 20,
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

#### questionId에 해당하는 질문이 없는 경우
<!-- 실패시에는 어떻게 해서 실패한 코드인지 반드시 실패 사유를 적어주세요. -->

```json
// 응답시 HTTP Status Code는 아래와 같습니다.
STATUS CODE: 404 NOT FOUND

// 아래는 응답시 전달될 데이터 예시입니다.
{
    "message" : "question not found"
}
```
<!-- 실패 사유가 여러가지 존재하여서 2개 이상의 실패 응답을 정의할 때에는 복수의 ### [실패사유] 탭을 만들어 주세요.-->