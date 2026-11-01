# KW Univ. Computer Network 실습

광운대학교 전공수업 **컴퓨터 네트워크** 과목에서 진행한 실습을 모아둔 저장소입니다.

## 저장소 구성

| 경로 | 설명 |
| --- | --- |
| `src/`, `build.gradle` | 소켓 프로그래밍 실습용 Spring Boot 프로젝트 (`CN-socket`) |
| `KW_MMDS_Colab_2.ipynb` | Spark를 이용한 빈발 패턴 마이닝(FP-Growth) Colab 실습 |

## 1. 소켓 프로그래밍 (`CN-socket`)

Java / Spring Boot 기반의 소켓 프로그래밍 실습 프로젝트입니다.

### 기술 스택

- Java 21
- Spring Boot 3.5.6
- Spring Integration
- Lombok
- Gradle (Wrapper 포함)

### 프로젝트 구조

```
src
├── main
│   ├── java/kwu/CN_socket/CnSocketApplication.java   # 애플리케이션 진입점
│   └── resources/application.properties
└── test
    └── java/kwu/CN_socket/CnSocketApplicationTests.java
```

> 현재는 프로젝트 초기 설정(스캐폴딩) 단계이며, 소켓 통신 로직은 이후 구현하여 추가할 예정입니다.

### 실행 방법

JDK 21이 설치되어 있어야 합니다.

```bash
# 실행
./gradlew bootRun

# 테스트
./gradlew test
```

Windows에서는 `gradlew.bat`을 사용합니다.

## 2. Frequent Pattern Mining in Spark (`KW_MMDS_Colab_2.ipynb`)

Instacart 주문 데이터(약 13만 건)에 Spark MLlib의 **FP-Growth** 알고리즘을 적용해 빈발 항목집합과 연관 규칙을 찾는 실습입니다.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SXXNHU/kwu-computer-network/blob/master/KW_MMDS_Colab_2.ipynb)

### 진행 내용

1. `products`와 `order_products__train`을 join한 뒤 `order_id`별로 상품명을 묶어 장바구니(basket) 단위로 변환
2. `minSupport=0.01`, `minConfidence=0.5`로 FP-Growth를 학습하고 빈발 항목집합 및 연관 규칙의 개수 계산
3. 가장 빈번하게 등장하는 상품 찾기
4. `minSupport=0.001`로 낮춰 재학습하고 결과 개수 비교
5. 연관 규칙을 `confidence` 내림차순으로 정렬해 확인하고, 규칙에서 읽을 수 있는 소비 패턴 해석

### 실행 환경

- Google Colab
- PySpark, OpenJDK 8
- 데이터는 노트북 안에서 Google Drive 인증 후 내려받습니다. 실행 시 안내에 따라 인증해야 합니다.

## 작성자

- [SXXNHU](https://github.com/SXXNHU)
