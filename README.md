# Stock Price Prediction API Server (Jupyter Notebook)

This project provides a simple FastAPI server that performs stock price prediction using a Transformer-based model. It is designed to run within a Jupyter Notebook environment and allows external API access through ngrok.

## Key Features

* Loads a 4-bit quantized stock prediction model (`finma-7b`)
* Runs a REST API server using FastAPI
* Generates an external access URL via ngrok

## Required Libraries

The following libraries should be installed within the notebook:

```bash
pip install fastapi uvicorn nest-asyncio pyngrok
pip install transformers accelerate torch pandas yfinance finance-datareader
pip install bitsandbytes peft shap matplotlib
```

## How to Run

1. Open the `API_server.ipynb` file and run each cell sequentially.
2. Load the model → Start the server → Display the ngrok URL
3. Use the displayed ngrok URL to make API calls from outside the notebook.

## Example Request

```http
GET /predict?ticker=005930.KS&horizon_days=7
```

* `ticker`: Stock symbol (e.g., AAPL, 005930.KS)
* `horizon_days`: Prediction period (choose from 1, 7, or 30 days)

## Notes

* Requires at least 6GB of GPU RAM. Not compatible with EC2 free tier; assumed to run on Google Colab.
* For production deployment, consider converting to a standalone Python script or Docker container.
* Registration of Hugging Face and ngrok tokens is necessary.
