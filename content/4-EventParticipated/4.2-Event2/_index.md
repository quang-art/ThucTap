---
title: "Event 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy it verbatim** into your report, including this warning.
{{% /notice %}}

# Workshop Summary: “GenAI-powered App-DB Modernization”
#### EVENT PURPOSE
Knowledge Sharing: Discuss practical solutions and best practices for applying Artificial Intelligence (AI/LLM) and optimizing cloud infrastructure (AWS).
Advanced AI Architectures: Introduce cutting-edge AI design patterns, including Multi-Agent Systems, Context Engineering, and AI Assistants.Infrastructure Optimization: Guide workflows for cost optimization, security hardening, and operational performance enhancement from the Edge to the Origin server.
Real-World Experience: Share battle-tested lessons and key takeaways from Hackathons and tech product development under intense pressure.
# SPEAKERS & TEAM
Vy Lam – Senior Business Systems Analyst at VPBank.Đức Đào – Solutions Architect at Cloud Kinetics.
Team VIB – The development team behind the UTMorpho project at Lotus Hacks.
Phạm Ng Hải Anh – G-AsiaPacific Vietnam, AWS Community Builder.
Nguyễn Tuấn Thịnh – DevOps Engineer.
Tinh Truong (Trương Tịnh) – Platform Engineer at GoTymeX.
# KEY HIGHLIGHTS (FROM PRESENTATIONS)

# 1. Enterprise-Grade Multi-Agent Systems (Speaker: Vy Lam)
The Misalignment Issue: Traditional bank credit scoring systems (requiring 3 years of financial data and physical collateral) are completely incompatible with startups, which typically only have 6–18 months of operational data, intellectual property/human capital, and unstructured datasets.
The Virtual Credit Committee (Multi-Agent Paradigm): Instead of relying on a single Agent—which suffers from context dilution—the system decomposes the workflow into specialized Agents (Financial Analyst, Market Analyst, Team Evaluator, Risk Assessor, Compliance) interconnected via the Model Context Protocol (MCP) to collaboratively grade applications.
Outstanding ROI: Reduced application processing time from 2–3 weeks down to 2–4 hours (a 95% speedup) while cutting operational costs by over 90%.Enterprise Security: Implemented via Bedrock AgentCore and Terraform, enforcing strict Guardrails to protect Personally Identifiable Information (PII) and block Prompt Injection.

