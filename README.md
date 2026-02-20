# Telegram Trade Signal Bridge

## Overview

An **event-driven system** that captures trading signals from communication platforms (e.g. Telegram / Discord), processes them via a **.NET Core ASP.NET API**, and executes trades automatically using **MQL5** on MetaTrader 5.

The system includes a **UWP frontend** for configuration and monitoring and is designed for **real-time signal handling, modularity, and extensibility**.

This project demonstrates end-to-end integration between UI, backend services, and external trading systems.

---

## Key Challenges & Solutions

### Platform Restrictions
Some platforms restrict bot access in private or protected groups. To work around this, the system uses a **notification listener** to capture incoming messages and extract relevant signals without direct bot integration.

### Real-Time Data Flow
Ensuring low-latency signal delivery required a **decoupled, event-driven architecture** capable of handling concurrent requests reliably.

### Reliability & Safety
Robust **error handling and logging** were implemented to ensure stability during live trading scenarios.

---

## Architecture

The system is composed of three main components:

### 1. UWP Frontend (C#)
- User interface for configuring signal sources and trading parameters
- Start/stop signal listening
- Displays system status and notifications

### 2. ASP.NET Core API (C#)
- Acts as an intermediary between the UI and trading engine
- Receives, validates, and stores incoming signals
- Exposes endpoints for signal retrieval by MQL5

### 3. Trading Engine (MQL5)
- Polls the API for new signals
- Executes trades on MetaTrader 5
- Applies risk management logic (lot size, stop-loss, take-profit, breakeven)

---

## Data Flow

1. Signals are captured from platform notifications in the UWP app
2. Parsed signals are sent to the ASP.NET Core API as JSON
3. MQL5 scripts retrieve signals from the API
4. Trades are executed and managed automatically on MetaTrader 5

---

## Technologies Used

- **UWP (C#)** – Desktop UI and signal monitoring  
- **ASP.NET Core Web API (C#)** – Backend processing and communication  
- **MQL5** – Automated trade execution and management  
- **JSON** – Data exchange format across components  

---

## Why This Project Matters

This project showcases:
- Real-world **event-driven system design**
- **Cross-platform integration** (UI → API → trading engine)
- Practical handling of **external platform constraints**
- Clean separation of concerns and modular architecture
