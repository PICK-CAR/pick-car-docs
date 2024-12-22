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