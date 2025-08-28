> **Notice (Draft Spec)**  
> This repository contains an **early draft specification** of the Guided Conversation Language (GCL).  
> It is experimental and under active refinement.  
> Examples, usage guides, and UI prototypes will be added in future releases (v1.1+).  
> Feedback, issues, and discussions are welcome.  

---

# GCL - Guided Conversation Language for LLM Work  
*A lightweight and structured notation for guiding Large Language Models (LLMs)*

`GCL-core.yaml` | `GCL-extensions.yaml` | `GCL-safety-extension.yaml`  
License: CC-BY-4.0

---

## What is GCL?

GCL (Guided Conversation Language) is a **notation system** for shaping LLM outputs without verbose prompts.  
Instead of typing *“Please give me a short, three-line summary”*, you can use compact symbols for consistent results.

### Core Symbols

```
!   → Fast Draft (3-line summary or concise bullets)  
++  → Deep Analysis (Why×5, reasoning, evidence, risks)  
>   → Exec Brief (1-page decision note for leaders)
```

### Extended Modes

- `:tutor` → Language tutoring & correction  
- `:creative` → Brainstorming & ideation  
- `:story` → Narrative / storytelling  

Optional tags extend GCL across **Tech, Research, Workplace, Learning, Policy**.

---

## Draft Status

This repo is currently released as a **Draft Specification (v1.0)**.  
- **Purpose**: Share the concept early and collect feedback.  
- **Scope**: Core YAML declarations are stable, but examples and docs are incomplete.  
- **Next Steps**: Add domain examples, improve `/docs`, and publish a simple UI prototype.  

---

## Key Updates in v1.0

- **Tone Levels Standardized** → `low / medium / high` (optionally 1–5 scale).  
- **Guardrails Enum Extended** → `allow / caution / soft_refuse / refuse`.  
- **Telemetry Expanded** → `trace_id`, `parent_span`, `latency_ms`, `feedback_score`.  
- **Domain Packs with Tags** → Better categorization/filtering for packs like `design_doc`, `policy_review`.  

---

## How to Use

1. Start your chat with a short note that the LLM should follow GCL rules.  
2. Use the symbols at the beginning of your prompt.  

**Example**

```text
User:
++ Explain Kubernetes in simple terms.

LLM (Deep Analysis):
- Kubernetes is an open-source container orchestration platform...
- It groups containers into Pods and abstracts infrastructure...
- Risks: complexity, steep learning curve, misconfiguration issues...
```

See more in the [/examples](./examples) folder.

---

## Repository Structure

```
GCL/
├─ README.md
├─ LICENSE
├─ GCL-core.yaml              # Core declaration
├─ GCL-extensions.yaml        # Extension declaration
├─ GCL-safety-extension.yaml  # Safety/guardrail declaration
├─ examples/                  # Domain examples (in progress)
│  ├─ tech/
│  ├─ research/
│  ├─ workplace/
│  ├─ learning/
│  └─ policy/
└─ docs/                      # Guides & manual (planned)
```

---

## Roadmap

- **v1.0 (current)**  
  Core symbols (!, ++, >), tone levels, guardrails, telemetry, domain packs.  

- **v1.1 (planned, Q4 2025)**  
  Domain-specific examples + minimal usage guide.  

- **v1.2 (planned, H1 2026)**  
  Extended option modes (`:tutor`, `:creative`, `:story`) + advanced patterns.  

- **v2.0 (future)**  
  Full manual, best practices, and open community contributions.  

---

## License

Licensed under **Creative Commons Attribution 4.0 International (CC-BY-4.0)**.  
Use, modify, and share with attribution. See [LICENSE](./LICENSE).

---

## Vision

GCL is designed to be **LLM-agnostic**.  
In the future, chat UIs could present simple buttons like:  

[⚡ Quick Draft] [🤔 Deep Analysis] [👨‍💼 Exec Brief]  

Or auto-generate buttons from YAML-defined modes, e.g.:

```yaml
modes:
  research-critique:
    token: "??"
    intent: "evaluate_research"
    spec:
      steps: ["summary", "strengths", "weaknesses", "future-work"]
```

Rendering as [🧪 Research Critique] directly in the interface.  

Thus, GCL is both a **shared convention** and a **customizable interface layer** for all LLMs.
