Status: ready-for-agent

# 댓글 추천 토글 (Comment Recommend)

## Parent

`.scratch/board/PRD.md`

## What to build

회원이 댓글(대댓글 포함)에 보내는 1인 1회 추천(토글). 글 추천과 동일한 의미론이되 별도 엔티티로 관리한다.

- **CommentRecommend** 엔티티: (Member, Comment) 한 쌍당 1행. 글용 PostRecommend와 분리.
- 토글 동작·본인 추천 허용·비로그인 유도는 글 추천과 동일.
- 댓글마다 현재 추천수 노출. 삭제된 댓글(placeholder)에는 추천 비활성.

## Acceptance criteria

- [ ] 회원이 댓글을 추천하면 추천수가 1 증가하고 추천 상태로 표시된다
- [ ] 다시 누르면 추천이 취소되고 추천수가 1 감소한다(토글)
- [ ] 한 회원의 같은 댓글 추천 집계는 최대 1로 유지된다
- [ ] 본인 댓글도 추천할 수 있다
- [ ] 비로그인으로 추천 시도 시 로그인으로 유도된다
- [ ] 위 동작을 검증하는 MockMvc 통합 테스트가 통과한다

## Blocked by

- `.scratch/board/issues/06-comment-create-display.md`
