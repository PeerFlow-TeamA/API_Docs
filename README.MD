
# API_Docs_Peer 사전과제 A팀

## Description

이 레포지토리는 Peer 사전과제 A팀 프로젝트의 API 문서입니다.

## Directory

```
.
├── README.md
├── static // 문서에 필요한 정적파일이 들어있는 디렉토리
│   └── images // 이미지 파일
├── Main // 메인페이지 관련 API
├── Question // 질문 관련 API
│   └── Comment // 질문의 댓글 관련 API 
├── Answer // 답변 관련 API
    └── Comment // 답변의 댓글 관련 API
```

## API Docs 목록

아래는 기능명세 코드별 API 문서입니다.
기능명세 코드에 해당되는 API를 찾는 경우 이 표를 기준으로 찾아가시면 됩니다.

파일의 경로는 요청하는 API의 endpoint를 따라 분류되어 있습니다.

만약 요청하는 API의 endpoint가 `/v1/question`이라면 `question` 디렉토리에서 찾으시면 됩니다.
또, 만약 요청하는 API의 endpoint가 `/v1/question/comment`라면 `question` 디렉토리에서 `comment` 디렉토리를 찾으시면 됩니다.

| 기능명세 코드 | API 문서 위치 | 문서 설명 |
| --- | --- | --- |
| A-MAI-00 | [./main/A-MAI-00.md](./main/A-MAI-00.md) | 메인페이지 질문 목록 조회 |
| A-MAI-01 | [./main/A-MAI-01.md](./main/A-MAI-01.md) | 게시판 게시글 검색 |
| B-WRI-00 | [./question/B-WRI-00.md](./question/B-WRI-00.md) | 게시글 (질문) 작성하기 |
| B-WRI-01 | [./question/B-WRI-01.md](./question/B-WRI-01.md) | 게시글 (질문) 수정하기 |
| B-WRI-02 | [./question/B-WRI-02.md](./question/B-WRI-02.md) | 게시글 (질문) 삭제하기 |
| C-DET-00 | [./question/C-DET-00.md](./question/C-DET-00.md) | 게시글 (질문) 상세 조회하기 |
| C-DET-01 | [./answer/C-DET-01.md](./answer/C-DET-01.md) | 답글 작성하기 |
| C-DET-02 | [./answer/C-DET-02.md](./answer/C-DET-02.md) | 답글 수정하기 |
| C-DET-03 | [./answer/C-DET-03.md](./answer/C-DET-03.md) | 답글 삭제하기 |
| C-DET-04 | [./answer/C-DET-04.md](./answer/C-DET-04.md) | 답글 채택하기 |
| C-DET-05 | [./question/comment/C-DET-05.md](./question/comment/C-DET-05.md) | 질문 댓글 작성하기 |
| C-DET-06 | [./question/comment/C-DET-06.md](./question/comment/C-DET-06.md) | 질문 댓글 수정하기 |
| C-DET-07 | [./question/comment/C-DET-07.md](./question/comment/C-DET-07.md) | 질문 댓글 삭제하기 |
| C-DET-08 | [./question/comment/C-DET-08.md](./question/comment/C-DET-08.md) | 특정 질문 글에 쓰여진 모든 댓글 조회하기 |
| C-DET-09 | [./answer/comment/C-DET-09.md](./answer/comment/C-DET-09.md) | 답글의 댓글 작성하기 |
| C-DET-10 | [./answer/comment/C-DET-10.md](./answer/comment/C-DET-10.md) | 답글의 댓글 수정하기 |
| C-DET-11 | [./answer/comment/C-DET-11.md](./answer/comment/C-DET-11.md) | 답글의 댓글 삭제하기 |
| C-DET-12 | [./answer/comment/C-DET-12.md](./answer/comment/C-DET-12.md) | 특정 답글에 쓰여진 모든 댓글 조회하기 |
| C-DET-13 | [./question/C-DET-13.md](./question/C-DET-13.md) | 질문 추천하기 |
| C-DET-14 | [./answer/C-DET-14.md](./answer/C-DET-14.md) | 답글 추천하기 |


## API Docs 내역
각 문서에는 다음의 정보가 있습니다.

- URL(endpoint)
- method
- 기능명세 코드

- 요청시 데이터
    - Path Parameter, Body Parameter, Query Parameter 활용 여부
    - 활용 데이터 내역
    - 활용 데이터 예시
- 응답시 데이터
    - 성공
        - 데이터 예시
    - 실패
        - 데이터 예시

## API Docs 작성 규칙

- 문서는 [Markdown](https://gist.github.com/ihoneymon/652be052a0727ad59601)으로 작성합니다.

- 문서의 파일명은 기능명세 코드로 합니다.

- 문서의 제목은 {기능명세 코드}.md 로 합니다.

- API의 endpoint에 따라 디렉토리를 분류합니다.

- ./static/images 디렉토리에 이미지를 넣고 문서에 이미지를 삽입할 때는 다음과 같이 작성합니다.

    ```markdown
    ![이미지 설명](./static/images/이미지파일명.png)
    ```

- ./static/docs/api_docs_template.md 파일을 복사하여 문서를 작성합니다.