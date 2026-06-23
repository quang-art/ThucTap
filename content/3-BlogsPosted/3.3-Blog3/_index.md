---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# SESSION POLICIES IN AMAZON EKS POD IDENTITY

# EXPLORING THE MULTI-BUILD SOLUTION ON AMAZON GAMELIFT SERVERS ★★★
# Introduction
In online game development, updating and testing multiple game server versions is a frequent and routine task. However, deploying each new version to the infrastructure can be time-consuming and often disrupts the testing pipeline.

To solve this, AWS introduced the Multi-Build solution on Amazon GameLift Servers. This feature allows developers to host and run multiple game server versions on a single fleet, significantly accelerating game development and testing cycles.

# What is Amazon GameLift Servers?
Amazon GameLift Servers is a fully managed game server hosting service provided by AWS. It helps developers deploy, manage, and scale game server systems on a global scale. Many major titles in the gaming market leverage GameLift to ensure high scalability and rock-solid stability for millions of concurrent players.

# Challenges in Traditional Game Development
Typically, whenever a new server version is ready, developers must go through a tedious loop:

Rebuilding the server application.

Redeploying it entirely to the infrastructure.

Testing and verifying its operations.

Manually switching between versions when cross-testing is required.

This workflow consumes a massive amount of time, especially during the Alpha and Beta phases when updates are pushed constantly.

# The Multi-Build Solution
The Multi-Build solution allows multiple game server versions to coexist and run on the exact same Amazon GameLift fleet. Instead of redeploying the entire system from scratch, developers only need to:

Upload the new build version to Amazon S3.

The system automatically synchronizes the files down to the GameLift servers.

When creating a Game Session, simply specify the target BuildVersion.

The server automatically triggers and launches the corresponding version.

Thanks to this mechanism, switching between different game versions becomes incredibly fast, seamless, and flexible.

# Operational Architecture
The solution relies on two main containers working side-by-side:

1. Game Server Container
This container is responsible for:

Running the main game server process.

Receiving game session creation requests.

Dynamically launching the correct server version based on the requested BuildVersion.

2. S3 Sync Container
This container runs continuously in the background to:

Monitor changes and updates on Amazon S3.

Automatically synchronize new builds down to the local storage.

Clean up and delete old, unused builds.

Ensure that data is completely downloaded before execution.

Note: Both containers utilize a shared directory to seamlessly access the synchronized game builds.

# AWS Services Utilized
The Multi-Build solution integrates a powerful suite of AWS services:

Amazon GameLift Servers (Core hosting)

Amazon S3 (Build storage)

Amazon ECR (Container registry)

AWS IAM (Access management)

AWS CodeBuild (CI/CD pipeline)

AWS CloudFormation (Infrastructure as Code)

Amazon CloudWatch Logs (Monitoring and debugging)

As a result, the entire deployment and management pipeline is almost fully automated.

# Key Benefits of Multi-Build
Accelerated Development: Engineering teams can test multiple game versions simultaneously without needing to spin up or redeploy new fleets.

Massive Time Savings: Uploading a new build takes only a few minutes, completely bypassing the full infrastructure deployment cycle.

Streamlined Alpha & Beta Testing: Multiple game variants can run in parallel to serve different playtest groups or focus groups.

Centralized Management: All builds are securely managed in one place (Amazon S3) and automatically pushed to the servers.

# CONCLUSION
Amazon GameLift Servers Multi-Build is a highly efficient solution for game studios aiming to speed up their testing and release cycles. By allowing multiple builds to live together on a single fleet, AWS drastically cuts down deployment overhead and optimizes the entire game development workflow.

If your game project is currently in Alpha, Beta, or heavily iterating on new features, this is a solution well worth exploring and adopting.

# image
![alt text](image.png)
![alt text](image-1.png)
# Reference Link:
 https://aws.amazon.com/vi/blogs/gametech/rapid-game-server-iteration-on-amazon-gamelift-servers/