# GCL: Guided Conversation Language for LLM Work  
*A lightweight notation for guiding your interactions with Large Language Models (LLMs)*

`gcl-core.yaml` | License: CC-BY-4.0

---

## What is GCL?

GCL is a simple way to tell an LLM what kind of response you want without writing long instructions.  
Instead of typing *“give me a very short, three-line bulleted summary of…”*, I wanted a faster way to get consistent results.

The core of GCL uses three symbols:

```
!   → Fast Draft (3-line summary or concise bullets)
++  → Deep Analysis (Why×5, reasoning, risks, evidence)
>   → Exec Brief (1-page briefing note for decision-making)
```

This keeps conversations with LLMs short, consistent, and repeatable.  
On top of that, optional modes like `:tutor`, `:creative`, or `:story` can extend usage across domains such as **Tech, Research, Workplace, Learning, Policy**.

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
├─ gcl-core.yaml      # The core declaration of GCL
├─ examples/          # Practical examples for each domain
│  ├─ tech/
│  ├─ research/
│  ├─ workspace/
│  ├─ learning/
│  └─ policy/
└─ docs/              # Detailed guides and documentation (planned)
```

---

## Roadmap

- [x] Core declaration (v1.0)  
- [ ] Add more domain examples  
- [ ] Write detailed documentation and guides  
- [ ] Open to community issues and PRs  

---

## License

This project is licensed under the **Creative Commons Attribution 4.0 International License (CC-BY-4.0)**.  

You are free to use, modify, and share it, as long as you give proper attribution.  
For the full text, see the [LICENSE](./LICENSE) file.
