# MAYI — Managed AI Infrastructure

**Role:** Systems & Automation Architect  
**Project Type:** Self-hosted AI infrastructure, automation, and secure agentic gateway deployment  
**Status:** Completed public-safe case study  

## Executive Summary

MAYI is a production-style deployment of the OpenClaw framework on a remote Ubuntu Linux VPS. Unlike a standard chatbot, MAYI was designed as a persistent digital assistant that can support business workflows, personal productivity, long-term context, web-based interaction, and Telegram-based communication.

The project demonstrates hands-on experience in Linux systems administration, network troubleshooting, secure remote access, API integration, AI orchestration, and technical documentation.

> **Public Portfolio Note:** This case study intentionally removes or generalizes sensitive infrastructure details such as IP addresses, API keys, tokens, usernames, hostnames, private paths, exact ports, and live access URLs.

## Objective

Deploy a secure, self-hosted AI agentic gateway that can support workflow automation, personal productivity, and multi-channel communication while maintaining control over the deployment environment.

## Tech Stack & Infrastructure

| Area | Tools / Concepts |
|---|---|
| Host Environment | Ubuntu 24.04 LTS VPS |
| Agent Framework | OpenClaw Agentic Gateway |
| LLM Routing | OpenRouter-supported LLM providers |
| Orchestration | Linux process management, systemd concepts, manual runtime control |
| Networking | SSH tunneling, local binding, port troubleshooting |
| Security | Token-based authentication, secret isolation, controlled exposure |
| Storage / Context | Persistent memory concepts, JSON-based configuration, knowledge store |
| Interfaces | Web control interface and Telegram assistant workflow |

## Architecture Overview

```text
User Devices
  ├── Web UI
  └── Telegram
        ↓
Secure Access Layer
        ↓
Ubuntu VPS
        ↓
OpenClaw Gateway
        ├── Persistent Memory / Context
        ├── Custom Skills / Plugins
        └── LLM Provider Routing
```

A public-safe architecture diagram is included in [`assets/mayi-architecture.svg`](../assets/mayi-architecture.svg).

## Core Capabilities

- Persistent memory and contextual recall
- Web-based assistant interaction
- Telegram-based assistant interaction
- Tool / skill-based workflow automation
- Self-hosted Linux deployment
- LLM routing through an external provider
- Token-based gateway authentication
- Security-conscious deployment and documentation

## Troubleshooting Deep Dive

### Challenge 1: Hidden Service Restart Loop

During setup, the gateway entered a restart loop. A background service continued to auto-spawn the gateway process, which created repeated port conflicts and blocked manual configuration.

**Symptoms included:**

- Gateway process restarting after manual termination
- Port already in use errors
- Conflicting runtime behavior between manual commands and background services
- Difficulty determining which process was controlling the gateway

**Troubleshooting approach:**

- Inspected active processes and parent process relationships
- Reviewed Linux service behavior
- Identified the background service that was re-launching the gateway
- Stopped the conflicting process behavior
- Shifted toward a controlled runtime approach for testing and stabilization

**Outcome:**

The conflicting service behavior was isolated and the gateway was moved into a more controlled execution model. This allowed the system to be started, tested, and documented without the restart loop interfering with configuration.

### Challenge 2: Host Header and Origin Protection

After the gateway became reachable, the browser connection was rejected by security checks. The gateway treated the request as coming from a non-local or untrusted source, which caused host-header and origin validation failures.

**Troubleshooting approach:**

- Compared local and remote access behavior
- Reviewed gateway authentication and allowed-origin behavior
- Tested controlled access methods
- Avoided exposing the administrative interface directly to the public internet
- Used SSH tunneling concepts to keep access controlled

**Outcome:**

The final public-safe design emphasizes controlled remote access through secure tunneling instead of openly exposing sensitive administrative services.

### Challenge 3: Public-Safe Documentation

Because this project involves real infrastructure, authentication, and provider access, raw logs and screenshots could expose sensitive information if posted publicly.

**Sensitive details removed or generalized:**

- Public IP addresses
- Gateway tokens
- API keys
- Usernames
- Hostnames
- Private file paths
- Exact access URLs
- Exact command output that could reveal deployment structure

**Outcome:**

The final portfolio version focuses on the engineering process, architecture, troubleshooting, and career-ready skills while protecting the live environment.

## What I Learned

This project helped me understand that real infrastructure work is not just about installing software. It requires diagnosing process behavior, reading logs, understanding service managers, testing secure connectivity, managing secrets, and documenting technical decisions clearly.

The biggest lesson was that a working AI system depends on the infrastructure around it: networking, authentication, runtime control, logging, security, and maintainability.

## Career-Ready Skill Map

**Linux Systems Administration**  
Managed a remote Ubuntu environment, worked with processes, services, logs, and runtime behavior.

**Network Security**  
Applied secure remote-access concepts, controlled exposure, and avoided publishing sensitive administrative access directly.

**AI Orchestration**  
Configured an agentic gateway that connects user interfaces, tools, memory, and LLM providers.

**API Integration**  
Worked with external LLM routing and multi-channel assistant interaction.

**Technical Documentation**  
Created a public-safe case study, architecture summary, troubleshooting notes, and portfolio-ready explanations.

## Security Statement

This project follows a public-safe documentation approach. Any sensitive values shown during development have been removed, generalized, or rotated before being included in the portfolio. Public materials are intended to demonstrate the engineering process without exposing live infrastructure or secrets.

## Resume Summary

**MAYI — Managed AI Infrastructure**  
Built and deployed a self-hosted AI agentic gateway using OpenClaw on an Ubuntu VPS, integrating web and Telegram interfaces, persistent memory concepts, LLM routing, and workflow automation. Troubleshot Linux service restart loops, port conflicts, host-header/origin errors, and secure remote access while documenting a public-safe deployment with sensitive infrastructure details redacted.
