# Multi-Tier Distributed Healthcare Infrastructure 

An enterprise-grade, distributed clinical ecosystem designed to orchestrate medical histories, handle real-time medical scheduling queues, and securely process clinical file streaming. The architecture implements a fully decoupled multi-tier topology separating presentation layers, broker middleware nodes, and transaction backend servers.

## Architectural Topology & Component Mapping

The ecosystem is structurally divided into three independent operational boundaries:

1. **App_Server (Enterprise Backend):** Engineered in Java SE/EE and deployed across distributed clusters on Eclipse GlassFish Server. It houses core business definitions (`Objetos_SecretariaSalud`) and encapsulates transactional database connectivity endpoints (`BaseDatosExpedienteClinico`).
2. **Middleware (Routing Broker):** Built in Python using the Flask micro-framework. It acts as an API Gateway and dynamic routing manager (`rutas.py`), orchestrating payloads across distributed nodes and utilizing the MQTT protocol (via paho-mqtt and Mosquitto) for asynchronous message-event reacting.
3. **Web_Server (Client Viewport):** A lightweight client presentation layer built with web standards to ingest distributed streams and capture user transaction inputs.

## Infrastructure Stack & Protocols

* Enterprise Core: Java EE, GlassFish Application Server Deployment
* Middleware Broker: Python, Flask RESTful Framework
* Event fabrics: MQTT Protocol (Mosquitto Event Broker / Paho-MQTT client)
* Database Solution: MongoDB (Non-relational persistent electronic health records)
* Build Engine: Maven/Ant Dependency Lifecycle tools

## Deployment Execution Protocol

1. **Initialize App Database Assets:** Open the `App_Server/` repository in your IDE, compile `Objetos_SecretariaSalud` followed by `BaseDatosExpedienteClinico`. Execute the `Presets.java` runtime class to provision initial clinical constraints.
2. **Launch Python Middleware:** Navigate to the `Middleware/` footprint via terminal, configure environment routes inside `rutas.py`, and spin up the gateway:
   cd Middleware
   python app.py
3. **Deploy Enterprise Clusters:** Deploy all compiled Java application archives into active GlassFish running instances.
4. **Boot Presentation Services:** Open a distinct console footprint, instantiate the web host and navigate to local authentication screens:
   cd Web_Server
   python -m http.server 8800
