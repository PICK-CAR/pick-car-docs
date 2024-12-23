# Architecture

PickCar의 백엔드 서버 구조입니다.

![backend-architecture.png](backend-architecture.png)

## Cloud Run 선택 이유

- 완전 관리형 컨테이너 서비스로 서버 관리에 대한 부담을 줄일 수 있습니다.
- 고유 HTTPS 엔드포인트를 제공합니다.
- `Cloud Build`를 사용하여 쉽게 자동 배포 파이프라인을 구축할 수 있습니다.
- 매월 200만 개의 요청까지 무료로 사용할 수 있습니다.
  - 서버리스 형태이기 때문에 사용하지 않을 때는 요금이 발생하지 않습니다.
  - 무료 사용량을 초과하는 경우에도 사용한 만큼만 요금이 발생합니다.

<note>
    개발 초기에 컨테이너 최소 인스턴스 수를 0으로 설정하여 비용을 절감하고,
    이후 상황에 따라 최소 인스턴스 수 증가 및 CPU 부스트 설정으로 Cold Start 문제를 해결할 수 있습니다.
</note>

[Start Containers Quickly - Cloud Run Docs](https://cloud.google.com/run/docs/tips/general#start_containers_quickly)

## Cloud SQL 선택 이유

- VM 인스턴스를 생성하고 MySQL을 설치하거나 컨테이너를 준비하는 등의 복잡한 작업 없이 쉽게 MySQL 인스턴스를 생성할 수 있습니다.
- VM 인스턴스 구성 비용과 큰 차이가 없으며, 데이터베이스 관리에 대한 부담을 줄일 수 있겠다고 생각했습니다.

## Memory Store 선택 이유

- Cloud SQL과 마찬가지로 복잡한 작업 없이 Redis 인스턴스를 생성할 수 있습니다.
- 요금은 다소 비싸지만, GCP의 무료 크레딧을 사용할 수 있습니다.
  - 추가로 여러 서비스와 연동하여 활용해볼 수 있는 기회가 된다고 생각했습니다.

<note>
    무료로 제공된 크레딧을 모두 사용한 경우에는, VM 인스턴스 내부에 데이터베이스, 캐시 서버 등을 직접 구성하고 관리하는 방법으로 전환할 계획입니다.
</note>