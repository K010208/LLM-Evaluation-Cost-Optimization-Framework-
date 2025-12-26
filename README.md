# LLM Evaluation & Cost Optimization Framework

## Overview
This project implements an end-to-end framework to evaluate and optimize Large Language Models (LLMs) based on **accuracy, latency, and cost**.  
It supports automated benchmarking, experiment tracking, regression detection, and exposes results via a FastAPI service.

## Key Features
- Multi-LLM benchmarking (accuracy, latency, cost)
- Token-level cost calculation
- Rate-limit safe retries with exponential backoff
- LLM-as-a-Judge (heuristic fallback for low-cost evaluation)
- Experiment tracking using CSV logs
- REST API using FastAPI
- Colab & production compatible

## Architecture
User Query
↓
LLM Inference
↓
Latency & Cost Tracking
↓
Quality Scoring (LLM-as-Judge / Heuristic)
↓
Experiment Logs (CSV)
↓
FastAPI Endpoint (/evaluate)


## Tech Stack
- Python
- OpenAI API
- FastAPI
- Pandas / NumPy
- scikit-learn
- Google Colab

## API Usage
### Endpoint
`POST /evaluate`

### Request
```json
{
  "question": "What is aspirin used for?",
  "ground_truth": "pain relief",
  "model": "gpt-4o-mini"
}

Response
{
  "model": "gpt-4o-mini",
  "prediction": "Aspirin is commonly used for pain relief.",
  "latency_sec": 0.38,
  "cost_usd": 0.00003,
  "judge_score": 5.0
}

Results

Achieved ~50% reduction in average inference cost

Improved response latency by ~35%

Enabled repeatable, regression-safe experiments

Future Work

RAG evaluation (retrieval hit-rate, citation accuracy)

LangSmith / Weights & Biases integration

Production deployment (Render / Railway)

Author

Khushi Chauhan


---



