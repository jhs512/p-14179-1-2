Status: ready-for-agent

# 회원가입 (Member Signup)

## Parent

`.scratch/board/PRD.md`

## What to build

방문자가 username·password·nickname으로 회원이 되는 끝단 흐름. 회원가입 페이지에서 폼을 제출하면 검증을 거쳐 회원(Member)이 생성되고, 비밀번호는 BCrypt로 저장된다. 이 슬라이스에서 Member 엔티티 자체(소프트 삭제 정책 포함)를 도입한다.

- **회원(Member)** 엔티티: `username`(유니크, 불변), `nickname`(유니크), `password`(BCrypt 저장), `role`(USER/ADMIN, 기본 USER), `deleted` 플래그. `BaseEntity` 상속.
- 유니크 제약은 소프트 삭제 레코드에도 적용되어, 탈퇴한 식별자도 재사용 불가(ADR-0001).
- 가입 페이지 + 폼 검증(필수값, 형식) + 중복 username/nickname 거부.

## Acceptance criteria

- [ ] 회원가입 페이지가 렌더되고 username·password·nickname을 입력받는다
- [ ] 정상 입력 시 회원이 생성되고 password가 BCrypt 해시로 저장된다(평문 저장 안 됨)
- [ ] 이미 존재하는 username으로 가입하면 거부되고 오류가 표시된다
- [ ] 이미 존재하는 nickname으로 가입하면 거부되고 오류가 표시된다
- [ ] 소프트 삭제(탈퇴)된 회원의 username·nickname으로도 가입할 수 없다
- [ ] 위 동작을 검증하는 MockMvc 통합 테스트가 통과한다(성공 가입, username 중복, nickname 중복)

## Blocked by

- `.scratch/board/issues/00-walking-skeleton.md`
