---
title: "Event 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.3. </b> "
---

# Technical Report: Cloud-Native & DevOps Modernization Sharing Session

## Executive Summary
This sharing session focused on architecture modernizations, building loose coupling microservices through Domain-Driven Design (DDD) principles, and deploying infrastructure at scale. Industry professionals from AWS and premier consulting firms outlined key operational trade-offs across the compute spectrum and modern tech workflows.

## Presentation Lineup & Keynote Speakers
* **Dinh Trung Kien & Nguyen Minh Tho:** *Scaling and Deploying a URL Shortening Infrastructure on AWS*
* **Dat Pham & Cuong Nguyen:** *Organizational Culture & Career Paths inside Multinational Corporations*
* **Special Presentation:** *AWS Serverless Ecosystem: Core Integration Patterns*
* **Danh Hoang Hieu Nghi:** *Partner Growth Journey: Transitioning to AWS Partner Networks*
* **Trong H. Truong (DevOps Engineer):** *Architectural Automation: The True Focus of DevOps Engineering*

---

## Architectural Deep Dives & Key Technical Learnings

### 1. The Real Cost of Monolithic Architectures
The workshop analyzed structural roadblocks found in legacy application frameworks:
* **Slow Product Cycles:** Manual release pipelines delay features, leaving business units unresponsive to market trends.
* **Over-provisioned Resources:** Monolithic compute architectures result in significant waste and elevated cloud bills.
* **Security Isolation Risks:** Outdated packages create vulnerabilities, making systems vulnerable to target attacks.

### 2. Microservice Decoupling via Domain-Driven Design (DDD)
Modern architectures require splitting applications into business-aligned domains:
* **Asynchronous Integration:** Utilizing message brokers and queuing mechanisms to separate service dependencies.
* **Event Storming Methodology:** A team-wide design session mapping domain events $\rightarrow$ identifying actors/actions $\rightarrow$ grouping contexts.
* **Bounded Contexts Mapping:** Creating clear separation between internal service models to avoid database sharing.

### 3. Compute Evolution & The Serverless Model
Developers must evaluate infrastructure models based on specific project needs:
* **Infrastructure Spectrum:** Deciding between Virtual Machines (EC2), containers (ECS/Fargate), and serverless execution (AWS Lambda).
* **Benefits of Serverless:** Abstracting server management, scaling instantly from zero, and aligning costs directly with system usage.
* **SDLC Automation:** Implementing Amazon Q Developer to optimize codebases and expedite system upgrades.

### 4. Practical DevOps Practices & Data Instrumentation
* **DevOps Objective:** Shift from reactive firefighting to proactive automation (IaC, CI/CD pipelines, and health monitoring).
* **Data-Driven Operations:** Case studies from Colgate-Palmolive (IoT data collection on manufacturing lines) and Kamereo (real-time business operations tracking like $GMV$ and order completion rates) showed data engineering in action.

---

## Technical Action Items & Reflections

### Engineering Commitments
* Implement standard Event Storming sessions for current architectural plans.
* Replace direct API requests with SQS queues to prevent data loss in ticketing systems.
* Use Amazon Q Developer to run automated refactoring pipelines.

### Team and Career Growth
* **Post-Mortem Best Practices:** Shifting incident review meetings from personal blame to system improvement.
* **Learning Roadmaps:** Elevating personal capabilities from a standard executor (*Follower*) to a system designer (*System Thinker*).
* **Technical Hiring Profiles:** Preparing for multinational hiring processes using ATS optimization and STAR behavioral responses.

---

## Event Photos
![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)