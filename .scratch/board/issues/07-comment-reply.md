Status: ready-for-agent

# 대댓글 1단계 (Reply, single level)

## Parent

`.scratch/board/PRD.md`

## What to build

댓글에 달리는 대댓글(Reply). 회원이 특정 댓글에 답하면 그 댓글의 자식으로 노출된다. 계층은 글 → 댓글 → 대댓글 2단계에서 멈추며, 대댓글에는 다시 댓글을 달 수 없다.

- 대댓글은 `parent`(부모 Comment)를 가진 Comment.
- 부모가 이미 대댓글(parent != null)인 댓글에는 자식 댓글 작성을 거부(계층 2단계 상한 검증).
- 글 상세에서 댓글 아래에 대댓글이 들여쓰기 등으로 구분되어 노출.

## Acceptance criteria

- [ ] 회원이 댓글에 대댓글을 달면 그 댓글의 자식으로 저장·노출된다
- [ ] 대댓글에 다시 댓글(대대댓글)을 달려는 시도는 거부된다
- [ ] 글 상세에서 댓글과 대댓글의 계층이 시각적으로 구분된다
- [ ] 위 동작을 검증하는 MockMvc 통합 테스트가 통과한다(대댓글 작성, 2단계 초과 거부)

## Blocked by

- `.scratch/board/issues/06-comment-create-display.md`
