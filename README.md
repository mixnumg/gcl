# GCL - Guided Conversation Language for LLM Work  
*A lightweight notation for guiding your interactions with Large Language Models (LLMs)*

`GCL-core.yaml` | `GCL-extensions.yaml` | `GCL-safety-extension.yaml` | License: CC-BY-4.0

---

## What is GCL?

GCL (Guided Conversation Language) is a **notation system** for controlling how LLMs respond, without long or repetitive instructions.  
Instead of typing *“Please write me a short, three-line summary”*, you can simply use compact symbols or keywords for consistent, predictable results.

### Core Symbols


```
!   → Fast Draft (3-line summary or concise bullets)
++  → Deep Analysis (Why×5, reasoning, risks, evidence)
>   → Exec Brief (1-page briefing note for decision-making)
```

### Extended Modes

- `:tutor` → English practice / correction  
- `:creative` → Brainstorming & ideation  
- `:story` → Narrative / storytelling  

These optional tags extend GCL across **Tech, Research, Workplace, Learning, Policy** and more.


---

## Updates in v1.0

The specification has evolved with three YAML declarations:

- **Core Declaration (`GCL-core.yaml`)**  
  Defines the base modes, symbols, and templates.

- **Extensions (`GCL-extensions.yaml`)**  
  Adds optional features, such as domain packs, telemetry fields, and flexible option namespaces.

- **Safety Extension (`GCL-safety-extension.yaml`)**  
  Introduces guardrails, refusal tiers, and policy-safety mappings.

---

### Key Refinements

- **Tone Levels Standardized**  
  Unified scale: `low / medium / high` (numeric 1–5 optional).  

- **Guardrails Enum Extended**  
  More nuanced handling: `allow / caution / soft_refuse / refuse`.  

- **Telemetry Expanded**  
  Supports `trace_id`, `parent_span`, `latency_ms`, `feedback_score`.  

- **Domain Packs with Tags**  
  Domain packs (e.g., `design_doc`, `policy_review`) now support **tags** for categorization and filtering.  

---

## How to Use

1. At the start of your chat, note that the LLM should follow GCL rules.  
2. Prefix your request with a symbol or mode.  

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
├─ GCL-core.yaml              # Core declaration
├─ GCL-extensions.yaml        # Extension declaration
├─ GCL-safety-extension.yaml  # Safety/guardrail declaration
├─ examples/                  # Domain examples
│  ├─ tech/
│  ├─ research/
│  ├─ workplace/
│  ├─ learning/
│  └─ policy/
└─ docs/                      # Guides & manual (planned)

---

## Roadmap

- **v1.0 (current)**  
  Core declaration (`gcl-core.yaml`), base symbols (!, ++, >), extended guardrails, telemetry, tone, and domain packs.

- **v1.1 (planned for Q4 2025)**  
  More examples per domain, minimal /docs usage guide. 

- **v1.2 (planned for 2026 H1)**  
  Extended option modes (:tutor, :creative, :story), advanced multi-domain patterns.

- **v2.0 (future)**  
  Full manual, best practices, and open community contributions.

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
