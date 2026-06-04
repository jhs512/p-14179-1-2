Status: ready-for-agent

# 댓글 작성·표시 (Comment Create / Display)

## Parent

`.scratch/board/PRD.md`

## What to build

글에 달리는 댓글(Comment)의 작성과 표시. 인증된 회원이 글 상세에서 댓글을 달면, 글 상세에 작성자·작성일과 함께 노출된다. 이 슬라이스에서 Comment 엔티티를 평면 구조(글에 직접)로 도입한다(대댓글은 후속 슬라이스).

- **댓글(Comment)** 엔티티: 글(Post) 참조, 작성자(Member), 본문, `parent`(Comment, optional — 이 슬라이스에서는 null), `deleted` 플래그. `BaseEntity` 상속.
- 댓글 작성은 인증 필요. 조회는 `deleted = false` 기본 필터.

## Acceptance criteria

- [ ] 인증된 회원이 글 상세에서 댓글을 작성하면 저장되고 그 글 상세에 노출된다
- [ ] 비로그인 방문자가 댓글 작성을 시도하면 로그인으로 유도된다
- [ ] 글 상세에 댓글 목록이 작성자(nickname)·작성일과 함께 표시된다
- [ ] 위 동작을 검증하는 MockMvc 통합 테스트가 통과한다(작성, 표시, 비로그인 차단)

## Blocked by

- `.scratch/board/issues/04-post-create-list-detail.md`
