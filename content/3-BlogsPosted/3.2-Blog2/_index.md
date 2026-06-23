---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# SESSION POLICIES IN AMAZON EKS POD IDENTITY

# [AWS Tech Share] Turning Viewers into Players: Building Interactive Gaming Experiences with GameLift Streams
Today, I’d like to share how AWS tackles the "Interactive Streaming" challenge – transforming a passive game-streaming experience into a two-way, real-time interaction.

In game development, organizing playtests typically consumes a lot of time (downloading builds, environment setup, reviewing recorded videos). At the same time, community engagement faces significant barriers when viewers can only interact passively via text chat. To solve this dilemma, AWS has introduced an incredibly powerful combined architecture.

# The 3 "Pillars" of the Solution Architecture
Amazon GameLift Streams: Supports direct game streaming from the server to browsers using WebRTC with ultra-low latency. It delivers qualities up to 1080p at 60 FPS without requiring players to download or install anything.

Amazon IVS (Interactive Video Service): Ingests the gameplay stream and distributes it globally with sub-second latency.

AWS AppSync: Acts as the bridge, providing WebSocket APIs to instantly transmit messages, reactions, and control inputs from the audience back into the game.

How the Architecture Flow Works
Users interact with a React Frontend interface, with secure authentication handled via Amazon Cognito.

Amazon API Gateway and AWS Lambda manage communication and initialize the stream session.

On the server side, GameLift Streams runs the game while simultaneously launching a background process called the "Broadcast Sidecar".

This Sidecar application captures the video/audio, encodes it using the H.264 standard, and pushes the stream directly onto the Amazon IVS stage with a latency under 300ms.

Technical Highlight: The "Control Handoff" Mechanism
The most impressive part of this solution is how it handles passing control over to participants (Control Handoff). The system leverages the AWS AppSync Event API to coordinate explicit state-control messages, such as:

TAKEOVER_REQUEST: Requesting control privileges from the current player.

TAKEOVER_APPROVED: Granting approval and initiating session sharing via the CreateStreamSessionConnection API.

# Image
![alt text](image-1.png)
![alt text](image-2.png)

# SUMMARY
This architecture does not just optimize internal playtesting workflows for studios; it also unlocks massive potential for marketing campaigns. Viewers watching a live stream can now actively participate in the game (e.g., voting on pathways, spawning monsters) directly from their browser with zero latency friction.

# Link: 
https://aws.amazon.com/blogs/gametech/creating-interactive-gaming-experiences-with-amazon-gamelift-streams-and-amazon-interactive-video-service/