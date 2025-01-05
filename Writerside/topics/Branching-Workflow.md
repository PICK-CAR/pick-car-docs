# Branching Workflow

PickCar의 백엔드 서버 GitHub Branch 전략입니다.

<note>
코드 작성 및 리뷰, 테스트, 배포 등의 과정을 효율적으로 관리하기 위해 Branch 전략을 정의했습니다.
</note>

![branching_workflow.png](branching_workflow.png)

## Branches

- `main`
- `develop`
- `{keword}/{issue-number}-{issue-title}`

## main

가장 안정적인 버전의 코드가 있는 브랜치입니다. 주된 목표는 리뷰를 거쳐 피드백 주기를 가져가는 것입니다.

## develop

새로운 기능을 개발할 때 루트로 사용하는 브랜치이며, 개발 환경을 위한 배포 파이프라인을 가지고 있습니다. `main` 브랜치에서 분기되어 새로운 기능을 개발하고, 테스트합니다.

## keword/issue-number-issue-title

### keyword

- `feat`: 새로운 기능 추가 및 개선
- `fix`: 버그 수정 및 오류 해결
- `chore`: 빌드 및 배포 자동화 구성 등의 작업

예시: `feat/6-login`, `chore/16-database-config`

`develop` 브랜치에서 분기되어 개발하는 작은 브랜치입니다. 작업이 완료되면 `develop` 브랜치에 Pull Request를 생성합니다. 이후 [Test Pipeline](https://github.com/PICK-CAR/pick-car-server/actions/workflows/Test-Pipeline.yml)을 정상적으로 통과하면 `develop` 브랜치로 병합합니다.