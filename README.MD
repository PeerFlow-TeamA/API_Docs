
# API_Docs_Peer 사전과제 A팀

## Description

이 레포지토리는 Peer 사전과제 A팀 프로젝트의 API 문서입니다.

## Directory

```
.
├── README.md
├── static // 문서에 필요한 정적파일이 들어있는 디렉토리
│   └── images // 이미지 파일
├── Main // 메인페이지
├── Question // 질문 관련 API
│   └── Comment // 질문의 댓글 관련 API 
├── Answer // 답변 관련 API
│   └── Comment // 답변의 댓글 관련 API
```

## API Docs

아래는 기능명세 코드별 API 문서입니다.
기능명세 코드에 해당되는 API를 찾는 경우 이 표를 기준으로 찾아가시면 됩니다.

| 기능명세 코드 | API 문서 위치 | 문서 설명 |
| --- | --- | --- |
| A-MAI-00 | Main/A-MAI-00.md | 게시판 메인페이지의 질문 목록 조회 |


## API Docs 작성 방법
각 문서에는 다음의 정보가 있습니다.

- URL(endpoint)
- method
- 기능명세 코드

- 요청시 데이터
    - 데이터 예시
- 응답시 데이터
    - 성공
        - 데이터 예시
    - 실패
        - 데이터 예시