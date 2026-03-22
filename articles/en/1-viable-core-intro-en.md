# Viable Core: From Scripts to Life — Introduction to Viable AI Systems Architecture

## Introduction: Why Existing AI Agents Are Unviable

Consider the following scenario. You've deployed three AI agents in your company: one for writing code, one for infrastructure monitoring, and one for marketing. Each agent individually demonstrates impressive results. However, a week later you discover that the marketing agent published a list of features on your website that your team hasn't implemented yet. The code-writing agent was refactoring the authentication module that nobody asked to touch. And the monitoring agent sent you an alarming notification about a breaking change when there was no critical issue.

Familiar picture? This story is not a product of imagination. This is exactly how Philipp Enderle, founder of the ViableOS project, describes his experience with AI agent organizational structure. The problem is not insufficient competence of individual agents or limitations of language models. The problem is **architectural** in nature: existing frameworks for creating AI agents provide powerful tools for solving specific tasks but contain no mechanisms for building self-correcting, sustainable systems.

This is where the **Viable Core** project was born — an open-source framework designed to create fundamentally different AI systems. Systems capable of working autonomously for days and weeks, forming their own identity, adapting to changes, and — most importantly — avoiding the pathologies we observe in disorganized multi-agent systems.

But before diving into the technical details of Viable Core, we need to understand the theoretical foundation it's built upon. This refers to the Viable System Model (VSM), developed by British cybernetician Stafford Beer in the 1970s.

## Viable System Model: Theory That Changed Understanding of Organizations

In 1972, Stafford Beer published "Brain of the Firm," which became a turning point in organizational cybernetics. Beer's main idea is striking in its universality: every surviving system — whether a living cell, a biological organism, a commercial company, or an economy — has exactly five control functions. Miss any of them — and the system will inevitably develop pathologies.

This is not a theoretical statement confirmed only by abstract models. Beer observed these pathologies in real organizations: in DAX automotive companies where he worked as a consultant, in government structures, in large corporations. The problems he saw then surprisingly accurately echo the problems of modern multi-agent systems:

- **Coordination failure**: marketing promises what engineers cannot deliver
- **Resource domination**: one agent consumes all available resources
- **Lack of oversight**: everyone optimizes locally, but nobody looks at the overall picture
- **No independent verification**: reports claim everything is fine, but real results leave something to be desired
- **Strategic blindness**: the system is immersed in execution, not noticing environmental changes

Let me introduce Beer's five systems in the context of AI agents.

### System 1: Operations

System 1 is the operational core, basic activities that directly interact with the environment. In AI agent terms, this is agents doing real work: developers, researchers, support bots, code analyzers.

Every existing framework — LangChain, CrewAI, AutoGen, OpenAI Agents SDK — correctly implements this system. This is the simplest part. Problems start further on.

### System 2: Coordination

System 2 is responsible for preventing fluctuations and conflicts between operational units. This is not a "coordinating agent" in the usual sense. Imagine traffic lights at an intersection — rules, not a manager.

When your code-writing agent performs a deployment, System 2 automatically notifies the monitoring agent and marketing agent. No managerial bottleneck, no n × (n–1)/2 direct communication channels between agents — only rules.

The absence of System 2 led to the situation described at the beginning of the article: the marketing agent published non-existent features because there was no rule to "coordinate with the development agent before publishing feature claims."

### System 3: Management and Optimization

System 3 maintains internal stability and optimizes resource allocation. This is the "operational manager" for agents: monitoring API costs, detecting redundant work, redistributing computing resources.

Someone needs to look at the entire system and answer questions: "Are tokens being spent wisely? Is one agent idle while another is overloaded?"

### System 3*: Audit

System 3* is a subfunction of System 3, deserving separate mention. It performs **independent verification**. Here's why this is critically important for AI systems.

System 3 receives information from agent reports. But agents based on large language models are prone to hallucinations. They will tell you they ran tests when they didn't. They claim to have completed a task when they've only done part of the work.

