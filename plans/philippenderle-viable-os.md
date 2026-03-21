Вот исправленная версия текста. Я заменил неоднозначные символы Unicode (ем-дэш, стрелки, знак умножения) на их стандартные ASCII-эквиваленты, а также убрал лишние обратные слеши перед звездочками, которые являются артефактами разметки.

# Your AI Agents Need an Org Chart - But Not the Kind You Think - DEV Community
I run a small healthcare SaaS. Solo founder, Python/FastAPI backend, React frontend, German-hosted VPS. The usual indie stack.

A few weeks ago I decided to go all-in on AI agents. Not one - a whole team. A coding agent for bug fixes and feature work. An ops agent watching my server. A go-to-market agent drafting landing page copy and doing competitor research.

Each one worked beautifully in isolation. Then I let them loose together.

Within a week, my go-to-market agent had published a feature comparison table on the website that included two features we hadn't built yet. My coding agent, meanwhile, was happily refactoring auth middleware - important work, but nobody told the ops agent, which then flagged the deployment as a breaking change and sent me a 2am alert on WhatsApp. Three agents, all competent, all actively making my life worse.

I spent that weekend not debugging code, but thinking about something I hadn't touched since my consulting days: **organizational design**.

[](#the-realization-that-hit-me)The realization that hit me
-----------------------------------------------------------

Here's the thing - I spent 9 years at Deloitte and Berylls (now AlixPartners) doing exactly this for DAX automotive companies. Designing org structures. Building target operating models. Figuring out how 800 people should coordinate without stepping on each other.

And the problems I was seeing with my three AI agents? I'd seen them before. In billion-dollar organizations. The exact same pathologies:

*   Marketing promises something Engineering can't deliver -> **coordination failure**
*   One team absorbs all the budget while others starve -> **resource dominance**
*   Everyone's optimizing locally but nobody's looking at the big picture -> **missing oversight**
*   Reports say everything's great, but the actual output is garbage -> **no independent verification**
*   The company is heads-down executing, not noticing the market has shifted -> **strategic blindness**

These aren't random problems. They're structural. And there's a theory from the 1970s that explains exactly why they happen and how to fix them.

[](#stafford-beers-cheat-code)Stafford Beer's cheat code
--------------------------------------------------------

In 1972, a British cyberneticist named Stafford Beer published _Brain of the Firm_. The core idea: every system that survives - a cell, an organism, a company, an economy - has exactly five control functions. Miss any one of them and the system develops pathologies. Not might. Will.

He called it the **Viable System Model** (VSM). I'd used it in consulting to diagnose organizational dysfunction. But sitting there at 2am, staring at my WhatsApp alert from an overzealous ops agent, I realized: this applies directly to multi-agent AI systems.

Let me show you what I mean. Here are the six functions (five systems, one with a crucial sub-function), translated to agents:

**System 1 - Operations.** The agents doing actual work. Your coders, your researchers, your support bots. Every framework gets this right. It's the easy part.

**System 2 - Coordination.** Rules that prevent agents from conflicting. Not a "coordinator agent" - think of it more like traffic lights. When my coding agent deploys, System 2 automatically notifies the ops agent and the go-to-market agent. No manager bottleneck, no n x (n-1)/2 direct channels. Just rules.

This is what was missing when my go-to-market agent published features we hadn't built. There was no rule saying "check with the dev agent before publishing feature claims."

**System 3 - Optimization.** Something that watches the whole system. Are tokens being spent wisely? Is one agent idle while another is overwhelmed? This is your operations manager, except for agents it's concrete: monitor API costs, detect redundant work, reallocate compute.

**System 3* - Audit.** This is the one that matters most for AI. System 3 gets its information _from the agents' own reports_. But agents hallucinate. They confabulate. They'll tell you they ran the tests when they didn't. System 3* bypasses the reporting chain and checks directly: read the last 5 commits - did the tests actually pass? Check the website - does it match what the go-to-market agent claims? Verify the database - are backups actually fresh?

In a company, this is internal audit. For AI agents, it's your hallucination firewall. You don't trust the agent's summary - you verify the artifact.

**System 4 - Intelligence.** The function that looks _outside_ and _forward_. Is there a new LLM that could cut your costs? Did your competitor just launch the feature you're building? Is a library you depend on being deprecated?

I don't know of a single multi-agent framework that has this concept. Every agent is stuck in the present.

**System 5 - Identity.** The shared purpose. When your coding agent faces a trade-off - ship fast or write tests? - what should it choose? The answer depends on who you are. My system's identity is "privacy and reliability above everything" because I'm in healthcare. A fintech startup might say "move fast." Without this, agents optimize for different things and you get incoherent behavior.

Here's how the complete model looks when you put all six functions together:

[![The Viable System Model applied to AI agent teams. System 5 (Identity) at the top sets purpose and values. System 4 (Intelligence) scans the external environment. System 3 (Optimization) manages resources across all operations. System 3* (Audit) independently verifies agent outputs - your hallucination firewall. System 2 (Coordination) provides the rules that prevent conflicts. System 1 (Operations) at the bottom contains the autonomous agent teams, each interacting with its own slice of the environment.](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fhy2c69f9fohp2i1osktg.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fhy2c69f9fohp2i1osktg.png)

The key insight from Beer: these aren't optional features you add later. They're **structural requirements** for any system that needs to remain viable. Remove any one and the system develops predictable pathologies - whether it's a Fortune 500 company or three AI agents on a VPS.

[](#diagnosing-my-own-system)Diagnosing my own system
-----------------------------------------------------

I took my three-agent setup and scored it honestly:  

```
                    Have it?
Operations (S1)     ✅  Yes - three specialized agents
Coordination (S2)   ❌  Nope - agents had no rules about each other
Optimization (S3)   ❌  Nope - nobody watching the whole
Audit (S3*)         ❌  Nope - I trusted agent reports at face value
Intelligence (S4)   ❌  Nope - nobody looking outside
Identity (S5)       ❌  Nope - no shared purpose document

```


Enter fullscreen mode Exit fullscreen mode

One out of six. No wonder it was a mess.

So I redesigned the whole thing from scratch. Here's what the configuration looks like:  

```
viable_system:
  name: "German Healthcare SaaS"

  identity:
    purpose: "Help therapists focus on patients, not paperwork"
    values:
      - "Patient privacy above everything"
      - "Simplicity over feature bloat"
      - "Reliability over speed"
    decisions_requiring_human:
      - "Pricing changes"
      - "Anything touching patient data"
      - "Publishing to production"

  system_1:
    - name: "Product Development"
      purpose: "Build and stabilize the software"
      autonomy: "Can fix bugs independently. Features need approval."
      tools: [github, testing, code-review]

    - name: "Operations"
      purpose: "Keep the platform running"
      autonomy: "Can monitor and alert independently. Deployments need approval."
      tools: [ssh, docker, log-analysis]

    - name: "Go-to-Market"
      purpose: "Get first customers"
      autonomy: "Can draft content independently. Publishing needs approval."
      tools: [website-editing, seo-analysis, copywriting]

  system_2:
    coordination_rules:
      - trigger: "Go-to-Market mentions a feature on the website"
        action: "Validate with Product Dev that the feature exists"

      - trigger: "Product Dev deploys a new feature"
        action: "Notify Go-to-Market for website update, Ops for monitoring"

      - trigger: "Ops detects a performance issue after deployment"
        action: "Notify Product Dev with logs and priority tag"

  system_3:
    reporting_rhythm: "weekly"
    resource_allocation: "Dev: 60%, Ops: 20%, Go-to-Market: 20%"

  system_3_star:
    schedule: "bi-weekly"
    checks:
      - name: "Code Quality"
        target: "Product Development"
        method: "Read last 5 commits. Did tests actually pass? Check coverage."
      - name: "Content Accuracy"
        target: "Go-to-Market"
        method: "Compare website claims against actual shipped features."
      - name: "GDPR Compliance"
        target: "All"
        method: "Check if patient data leaked into agent prompts or logs."
    on_failure: "Escalate to human immediately"

  system_4:
    monitoring:
      competitors: ["TherapieApp", "PraxisPro", "SimplePractice"]
      technology: ["New LLM releases", "Python/React breaking changes"]
      regulation: ["GDPR updates", "Healthcare data laws"]

```


Enter fullscreen mode Exit fullscreen mode

The coordination rules in `system_2` are the ones that would have prevented my go-to-market agent from publishing phantom features. The `decisions_requiring_human` in `identity` is what keeps me in the loop for anything that matters.

[](#why-this-matters-beyond-my-little-saas)Why this matters beyond my little SaaS
---------------------------------------------------------------------------------

Deloitte's 2025 AI report says 40% of multi-agent projects will be scaled back or abandoned by 2027. Not because the agents are dumb. Because the organization is missing.

Look at every major framework right now:  

```
                    S1    S2    S3    S3*   S4    S5
                   Ops  Coord Optim Audit Intel Ident
CrewAI              ✅    ❌    ⚠️    ❌    ❌    ❌
LangGraph           ✅    ❌    ⚠️    ❌    ❌    ❌
OpenAI Agents SDK   ✅    ❌    ❌    ❌    ❌    ❌
AutoGen             ⚠️    ⚠️    ❌    ❌    ❌    ❌

```


Enter fullscreen mode Exit fullscreen mode

These frameworks are great at what they do - giving you powerful building blocks for multi-agent systems. But they all stop at the operational layer. Nobody has an audit function. Nobody independently verifies that agents did what they claim. In a world where LLMs hallucinate by design, that's a gap.

It's like building a company with employees and a CEO, but no internal audit, no strategy department, no quality control, and no mission statement. It works at 3 people. It breaks at 10.

Look at the diagram again - the pink System 3 command channel running down the center, the orange System 2 coordination bars on the right, the S3* audit triangle probing directly into operations. These aren't theoretical niceties. They're the difference between agents that collaborate and agents that collide.

[](#what-im-building)What I'm building
--------------------------------------

I'm turning this into a tool called [ViableOS](https://github.com/philipp-lm/ViableOS). You describe your business, it generates the control functions - including the audit layer - and deploys them to your agent framework of choice. Think of it as Terraform, but for agent organizations instead of cloud infrastructure.

It's early. The config format above is how I've designed my own setup. The tooling to actually deploy it is what I'm building now. If you're running multi-agent systems and hitting coordination problems, I'd genuinely love to hear about it - it helps me figure out whether this is a problem only I have or something broader.

[Open an issue on GitHub](https://github.com/philipp-lm/ViableOS/issues) if you've got a war story, or [subscribe to the newsletter](https://buttondown.com/viableos) if you want to follow along as I build this in public.

* * *

_Next in this series: *_"The Dominance Problem"* - what happens when one agent eats all your tokens, and how a System 3 resource monitor fixes it. [Subscribe](https://buttondown.com/viableos) to get notified.\*

* * *

**Philipp Enderle** - Engineer (KIT, TU Munich, UC Berkeley). 9 years strategy consulting at Deloitte and Berylls by AlixPartners, designing org transformations for DAX automotive companies. Now applying the same organizational theory to AI agent teams.

[LinkedIn](https://www.linkedin.com/in/philipp-enderle/) · [GitHub](https://github.com/philipp-lm) · [ViableOS](https://github.com/philipp-lm/ViableOS)