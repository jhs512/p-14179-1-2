Status: ready-for-agent

# 댓글 수정·삭제 + 권한 + placeholder (Comment Edit / Delete)

## Parent

`.scratch/board/PRD.md`

## What to build

댓글·대댓글의 수정·삭제와 권한, 그리고 소프트 삭제된 댓글의 자리표시. 작성자 본인 또는 ADMIN만 수정·삭제할 수 있고, 삭제된 댓글은 "삭제된 댓글입니다" 자리표시(placeholder)로 남아 대댓글 맥락을 보존한다(ADR-0001).

- 권한 검증: 작성자 본인 또는 `role = ADMIN`.
- 삭제는 소프트 삭제. 삭제된 댓글은 글 상세에서 "삭제된 댓글입니다" 자리표시로 노출하되 본문·추천 액션은 비활성. 그 아래 살아있는 대댓글은 계속 보인다.

## Acceptance criteria

- [ ] 작성자 본인이 자기 댓글·대댓글을 수정·삭제할 수 있다
- [ ] 다른 일반 회원은 남의 댓글을 수정·삭제할 수 없다(거부)
- [ ] ADMIN은 임의의 댓글을 수정·삭제할 수 있다
- [ ] 삭제된 댓글은 "삭제된 댓글입니다" 자리표시로 노출되고 본문은 숨겨진다
- [ ] 삭제된 부모 댓글 아래의 살아있는 대댓글은 계속 표시된다
- [ ] 위 동작을 검증하는 MockMvc 통합 테스트가 통과한다(본인/타인/ADMIN, 삭제 후 placeholder, 대댓글 보존)

## Blocked by

- `.scratch/board/issues/07-comment-reply.md`
