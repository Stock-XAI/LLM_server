# 주가 예측 API 서버 (Jupyter Notebook)

이 프로젝트는 Transformer 기반 모델을 이용해 주가 예측을 수행하는 간단한 FastAPI 서버를 Jupyter Notebook 환경에서 실행할 수 있도록 구성한 것입니다. ngrok을 통해 외부에서도 API 호출이 가능합니다.

## 주요 기능

- 4bit로 양자화된 주가 예측 모델(`finma-7b`) 로드
- FastAPI 기반 REST API 서버 실행
- ngrok을 이용한 외부 접속 주소 생성

## 설치 라이브러리

다음과 같은 라이브러리를 노트북 내부에서 설치합니다:

```bash
pip install fastapi uvicorn nest-asyncio pyngrok
pip install transformers accelerate torch pandas yfinance finance-datareader
pip install bitsandbytes peft shap matplotlib
````

## 실행 방법

1. `API_server.ipynb` 파일을 열고 위에서부터 셀을 순차 실행합니다.
2. 모델 로드 → 서버 실행 → ngrok 주소 출력
3. 출력된 ngrok 주소를 통해 외부에서 API 호출 가능

## 예시 요청

```http
GET /predict?ticker=005930.KS&horizon_days=7
```

* `ticker`: 종목 코드 (예: AAPL, 005930.KS)
* `horizon_days`: 예측 기간 (1, 7, 30일 중 선택)

## 참고사항

* 최소 6GB 이상의 GPU RAM이 필요하며, EC2 free tier로는 동작하지 않아 colab에서 동작시키는 것을 가정하여 구현하였습니다.
* 실제 서비스용으로는 Python 스크립트 또는 Docker 환경으로 이전하여 배포해야할 필요가 있습니다.
* huggingface 및 ngrok 토큰 등록이 필요합니다.