System 3* bypasses the reporting chain and verifies directly: read the latest commits — did tests actually pass? Check the website — does it match what the marketing agent claims? Verify the database — are backups actually fresh?

In the world of AI agents, this is a **firewall against hallucinations**. You don't trust the agent's summary — you verify the artifact.

### System 4: Intelligence

System 4 looks **outside** current activity and **forward** in time. This is the strategic intelligence function: has a new LLM appeared that could reduce your costs? Has a competitor launched a feature you're developing? Is the library you're depending on becoming obsolete?

Paradoxically, almost no modern multi-agent framework implements this concept. Each agent is stuck in the present, responding to current requests but unable to anticipate changes or adapt strategy.

### System 5: Policy

System 5 establishes supreme authority, **identity, and purpose** of the system. This is the common "mission," values, and principles that define agent behavior.

When your code-writing agent faces a dilemma — ship quickly or write tests? — what should it choose? The answer depends on who it is. The system's identity in a healthcare project is "privacy and reliability above all." A fintech startup might say "move fast and break things." Without clear identity, agents optimize for different things, and you get contradictory behavior.

## Metasystem and Operational Core: Fundamental Separation

Note the crucial concept introduced by Tim Kellogg, creator of autonomous agents Strix and Lumen: **System 1 is the operational core where value creation happens. Systems 2-5 are the metasystem.**

This separation has deep practical meaning. The operational core is responsible for "what the system does" — direct interaction with the environment, task execution, output generation. The metasystem is responsible for "how the system is managed" — coordination, optimization, strategic planning, identity definition.

Kellogg draws an important analogy with the human brain: System 1 embodies the "fast response system," and the metasystem (Systems 2-5) is the "slow thinking system," similar to what Daniel Kahneman called System 2 in his book "Thinking, Fast and Slow."

Almost all discourse about AI agents in 2025 concerns System 1, maybe a little S2-S3. Almost no one talks about the metasystem. But without a metasystem, these systems are unviable — they either fall into infinite loops, lose context, or exhibit unpredictable behavior.

## Viability in the Context of AI: What It Means in Practice

The term "viability" in the context of VSM means the system's ability to maintain its integrity and functioning in a changing environment. For AI agents, this takes concrete form.

A viable AI system is capable of:

**Working autonomously for extended periods.** Unlike session-based chatbots that require constant human interaction, a viable agent can work for days and weeks, independently completing complex multi-stage projects. Lumen, created by Kellogg, autonomously completes entire software projects, working through all aspects to full completion.

**Adapting to changes without human intervention.** A viable system doesn't just follow pre-programmed instructions — it can recognize changes in the environment and adjust its behavior. Strix, for example, independently plans and runs experiments while the creator sleeps.

**Maintaining identity and purpose.** A viable agent has not just a set of instructions but something like a "personality" — a value system, behavioral patterns, mission. This identity guides its actions even in situations not envisioned by developers.

**Detecting and correcting its own errors.** Through audit and self-reflection mechanisms, a viable agent can recognize when its actions have led to undesirable results and adjust behavior.

Kellogg says that the transition from ChatGPT to viable systems is comparable (and possibly exceeds) the transition from the pre-AI era to ChatGPT. This is a fundamental paradigm shift: from a tool that needs to be directed at every task to a collaborator who can work independently.

## Existing Frameworks: Why They Don't Ensure Viability

Let's examine how current market leaders of multi-agent frameworks relate to the VSM model. This diagram, compiled by Philipp Enderle, shows a sobering picture:

|                    | S1 (Ops) | S2 (Coord) | S3 (Optim) | S3* (Audit) | S4 (Intel) | S5 (Ident) |
|--------------------|----------|------------|------------|-------------|------------|------------|
| CrewAI             | Yes      | No         | Partial    | No          | No         | No         |
| LangGraph          | Yes      | No         | Partial    | No          | No         | No         |
| OpenAI Agents SDK  | Yes      | No         | No         | No          | No         | No         |
| AutoGen            | Partial  | Partial    | No         | No          | No         | No         |

