# Docker

* 컨테이너 개념을 사용하여 애플리케이션 생성과 배포 과정을 단순화하는데 사용되는 오픈 소스 컨테이너화 도구
* 어플리케이션 프로그램과 어플리케이션 프로그램 실힝 필요한 제반 환경을 Dockerfile을 이용하여 image로 빌드, 빌드된 image를 docker 환경에서 컨테이너화하여 이미지가 실행될 수 있도록함으로 개발과 운영 간의 프로그램 배포 상의 환경적 불일치를 해소하여 신속한 배포를 가능하게 하는 툴



* Docker가 동작하기 위한 3가지 요소
  * Docker Image
    * 파일들의 집합으로 만들어진 read-only 템플릿
    * 컨테이너 실행에 필요한 파일과 설정값등을 포함하고 있는 것으로 상태값을 가지고 변하지 않음
    *   가상머신 환경에서 이미지는 일종의 snapshot과 같은 것으로 동일한 이미지로 여러개의 컨테이너를 실행 가능

        \-> container의 상태가 바뀌거나 수정되어도 이미지는 변하지 않음
  * Docker Container
    * 이미지를 실행한 상태로 프로세스라 할 수 있음
    * 추가되거나 변하는 값은 컨테이너에 저장됨
    * Docker Image에 의해 만들어지고 시작, 정지, 이동, 삭제 할 수 있음
    * 각 컨테이너는 독립적이고 안전한 애플리케이션 구동 환경
  * Docker Registry
    * Image를 보관하며, 공개 또는 비공개로 보관 이미지의 업로드와 다운로드가 가능
    * 공개 Docker Registry로 Docker Hub가 제공되며, Local Registry도 구성 가능



* Docker File
  * 사용자가 정의한 명령을 포함하고 있는 일반 텍스트 파일

```docker
FROM IMAGE_NAME:VERSION
COPY RESOURCE RESOURCE_PATH
ENTRYPOINT ["START_ACTION"]
CMD ["VALUE"]
```
