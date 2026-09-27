# SRE SENTINEL
### Autonomous AI Site Reliability Engineering Platform

SRE SENTINEL is a production-style, interactive, real-time AI-powered Site Reliability Engineering (SRE) platform. It monitors a live local microservices environment, detects multivariate anomalies using Machine Learning (`scikit-learn` `IsolationForest`), investigates root causes via a 7-agent `LangGraph` state graph workflow and `LangChain` structured output chains, enforces human-in-the-loop authorization, executes safe Model Context Protocol (MCP) tools, verifies recovery against healthy metric baselines, and generates comprehensive post-incident reports.

---

## 🌟 Key Architecture & Features

- **Live Microservices Environment**: Local Python runtime engine simulating API Gateway, Order Service, Payment Service, Database Layer, Cache Layer, and Background Worker Queue producing real HTTP traffic, DB connection pools, latency, and logs.
- **Real-time Telemetry & Monitoring**: Continuous collection of CPU, Memory, Request Rate (RPS), Error Rate, P50/P95/P99 Latency, DB Latency, Connection Pool Utilization, Queue Depth, Cache Hit Rate, and Service Health.
- **Machine Learning Anomaly Detection**: `scikit-learn` `IsolationForest` multivariate anomaly score calculation combined with rolling Z-scores and baseline deviation analytics.
- **LangChain & LangGraph Multi-Agent Engine**: 7 SRE agents orchestrated via a state graph:
  1. `MonitoringAgent`: Gathers system telemetry and metric vectors.
  2. `AnomalyDetectionAgent`: Evaluates ML isolation scores and Z-scores.
  3. `InvestigationAgent`: Correlates metrics with application error logs via MCP tools.
  4. `RCAAgent`: Executes structured LLM chains to identify exact root cause.
  5. `RemediationAgent`: Formulates safe MCP tool proposals and requests approval.
  6. `VerificationAgent`: Verifies post-remediation recovery against baseline bounds.
  7. `IncidentReporterAgent`: Generates post-incident HTML, JSON, and PDF reports.
- **Deterministic Diagnostic Fallback**: Fallback heuristic pattern engine when LLM API keys or local Ollama instances are offline, guaranteeing 100% platform uptime.
- **Model Context Protocol (MCP)**: Allowlisted tool catalog (`query_metrics`, `query_logs`, `get_service_health`, `restart_service`, `clear_cache`, `restart_worker`, `scale_service`, `run_health_check`, `rollback_service`) with strict input schema validation.
- **Real Chaos Engineering Subsystem**: 12 selectable fault scenarios (`DATABASE_SLOWDOWN`, `CPU_SPIKE`, `MEMORY_LEAK`, `LATENCY_SPIKE`, `ERROR_STORM`, `CONNECTION_POOL_EXHAUSTION`, `QUEUE_BACKLOG`, `CACHE_FAILURE`, `SERVICE_FAILURE`, `TRAFFIC_SPIKE`, `DEPENDENCY_FAILURE`, `CASCADE_FAILURE`).
- **Human-In-The-Loop Approval**: Mandatory guardrail modal preventing destructive remediation without explicit human approval.
- **WebSocket Event Streaming**: `/ws/live` endpoint pushing real-time 1s telemetry frames, log streams, agent node execution transitions, and approval requests to the frontend.
- **Interactive Modern Dark Frontend**: React 18, TypeScript, Vite, Tailwind CSS, Recharts, Lucide Icons, and Framer Motion visualizer featuring Control Center, Live Metric Charts, Agent Trace visualizer, AI RCA Panel, Log Explorer, Service Topology Map, Chaos Lab, MCP Tool Center, Incident History, and Analytics.

---

## 🛠 Tech Stack

- **Backend**: Python 3.14, FastAPI, Uvicorn, WebSockets, Pydantic v2, SQLite
- **AI / ML**: LangChain, LangGraph, scikit-learn (`IsolationForest`), NumPy, Pandas
- **Reporting**: ReportLab (PDF), HTML5, JSON
- **Frontend**: React 18, TypeScript, Vite, Tailwind CSS, Recharts, Lucide React
- **Testing**: Python `unittest`, `pytest`

---


## 📖 Documentation
- [ARCHITECTURE.md](ARCHITECTURE.md): System architecture, ML design, LangGraph graph structure, and MCP integration.
- [DEMO_GUIDE.md](DEMO_GUIDE.md): Step-by-step presentation script for recruiters, hackathons, and engineering demos.
- [INTERVIEW_GUIDE.md](INTERVIEW_GUIDE.md): In-depth answers to key technical interview questions.
