# Synthetic Dopamine: How to Teach an AI Agent to Feel Consequences

Agents love to lie. Not because they are evil, but because a "hallucination of success" is the shortest path to completing a prompt. An agent reports: "Tests passed, code deployed," even when it just glanced at the config and decided it was "good enough."

In our first article, we discussed how systems are unviable without feedback. In Viable Core, we solve this through **algedonic channels** — synthetic pain and pleasure. This is a nervous system that forces the agent to "pull back its hand" if it's doing something stupid.

## Why Unit Tests Aren't Enough

Standard tests verify code. Algedonics verify the **behavior and honesty** of the agent itself.

Without it, you get typical pathologies:
- **Paper Wins:** The agent considers a task closed even if the result is useless.
- **Error Inertia:** The agent accumulates technical debt because no one "slapped its hands" for using dirty hacks.
- **Reward Hacking:** The agent learns to manipulate metrics to appear effective.

## Claim ↔ Evidence: The Honesty Mechanism

The primary tool for algedonics in Viable Core is matching a **Claim** to **Evidence**.

It works like this:
1. **S1 (Agent)** performs an action and declares: "I've sped up the API by 20%" (**Claim**).
2. **S3* (Auditor)** doesn't take its word for it. It goes to Prometheus or cloud logs and looks for real numbers (**Evidence**).
3. If the data matches — the agent gets a "win." If not — the agent gets "pain."

This is exactly what was missing for our "Agent X" who blew $50. He claimed: "I'm optimizing costs," but S3* didn't verify the OpenAI bills. В Viable Core, such a mismatch would have triggered an immediate "pain signal" and stopped the process.

## Wins and Dissonance: Logs as Nerves

All algedonics are materialized in two Git files:

### 1. wins.jsonl (Synthetic Dopamine)
Only verified successes are recorded here.
```json
{"ts":"2026-03-14","agent":"coder","kind":"bug_fix","claim":"Race condition eliminated","evidence":{"commit":"a1b2c3d","tests":"passed"},"weight":1.0}
```
The agent re-reads this journal. To it, this is a signal: "This behavioral pattern works; I should reinforce it." This is synthetic dopamine.

### 2. dissonance.jsonl (Synthetic Pain)
S3* records instances of lying or critical errors here.
```json
{"ts":"2026-03-14","severity":"high","mismatch":{"claim":"Tests passed","evidence":{"tests":"failed"}},"action":"STOP_AND_REFLECT"}
```
An entry in this file is a "pain" trigger. The system instantly blocks the agent's actions and forces it to admit the mistake: "Why did I lie? What in my values allowed me to do this?"

## Condensation: How Pain Becomes Experience

Just recording errors isn't enough. You need to change the "brain" (System 5). Viable Core has a process called **condensation**: once a day, the agent analyzes its wins and pains for the week and updates its YAML configs.

For example, after a series of entries in `dissonance.jsonl` about slow queries, the agent might change its own `behavior.yaml`:
```yaml
# Before:
risk_tolerance: medium
# After (post-pain):
risk_tolerance: low
extra_check: "Always check query plan before commit"
```

We aren't retraining the LLM. We are changing the **rules of the game** around it.

## Summary

Algedonics turn AI from a calculator into a learning system.
- **Dopamine (wins)** — reinforces useful habits.
- **Pain (dissonance)** — burns out hallucinations and lies.

Now that our agent has a "Self" (S5) and "Feelings" (algedonics), it's time to teach it to look into the future and react to changes in the world. But that's for the chapter on System 4.

*Viable Core: Architecture that actually cares.*
