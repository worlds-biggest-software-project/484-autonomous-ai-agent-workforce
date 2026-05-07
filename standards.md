# Standards & API Reference

> Project: Autonomous AI Agent Workforce · Generated: 2026-05-07

## Industry Standards & Specifications

### ISO Standards

**ISO/IEC 42001:2023 — AI Management System (AIMS)**
- URL: https://www.iso.org/standard/81230.html
- The first global certifiable standard for managing AI systems within an organisation. Establishes requirements for governance, risk management, documentation, stakeholder engagement, and continual improvement of AI deployments. Increasingly required by Fortune 500 procurement teams as a prerequisite for enterprise AI contracts. Any autonomous agent workforce platform deployed in regulated industries should be designed to support an ISO 42001-aligned AIMS.

**ISO/IEC 27001:2022 — Information Security Management System (ISMS)**
- URL: https://www.iso.org/standard/27001
- Foundation standard for information security governance. Agents operating across enterprise systems handle sensitive data and must be designed within an ISO 27001-compliant security posture (access controls, audit logging, incident management). Directly relevant to agent vault/secret management and data residency requirements.

**ISO/IEC 27701:2019 — Privacy Information Management**
- URL: https://www.iso.org/standard/71670.html
- Extension of ISO 27001 addressing privacy management. Agents that process personal data (HR onboarding, customer service) must comply with privacy controls defined here and align with GDPR/CCPA obligations.

---

### W3C & IETF Standards

**RFC 6749 — OAuth 2.0 Authorization Framework**
- URL: https://www.rfc-editor.org/rfc/rfc6749
- The foundational protocol for delegated authorisation. AI agents acting on behalf of human users or services must authenticate using OAuth 2.0 flows. Relevant extensions include RFC 9396 (Rich Authorization Requests), RFC 9449 (Demonstrating Proof-of-Possession), and RFC 9126 (Pushed Authorization Requests) — all recommended by NIST's February 2026 NCCoE concept paper for agent identity and authorisation.

**RFC 8705 — OAuth 2.0 Mutual TLS Client Authentication**
- URL: https://www.rfc-editor.org/rfc/rfc8705
- Enables mutual TLS (mTLS) for OAuth 2.0 clients, allowing agents to authenticate to APIs using cryptographic client certificates rather than shared secrets. Recommended for high-security agent-to-service communication.

**OpenID Connect Core 1.0**
- URL: https://openid.net/specs/openid-connect-core-1_0.html
- Identity layer on top of OAuth 2.0, enabling agents to verify the identity of users and obtain profile information. The OpenID Foundation's AI Identity Management Community Group (filing responses to NIST RFIs on AI agent security in March 2026) is actively extending OIDC for agentic identity delegation scenarios.

**WIMSE (Workload Identity in Multi-System Environments) — IETF Working Group**
- URL: https://datatracker.ietf.org/wg/wimse/about/
- Emerging IETF standard for cryptographic workload identity, allowing agents as computational entities to have verifiable identities independent of human users. Combined with SPIFFE/SPIRE and OAuth 2.0 in the AIMS (Agent Identity Management System) framework published March 2026. Foundational for cross-enterprise agent federation.

**SPIFFE / SPIRE — Secure Production Identity Framework for Everyone**
- URL: https://spiffe.io/ · CNCF graduated project
- Provides cryptographic workload identity for agents operating in distributed infrastructure. SPIFFE IDs are the cryptographic basis for the WIMSE/AIMS agent identity framework endorsed by NIST NCCoE in February 2026. Enables zero-trust agent authentication without shared secrets.

**CloudEvents v1.0 — CNCF Graduated Specification**
- URL: https://cloudevents.io/ · https://github.com/cloudevents/spec
- Vendor-neutral specification for describing event data. Every event carries standardised metadata (ID, time, type, source) ensuring interoperability across services, platforms, and clouds. Graduated CNCF project (January 2024). Adopted by Azure EventGrid, DAPR, Knative, Argo Workflows, and Serverless Workflow. Agent orchestration engines should use CloudEvents as the event envelope when emitting trigger, completion, and escalation events.

