---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy it verbatim** into your report, including this warning.
{{% /notice %}}

# MEETUP & WORKSHOP SUMMARY REPORT
# Event Objectives
Sharing Best Practices in Modern Application Design: Updating trends in shifting application architecture from Legacy to Cloud-native to optimize performance, enhance security, and minimize operational costs for enterprises.

Introducing DDD and Event-Driven Architecture: Orienting a business-first approach to system design, guiding how to decompose microservices through Event Storming, and building loose coupling systems.

Guiding the Selection of Appropriate Compute Services: Analyzing the compute spectrum from virtual machines (EC2) and Containers (ECS/Fargate) to Serverless (AWS Lambda) to help engineers clearly understand the trade-offs and apply them accurately to each use case.

Introducing AI Tools Supporting the Development Lifecycle: Gaining hands-on experience with the capabilities of Amazon Q Developer in automating the Software Development Lifecycle (SDLC)—from planning and automated code modernization to system maintenance—to boost productivity.

Shaping the Development Roadmap and Mindset of the New Generation of Engineers: Clarifying the real-world job scope of a DevOps Engineer or Data Analytics Engineer; guiding the roadmap to upgrade personal capability from a follower to a problem solver and system thinker.

Spreading Progressive Work Cultures from Global Tech Corporations: Introducing modern corporate cultural values, such as the No-Blame Post-Mortem mindset (refraining from blaming individuals when critical system failures occur) and standardized recruitment processes at MNCs, thereby narrowing the gap between academic environments and actual industry practices.

# Speakers & Presentation Topics
Dinh Trung Kien & Nguyen Minh Tho: A Scalable URL Shortening Service on AWS

Dat Pham & Cuong Nguyen: Real-world Stories to Multinational Corporation Culture

SA: Serverless Amazon Web Services

Danh Hoang Hieu Nghi: From First Cloud AI Journey to AWS Partner

  

Trong H. Truong: DevOps Engineer @ Endava Vietnam (Topic: What Does a DevOps Engineer Really Do?)

# Key Highlights
# 1. Negative Impacts of Legacy Application Architectures
Slow Release Velocity: Cumbersome processes prolong product launch times, leading to lost revenue and missed competitive opportunities.
Operational Inefficiencies: Causes a waste of engineering productivity and drives up operational and maintenance costs.
Security Risks: Failure to meet modern security standards increases the risk of data breaches and diminishes corporate reputation.
# 2. Transitioning to Microservices & Domain-Driven Design (DDD)
Independent Modular System: Decoupling applications into small, autonomous services that communicate asynchronously via events (Event-driven) based on three core pillars: Queue Management, Caching Strategy, and flexible Message Handling.
4-Step DDD Process: Identify domain events $\rightarrow$ Arrange the timeline $\rightarrow$ Identify actors $\rightarrow$ Determine bounded contexts.
Context Mapping: Applying 7 patterns to integrate bounded contexts seamlessly, illustrated through a real-world bookstore case study.
# 3. Event-Driven Architecture & Compute Evolution
3 Core Integration Patterns: Publish/Subscribe (Pub/Sub), Point-to-point, and Streaming to construct loosely coupled systems, increasing scalability and resilience.
Infrastructure Evolution (Shared Responsibility Model): Shifting from traditional virtual machines (EC2) $\rightarrow$ Containers (ECS/Fargate) $\rightarrow$ Serverless (AWS Lambda). Serverless delivers outstanding benefits: no server management, auto-scaling based on traffic, and a pay-for-value cost model.
Amazon Q Developer: An AI assistant that automates the entire SDLC. This tool helps modernize source code (Java upgrades, .NET modernization) and activates AWS Transform agents for automated system migrations (VMware, Mainframe).
# 4. The Real-World Role of DevOps & Skill Development Roadmap
Nature of DevOps Work: Building CI/CD pipelines, managing Infrastructure as Code (IaC), deploying Containers & K8s, integrating Cloud Providers (AWS, Azure), and monitoring systems (Logging/Monitoring). In reality, DevOps is not a midnight "firefighting hero" but rather a system optimizer who prevents incidents from happening in the first place.
Learning Roadmap (DevOps Fundamentals):
Mastering the Roots: Linux Operating System and Networking basics.
Programming Languages: Python, Golang.
Source Control & Virtualization Tools: Git, CI/CD, and Containers (Docker).
Hands-on Practice: Deploying small projects, configuring environment variables, intentionally breaking the system, and learning how to fix it.
# 5. Data Analytics Engineering & Global Work Culture (MNCs)
# Domain-Specific Work Realities:
At Kamereo: Building periodic operational reports; designing Dashboards to monitor data trends and detect anomalies to support business decision-making.
At Colgate-Palmolive: Analyzing machinery and IoT device data in factories to optimize production costs and drive digital transformation initiatives.
Core Skill Set: Critical thinking, communication skills, root-cause problem solving, and data storytelling through operational metrics ($GMV$, Fulfillment cost, Fill rate...).
Personal Capability Development Model: Progressing through 5 distinct levels: Follower (Executor) $\rightarrow$ Learner (Active Learner) $\rightarrow$ Problem Solver $\rightarrow$ System Thinker $\rightarrow$ Super Star (Leader/Visionary).
Progressive Corporate Cultures at Large Scale:
No-Blame Post-Mortem Culture: When a critical system failure occurs, engineers focus on root-cause analysis to upgrade the system rather than assigning blame to individuals.
Caring & Inclusive Culture: Respecting diversity and placing people at the center of all organizational growth.
# Key Takeaways
# Design Thinking & Orientation
Business-First Approach: Every technical architecture must stem from and serve the actual needs of the business domain.

