# **MarineSense Map: 해양 환경 모니터링 시스템**

---

## **프로젝트 개요**

**MarineSense Map**은 선박에서 수집된 데이터를 기반으로, 해양 환경과 수질 상태를 실시간으로 모니터링하고 시각적으로 표시하는 플랫폼입니다.  
실제 데이터를 대신하여 **API를 통해 실시간 데이터를 받아와** 시스템의 주요 기능을 구현하였습니다.

플랫폼은 선박의 이동 경로와 수질 데이터를 시각화하여 직관적인 정보를 제공합니다. 또한, 데이터는 **Firebase**를 통해 실시간으로 동기화 및 관리됩니다.

![KakaoTalk_20241210_003708224 (2)](https://github.com/user-attachments/assets/7f1db221-bbe7-454b-9095-5f1b7962b54c)

---

## **주요 데이터 구성**

1. **AIS 데이터**

   - **API**를 통해 선박의 실시간 위치 및 ID 데이터를 수집.
   - 위도와 경도를 기반으로 선박의 이동 경로를 지도에 표시.

2. **수질 데이터**

   - 온도, 염도, 탁도 등의 수질 정보를 처리.
   - **수질** **지수**(WQI)를 5단계로 구분하여 색상화:
     - **파란색:** 매우 좋음 (80~100)
     - **초록색:** 좋음 (60~79)
     - **노란색:** 보통 (40~59)
     - **주황색:** 나쁨 (20~39)
     - **빨간색:** 매우 나쁨 (0~19)

3. **시간 변화 데이터**

   - 실시간 데이터 업데이트를 통해 변화하는 수질 상태를 추적.

4. **Firebase 데이터 저장**
   - 데이터를 Firebase에 저장하여 효율적인 동기화와 실시간 데이터 관리 구현.

---

## **주요 기능**

### **1. 실시간 AIS 데이터 관리**

- **API**를 통해 선박의 위치, ID, 이동 경로 데이터를 수집하여 지도에 표시.
- 사용자는 선박의 상태와 경로를 실시간으로 확인 가능.

### **2. WQI 기반 색상화**

- 수질 지수(WQI)에 따라 선박의 상태를 색상으로 표시:
  - **파란색:** 매우 좋음
  - **초록색:** 좋음
  - **노란색:** 보통
  - **주황색:** 나쁨
  - **빨간색:** 매우 나쁨

![수질 등급 색상화 예시](https://github.com/user-attachments/assets/3d9fc08a-80b6-4b31-827a-74f962c43b61)

### **3. 경유 선박 리스트**

- WQI 기준 "나쁨" 이하로 평가된 선박을 자동으로 식별하여 리스트화.
- 리스트에서 해당 선박의 상세 정보를 제공하여 오염 원인 추적 가능.

![경유 선박 리스트 예시](https://github.com/user-attachments/assets/90a159be-4f48-4389-9662-d81879b29eb0)

### **4. 수질 데이터 시각화**

- **파이 차트:** 전체 선박의 수질 등급 분포를 요약하여 표시.

![수질 데이터 시각화 예시](https://github.com/user-attachments/assets/a37db440-0824-43a2-a55d-c8d950c8b01d)

### **5. 상세 측정 정보 제공**

- 선박별 온도, 염도, 탁도 등 세부 데이터를 제공.

![상세 측정 정보 예시](https://github.com/user-attachments/assets/7e48fc32-ed0b-415e-91d3-ce281a19a288)

### **6. 측정 현황 분석**

- **라인 차트:** 시간에 따른 WQI 변화를 시각화.
- 특정 시간 간격으로 업데이트되는 데이터를 차트로 표현하여 경향성 분석 가능.
- 지역별 수질 문제를 파악하여 환경 관리에 도움.

![측정 현황 분석 예시](https://github.com/user-attachments/assets/ab509d3d-de39-4067-8ef2-86045ff8bd15)

---

## **설치 및 실행 방법**

### **요구사항**

- **Python** >= 3.10
- **Firebase 계정 및 프로젝트 설정**
- **GIS 데이터 처리 라이브러리**

### **실행 절차**

1. **저장소를 클론합니다.**

   ```bash
   git clone https://github.com/erinyan2002/MarineSenseMap.git
   ```

2. **의존성을 설치합니다.**

   ```bash
   pip install -r requirements.txt
   ```

3. **Python 스크립트를 실행하여 데이터를 처리합니다:**

   ```bash
   python ais_json_generator.py
   ```

4. **브라우저에서 **http://localhost:3000**으로 접속하여 실시간 데이터를 확인합니다.**

---

## **사용 방법**

### **1. 지도 인터페이스**

- 각 선박의 아이콘을 클릭하면 해당 선박의 **세부 데이터를 확인**할 수 있습니다.

### **2. 수질 등급 필터링**

- "나쁨" 이하의 등급만 필터링하여 지도에 표시할 수 있습니다.

### **3. 데이터 분석 차트**

- **파이 차트**를 통해 선박의 수질 등급 분포를 시각적으로 확인합니다.
- **라인 차트**에서 시간에 따른 WQI 변화를 분석합니다.

### **4. 오염 의심 선박 추적**

- "경유 선박 리스트"를 통해 수질 오염 원인을 추적하고 필요한 조치를 파악합니다.

---

## **기대 효과**

### **1. 실시간 데이터 모니터링**

- **Firebase**와 **API 데이터**를 통해 시스템의 기능과 성능을 검증할 수 있습니다.

### **2. 환경 관리 최적화**

- 실시간 데이터를 활용하여 시스템을 환경 보호 목적으로 테스트하고 최적화합니다.

### **3. 확장성 검증**

- Firebase와 통합하여 다양한 선박 수와 시나리오에서 시스템의 성능과 확장성을 확인할 수 있습니다.

### **4. 사용자 친화적 데이터 시각화**

- 직관적인 인터페이스와 차트를 통해 데이터를 쉽게 분석하고 이해할 수 있습니다.

---

## **결론**

**MarineSense Map**은 **API**와 **Firebase**를 활용하여 해양 환경을 효율적으로 관리할 수 있는 혁신적인 도구입니다.<br/>
직관적인 시각화와 분석 도구를 통해 사용자는 데이터 기반 의사결정을 내릴 수 있으며, 환경 보호와 지속 가능한 해양 관리를 지원합니다.
