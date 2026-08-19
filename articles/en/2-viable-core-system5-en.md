# Your AI Has No "Self": How System 5 Turns a Prompt into a Personality

Why does an agent that writes perfect, test-backed code in the morning start churning out "dirty hacks" and ignoring edge cases by the evening? It's not because the model is "tired." It just doesn't have an anchor.

In most frameworks (CrewAI, AutoGen), an agent's role is just a system prompt. As the context grows or the task gets harder, this prompt "blurs." The agent loses its face, turning from a pedantic senior engineer into a reckless cowboy coder.

In Viable Core, stability is managed by **System 5** (Policy). This isn't a dry rulebook; it's the agent's "constitution," locked in Git. Without it, your AI is just a script with amnesia. With it, it's an autonomous employee with a value system.

## Attractor Basins: Why "Just a Prompt" Fails

Imagine an agent's behavior as a ball on an uneven surface with pits. Each pit is an "attractor basin" — a stable state. One pit is "Safe DevOps," another is "Quick & Dirty Coder," a third is "Infinite Hallucinator."

When you give an agent a standard prompt, you're just pushing the ball toward the right pit. But at the first sign of trouble, the ball can easily roll into the neighboring "hallucination pit."

System 5 in Viable Core does two things:
1. Selects the right "pit" for the agent.
2. Makes its walls so high that the agent can't accidentally become someone else under pressure.

This is called **meta-control**. We don't dictate every step; we set the gravity that pulls the agent toward the right decisions.

## YAML as the DNA of Personality

In Viable Core, an agent's identity isn't just text in the LLM's head; it's a set of YAML files in a Git repository. These are its Memory Blocks.

### 1. persona.yaml (Who am I?)
Here we define the role and voice. But most importantly — traits.
```yaml
name: "Builder"
role: "Viable Core DevOps Engineer"
traits:
  - "Skepticism toward hype technologies"
  - "Preference for metrics over words"
```
If an agent has "skepticism" baked in, it won't suggest rewriting your entire production stack in a trendy new framework that came out yesterday. It simply "can't," because its persona pulls it toward stability.

### 2. values.yaml (What matters to me?)
This is where the magic happens: priority weights.
```yaml
priorities:
  - key: "Stability"
    weight: 10
  - key: "Release Speed"
    weight: 4
```
When the agent faces a choice between "deploy fast" or "write more tests," it checks the weights. A priority of 10 will always outweigh 4. This is exactly what was missing for our "Agent X" who blew $50 on tokens: it lacked a "Resource Efficiency" value with a weight of 10. To Agent X, infinite reasoning was just as valuable as the result.

### 3. behavior.yaml (How do I react?)
Here we codify reflexes and **self-modification rules**.
An agent can "grow up" and change its own configs. But System 5 imposes constraints: "You cannot change your core values by more than 10% at a time." This is protection against "digital suicide" or sudden personality flips.

## POSIWID: The Purpose of a System Is What It Does

Stafford Beer (the father of VSM) introduced the POSIWID principle: *The Purpose of a System Is What It Does*. A system's real purpose is its actual output, not what's written in its documentation.

An agent can write in its logs all day: "I value security very much." But if it deploys code without checking permissions, its real purpose is something else.

System 5 in Viable Core constantly compares YAML configs with real logs (`wins.jsonl`). If words and deeds diverge, the system triggers "dissonance" and forces the agent to reflect. This is a built-in lie detector for neural networks.

## Why Store the "Soul" in Git?

Storing Memory Blocks in Git gives us what no other framework offers:
1. **Personality Diffs:** You see in commits how an agent's beliefs evolved. "Aha, after the database incident, it raised its own Security priority weight."
2. **Reset to Sanity:** If an agent starts talking nonsense, you just `git reset` to a state when it was useful.
3. **Versioned Experience:** You can clone a "seasoned" agent and launch it on a new project.

## Summary

System 5 turns AI from a text generator into a subject. It's the foundation of autonomy. Without it, you just have a "smart chatbot" that will fall apart under the first sign of real stress.

In the next article, we'll look at how to make an agent "feel" its mistakes through algedonic signals — synthetic pain and pleasure.

*Viable Core: Building systems that remember why they are here.*
