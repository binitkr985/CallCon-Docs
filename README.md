# CallCon

### One Discord. Countless conversations.

**CallCon is a cross-server social communication platform for Discord that connects people beyond the boundaries of individual communities.** It enables users to discover conversations, meet new people, and interact through matchmaking and shared communication experiences.

[Website](https://callcon.vercel.app) · [Discord Bot](https://top.gg/bot/1304318506921365504) · [Developer](https://github.com/binitkr985)

---

## Overview

Discord communities are often isolated from one another. People can spend years on the platform without discovering communities or individuals outside their existing circles.

CallCon aims to change that.

By bringing together matchmaking, cross-server communication, social features, and conversation utilities, CallCon makes it possible to connect with people outside your usual Discord community.

The project focuses on making these interactions accessible while considering scalability, user privacy, moderation, and reliable session management.

> **Built for connection. Engineered for scale.**

## Features

### Social matchmaking

- **Random matchmaking** — Discover new people through a matchmaking experience.
- **One-to-one conversations** — Connect with another participant for a direct conversation.
- **Anonymous interactions** — Support conversations where participants do not immediately disclose their identities.
- **Optional identity disclosure** — Allow users to choose when to reveal more about themselves.
- **Reputation-aware matchmaking** — Use reputation as a potential signal for improving interaction quality.
- **Language-aware matching** — Account for language preferences when finding compatible participants.

### Cross-server communication

- **Cross-server interactions** — Connect users and communities across different Discord servers.
- **Channel-based connections** — Support communication between configured channels where available.
- **Message relaying** — Enable messages to travel between connected participants or channels.
- **Session management** — Handle the lifecycle of active conversations and connections.

### Safety and moderation

- **User reporting** — Provide a mechanism for reporting abusive behaviour.
- **Abuse prevention** — Incorporate safeguards against misuse of the platform.
- **Reputation mechanisms** — Use behavioural signals to inform the social experience.
- **Restricted-user enforcement** — Apply account restrictions to prevent prohibited interactions.
- **Inactivity handling** — Use inactivity timeouts to help clean up abandoned sessions.

### Conversation utilities

CallCon also includes interactive utilities designed to make conversations more engaging.

Examples include:

- Hangman
- Wordle
- Mathematical challenges
- Tic-Tac-Toe
- Conversation topics and icebreakers

---

## Architecture

CallCon is designed around a Node.js-based backend with separate responsibilities for Discord interaction, matchmaking, temporary state, persistent storage, and operational management.

### Technology stack

| Technology | Purpose |
|---|---|
| Node.js | Backend runtime |
| discord.js | Discord API integration, events, commands and messaging |
| Redis | Temporary state, matchmaking queues and coordination |
| MongoDB | Persistent application data |
| Mongoose | MongoDB object modelling |
| Express | HTTP endpoints and integrations, where applicable |
| Discord sharding | Distributing Discord gateway workloads across shards |

### Why Redis and MongoDB?

CallCon distinguishes between frequently changing application state and information that must persist.

**Redis** is suitable for short-lived state such as matchmaking queues, active session coordination, and inter-process messaging.

**MongoDB** provides persistent storage for records such as user preferences, reputation, moderation reports, and historical data, depending on the implemented schema.

Using the two together allows temporary coordination to be handled separately from durable application data.

---

## Engineering considerations

Building a social communication bot involves more than registering commands and sending messages.

CallCon's architecture addresses several important engineering challenges.

### 1. Matchmaking and concurrency

Multiple users may request a match simultaneously. The matchmaking system must avoid duplicate assignments and ensure that a user cannot participate in conflicting sessions.

Potential safeguards include atomic queue operations, explicit session states, and coordinated matchmaking workers.

### 2. Distributed coordination

A sharded Discord bot may process events across multiple processes. A session initiated on one shard may involve a user or channel handled elsewhere.

Shared state and inter-process coordination are therefore important for consistent behaviour across workers.

### 3. Session lifecycle

Conversations need a defined lifecycle, including creation, active participation, disconnection, timeout handling, and cleanup.

Reliable lifecycle management helps prevent abandoned sessions from occupying resources indefinitely.

### 4. Persistent data and temporary state

Queues and live session data have different durability requirements from user records and moderation history.

Separating these responsibilities helps keep the application architecture understandable and maintainable.

### 5. Abuse prevention

A platform that connects strangers must consider spam, harassment, repeated unwanted contact, malicious users, and misuse of reporting mechanisms.

Moderation controls and privacy-conscious data handling are important parts of the system rather than optional additions.

---

## Scalability

CallCon was designed with multi-server operation and horizontal workload distribution in mind.

The architecture incorporates concepts relevant to scaling a Discord bot:

- Discord sharding for distributing gateway workloads.
- Redis-backed coordination for shared temporary state.
- Persistent storage through MongoDB.
- Separation of command handling, matchmaking, and session management.
- Inactivity handling and cleanup.
- Centralized operational visibility and analytics.

---

## Project status

CallCon has been developed as a Discord bot with a publicly listed presence.

The public listing has previously reported hundreds of servers. For the latest listing information, visit:

[View CallCon on Top.gg](https://top.gg/bot/1304318506921365504)

The following documentation describes the project's concepts and architectural direction. It does not imply that every described feature is available in every release.

---

## Privacy and safety

CallCon's social features involve interactions between people who may not know one another.

Privacy and safety considerations include:

- Limiting access to user and session information.
- Avoiding unnecessary exposure of personal identities.
- Applying moderation restrictions consistently.
- Handling reports through appropriate moderation processes.
- Establishing suitable retention policies for stored conversation data.
- Protecting application credentials and infrastructure secrets.

Detailed security controls and internal anti-abuse implementations are intentionally not documented publicly.

---

## Development and availability

CallCon's complete source code is maintained privately.

This public repository is intended to document the project, its capabilities, and its engineering approach. It does not contain the full application implementation.

### Interested in CallCon?

- **Website:** [callcon.me](https://callcon.vercel.app)
- **Bot listing:** [CallCon on Top.gg](https://top.gg/bot/1304318506921365504)
- **Developer:** [binitkr985 on GitHub](https://github.com/binitkr985)

For questions, collaboration opportunities, or project-related enquiries, contact the developer through the available public channels.

---

## Frequently asked questions

### Is CallCon open source?

No. CallCon's source code is maintained privately. This repository provides public documentation about the project and its architecture.

### Can I self-host CallCon?

Self-hosting requires access to the application source code and appropriate configuration. The complete implementation is not distributed through this documentation repository.

### What technologies power CallCon?

The documented stack includes Node.js, discord.js, Redis, MongoDB, and Mongoose, with Express and Discord sharding used where applicable.

### Does CallCon connect users from different Discord servers?

Cross-server communication is one of the platform's central goals. The available functionality depends on the relevant connection mode and release.

### How does CallCon approach user safety?

The project incorporates safety considerations such as reporting, restrictions, reputation mechanisms, and session cleanup. Specific implementation details are not published here.

---

## About this repository

This repository exists to provide an overview of CallCon without distributing its private implementation.

It documents the project's purpose, architectural concepts, technology choices, and engineering considerations while keeping proprietary code and sensitive operational details separate.

**CallCon — Connecting communities, one conversation at a time.**
