# Exercise 0 - Introduction

In this exercise, we will explain the concepts we are using in the exercise and set up our environment.

## Exercise 0.1 What is Agentic Coding?

Agentic coding is a software development approach in which autonomous AI agents plan, write, test, and optimize code independently according to high-level goals, minimizing the need for ongoing human direction. These agents can reason about requirements, break down tasks, collaborate, and iteratively improve solutions—essentially transforming the developer’s role from manual implementer to supervisor and goal-definer. 

### Key Features  
- Autonomous code generation and modification by AI agents.
- High-level objectives are translated into actionable development plans with minimal human intervention.
- Proactive error detection, self-testing, and optimization.
- Agentic systems can coordinate multiple agents for different roles, from architecture to deployment.
- Continuous and adaptive enhancement of codebases.  

Agentic coding represents a paradigm shift, optimizing for system-wide intelligence and automated collaboration rather than individual developer output.



## Exercise 0.2 What are MCP servers?

The Model Context Protocol (MCP) is the "USB-C port for AI". It is an open standard designed to create a universal connection between AI models, and external data sources, tools, and systems. It aims to replace the fragmented system of custom integrations with a single, standardized protocol, making it easier for AI to access and interact with the information it needs to provide more relevant and capable responses.

## How does it work
MCP operates on a client-server architecture, which simplifies communication between AI applications and external systems.
	•	Host Application: This is the AI application, such as an LLM chat interface or an AI-enhanced code editor, that interacts with the user and initiates connections.
	•	MCP Client: Integrated within the host application, the client translates the host’s needs into the MCP standard and manages the connection to MCP servers.
	•	MCP Server: This is a service that exposes a specific data source or tool (like a GitHub repository, a database, or the SAP Tools) to the AI system through the MCP standard.


## Key Features and Capabilities
MCP allows developers to build more powerful and integrated AI systems by providing a standard way for them to:
	•	Share Resources: Provide contextual information and data from external systems to the AI model.
	•	Expose Tools: Enable the AI model to execute functions and interact with external applications, such as running code or accessing APIs.
	•	Initiate Prompts: Use pre-defined message templates and workflows to guide user interactions.
	•	Handle Security: The protocol includes principles for user consent, data privacy, and tool safety, though implementation is the responsibility of the developers.

## Exercise 0.3 Which MCP servers does SAP provide?

SAP is committed to meeting developers where they’re at – that means no matter where or how you code, you have the freedom to choose the environment that best suits your needs and access to the tools that maximize your productivity and impact.

SAP is introducing Model Context Protocol (MCP) servers to boost development with the following technologies:

- Cloud Application Programming Model (CAP)
- SAP Fiori Elements 
- SAPUI5 

By adopting these new MCP standards, developers can seamlessly extend SAP’s development capabilities into multiple environments, ensuring flexibility and choice. SAP Build now enhances popular IDEs and AI coding assistants such as Cursor, Windsurf, Github Copilot, Cline and Claude Code.

The MCP Servers are being released as an open-source projects, licensed under the Apache-2.0 license. This marks another step in our commitment to openness and community-driven innovation.

Value of SAP MCP Tools:
- Best Practices Built-In: Generated code with CAP, UI5 and Fiori elements code already provides you with the right starting point for reaching SAP standards and proven design guidelines.
- Guided Development: Developers receive recommendations and guardrails tailored to SAP Business Technology Platform (BTP).
- Consistency:  SAP’s MCP tools are and will be reused across our tooling portfolio, ensuring consistent developer experience and outcomes wherever you build SAP applications. Whether you’re generating backend services, UIs, or business logic, you can rely on the same quality, structure, and compliance.

## Exercise 0.3 Install MCP server

Install Github Copilot?
In Github Copilot install MCP server.
In github Copilot add instructions.

## Summary

You've now learnt what Agentic AI and MCP is and we setup our development environment. Let's jump into the first part of the exercise [Exercise 1 - Create a CAP application ](../ex1/README.md)