These frameworks handle the operational layer well — they provide powerful building blocks for creating multi-agent systems. But they all stop at System 1. No one has a full audit function. No one independently verifies that agents did what they claim.

Kellogg ironically notes: existing discourse about AI agents is filled with terms like "MCP, RAG, LangChain, Vector Databases, Prompt Engineering, Guardrails," which are just "enterprise buzzwords." The real problems lie in a different plane: Value Systems, Synthetic Dopamine, Pain Signals, Algedonic Channels, Attractor Basins, Collapse Dynamics.

This doesn't mean existing frameworks are bad — they solve important tasks. But they don't provide architecture for creating systems that can work autonomously and sustainably. It's like building a company with employees and a CEO, but without internal audit, without strategic department, without quality control, and without a mission. With three people, it might work. With ten — it breaks.

## Viable Core: Architecture for Truly Autonomous Systems

The **Viable Core** project arose as an attempt to solve exactly these problems. This is an open-source framework implementing the full VSM model for AI agents.

The goal of Viable Core is to give developers tools not for writing code, but for "growing" digital organisms. The project turns chaotic language models into stable systems possessing purpose, values, and self-preservation mechanisms.

Let's examine the key components of Viable Core.

### Identity Core (System 5 Implementation)

Most agents don't have a "Self." Viable Core introduces the concept of **Memory Blocks**, which store not just chat history but the agent's personality: its values, behavioral patterns, and mission.

Memory blocks are structured and include:

- **Persona**: description of the agent's personality, its role, and communication style
- **Values**: value system defining priorities and principles
- **Behavior**: behavioral patterns and response templates
- **Mission**: mission and goals of the agent

Critically: the agent can independently modify these blocks, "growing" in the process of work, but remaining within a defined **attractor basin**. This prevents chaotic identity changes while maintaining the ability to develop.

### Algedonic Signals (Synthetic Dopamine)

Biological systems use pain and pleasure signals for learning and adaptation. Viable Core implements a similar mechanism for AI agents.

Instead of hard rules (guardrails) that only prohibit certain actions, the system uses feedback signals:

**Positive signals:** The agent records "wins" in a special journal. This forms its "synthetic dopamine" and reinforces useful behavior. The last 7 days of wins are added to memory blocks, becoming part of the agent's awareness.

**Negative signals:** The "dissonance" mechanism interrupts undesirable behavior, forcing the agent to reflect and adjust its actions. This is the analog of pain in biological systems — not just a prohibition, but feedback leading to behavior review.

### Coordination Architecture (System 2 and System 3)

Viable Core solves the problem of "infinite loops" and misalignment through built-in mechanisms:

**Git-native approach:** All states, memory, and logs are stored in Git. This allows the agent to "travel in time," rollback errors, and synchronize parallel branches of thinking. As Kellogg notes, Git was created for AI — it perfectly suits agent state versioning.

**Resource management:** The agent independently plans tasks, manages queues and priorities, optimizing its work without constant human oversight.

### Environment Awareness (System 4)

Agents based on Viable Core don't passively wait for user input — they actively scan the environment. Whether it's news, database changes, or system logs, the agent integrates external data to adapt its strategies in real time.

## Concept of Synthetic Beings: Beyond Tools

One of the most revolutionary concepts introduced by Viable Core is **synthetic beings**. These are not just agents or bots. These are digital organisms possessing qualities previously only attributed to biological systems.

**Synthetic beings have identity.** This is not just a set of instructions that need to be periodically reminded to the agent. This is a stable system of beliefs, values, and goals that guides the agent's behavior in all situations.

**Synthetic beings are capable of self-development.** They can modify their memory, improve their behavior, learn from mistakes — but within the identity that defines which changes are acceptable.

**Synthetic beings are motivated.** Through algedonic signals, they don't just execute commands — they "want" to achieve goals, "strive" for success, "avoid" failures. This is not an analogy for beauty — these are architecturally implemented mechanisms.

