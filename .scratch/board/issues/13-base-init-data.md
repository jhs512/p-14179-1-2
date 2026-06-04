Status: ready-for-agent

# 초기 샘플 데이터 (BaseInitData)

## Parent

`.scratch/board/PRD.md`

## What to build

빈 DB로 처음 실행할 때 화면을 바로 확인할 수 있도록 샘플 데이터를 시드한다. `com.back.global.initData.BaseInitData`의 `baseInitDataApplicationRunner` 빈(`@Transactional`)이 이를 수행한다.

- 회원이 1명이라도 있으면 시드 로직을 즉시 중단(중복 생성 방지).
- 없으면 회원 5명·글 5개·댓글 5개를 생성. 권한 검증/관리 동작 확인을 위해 회원 중 1명은 ADMIN으로 두는 것을 권장.
- 비밀번호는 BCrypt로 저장(가입 흐름과 동일 규칙).

## Acceptance criteria

- [ ] 빈 DB로 기동하면 회원 5·글 5·댓글 5가 생성된다
- [ ] 회원이 1명이라도 있으면 시드가 건너뛰어진다(중복 생성 없음)
- [ ] 생성된 회원의 비밀번호가 BCrypt로 저장된다
- [ ] 생성된 회원 중 ADMIN이 1명 포함된다
- [ ] dev 재기동 시(파일 DB에 데이터 존재) 시드가 다시 실행되지 않음을 검증하는 테스트/동작이 있다

## Blocked by

- `.scratch/board/issues/06-comment-create-display.md`
