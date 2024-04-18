# Docker File

* 주요 지시어
  * FROM : docker image 를 위한 부모 이미지를 지시하는 것
  * RUN : 이미지에 소프트웨어를 설치하고 스크립트나 명령 및 기타 작업을 실행
  * COPY : 로컬파일을 container로 복사
  *   ADD : 파일 복사는 물론 tar 파일을 이미지에 추출하거나 원격 소스의 컨텐츠를 추가

      \-> ADD 보다는 COPY를 사용하도록 권고
  *   EXPOSE : Docker에게 container 실행 시 연결 요청을 수신하기 위해 대기포트를 지정

      \-> Container의 network service에 access 할 수 있도록 port 개방
  *   ENTRYPOINT : Image가 Container화 될때 기본으로 실행되는 명령어를 설정하는것

      \-> overwrite가 되지 않음
  *   CMD : Container가 실행될 때 container에 포함되어 있는 소프트웨어 서비스, 명령어를 런타임시 실행

      \-> Image가 Container화 될때 명령어의 매개변수 지정
  *   USER : 명령어의 실행 주체를 정의할 때 사용

      \-> USER 지시어로 지정된 사용자는 존재해야 함. 즉, 이전에 사용자가 추가되어야 함
  * WORKDIR : 이미지 빌드시 디렉토리 이동
  * ENV : Container의 환경 변수를 설정
  * ONBUILD : 포함하고 있는 이미지를 기반으로 다른 이미지를 생성할 때 새롭게 생성되는 이미지에서 실행
  * ARG : 빌드시 사용하는 변수, 빌드 후에 사용 X
  *   VOLUME : Docker container가 생성한 데이터 저장 영역(폴더)를 호스트에 탑재, 유지

      \-> Container 내에 /myvol 디렉토리가 만들어지고 호스트의 docker 영역에 자동 마운트

      \-> Container 가 생성하는 데이터를 저장하면, 호스트에서 데이터를 유지할 수 있지만, 컨테이너가 실행 중인 경우에만 유효

      \-> Container 내의 데이터가 호스트에 유지되도록 하기 위해서는 host와 container 간 volume을 수동으로 mount 해야함

