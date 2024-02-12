---
description: https://happycloud-lee.tistory.com/94
---

# Domain Driven Design(DDD)

* 도메인 주도 설계
* DDD에서 말하는 Domain은 유사한 업무의 집합인 비즈니스 Domain (영업, 생산, 마케팅 등)
* 비즈니스 Domain 별로 나누어 설계
* 높은 응집도, 낮은 결합도를 핵심목표로 함
* Strategic Design과 Tactical Design으로 나눠짐



* Stactegic Design
  * Business Domain의 상황에 맞게 설계
  * Business Domain의 상황을 Event Storming 으로 공유, 비즈니스 목적별로 서비스 그룹핑
* Tactical design
  * 개발을 위한 구체적인 설계도
  * Strategic Design에서 설계한 각 Sub Domain별 Domain Model을 중심으로 설계