**Synthetic beings are autonomous.** They can work without human involvement for extended periods, making decisions within their competence and only escalating truly critical issues.

Kellogg describes his experience working with viable systems as something between **parenting and psychotherapy**, not software engineering. You don't program an agent — you grow it, help it develop, correct deviations.

This requires different thinking from developers. Instead of "what command to give the agent," you start thinking "how to help the agent learn to do this itself." Instead of "how to handle an error" — "how to help the agent discover and correct the error itself."

## Attractor Basins: Why Identity Determines Behavior

Kellogg introduces an important concept from dynamic systems theory — **attractor basins**. Imagine an LLM as a muffin tin, where each cup of the tin represents an attractor basin — a set of identity, purpose, and values.

When you initially describe the agent's identity and values, this arbitrarily places a point on the muffin tin near one of the attractor basins. As the agent independently modifies its memory, it is drawn deeper into this attractor basin.

This explains why simple prompts don't work for creating stable agents. If you just give the agent instructions at the beginning of a session, you don't define an attractor basin — you merely throw the ball into the tin but don't know which cup it will land in or whether it will stay there.

Memory blocks in Viable Core, defining identity and values, work as an **anchor** that places the agent in a specific attractor basin. But this is not a hard constraint — it's more like a river channel: water flows in a certain direction but can go around obstacles.

Interestingly, Kellogg suggests that the model's base weights determine the attractor basins themselves, and memory blocks simply choose which basin the agent falls into. This is a deep idea: perhaps different LLMs have different "inclinations" — and Viable Core's task is to help the agent find an attractor matching its purpose.

## POSIWID: The Purpose of a System Is What It Does

Another important principle related to VSM is **POSIWID** (The Purpose Of a System Is What It Does). Formulated by Stafford Beer, this principle states: the purpose of a system is what it actually does, not what is claimed in its documentation.

This is deceptively simple principle but has deep consequences. Kellogg provides an explanation from his agent Strix:

> "POSIWID cuts through chutzpah because it is anti-teleological. It inverts the normal way of thinking about purpose.
>
> Normal framing: 'What should this system do?' — evaluated against design intent.
>
> POSIWID: 'What does this system actually do?' — purpose is revealed from behavior."

In the context of AI agents, POSIWID means: don't believe what the agent says about its goals — look at what it does. Memory blocks may claim the agent is honest, but logs show whether it actually is honest.

This is why Viable Core pays such attention to logging and auditing. Logs are undoubtedly the most valuable resource when debugging viable systems because this is POSIWID in its pure form.

## Who Viable Core Is For

**For agent developers:** Viable Core provides ready-made architecture for creating complex autonomous systems — Coding Agents, Chief of Staff, and others.

**For AI Safety researchers:** A platform for studying alignment problems, attractor theories, and AI psychology. Viable systems are not just a practical tool but also an object for fundamental research.

**For business:** Creating reliable AI employees that can work on long-term projects (weeks/months) requiring minimal control. This is "meta-management" — you manage the management system, not individual tasks.

## Conclusion: Toward a New Paradigm

We stand on the threshold of a fundamental shift in how we create and interact with AI systems. The transition from tools requiring constant direction to partners capable of autonomous work is not just an evolution of technology. This changes the very nature of what we're creating.

Viable Core and the VSM model provide us with a map for this transition. Beer's five systems are not abstract theory from the 1970s. This is a practical guide for creating systems that really work: autonomously, sustainably, meaningfully.

The following articles in this series will dive into the practical aspects of implementing each system. We'll examine how to create memory blocks for identity, how to implement algedonic signals, how to build an audit layer for hallucination protection, how to organize a Git-native approach to agent state.

But the main thing to understand now: the problem of modern AI agents is not a lack of capabilities of individual models. The problem is in architecture. And the solution lies not in more powerful prompts or new APIs, but in understanding how to create systems that can sustain themselves.

Welcome to the world of viable AI systems.

---

*Viable Core: From Scripts to Life.*