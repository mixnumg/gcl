# GCL - Guided Conversation Language for LLM Work  
*A lightweight notation for guiding your interactions with Large Language Models (LLMs)*

`gcl-core.yaml` | `gcl-extensions.yaml` | License: CC-BY-4.0

---

## What is GCL?

GCL is a structured but lightweight way to guide LLM responses without verbose instructions.  
Instead of typing *“give me a very short, three-line bulleted summary of…”*, you can use compact symbols or keywords to get consistent results.

The **core of GCL** defines three base symbols:

```
!   → Fast Draft (3-line summary or concise bullets)
++  → Deep Analysis (Why×5, reasoning, risks, evidence)
>   → Exec Brief (1-page briefing note for decision-making)
```

This keeps conversations short, consistent, and repeatable.  

On top of the core, **optional modes** like `:tutor`, `:creative`, or `:story` extend usage across domains such as **Tech, Research, Workplace, Learning, Policy**.

---

## Updates in v1.0

The following refinements have been added since the initial draft:

- **Tone Levels Standardized**  
  Unified levels: `low / medium / high` (or optionally a 1–5 numeric scale).

- **Guardrails Enum Extended**  
  Now supports: `allow / caution / soft_refuse / refuse`  
  (enabling more nuanced safety handling in domain-specific contexts, e.g., `med_legal_finance: soft_refuse`).

- **Telemetry Extended**  
  In addition to `trace_id`, optional fields like `parent_span`, `latency_ms`, and `feedback_score` are supported for observability.

- **Domain Packs with Tags**  
  Domain packs (e.g., `design_doc`, `policy_review`) can now carry **tags** for better categorization and filtering.

---

## How to Use

1. Start your chat with a short note that the LLM should follow GCL rules.  
2. Use the symbols at the beginning of your prompt to guide the style.  

**Example**

```text
User:
++ Explain Kubernetes in simple terms.

LLM (Deep Analysis):
- Kubernetes is an open-source container orchestration platform...
- It groups containers into Pods and abstracts infrastructure...
- Risks: complexity, steep learning curve, misconfiguration issues...

→ More examples can be found in the [/examples](./examples) folder.
```

---

## Repository Structure

```
GCL/
├─ README.md
├─ LICENSE
├─ GCL-core.yaml            # The core declaration of GCL
├─ GCL-extensions.yaml      # The extensions declaration of GCL
├─ examples/                # Practical examples for each domain
│  ├─ tech/
│  ├─ research/
│  ├─ workspace/
│  ├─ learning/
│  └─ policy/
└─ docs/                    # Detailed guides and documentation (planned)
```

---

## Roadmap

- **v1.0 (current)**  
  Core declaration (`gcl-core.yaml`), base symbols (!, ++, >), extended guardrails, telemetry, tone, and domain packs.

- **v1.1 (planned for Q4 2025)**  
  Domain-specific examples (tech, research, workspace, learning, policy)  
  Minimal usage guide in `/docs`  

- **v1.2 (planned for 2026 H1)**  
  Extended option modes (`:tutor`, `:creative`, `:story`)  
  Advanced multi-domain examples and usage patterns  

- **v2.0 (future)**  
  Full documentation set (manual, architecture, best practices)  
  Open community contributions (issues/PRs, external examples)

---

## License

This project is licensed under the **Creative Commons Attribution 4.0 International License (CC-BY-4.0)**.  

You are free to use, modify, and share it, as long as you give proper attribution.  
For the full text, see the [LICENSE](./LICENSE) file.

---

## Vision

Although GCL is designed to be LLM-agnostic, at the moment I can only use it fully with GPT (where memory storage is available).  
Other LLMs don’t yet support this kind of persistent setup easily.

My hope is that, in the future, chat interfaces for any LLM will come with simple buttons like:  
[⚡️ Quick Draft] [🤔 Deep Analysis] [👨‍💼 Exec Brief]  

Even better, users could define their own **custom modes** in `gcl-core.yaml`, and the chat UI would generate matching buttons automatically.  
For example:  

```yaml
modes:
  research-critique:
    token: "??"
    intent: "evaluate_research"
    spec:
      steps: ["summary", "strengths", "weaknesses", "future-work"]
```

This would render as a button like [🧪 Research Critique] directly in the interface.

That way, GCL could serve as both a shared convention and a customizable interface layer for all LLMs.
