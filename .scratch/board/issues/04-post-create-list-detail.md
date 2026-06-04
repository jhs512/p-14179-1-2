Status: ready-for-agent

# 글 작성·목록·상세 (Post Create / List / Detail)

## Parent

`.scratch/board/PRD.md`

## What to build

글(Post)의 작성과 읽기 경로. 인증된 회원이 글을 작성하고, 누구나(비로그인 포함) 글 목록과 상세를 읽는다. 이 슬라이스에서 Post 엔티티를 도입한다.

- **글(Post)** 엔티티: 작성자(Member 참조), 제목·본문, `viewCount`(기본 0), `deleted` 플래그. `BaseEntity` 상속.
- 글 작성은 인증 필요. 목록·상세 읽기는 비로그인 허용.
- 상세에 작성자(nickname)·작성일·조회수·추천수 자리를 표시(조회수 증가·추천 동작은 후속 슬라이스).
- 모든 조회는 `deleted = false` 기본 필터(ADR-0001).

## Acceptance criteria

- [ ] 인증된 회원이 제목·본문으로 글을 작성하면 저장되고 상세로 이동한다
- [ ] 비로그인 방문자가 글 작성을 시도하면 로그인으로 유도된다
- [ ] 누구나 글 목록을 읽을 수 있고 최신순으로 노출된다
- [ ] 누구나 글 상세를 읽을 수 있고 작성자(nickname)·작성일·조회수·추천수가 표시된다
- [ ] 위 동작을 검증하는 MockMvc 통합 테스트가 통과한다(작성, 목록, 상세, 비로그인 작성 차단)

## Blocked by

- `.scratch/board/issues/02-login-logout.md`
