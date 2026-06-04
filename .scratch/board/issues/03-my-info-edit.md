Status: ready-for-agent

# 내 정보 변경 (My Info Edit)

## Parent

`.scratch/board/PRD.md`

## What to build

로그인한 회원이 내 정보 페이지에서 nickname과 password를 변경하는 흐름. username은 불변으로 노출하되 수정 불가.

- nickname 변경 시 유니크 재검증(다른 회원과 겹치면 거부).
- password 변경 시 BCrypt로 재해시 저장.
- 내 정보 페이지는 인증 필요(비로그인 접근 시 로그인 유도).

## Acceptance criteria

- [ ] 내 정보 페이지가 인증된 회원에게만 열린다(비로그인은 로그인으로 유도)
- [ ] nickname을 변경하면 저장되고 화면에 반영된다
- [ ] 다른 회원이 쓰는 nickname으로 변경하면 거부된다
- [ ] password를 변경하면 BCrypt로 재해시되어 저장되고, 새 비밀번호로 로그인된다
- [ ] username은 수정할 수 없다(불변)
- [ ] 위 동작을 검증하는 MockMvc 통합 테스트가 통과한다

## Blocked by

- `.scratch/board/issues/02-login-logout.md`
