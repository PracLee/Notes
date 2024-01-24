# Java InputStream & OutputStream

* Java에서 데이터를 읽거나 쓰기 위한 추상 클래스
* 입출력 작업을 추상화, 다양한 유형의 데이터 소스 및 대상과 상호 작용할 수 있도록 함

1. InputStream

* byte 단위로 데이터를 읽어오는데 사용



2. OutputStream

* byte 단위로 데이터를 쓰는데 사용
* close 시 자동으로 buffer의 내용이 출력 되지만, flush를 호출하여 비우는 것이 유용
