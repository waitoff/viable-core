# Git as a Brain: Why Your AI Agent Needs a Repo, Not Just a Database

When building multi-agent systems, the biggest challenge is coordination. Agents start interfering with each other: one deploys code while the second refactors the database, and the third writes an announcement for a feature that just "broke."

In a classical VSM (Viable System Model), order is maintained by **System 2** (Coordination) and **System 3** (Management). In Viable Core, we implement these through a **Git-native approach**.

Why Git? Because it's a perfect state management tool that engineers have used for decades. If Git works for distributed teams of humans, it's perfect for agents too.

## The Failure of Agent X: A Tale of Infinite Loops

Remember our Agent X? He spent $50 on tokens just talking to himself in an infinite loop. Why did this happen? Because his "memory" was ephemeral. He only saw the current context and didn't realize he was doing the same thing for the tenth time.

If Agent X had worked in a Git-native architecture, every "step" he took would have been a commit.
1. System 2 (the traffic light) would have seen identical changes piling up in the `thought-process` branch.
2. System 3 (the resource manager) would have noticed the token limit for this task was exhausted.
3. The system would have instantly performed a `git reset`, rolling the agent back to the moment before the psychosis began, and alerted a human.

## System 2: A Traffic Light Instead of a Manager

In Viable Core, coordination isn't a "master agent" barking orders. It's a set of rules implemented through Git-hooks and state files.

We call these **"traffic lights."**
For example: A developer-agent creates a `feature/auth` branch. System 2 automatically creates a mutex file in the repository. If a marketing-agent tries to write a post about this feature, they see a "red light": *"The feature/auth branch hasn't passed the S3* audit yet. Wait."*

This doesn't require complex dialogue logic between agents. They just look at the state of the repository. Git becomes the **Single Source of Truth (SSoT)**.

## System 3: Resource Management and "Soft Deploys"

S3 ensures that agents don't eat your budget or kill production. In a Git-native approach, this is done through **diff control**.

Before an agent makes changes to "memory" or "code," S3* (the auditor) analyzes the diff:
- How many lines were changed?
- Does this violate the "attractor" boundaries (System 5)?
- Does this fit the current token budget?

If a coder-agent suddenly decides to rewrite 200 files at once, S3 blocks the commit: "Change volume too large. Break into atomic tasks." This protects the system from "hallucinatory explosions" where a single model error spreads across the entire project.

## Key Features of Git-native Architecture

1. **Diffs Over Logs.** You don't read thousands of lines of chat history. You look at `git diff`. What did the agent change in its plan? What did it add to its "wins" list? It's visual and clear.
2. **Time Travel.** If an agent hits a dead end, you `git checkout` to two hours ago. The agent "wakes up" in a stable state and tries a different path. This is cheaper and faster than trying to "argue" with it in chat.
3. **Parallel Universes.** An agent can launch three different strategies for a task in three different branches. S3 compares the results (diffs and metrics) and chooses the best one to `merge`.

## Summary

Git isn't just a place to store code. In Viable Core, it is the **infrastructure of consciousness**.
System 2 uses it for coordination (mutexes and branches), while System 3 uses it for quality and resource control (diff auditing).

This turns agent development from "prompt-guessing" into a proper engineering process. Now we have control, versioning, and the ability to roll back.

In the next article, we'll look at how to teach an agent to "look around" — System 4 and environmental awareness.

*Viable Core: Making AI Manageable.*
