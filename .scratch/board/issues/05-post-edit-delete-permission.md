Status: ready-for-agent

# 글 수정·삭제 + 권한 + 소프트삭제 숨김 (Post Edit / Delete)

## Parent

`.scratch/board/PRD.md`

## What to build

글의 수정·삭제와 권한, 그리고 소프트 삭제된 글의 숨김 처리. 작성자 본인 또는 ADMIN만 수정·삭제할 수 있고, 삭제된 글은 목록·상세에서 완전히 사라진다(ADR-0001).

- 수정·삭제 권한 검증은 서비스 레벨에서: 작성자 본인 또는 `role = ADMIN`.
- 삭제는 소프트 삭제(`deleted = true`). 삭제된 글은 목록·상세에서 숨김(직접 접근도 보이지 않음, 자리표시 없음).

## Acceptance criteria

- [ ] 작성자 본인이 자기 글을 수정·삭제할 수 있다
- [ ] 다른 일반 회원은 남의 글을 수정·삭제할 수 없다(거부)
- [ ] ADMIN은 임의의 글을 수정·삭제할 수 있다
- [ ] 삭제는 소프트 삭제로 처리되어 데이터는 남되 목록·상세에서 숨겨진다
- [ ] 삭제된 글 상세에 직접 접근해도 열리지 않는다
- [ ] 위 권한·숨김 동작을 검증하는 MockMvc 통합 테스트가 통과한다(본인/타인/ADMIN, 삭제 후 숨김)

## Blocked by

- `.scratch/board/issues/04-post-create-list-detail.md`
