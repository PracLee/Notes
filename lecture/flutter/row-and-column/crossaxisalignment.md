---
description: CrossAxisAlignment 의 Options
---

# CrossAxisAlignment

* CrossAxisAlignment.start : 반대축의 시작에 정렬&#x20;
  * (111000000)
  * (00000000)
  * (00000000)
* CrossAxisAlignment.end : 반대축의 끝에 정렬
  * (00000000)
  * (00000000)
  * (111000000)
* CrossAxisAlignment.center : 반대축의 중앙에 정렬 (default)
  * (00000000)
  * (111000000)
  * (00000000)
* CrossAxisAlignment.stretch : 반대축의 위젯들을 최대로 확장
  * (11100000)
  * (11100000)
  * (11100000)
*   CrossAxisAlignment.baseline : 텍스트 기준선을 기준으로 위젯을 정렬&#x20;

    -> TextBaseline.alphabetic : 글자 하단을 남긴 기준선 : 일반적으로 사용

    -> TextBaseline.ideographic : 글자 하단을 남기지 않은 기준선