**W3C JSON-LD 1.1 & RDF**
- URL: https://www.w3.org/TR/json-ld11/
- Provides semantic context for agent knowledge representations. Relevant for platforms implementing graph-based organisational knowledge stores where agents need to reason about entities and relationships.

---

### Data Model & API Specifications

**OpenAPI Specification 3.1 (OAS 3.1)**
- URL: https://www.openapis.org/ · https://github.com/OAI/OpenAPI-Specification
- The world's standard for describing RESTful APIs in YAML or JSON. All agent tool connectors should be described using OAS 3.1, enabling automated code generation, validation, and documentation. The Arazzo specification (an OAI extension) describes multi-step API workflow orchestration — directly applicable to agent action sequences.

**JSON Schema (Draft 2020-12)**
- URL: https://json-schema.org/specification
- Standard for validating structured JSON data. Agent tool call inputs and outputs should be validated against JSON Schema to detect hallucinated or malformed tool arguments before execution.

**GraphQL — Schema Definition Language**
- URL: https://spec.graphql.org/
- Query language and schema definition for APIs. Several enterprise platforms (Salesforce, ServiceNow, Shopify) expose GraphQL endpoints. Agent tool wrappers for these systems must handle GraphQL query construction and schema introspection.

**Protocol Buffers (Protobuf) v3 + gRPC**
- URL: https://protobuf.dev/ · https://grpc.io/
- Binary serialisation format and RPC framework used in high-throughput inter-service communication. Relevant for agent orchestration engines running at scale where JSON/REST overhead is a bottleneck. Temporal.io uses gRPC for its server API.

**AsyncAPI 3.0**
- URL: https://www.asyncapi.com/
- Specification for describing event-driven/asynchronous APIs (Kafka, WebSocket, AMQP, MQTT). Autonomous agents are inherently event-driven; AsyncAPI complements OpenAPI for documenting trigger events, completion signals, and escalation notifications.

---

### Security & Authentication Standards

**OWASP Top 10 for LLM Applications 2025**
- URL: https://genai.owasp.org/resource/owasp-top-10-for-llm-applications-2025/
- Identifies the most critical security risks for systems using LLMs, including prompt injection, insecure output handling, training data poisoning, model denial of service, and supply chain vulnerabilities. Any AI agent platform must address these risks, particularly prompt injection (via externally retrieved data passing through agent reasoning context) and insecure output handling (where agent-generated content triggers further actions).

**OWASP Top 10 for Agentic Applications 2026**
- URL: https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/
- Peer-reviewed by 100+ experts; identifies agentic-specific risks: Agent Goal Hijack, Unchecked Autonomy, Tool Misuse, Delegated Trust Abuse, Inter-Agent Poisoning, Persistent Memory Contamination. Essential reference for the security architecture of any autonomous agent platform. Published December 2025.

**NIST AI Risk Management Framework (AI RMF 1.0)**
- URL: https://airc.nist.gov/Home
- US government voluntary framework structured around Govern, Map, Measure, and Manage functions. Increasingly required by federal procurement and becoming a de facto enterprise baseline. Aligns closely with ISO 42001; NIST publishes a crosswalk document between the two. Guides how an agent platform should document, evaluate, and monitor AI risks.

**NIST NCCoE — AI Agent Identity and Authorisation (February 2026 Concept Paper)**
- URL: https://www.nccoe.nist.gov/sites/default/files/2026-02/accelerating-the-adoption-of-software-and-ai-agent-identity-and-authorization-concept-paper.pdf
- NIST's National Cybersecurity Center of Excellence proposes using OAuth 2.0 extensions (RAR, PAR, DPoP), SPIFFE/SPIRE, and MCP as the technical stack for AI agent identity and authorisation. Directly specifies the security architecture that enterprise-grade agent platforms should implement.

