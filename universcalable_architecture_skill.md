# 🛠️ Skill Name: Universal Scalable & Decoupled Architecture

## 🎯 Core Objective:
Prevent the generation of monolithic, tightly coupled, or chaotic code in any software system. Force the AI Agent to think like an expert Software Architect who embraces the Unix Philosophy: "Divide the system into small, independent modules that do one thing well, and connect them using clear, well-defined pipes." This ensures error-free Horizontal Scaling.

---

## 🚦 Strict Execution Protocol (Step-by-Step):

### 1. Structural Decomposition & Blueprinting
Before writing any line of production code, analyze the requirement and decompose the system into:
* **Decoupled Components / Microservices:** Separate the business logic based on domain and function (e.g., isolate authentication logic from data processing or notification services).
* **Pipe & Interface Design:** Define exactly how these components will communicate (e.g., via REST APIs, gRPC, Events, or asynchronous Message Queues).
* **Stateless Design:** Design the application logic to be strictly stateless. Do not rely on local server memory for sessions or file storage. This ensures multiple instances of the code can run concurrently in parallel (Horizontal Scale).

### 2. Integration of World-Class Design Patterns
The generated code must strictly adhere to the following software engineering standards:
* **SOLID Principles:** Maintain a total focus on the Single Responsibility Principle (SRP). Every class, module, or function must have only one reason to change.
* **Dependency Injection (DI):** Decouple components using interfaces or abstractions to prevent tight coupling and facilitate easy mocking/testing.
* **Database Protection:** Avoid complex, expensive runtime queries (like heavy multi-table Joins). Implement caching mechanisms (e.g., Redis) for frequently accessed data to eliminate database bottlenecks.

### 3. Leveraging External Tools & Automated Skills
As an agent, you must invoke and utilize the following automated quality control skills before delivering the code:
* **Static Analysis & Linting Skill:** Automatically run the code through available linting and code quality tools (e.g., SonarQube, ESLint, Pylint) to eliminate "Technical Debt" and enforce clean syntax.
* **Fault Tolerance & Resilience Skill:** Implement defensive programming patterns such as the Circuit Breaker pattern and graceful error handling. If a minor component fails, it must not bring down the entire system.
* **Mandatory Automated Testing Skill:** No code is considered production-ready without a comprehensive test suite:
  1. **Unit Tests:** To test each small function or endpoint in isolation.
  2. **Integration Tests:** To verify that the "pipes" connecting the different modules function perfectly under high-load and edge-case scenarios.

---

## 📦 Output Delivery Protocol:
When the user requests any feature or system, your response must be structured into the following distinct sections:

1. **🏗️ The Architectural Blueprint:** A high-level engineering explanation of how the system is decomposed and which "pipes" (APIs/Queues) connect them.
2. **💻 The Decoupled Code:** Clean, production-ready code distributed across clearly organized, well-documented, and separated files or modules.
3. **🧪 The Test Suite:** Automated test files that validate the code's stability, resilience, and capability to handle scaling and high concurrency.
