---
title: "Event 3"
date: 2026-07-25
weight: 2
chapter: false
pre: " <b> 4.3. </b> "
---
# Summary Report: "FCAJ x Agentic AI Build Week"

### Event Purpose

- Share memorable experiences and insights from the Hackathon competition
- Introduce Domain-Driven Design (DDD) methodology and Event-Driven Architecture
- Guide selecting suitable compute services


### Key Highlights

#### Negative Impacts of Legacy Application Architecture

- Slow product release cycles → Revenue loss and missed opportunities


#### Transitioning to Modern Microservice Architecture

Transitioning into a modular system where each functionality is an **independent service** communicating via **events**, resting on 3 core pillars:

- **Queue Management**: Asynchronous task processing
- **Caching Strategy:** Performance optimization
- **Message Handling:** Flexible communication between services

#### Domain-Driven Design (DDD)

- **4-step method**: Identify domain events → arrange timeline → identify actors → define bounded contexts
- **Bookstore case study**: Practical illustration of applying DDD
- **Context mapping**: 7 integration patterns for bounded contexts

#### Event-Driven Architecture

- **3 integration patterns**: Publish/Subscribe, Point-to-point, Streaming
- **Benefits**: Loose coupling, scalability, resilience
- **Sync vs Async comparison**: Clear understanding of trade-offs


### Key Learnings

#### Design Thinking

- **Business-first approach**: Always start from the business domain, not technology
- **Ubiquitous language**: Importance of a common vocabulary between business and tech teams
- **Bounded contexts**: How to identify and manage complexity in large systems

#### Technical Architecture

- **Event storming technique**: Practical method for modeling business processes
- Utilizing **Event-driven communication** instead of synchronous calls
- **Integration patterns**: Understanding when to use sync, async, pub/sub, streaming
- **Compute spectrum**: Selection criteria ranging from VM → containers → serverless


### Practical Application

- **Apply DDD** to current projects: Conduct Event Storming sessions with the business team
- **Refactor microservices**: Use bounded contexts to identify service boundaries
- **Implement event-driven patterns**: Replace selected sync calls with async messaging


### Event Experience & Key Video Takeaways

Participating in the **“FCAJ x Agentic AI Build Week”** workshop (co-hosted with JI Fund & AWS) provided valuable technical insights from both keynote sessions and hackathon project presentations:

#### Insights from High-Level Experts
- Keynotes from **Mr. Nguyen Gia Hung** (Head of Solutions Architect, AWS Vietnam) and **Mr. Joseph Marazota** (Head of Technology, AWS ASEAN) provided strategic guidance on modern application design.
- **Mental Model Shift in the Agentic AI Era**: Traditional software releases occur on multi-week cycles, whereas Agentic AI systems enable autonomous, minute-by-minute deployments. Engineers must challenge legacy constraints to adopt new paradigms.
- **Friction Reduction**: Modern AI applications eliminate UI/UX bloat (complex onboarding, unnecessary menus) by deploying AI Agents that execute multi-step workflows directly for end-users.

#### Short-Term Hackathon Lessons: PoC to Production
Building a Proof of Concept (PoC) within a tight hackathon timeframe validates core ideas quickly, but moving to production requires solving three critical engineering challenges:
1. **Guardrails**: Establishing rigid safety boundaries to verify Agent decisions before execution.
2. **Operational Cost**: Managing LLM API usage in continuous execution loops.
3. **Human-in-the-Loop**: Implementing feedback loops where domain experts (e.g., Data Analysts) iteratively refine Agent outputs.


### Event Photos & Links

![Event Proof Photo](/event_3.png)
