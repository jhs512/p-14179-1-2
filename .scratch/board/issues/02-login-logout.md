Status: ready-for-agent

# 로그인·로그아웃 (Login / Logout)

## Parent

`.scratch/board/PRD.md`

## What to build

회원이 username·password로 로그인하고 로그아웃하는 흐름. Spring Security 폼 로그인을 회원(Member)·BCrypt와 연결해 실제 인증이 동작하게 한다. 로그인 상태가 화면에 반영된다(예: 로그인/로그아웃 링크, 현재 nickname).

- Spring Security `UserDetailsService`가 Member를 로드하고 BCrypt로 비밀번호를 검증한다.
- 소프트 삭제(탈퇴)된 회원은 로그인할 수 없다.
- 로그인 페이지, 로그아웃, 공통 레이아웃의 인증 상태 표시.

## Acceptance criteria

- [ ] 올바른 username·password로 로그인하면 인증 세션이 생성된다
- [ ] 잘못된 자격증명은 거부되고 로그인 페이지에 오류가 표시된다
- [ ] 탈퇴(소프트 삭제)된 회원은 로그인할 수 없다
- [ ] 로그아웃 시 세션이 종료된다
- [ ] 공통 레이아웃이 로그인 여부에 따라 다른 메뉴(로그인 vs nickname/로그아웃)를 보여준다
- [ ] 로그인 성공·실패·로그아웃을 검증하는 MockMvc 통합 테스트가 통과한다

## Blocked by

- `.scratch/board/issues/01-member-signup.md`
