
# AI Stock Trading Agent - by Thirunere Chelvan R.

## Overview

This is a fully autonomous AI-powered stock trading agent built using n8n, Zerodha Kite API, and Python. It analyzes Indian and global market data, financial news sentiment, and technical indicators to make intelligent buy/sell decisions in real-time. The agent adapts strategies based on performance and logs every decision.

## Features

- Real-time stock market analysis (India + global indices)
- Sentiment analysis on financial news using OpenAI/Gemini
- Technical indicator evaluation (RSI, MACD, volume)
- Automated buy/sell execution via Zerodha Kite API
- WhatsApp alerts for trade updates
- Strategy monitoring and auto-update when losing
- Full decision logs with reasons

## Components & Roles

| File | Purpose |
|------|---------|
| `n8n_workflow.json` | n8n automation to orchestrate all components |
| `strategy_engine.py` | Combines indicators, sentiment, and scoring logic |
| `sentiment_analyzer.py` | Uses OpenAI/Gemini to analyze market news |
| `trade_executor.py` | Executes trades using Zerodha Kite Connect |
| `global_markets_fetcher.py` | Fetches international market and economic data |
| `logger.py` | Logs all trade actions and strategy outcomes |
| `strategy_updater.py` | Automatically updates strategy if performance drops |
| `config.env` | Environment variables: API keys, preferences |
| `logs_template.csv` | Template to log trade data and agent decisions |
| `README.md` | Documentation (you are here) |

## Prerequisites

- Zerodha Kite Connect Account & API Key
- OpenAI or Gemini API Key for sentiment analysis
- Twilio/360Dialog API for WhatsApp messages
- Python 3.9+
- n8n (self-hosted or desktop)

## Setup Guide

### 1. Clone & Setup Environment

```bash
git clone <this_repo>
cd AI_Trading_Agent_By_Thirunere
cp config.env.example config.env
```

### 2. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure API Keys

Fill in the `config.env` with your:

- `ZERODHA_API_KEY`, `ZERODHA_API_SECRET`, `ACCESS_TOKEN`
- `OPENAI_API_KEY` or `GEMINI_API_KEY`
- `TWILIO_SID`, `TWILIO_AUTH_TOKEN`, `WHATSAPP_FROM`, `WHATSAPP_TO`

### 4. Import n8n Workflow

- Open your n8n instance
- Import `n8n_workflow.json`
- Adjust any credentials or webhook settings

### 5. Run Agent

You can either:
- Run Python modules via `n8n` automation, or
- Trigger manually: `python strategy_engine.py`

### 6. Monitoring

- WhatsApp alerts on each buy/sell with reason
- `logs_template.csv` will be filled automatically
- Check logs for decision logic, success/failure

## AI Agent Behavior

- Agent runs on schedule (every 5-15 minutes)
- It fetches real-time stock data
- Performs sentiment analysis on top news
- Scores each stock based on 3 factors:
  - Technical indicators
  - Sentiment
  - Global impact
- Executes trades via Zerodha if score passes threshold
- If 3 or more losing trades, strategy switches automatically

## Security Notes

- Keep `config.env` private
- Run n8n in a secure local or cloud environment
- Avoid sharing logs containing sensitive trading info

## License

Private & Confidential - owned by Thirunere Chelvan R.
