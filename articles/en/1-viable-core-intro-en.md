# Why Your AI Agent is Going Insane and How Git Can Become Its Brain

We once launched an autonomous agent to optimize cloud spending. Three hours later, it managed to blow $50 on tokens by running in circles: it created a ticket, replied to itself, found an error in its own reply, and started the cycle all over again. In the logs, it looked like productive work; in reality, it was a digital psychosis.

Sound familiar? If you've tried building anything more complex than a basic chatbot using LangChain or CrewAI, you've likely hit this wall. Agents hallucinate, lose context, or start refactoring code they weren't even supposed to touch.

The problem isn't that LLMs are "stupid." The problem is the architecture. We're trying to build complex systems using only "hands" (System 1), forgetting that any organism needs a brain and a nervous system (Systems 2–5).

This pain led to the creation of **Viable Core** — an open-source framework for building autonomous systems that don't fall apart after an hour of work. It's based on Stafford Beer’s Viable System Model (VSM), a cybernetic framework proven by decades of real-world business application.

## Five Systems That Will Save Your Project

Stafford Beer proved back in the 70s that any viable system — from a cell to a corporation — consists of five functions. If you drop even one, pathologies inevitably emerge. In the world of AI agents, it looks like this:

### 1. Operations (System 1)
These are the agents themselves: coders, researchers, analysts. Every modern framework does this. They are the "muscles."

### 2. The Traffic Light, Not a Manager (System 2)
These are coordination rules. Imagine a coder-agent deploying code. System 2 automatically pauses the marketing-agent to prevent them from announcing a feature before the tests are finished. It's not a complex boss-subordinate logic; it's just a set of protocols to prevent conflicts.

### 3. Resource Audit (System 3 and 3*)
S3 keeps an eye on spending. If an agent starts burning $10 a minute on empty cycles, S3 should notice and hit the brakes.

But there’s also S3* — the **hallucination detector**. Agents love to lie. They say, "I ran the tests, everything is fine." S3* doesn't take their word for it. It goes into Git, checks the CI/CD logs, and looks at the actual commits. If there’s no artifact, the agent is hallucinating. We trust facts in the repository, not the model’s words.

### 4. Intelligence (System 4)
Most agents live "in the moment." S4 looks outward and forward. Is there a new library version? A cheaper and faster model? S4 scans the environment and suggests adapting the strategy before things break.

### 5. Identity (System 5)
This is the "Self" of the system. A set of values and a mission. Without S5, an agent doesn't know what to choose: move fast or do it right? S5 sets the vector ("reliability above all"), keeping the entire system within the bounds of common sense.

## Git-native: Why Does an Agent Need a Repo?

One of the key features of Viable Core is storing all memory and state in Git.

Why does it matter?
- **Time Travel:** If an agent "goes insane" and corrupts its memory, you just `git checkout` back to a stable state.
- **Transparency:** You see every change in the agent's "personality" or "plans" as diffs.
- **Synchronization:** Multiple agents can work on different branches of the same task and then merge their results, resolving conflicts.

Git isn't just a place to store code; it's the perfect "external memory" for autonomous systems.

## From Scripts to Digital Organisms

We're used to treating AI as tools. Call it — get a result. Но for long-term tasks (lasting weeks or months), we need **autonomous employees**.

Viable Core allows you to "grow" a system rather than just "write prompts." You give it an identity core (Memory Blocks in YAML), set up pain and pleasure signals (algedonics), and let it work.

This requires a paradigm shift. Development becomes something between systems architecture and parenting: you don't fix a bug in the code; you correct the agent's values so it doesn't make that mistake again.

---

This is the first article in a series on viable systems. Next, we'll dive into how to implement "synthetic dopamine" and how to build an S5 that keeps your agent from turning into an expensive spam bot.

*Viable Core: Architecture for those tired of unstable agents.*