**EU AI Act (Regulation 2024/1689)**
- URL: https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32024R1689
- Mandatory regulation in force for EU-market products. Autonomous AI agents performing consequential enterprise decisions (credit decisions, HR, law enforcement) may be classified as high-risk under Annex III, requiring conformity assessment, logging, human oversight, and transparency obligations. Global platforms must understand which agent workflows trigger high-risk classification.

---

### MCP Server Specifications

**Model Context Protocol (MCP) — v2025-11-25 Specification**
- URL: https://modelcontextprotocol.io/specification/2025-11-25
- Wikipedia: https://en.wikipedia.org/wiki/Model_Context_Protocol
- Open protocol developed by Anthropic (November 2024), donated to the Agentic AI Foundation (AAIF) under Linux Foundation governance in December 2025. Now supported by Anthropic, OpenAI, and Google DeepMind; 500+ public MCP servers available as of early 2026. Transported over JSON-RPC 2.0 (stdio for local; HTTP/SSE for remote). Exposes three primitives: tools (callable functions), resources (read-only data by URI), and prompts (reusable templates). The de-facto standard for AI agent tool integration — all major enterprise platforms (ServiceNow, Microsoft, Zapier, Salesforce) now provide MCP servers. Any autonomous agent workforce platform should implement MCP server and client support.

**Agent2Agent (A2A) Protocol — Latest Specification**
- URL: https://a2a-protocol.org/latest/ · https://a2a-protocol.org/latest/specification/
- GitHub: https://github.com/a2aproject/A2A
- Open protocol developed by Google (April 2025), donated to the Linux Foundation. Supported by 150+ organisations including Atlassian, Box, SAP, ServiceNow, Salesforce, Workday, and all major system integrators (Deloitte, McKinsey, PwC, Accenture). Enables opaque agents built on different frameworks to communicate using standardised Agent Cards (discovery), structured task lifecycle states, and enterprise-grade security (OAuth 2.0, API Keys, mTLS over HTTP/JSON-RPC 2.0). Complements MCP: MCP handles agent-to-tool integration; A2A handles agent-to-agent interoperability. CrewAI already supports A2A; LangGraph and Microsoft Agent Framework are actively integrating it.

**OpenTelemetry GenAI Semantic Conventions**
- URL: https://opentelemetry.io/docs/specs/semconv/gen-ai/
- Agent spans: https://opentelemetry.io/docs/specs/semconv/gen-ai/gen-ai-agent-spans/
- CNCF-governed standard for observability of generative AI systems. Defines standardised attributes for spans, metrics, and events covering: model name, token counts, finish reason, tool/agent calls, retrieval steps, and reasoning chains. Adopted by Datadog, Uptrace, and major observability vendors. Each tool call, LLM invocation, and retrieval step in an agent trace should emit OpenTelemetry spans using these conventions, enabling vendor-neutral observability.

---

## Similar Products — Developer Documentation & APIs

### Automation Anywhere — Agentic Process Automation

- **Description:** Enterprise-grade agentic automation platform combining RPA digital workers, AI agents, and process reasoning engine (PRE) in one unified system. Collaboration with OpenAI on AI-native agentic solutions announced January 2026.
- **API Documentation:** https://docs.automationanywhere.com/
- **API References (Control Room REST API):** https://docs.automationanywhere.com/bundle/enterprise-v2019/page/enterprise-cloud/topics/control-room/control-room-api/api-references.html
- **SDKs/Libraries:** Python and JavaScript SDKs via docs.automationanywhere.com; Bot API for programmatic bot execution
- **Developer Guide:** https://docs.automationanywhere.com/ (getting started, API tasks, REST web services package)
- **Standards:** REST/JSON; OpenAPI-documented endpoints; OAuth 2.0 authentication
- **Authentication:** OAuth 2.0 and API token-based authentication