Ubiquitous Language: The vital importance of synchronizing terminology and building a common vocabulary between business and tech teams to eliminate misunderstandings.

Wakon Yosai & the "Right Work" Philosophy: Learning and mastering the world's advanced technologies while maintaining a solid core mindset to upgrade oneself into a true Problem Solver.

# Architecture & System Engineering
Proficiently utilizing the Event Storming technique to model complex business workflows into a sequence of Domain events.

Deeply understanding trade-offs to select the correct communication model (synchronous vs. asynchronous) and the appropriate compute model across the spectrum (VM, Container, to Serverless).

Grasping the core philosophy of DevOps: "Tools may change constantly, but fundamentals stay forever". Leveraging AI to boost performance rather than relying on it to bypass critical thinking.

# Modernization Strategy
System modernization must be a step-by-step roadmap (Phased approach), utilizing the 7Rs framework to analyze the characteristics of each application before migration.

Every transformation needs to be measured precisely through two indicators: Cost reduction and Business agility

# Practical Application
Deploying DDD & Event Storming: Organizing collaborative Event Storming sessions with operational/business teams to standardize a "Ubiquitous Language" for current projects.

Refactoring Microservices: Using the learned Bounded Contexts to draw clear boundaries between services, minimizing cross-dependencies (Coupling).

Integrating Event-Driven Patterns: Planning to gradually replace synchronous calls (Sync) with asynchronous messaging queues (Async) to enhance system fault tolerance.

Experimenting with Serverless: Selecting a few independent features or use cases to run a pilot on AWS Lambda to optimize infrastructure costs.

Adopting AI Assistants: Integrating Amazon Q Developer into daily coding and code review workflows to elevate software development lifecycle (SDLC) automation.

Transforming Personal Work Mindset: Applying the personal growth model to transition from a "Follower" to a "Problem Solver"; cultivating the habit of asking "Why" before searching for "How" when dealing with architectural challenges.

# Event Experience
Attending the “GenAI-powered App-DB Modernization” workshop and the technology sharing series was an incredibly valuable experience, providing me with a comprehensive view of modern tech trends.

# Learning from Industry Leaders
Listening to the invaluable experiences and "blood, sweat, and tears" lessons from experts representing AWS, Endava Vietnam, and major global multinational corporations.

Real-world case studies—such as building data management dashboards at Kamereo or optimizing production systems at Colgate-Palmolive—made it easy to map theoretical concepts to corporate realities.

# Technical & Cultural Insights
Gaining a clear picture of the tech recruitment landscape in Vietnam, including standardized interview tracks (ATS screening, competency tests, and technical interviews via the STAR model).

Deeply impressed by the No-Blame Post-Mortem cultural mindset. This experience reshaped how I view system errors: seeing failures as opportunities for architectural improvement rather than a source of pressure to find someone to blame.

# Expanding the Network (Networking)
The event offered an excellent environment to connect directly with the AWS Community Builders, AWS Student Builders, and software and data engineers across the industry.  

Open discussions helped me cultivate a system-thinking mindset, understanding the cross-functional connections between Tech and Business units to collaboratively solve operational challenges for long-term efficiency.
#### Some event photos
![alt text](image.png)
