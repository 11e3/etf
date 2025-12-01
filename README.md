# 📈 ETF Asset Allocation & Swtiching Strategy (KIS API & Data Engineering)

### ⚙️ Project Overview
한국투자증권(KIS) API를 활용하여 KODEX KOSDAQ 150 레버리지/인버스 ETF를 스위칭하는 동적 자산 배분(Dynamic Asset Allocation) 전략입니다.

### 🔑 Advanced API Integration (금융 시스템 연동)
* **KIS API 구현:** **래퍼 패키지 없이** 직접 Requests를 사용하여 **Access Token 발급 및 Hash Key 생성** 로직을 구현했습니다.

### 💾 Data Engineering & Acquisition
* **Custom Data Pipeline:** API가 제공하지 않는 장기간의 시세 데이터 확보를 위해 **BeautifulSoup**을 활용하여 네이버 금융 데이터를 크롤링했습니다.
* **Data Validation:** 수집된 시계열 데이터(Time Series Data)를 Pandas로 정형화하고 백테스팅 엔진에 공급하는 **파이프라인**을 구축했습니다.

### 📊 Strategy & Backtesting
* **Strategy:** 변동성 돌파 전략에 **이동평균(MA)** 및 **노이즈 비율(Noise Ratio)** 필터를 적용하여, 시장 상황에 따라 레버리지 또는 인버스 ETF로 자산을 전환(Switching)합니다.
* **Verifier:** `etf_bt.py`는 **Pandas/NumPy** 기반의 자체 벡터 백테스팅 엔진을 사용하여 전략의 수익률, MDD, Calmar Ratio를 계산합니다.

<img width="1200" height="800" alt="2017-09 ~ 2025-03 etf equity curve" src="https://github.com/user-attachments/assets/4a9f34e6-d0dc-4528-be6e-1d888e986bbb" />

### 🔍 Technology Stack
* **Language:** Python 3.11
* **Libraries:** Pandas, NumPy, Matplotlib, **Requests, BeautifulSoup**
* **API:** 한국투자증권 Open API (Real-Time Trading), Naver Finance (Data Source)
