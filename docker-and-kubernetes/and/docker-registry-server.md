# Docker Registry Server

* Docker Image를 저장하고 배포 할 수 있는 서버 측 애플리케이션으로 상태가 없고 확장성이 뛰어남
* Permissive Apache 라이센스에 의한 공개 소스
* 이미지 저장 위치를 엄격하게 제어, 이미지 배포 파이프 라인을 완전히 소유, 이미지 저장 및 배포를 사내 개발 workflow에 밀접하게 통합하고자 할 때 사용
* 컨테이너로 동작하는 자체 레지스트리로 모든 서비스를 제공
* private, public 또는 둘 사이의 혼합 저장소 제공
* 호스팅하는 이미지 수 또는 제공하는 pull 요청 수에 따라 registry 크기를 조정
* 모든 것이 명령어 기반 (CLI)
* 상업적으로 지원되는 registry : Docker Tusted Registry
* vs Docker Hub
  * GUI 기반 인터페이스
  *
