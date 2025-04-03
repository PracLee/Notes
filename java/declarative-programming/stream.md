---
description: Java 8
---

# stream()

* 기존방식
  * Collection들을 처리할 때 쓰레드 하나에서 for문으로 처리하는 과정이 멀티코어 프로세서가 흔한 현대의 하드웨어 에서 효율적 사용이 어려울 수 있음



* stream
  * stream()을 사용하면 데이터를 병렬로 처리하여 멀티코어 환경에서 성능을 향상 시킬 수 있음
  * 내부적으로 데이터를 여러 부분으로 나누어 병렬 쓰레드에서 처리하고, 그 결과를 다시 합치는 작업을 수행하여, 여러 코어가 동시에 작업을 수행하면서 전체적인 처리 속도를 향상



* return값 : Stream 객체
  * 중간 연산(intermediate operations)과 최종 연산(terminal operations)을 제공&#x20;
  * 중간 연산을 여러 번 연결하여 사용할 수 있음
  * 최종 연산을 호출하기 전까지는 실제로 데이터를 처리하지 않고 지연 평가를 수행(점유 X)
  * 최종 연산이 호출되면 Stream은 닫히고 데이터 처리가 시작
  * 중간 연산(intermediate operations)
    * map : 각 요소에 주어진 함수를 적용하여 새로운 값을 생성
    * filter : 주어진 조건을 만족하는 요소만을 선택
    * distinct : 중복된 요소를 제거
    * sort : 요소를 정렬
    * limit : 요소의 개수를 제한
    * flatMap : 각 요소에 대해 여러개의 요소를 생성하여 하나의 Stream으로 평탄화
  * 최종 연산(terminal operations)
    * forEach : 각 요소에 대해 주어진 동작을 수행
    * collect : Stream의 요소를 수집하여 다른 형태의 collection으로 변환
    * reduce : Stream의 요소를 하나로 줄여서 반환
    * count : Stream의 요소 개수를 반환
    * anyMatch, allMatch, noneMatch : 각각 어떤 요소가 조건을 만족하는지, 모든 요소가 조건을 만족하는지, 어떤 요소도 조건을 만족하지 않는지를 확인
    * findFirst, findAny : Stream의 첫 번째 요소 또는 임의의 요소를 반환