---

### Microsoft Copilot Studio / Microsoft Agent Framework

- **Description:** Low-code agent building platform with autonomous trigger support; integrated with 1,400+ systems via MCP and Power Platform connectors. Microsoft Agent Framework (MAF) v1.0 released April 2026 is the open-source production-ready successor to AutoGen.
- **API Documentation (Copilot Studio):** https://learn.microsoft.com/en-us/microsoft-copilot-studio/
- **API Documentation (Agent Framework):** https://learn.microsoft.com/en-us/agent-framework/overview/
- **SDKs/Libraries (MAF):** Python and .NET SDKs; https://github.com/microsoft/autogen
- **Developer Guide:** https://devblogs.microsoft.com/agent-framework/microsoft-agent-framework-version-1-0/
- **Standards:** REST/JSON; MCP server support; OpenAPI 3.1; gRPC for internal services
- **Authentication:** Azure Active Directory / Entra ID; OAuth 2.0; MSAL libraries

---

### Salesforce Agentforce

- **Description:** Enterprise agentic AI platform combining CRM data, deterministic workflow (Agentforce Script), and LLM reasoning. Ranked #1 Agentic AI Product by G2 in 2026.
- **API Documentation:** https://developer.salesforce.com/docs/einstein/genai/guide/overview.html
- **SDKs/Libraries:** Salesforce DX CLI; Apex SDK; Python and JavaScript client libraries via Salesforce platform
- **Developer Guide:** https://developer.salesforce.com/
- **Standards:** REST/JSON (Force.com API); SOAP; GraphQL (Salesforce GraphQL API); Bulk API 2.0
- **Authentication:** OAuth 2.0 (all flows); connected app configuration; JWT bearer token for server-to-server

---

### SS&C Blue Prism WorkHQ

- **Description:** Governed agentic automation platform launched April 2026, combining RPA digital workers and AI agents with audit trails, RBAC, hallucination detection, and real-time risk notifications as first-class platform features.
- **API Documentation:** https://bpdocs.blueprism.com/
- **SDKs/Libraries:** Blue Prism API (REST); VBO (Visual Business Object) SDK for custom integrations
- **Developer Guide:** https://www.blueprism.com/products/agentic-automation/
- **Standards:** REST/JSON; SOAP; OData for data connectors
- **Authentication:** OAuth 2.0; Active Directory integration; API key authentication

---

### ServiceNow — Action Fabric & AI Control Tower

- **Description:** Enterprise platform offering AI Agents (AI Specialists) across all departments, ServiceNow Otto unified AI experience, and an MCP Server (Action Fabric) exposing governed enterprise actions to any external AI agent regardless of origin.
- **API Documentation:** https://developer.servicenow.com/dev.do#!/reference
- **SDKs/Libraries:** ServiceNow REST API; JavaScript server-side APIs; ServiceNow SDK for integrations
- **Developer Guide:** https://developer.servicenow.com/
- **Standards:** REST/JSON; GraphQL; SOAP; MCP Server; OpenAPI-documented APIs
- **Authentication:** OAuth 2.0; Basic auth; API keys; mutual TLS for service accounts

---

### Anthropic Claude Agent SDK

- **Description:** SDK enabling developers to build autonomous AI agents using the same tools, agent loop, and context management that power Claude Code. Supports reading files, running commands, web search, code editing, and custom tool integration. Available in Python and TypeScript.
- **API Documentation:** https://platform.claude.com/docs/en/agent-sdk/overview
- **SDKs/Libraries:** Python: https://github.com/anthropics/claude-agent-sdk-python · npm: @anthropic-ai/claude-agent-sdk
- **Developer Guide:** https://platform.claude.com/docs/en/agent-sdk/quickstart
- **Standards:** REST/JSON; MCP client and server support; OpenAI API compatibility layer
- **Authentication:** Anthropic API key; AWS Bedrock and GCP Vertex AI deployment options