# 2. The Non-Deterministic Nature of "Deterministic" LLMs (Speaker: Đức Đào)
The Temperature = 0 Myth: Users often assume that setting $T = 0$ (Greedy Decoding) guarantees that an AI model will return a 100% identical output for the exact same prompt every single time.
Research Findings: No Large Language Model (including GPT-4o, Llama-3, Mixtral) is perfectly deterministic at $T = 0$. This variance stems from GPU hardware architectures, floating-point calculation errors, and inference optimization algorithms.
Impact & Remedies: A strict $T = 0$ setting can trap models in repetitive feedback loops. The solution is to set $T = 0.1$ (introducing a tiny stochastic nudge to break out of loops), increase the repetition penalty, and design systems with a probabilistic mindset. Furthermore, structured outputs (JSON/YAML) should be enforced using system parameters rather than relying solely on prompting.
# 3. 36-Hour Hackathon Chronicles: Building UTMorpho (Team VIB)
Starting from Scratch: Entering Lotus Hacks 2026 (Vietnam's largest Hackathon) with a blank slate, the team derived their core idea directly from everyday operational friction to build UTMorpho.
Real-World Challenges: Navigating suffocating time constraints, battling AI overgeneration issues, hitting Token Limits, and managing team burnout right before Pitch Time.
The Turning Point: Overcoming obstacles by locking into a Focused Editing Experience and maintaining absolute team synchronization.
# 4. User-Friendly AI Assistants with Amazon Q (Speaker: Hải Anh)
Business User Pain Points: Wasting excessive time gathering data from fragmented sources, drowning in repetitive manual tasks, and relying heavily on technical experts for deep data analysis.
The Amazon Q Suite Solution: Providing a unified workspace where humans and AI Agents collaborate. It connects over 40 data sources, Bedrock models, and user files to bridge the gap between "insight" and "action" rapidly.
Practical Application (PM Assistant): Fully automating the Meeting Minutes (MoM) workflow $\rightarrow$ Auto-emailing relevant stakeholders $\rightarrow$ Auto-scheduling follow-up sessions.
# 5. Optimizing Core Network Infrastructure with CloudFront (Speaker: Tuấn Thịnh)
Cloud Bill Anxiety: Businesses frequently worry about cloud cost spikes triggered by unpredictable traffic surges or DDoS attacks (due to usage-based billing).
Fixed-Price Plan Solutions: CloudFront introduces predictable monthly subscription tiers (Free, Pro, Business, Premium) to help manage budgets, guaranteeing zero overage fees and ensuring that blocked malicious traffic does not incur charges.
Performance Gains: Leveraging 700+ Global PoPs and persistent connection mechanisms to drop EC2 origin CPU utilization from 5% down to 1%. Integrating HTTP/3 multiplexing enables parallel asset loading and data compression, reducing response latencies by 81% (from 123ms to 24ms).
# 6. Context Engineering – Context Is Everything (Speaker: Tịnh Trương)
Core Message: Today's AI models are incredibly powerful. Poor or generic AI outputs are usually caused by weak input context, not a flawed model.
# 3 Classic AI Mistakes:
The "Internet Puller": Cramming massive, unfiltered documents into the chat, which dilutes key details and burns tokens unnecessarily.
Stating the Obvious: Providing existing code to the AI and telling it how to configure that exact same technology rather than focusing on the target logic that needs fixing.
Lack of Goals and Constraints: Making vague requests that force the AI into guesswork.
Simple Context Framework: Before writing a prompt, always lay out 4 elements: Goal, Relevant Information, Constraints, and Success Criteria.

# KEY TAKEAWAYS
# Design & Application Development Mindset
Business-First Approach: The best tech products always start by solving actual, real-world business friction and operational pain points, not by blindly chasing tech trends.
Context Engineering as a Core Skill: The future isn't a battle of Humans vs. AI, but rather Humans who know how to engineer context vs. those who don't. The paradigm is shifting rapidly from Prompting $\rightarrow$ Context Systems $\rightarrow$ Long-term Memory.
Agentic System Architecture: For complex enterprise problems, a collaborative Multi-Agent design (orchestrating specialized agents) delivers superior accuracy, testability, and ROI compared to a monolithic single-agent setup.

# Technical Architecture & Infrastructure Operations
Probabilistic Mindset: When building LLM-backed applications, systems must be architected to handle output variance (even at $T = 0$). Developers need to wrap downstream logic with validation checks and continuous testing rather than assuming absolute model determinism.
 Edge Optimization: Utilize Edge Computing solutions like CloudFront Functions or Lambda@Edge to process routing logic, security checks, and URL rewrites directly at the edge, drastically reducing origin load and decreasing user latency.

 # PRACTICAL APPLICATIONS 
 Prompt Optimization: Immediately adopt the Simple Context Framework (Goal, Info, Constraints, Success Criteria) in daily workflows to elevate code quality and documentation precision.
 AI Agent Feature Design: Transition from single-prompt features to decentralized Multi-Agent workflows for complex tasks, while utilizing $T = 0.1$ to mitigate infinite loops.
Exploring Amazon Q & MCP: Experiment with tool-calling integrations and corporate knowledge bases to automate administrative loops (e.g., auto-generating meeting summaries and status reports).
 Network Infrastructure Tuning: Propose CDN/CloudFront configurations combined with Origin Cloaking for web projects to safeguard backend systems from DDoS attacks and stabilize bandwidth spend via fixed-price plans.
 # EVENT EXPERIENCE (AWS COMMUNITY DAY / CLOUD AI JOURNEY)
 Attending this presentation track was an incredibly grounded and high-value experience, bridging the gap between theoretical AI/infrastructure concepts and tangible enterprise problems.
 Learning from Battle-Tested Experts: Hearing directly from Solutions Architects, DevOps Engineers, and BSAs from major organizations (VPBank, GoTymeX, Cloud Kinetics, G-AsiaPacific) provided a deep understanding of how enterprises tackle data privacy, cloud cost vulnerabilities, and AI limitations.
 Multidimensional Technical Insights: The event delivered a perfect balance of deep-dive hardware topics (how GPU architectures alter LLM determinism) alongside raw, high-pressure reflections on the 36-hour survival race inside a Hackathon room.A Clear Roadmap Forward: Reaffirmed the vital importance of mastering Context Engineering and adopting an "Enterprise Mindset" when architecting AI systems—ensuring they don't just run, but run securely, reliably, and scalably.\
 # Event Highlights & PhotosInsert your event photos 
 ![alt text](z7866450150269_87bf550e28462644de70351a8524597e.jpg)
![alt text](z7866450137122_fa7ac674224cf3e8b1fe76ae81263462.jpg)
![alt text](z7866450114341_f4f7bf1c450c1fbfc72d663d28be7689.jpg)