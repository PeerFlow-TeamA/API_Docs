# 답글 수정하기

## 공통 정보

<!-- 요청 시 URL 입니다. Root url에 대해서는 제외하고 서술합니다. -->
URL(endpoint): /v1/answer/{answerId}

<!-- 요청 시 method 입니다. HTTP method를 기준으로 합니다. -->
method: PUT

<!-- 요청 시 기능명세 코드 입니다. HTTP method를 기준으로 합니다. -->
기능명세 코드: C-DET-02

## 요청시 데이터

<!-- 요청시에 Path Variable, Request Parameter, 혹은 Query Parameter가 필요한 지에 대해 체크합니다. -->
<!-- 만약 해당되는 데이터가 없다면 표를 비워주세요. 제목을 포함한 항목을 지우시면 안됩니다.-->
Path Variable : <input type="checkbox" value="Path Variable" checked>

Request Body : <input type="checkbox" value="Request Body" checked>

Query Parameter : <input type="checkbox" value="Query Parameter">

### Path Variable

<!-- 요청 시 데이터에 대해 명시하는 테이블입니다. -->
<!-- Key, Data-Type, Description, Condition 순으로 작성해주세요. -->
<!-- Key는 요청 시 데이터의 Key를,
    Data-Type은 요청 시 데이터의 Data-Type을,
    Description은 요청 시 데이터의 설명을,
    Condition은 요청 시 데이터의 조건을 명시해주세요. -->
| Key | Data-Type | Description | Condition |
| --- | --- | --- | --- |
| answerId | int | 답글의 id | |

### Request Body

<!-- 요청 시 데이터에 대해 명시하는 테이블입니다. -->
<!-- Key, Data-Type, Description, Condition 순으로 작성해주세요. -->
<!-- Key는 요청 시 데이터의 Key를,
    Data-Type은 요청 시 데이터의 Data-Type을,
    Description은 요청 시 데이터의 설명을,
    Condition은 요청 시 데이터의 조건을 명시해주세요. -->
| Key | Data-Type | Description | Condition |
| --- | --- | --- | --- |
| password | string | 답글 작성자임을 판별할 수 있는 password | |
| content | string | 답글의 내용 | |
| updateAt | string | 답글 수정 시간 | 답글을 수정하여 수정하기 버튼을 누른 시점을 기준으로 할 것 |

### 예시

<img width="50%" src="../static/images/Main.png">

```json
// 아래는 요청할 때의 Path Variable 데이터 예시입니다.
{
    "answerId": 1
}

// 아래는 요청할 때의 Request Body 데이터 예시입니다.
{
  "password": "1234",
  "content": "minishell 이렇게 하시면 될 것 같아요.",
  "updateAt": "2023-07-01T12:12:12"
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

// 응답시 HTTP Status Code는 아래와 같습니다.
STATUS CODE: 201 CREATED

// 아래는 응답시 전달될 데이터 예시입니다.
{
    "message" : "Answer modified successfully"
}
```

### 실패

#### 잘못된 비밀번호로 요청을 보낼 경우
<!-- 실패시에는 어떻게 해서 실패한 코드인지 반드시 실패 사유를 적어주세요. -->

```json
// 응답시 HTTP Status Code는 아래와 같습니다.
STATUS CODE: 403 FORBIDDEN

// 아래는 응답시 전달될 데이터 예시입니다.
{
    "message": "Password is incorrect"
}
```

#### answerId에 해당하는 답글이 존재하지 않을 경우
<!-- 실패시에는 어떻게 해서 실패한 코드인지 반드시 실패 사유를 적어주세요. -->

```json
// 응답시 HTTP Status Code는 아래와 같습니다.
STATUS CODE: 404 NOT FOUND

// 아래는 응답시 전달될 데이터 예시입니다.
{
    "message" : "Answer not found"
}
```
<!-- 실패 사유가 여러가지 존재하여서 2개 이상의 실패 응답을 정의할 때에는 복수의 ### [실패사유] 탭을 만들어 주세요.-->