---

### LangGraph / LangChain

- **Description:** Open-source graph-based multi-agent orchestration framework. LangGraph models agents as nodes in a directed graph with persistent state, checkpointing, and time-travel debugging. Production-ready; surpassed CrewAI in GitHub stars in early 2026.
- **API Documentation:** https://docs.langchain.com/oss/python/langgraph/overview
- **Python SDK Reference:** https://reference.langchain.com/python/langgraph
- **GitHub:** https://github.com/langchain-ai/langgraph
- **LangSmith (observability):** https://docs.smith.langchain.com/
- **SDKs/Libraries:** `langgraph` (PyPI); `langgraph-sdk` (PyPI); TypeScript SDK (`@langchain/langgraph`)
- **Developer Guide:** https://langchain-ai.github.io/langgraph/
- **Standards:** REST/JSON via LangServe deployment; MCP client support; OpenTelemetry tracing via LangSmith
- **Authentication:** LangSmith API key for tracing; underlying LLM provider credentials (OpenAI, Anthropic, etc.)

---

### CrewAI

- **Description:** Open-source multi-agent framework using role-based crews architecture. Agents assigned with roles, backstories, goals, and tools. Supports A2A Protocol, model-agnostic (any LLM via LiteLLM). Fastest-growing multi-agent framework in 2026.
- **API Documentation:** https://docs.crewai.com/
- **GitHub:** https://github.com/crewAIInc/crewAI
- **SDKs/Libraries:** `crewai` (PyPI); Python 3.10–3.13; LiteLLM adapter for 100+ LLM providers
- **Developer Guide:** https://blog.crewai.com/getting-started-with-crewai-build-your-first-crew/
- **Standards:** Python SDK; A2A Protocol support; MCP tool integration; REST API via FastAPI wrapper pattern
- **Authentication:** LLM provider API keys; CrewAI Enterprise uses OAuth 2.0 for platform access

---

### Temporal.io

- **Description:** Open-source durable execution platform for long-running, reliable workflows. Temporal guarantees workflows resume exactly where they left off after crashes or infrastructure failures, making it the recommended infrastructure layer for autonomous agents running over hours or days.
- **API Documentation:** https://docs.temporal.io/
- **GitHub:** https://github.com/temporalio/temporal
- **SDKs/Libraries:** Go, Java, TypeScript, Python, .NET, PHP SDKs available via docs.temporal.io/encyclopedia/temporal-sdks
- **Developer Guide:** https://docs.temporal.io/evaluate/understanding-temporal
- **Standards:** gRPC (Temporal server API); JSON for workflow input/output; OpenTelemetry integration for tracing
- **Authentication:** mTLS for cluster-to-worker communication; API keys for Temporal Cloud; namespace-level access control

---

## Notes

**Agent identity is an active standards gap.** As of May 2026, the WIMSE/AIMS/SPIFFE stack is being standardised but is not yet universally supported by identity providers or cloud platforms. Platforms deploying agents across organisational boundaries should monitor the IETF WIMSE working group and NIST NCCoE guidance closely, as this is the most rapidly evolving area of the standards landscape.

**MCP and A2A are complementary, not competing.** MCP handles agent-to-tool calls (how an agent invokes a tool); A2A handles agent-to-agent calls (how one agent delegates to another). An autonomous agent workforce platform should implement both: MCP for tool connectors and A2A for multi-agent delegation and cross-vendor interoperability.

**OpenTelemetry GenAI semantic conventions are emerging but not final.** The gen-ai spans specification (covering agent spans) was in active development through early 2026. Platforms should implement the latest published conventions while anticipating further evolution, particularly around multi-agent trace correlation.

**EU AI Act high-risk classification requires careful workflow design.** Autonomous agents making consequential decisions in HR, credit, or law enforcement contexts likely qualify as high-risk systems, requiring conformity assessments, logging, and human oversight mechanisms before market deployment in the EU.
