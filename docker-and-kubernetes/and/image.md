# Image

```bash
# application 실행 환경과 image 생성
docker image build -t <REPOSITORY>/<IMAGE NAME>:<TAG> <PATH_TO_DOCKERFILE>
# ex
docker image build . -t imageFileName
# 실행중인 Image list -> Linux 기본 명령어 사용가능
docker image ls # -a
```

```bash
# Image를 Registry(Docker hub)에 배포하기 위한 로그인
docker login
# 배포
docker image push root/imageFileName
# Registry(Docker hub)에 배포된 이미지 다운로드
docker image pull root/imageFileName
# 실행
docker [CONTAINER] run [OPTION] IMAGE [COMMAND] [ARG...]
# ex
docker run -d --name containerName -p 8080:80 imageName
# 결과 확인
docker ps
docker container ls
```
