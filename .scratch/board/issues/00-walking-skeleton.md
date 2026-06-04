Status: ready-for-agent

# 워킹 스켈레톤 (Walking Skeleton)

## Parent

`.scratch/board/PRD.md`

## What to build

자프링 게시판의 걸어다니는 골격. `back/`에 Spring Boot 4.0.6 / JDK 25 / Gradle Kotlin DSL 프로젝트를 세우고, 홈 페이지 한 장이 HTTP 요청 → 컨트롤러 → Thymeleaf 렌더까지 관통해 뜨는 것까지를 한 슬라이스로 완성한다. 이후 모든 도메인 슬라이스가 올라탈 인프라(엔티티 공통 베이스, 프로파일, 보안 골격, 공통 레이아웃, 첫 통합 테스트)를 포함한다.

- 루트 패키지 `com.back`, 메인 클래스 `com.back.BackApplication`(`@EnableJpaAuditing`).
- 의존성: DevTools, Lombok, Spring Data JPA, Validation, Spring Security, H2, Thymeleaf, thymeleaf-layout-dialect.
- 작성일·수정일을 가진 `BaseEntity`(JPA Auditing)로 이후 모든 엔티티가 상속할 베이스 제공.
- OSIV 비활성화, 트랜잭션은 액션(서비스) 메서드 레벨 `@Transactional` 원칙.
- 프로파일: dev = `application.yml` + `application-dev.yml`, 파일 DB `./db_dev.mv.db`, `ddl-auto: update`, h2-console. test = `application.yml` + `application-test.yml`, H2 인메모리, `ddl-auto: create`.
- Spring Security 골격: 지금은 홈·정적 리소스 등 공개 경로 permitAll, 폼 로그인 기본 골격만(실제 회원 인증은 후속 슬라이스).
- 공통 레이아웃(thymeleaf-layout-dialect) 1개 + Tailwind 4.x Play CDN + DaisyUI + Pretendard 동적 서브셋을 레이아웃에 연결.
- 홈 페이지 1장 + 이를 검증하는 첫 `@SpringBootTest` + MockMvc 테스트(이후 테스트의 기준 패턴).

## Acceptance criteria

- [ ] `back/`에서 Gradle(KTS)로 빌드·실행되고 `com.back.BackApplication`이 기동한다
- [ ] dev 실행 시 파일 DB(`./db_dev.mv.db`)와 h2-console가, test 실행 시 인메모리 DB가 사용된다(프로파일별 ddl-auto: update/create)
- [ ] OSIV 비활성화 설정이 적용되어 있다
- [ ] `BaseEntity`가 작성일·수정일을 자동 기록한다(JPA Auditing 활성)
- [ ] 공통 레이아웃이 Tailwind/DaisyUI/Pretendard를 포함하고 홈 페이지가 이를 사용해 렌더된다
- [ ] 홈 페이지 GET이 200으로 렌더됨을 검증하는 MockMvc 통합 테스트가 test 프로파일에서 통과한다

## Blocked by

None - can start immediately
