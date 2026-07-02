---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Report: AWS Cloud & DevOps Meetup & Workshop

## Executive Summary
Attending this meetup series provided deep insights into modern software engineering paradigms, transitioning from legacy architectures to cloud-native ecosystems, and standardizing operational practices. The session brought together industry experts from AWS, Endava, and other multinational corporations to share concrete case studies on systems reliability and technical team culture.

## Meetup Agenda & Distinguished Speakers
* **Dinh Trung Kien & Nguyen Minh Tho:** *Designing and Scaling a URL Shortening Service on AWS*
* **Dat Pham & Cuong Nguyen:** *Navigating Work Culture in Global Tech Corporations (MNCs)*
* **Solutions Architect (SA) Presentation:** *Demystifying Serverless Architectures on AWS*
* **Danh Hoang Hieu Nghi:** *Evolution Roadmap: From First Cloud AI Journey to AWS Partner*
* **Trong H. Truong (DevOps Engineer @ Endava):** *Under the Hood: What a DevOps Engineer Truly Does*

---

## Core Technical & Architectural Insights

### 1. Modernizing Legacy Architectures
The session highlighted the critical limitations of outdated monolithic systems:
* **Deployment Bottlenecks:** Legacy setups severely hamper feature release cycles, leading to slower time-to-market.
* **Cost & Maintenance Drag:** Heavy server footprints generate compute waste and increase regular support costs.
* **Security & Compliance Risks:** Failing to update legacy dependencies introduces security vulnerabilities.

### 2. Decomposing Monoliths via DDD & Microservices
Transitioning to microservices requires a business-first design approach:
* **Loose Coupling:** Segmenting applications into independent, event-driven services that handle caching, queues, and message routing.
* **Event Storming Workflow:** Decomposing domains by mapping events sequentially $\rightarrow$ identifying triggers/actors $\rightarrow$ establishing bounded contexts.
* **Context Mapping:** Deploying integration patterns to orchestrate relationships between business domains.

### 3. Compute Spectrum & Serverless Transition
Selecting the appropriate compute model involves understanding trade-offs:
* **Compute Progression:** Evaluating Virtual Machines (EC2), Container orchestration (ECS/Fargate), and Serverless (AWS Lambda).
* **Serverless Benefits:** Shifting operational overhead to AWS, scaling dynamically with traffic, and running a pay-per-execution billing model.
* **AI-Assisted Development:** Utilizing Amazon Q Developer to automate routine tasks (Java upgrades, .NET migrations) throughout the SDLC.

### 4. Real-world DevOps & Data Engineering Realities
* **DevOps Focus:** The primary goal of a DevOps engineer is to build reliable CI/CD pipelines, manage infrastructure-as-code (IaC), and automate monitoring to prevent outages rather than reacting to failures.
* **Data in Action (Colgate-Palmolive & Kamereo):** Case studies demonstrated how Colgate-Palmolive leverages IoT data to monitor factory machinery, and how Kamereo uses real-time business metrics ($GMV$, fulfillment rate) to guide operational choices.

---

## Key Reflections & Practical Takeaways

### Cultural & Professional Growth
* **No-Blame Post-Mortem Mindset:** Cultivating a culture where system failures are treated as architectural improvement opportunities rather than pointing fingers at individuals.
* **Career Evolution Model:** Shifting personal learning goals from a simple executor (*Follower*) to a systems architect (*System Thinker*).
* **Standardized Recruitment:** Understanding MNC hiring paths using ATS screenings and the STAR model for competency evaluations.

### Engineering Applications
* Implementing collaborative Event Storming sessions to bridge the gap between product and engineering teams.
* Planning migration routes to replace tightly coupled API requests with SQS message queues.
* Using Amazon Q Developer locally to accelerate code reviews and document architectural decisions.

---

## Event Photos
![alt text](image.png)
