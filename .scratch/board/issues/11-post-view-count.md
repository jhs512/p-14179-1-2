Status: ready-for-agent

# 조회수 쿠키 24시간 중복제거 (Post View Count)

## Parent

`.scratch/board/PRD.md`

## What to build

글이 열람된 횟수를 집계하되, 같은 방문자의 재조회는 글별 쿠키로 24시간 동안 중복 집계하지 않는다. 조회수는 글에만 있고 댓글에는 없다.

- 글 상세 진입 시, 해당 글에 대한 쿠키가 없으면 `viewCount` +1 후 24시간 만료 쿠키를 설정. 쿠키가 있으면 증가하지 않음.
- 로그인 여부와 무관하게 쿠키 기준으로 판정.

## Acceptance criteria

- [ ] 글 상세를 처음 열면 조회수가 1 증가한다
- [ ] 같은 글을 24시간 내 다시 열면 조회수가 증가하지 않는다(쿠키 기준)
- [ ] 서로 다른 글은 각각 독립적으로 조회수가 집계된다
- [ ] 비로그인 방문자도 동일한 쿠키 기준으로 집계된다
- [ ] 위 동작을 검증하는 MockMvc 통합 테스트가 통과한다(최초 증가, 쿠키 보유 시 불변)

## Blocked by

- `.scratch/board/issues/04-post-create-list-detail.md`
