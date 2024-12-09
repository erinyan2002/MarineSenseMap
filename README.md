# **MarineSense Map: 해양 환경 모니터링 시스템**

---

## **프로젝트 개요**

**MarineSense Map**은 선박에 부착된 센서를 통해 수집된 데이터를 기반으로, 해양 환경과 수질 상태를 실시간으로 모니터링하고 시각적으로 표시하는 플랫폼입니다.  
실제 데이터를 대신하여 **API를 통해 실시간 데이터를 받아와** 시스템의 기능을 검증하고 시연할 수 있도록 설계되었습니다.  

시뮬레이션 환경에서는 선박의 이동, 수질 상태, 그리고 수질 지수(WQI)를 기반으로 생성된 데이터를 활용하며, 지도와 차트를 통해 직관적으로 데이터를 확인할 수 있습니다.  
데이터는 **Firebase**에 저장되어 실시간 동기화 및 관리를 지원합니다.

![KakaoTalk_20241210_003708224 (1)](https://github.com/user-attachments/assets/a6f3913f-d69d-49b3-99cb-2717478126fa)


---

## **시뮬레이션 기반 데이터 구성**

1. **AIS 데이터**
   - **API**를 통해 선박의 실시간 위치 및 ID 데이터를 받아왔습니다.
   - 위도 및 경도를 기반으로 이동 경로를 지도에 표시.

2. **수질 데이터**
   - 온도, 염도, 탁도 등의 수질 변수를 API에서 가져온 데이터를 기반으로 처리.
   - **수질 지수(WQI)**를 기준으로 데이터를 5단계 등급으로 색상화:
     - **매우 좋음 (파란색):** 80~100
     - **좋음 (초록색):** 60~79
     - **보통 (노란색):** 40~59
     - **나쁨 (주황색):** 20~39
     - **매우 나쁨 (빨간색):** 0~19

3. **시간 변화 데이터**
   - 특정 시간 간격(예: 10초)마다 데이터를 업데이트하며 실시간 모니터링을 구현.

4. **Firebase 데이터 저장**
   - 수집된 데이터를 Firebase에 저장하여 효율적인 데이터 동기화 및 관리.
   - Firebase의 실시간 데이터베이스를 사용하여 사용자 인터페이스와 데이터를 실시간으로 업데이트.

---

## **주요 기능**

### **1. AIS Stream 데이터 관리**
- **API**를 통해 선박의 실시간 위치, ID, 이동 경로 데이터를 받아 지도에 표시.
- 데이터를 통해 선박의 이동 상태와 경로를 실시간으로 확인 가능.

### **2. WQI 기반 색상화**
- 수질 지수를 기반으로 선박의 상태를 시각적으로 구분:
  - **파란색:** 매우 좋음
  - **초록색:** 좋음
  - **노란색:** 보통
  - **주황색:** 나쁨
  - **빨간색:** 매우 나쁨
 
![image](https://github.com/user-attachments/assets/3d9fc08a-80b6-4b31-827a-74f962c43b61)


### **3. 경유 선박 리스트**
- WQI 기준에서 "나쁨" 이하로 평가된 선박을 자동으로 식별하고 리스트화.
- 관련 선박의 상세 정보를 제공하여 수질 오염 원인을 추적.

  
![image](https://github.com/user-attachments/assets/90a159be-4f48-4389-9662-d81879b29eb0)


### **4. 수질 데이터 시각화**
- 지도에서 선박의 위치와 WQI 상태를 확인.
- **파이 차트:** 전체 선박의 수질 등급 분포를 요약.
- **라인 차트:** 시간에 따른 수질 데이터 변화를 시각화.

![image](https://github.com/user-attachments/assets/a37db440-0824-43a2-a55d-c8d950c8b01d)



### **5. 상세 측정 정보**
- 각 선박의 온도, 염도, 탁도 등 세부 데이터를 사용자에게 제공.

![image](https://github.com/user-attachments/assets/7e48fc32-ed0b-415e-91d3-ce281a19a288)


### **6. 측정 현황 분석**
- 시간에 따른 WQI 변화를 차트로 표현하여 경향성을 분석.
- 특정 지역에서의 수질 문제를 추적.

![image](https://github.com/user-attachments/assets/ab509d3d-de39-4067-8ef2-86045ff8bd15)



---

## **설치 및 실행 방법**

### **요구사항**
- **Python** >= 3.10
- **Firebase 계정 및 프로젝트 설정**
- **GIS 데이터 처리 라이브러리**

### **실행 방법**
### **1. 저장소를 클론합니다.**
   ```bash
   git clone https://github.com/erinyan2002/MarineSenseMap.git
   
### **2. 의존성을 설치합니다.**
  ```bash
   pip install -r requirements.txt


3. Python 스크립트를 실행하여 데이터를 처리합니다:
 ```bash
   python simulate.py
   
4. 브라우저에서 **http://localhost:3000**으로 접속하여 실시간 데이터를 확인합니다.


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

**MarineSense Map**은 **API**와 **Firebase**를 활용하여 해양 환경을 효율적으로 관리할 수 있는 혁신적인 도구입니다.  
직관적인 시각화와 분석 도구를 통해 사용자는 데이터 기반 의사결정을 내릴 수 있으며, 환경 보호와 지속 가능한 해양 관리를 지원합니다.





