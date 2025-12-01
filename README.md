# 📈 Long/Short Volatility Breakout Strategy on KOSDAQ 150 (KIS API & Data Pipeline)

### ⚙️ Project Overview
한국투자증권(KIS) API를 활용하여 KODEX KOSDAQ 150 **Leverage/Inverse ETF**에 동일한 **변동성 돌파 로직**을 적용한 **양방향(Long/Short) 모멘텀 전략** 시스템입니다.
**복잡한 금융사 API 및 외부 데이터 파이프라인**을 구축하는 데 초점을 맞췄습니다.

### 🔑 Advanced API Integration (금융 시스템 연동)
* **KIS API 구현:** **래퍼 패키지 없이** 직접 Requests를 사용하여 **Access Token 발급 및 Hash Key 생성** 로직을 구현했습니다.

### 💾 Data Engineering & Acquisition
* **Custom Data Pipeline:** API가 제공하지 않는 장기간의 시세 데이터 확보를 위해 **BeautifulSoup**을 활용하여 네이버 금융 데이터를 크롤링했습니다.
* **Efficiency:** 수집된 시계열 데이터(Time Series Data)를 Pandas로 정형화하고 백테스팅 엔진에 공급하는 **안정적인 파이프라인**을 구축했습니다.

### 📊 Strategy & Backtesting
* **Strategy:**
    1.  **방향성 결정:** KOSDAQ 150 레버리지 ETF에 변동성 돌파 로직(Target Price > Current Price)이 감지되면 **'롱(Long)' 포지션** 진입 (Leverage 매수).
    2.  **하락 베팅:** 반대로 인버스 ETF에 동일 로직이 감지되면 **'숏(Short)' 포지션** 진입 (Inverse 매수).
    3.  **청산:** 다음 날 시장 시가(Open Price)에 무조건 청산하는 **단기 트레이딩** 방식.
* **Verifier:** `etf_bt.py`는 **Pandas/NumPy** 기반의 자체 벡터 백테스팅 엔진을 사용하여 전략의 수익률, MDD, Calmar Ratio를 계산합니다.

<img width="1200" height="800" alt="2017-09 ~ 2025-03 etf equity curve" src="https://github.com/user-attachments/assets/4a9f34e6-d0dc-4528-be6e-1d888e986bbb" />

### 🔍 Technology Stack
* **Language:** Python 3.11
* **Libraries:** Pandas, NumPy, Matplotlib, **Requests, BeautifulSoup**
* **API:** 한국투자증권 Open API (Real-Time Trading), Naver Finance (Data Source)
