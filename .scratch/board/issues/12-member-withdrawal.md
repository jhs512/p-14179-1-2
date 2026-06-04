Status: ready-for-agent

# 회원 탈퇴 + "탈퇴한 회원" 표시 (Withdrawal)

## Parent

`.scratch/board/PRD.md`

## What to build

회원이 서비스를 떠나는 흐름. 탈퇴는 소프트 삭제로 처리되어 레코드가 남고, 작성한 글·댓글은 그대로 보존되며 작성자명은 "탈퇴한 회원"으로 표시된다. 탈퇴한 username·nickname은 재사용할 수 없다(ADR-0001).

- 내 정보 페이지에서 탈퇴 실행 → Member `deleted = true`, 세션 종료.
- 탈퇴 회원은 로그인 불가(이미 02에서 적용된 규칙 재확인).
- 글 목록·상세, 댓글·대댓글에서 탈퇴 회원의 작성자명이 "탈퇴한 회원"으로 노출(글·댓글 자체는 유지).

## Acceptance criteria

- [ ] 로그인한 회원이 탈퇴를 실행하면 소프트 삭제되고 세션이 종료된다
- [ ] 탈퇴 후 같은 username·nickname으로 재가입할 수 없다
- [ ] 탈퇴 회원이 작성한 글·댓글은 삭제되지 않고 유지된다
- [ ] 탈퇴 회원의 글·댓글 작성자명이 "탈퇴한 회원"으로 표시된다
- [ ] 위 동작을 검증하는 MockMvc 통합 테스트가 통과한다(탈퇴, 재가입 차단, 콘텐츠 유지·작성자 표시)

## Blocked by

- `.scratch/board/issues/04-post-create-list-detail.md`
- `.scratch/board/issues/06-comment-create-display.md`
