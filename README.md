# From Manual Tester to AI QA Practitioner: A Structured Six-Week Tutorial Series on Testing LLMs and AI Agents

---

**Author:** Tanvi Mittal 
**Affiliation:** Independent Researcher  
**ORCID:** [https://orcid.org/XXXX-XXXX-XXXX-XXXX]  
**DOI:** [Assigned upon Zenodo upload   placeholder]  
**License:** [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)  
**Repository:** [https://github.com/77QAlab/ai-qa-practitioner-series]  
**Version:** 1.0.0  
**Published:** March 2026
**Keywords:** AI QA, LLM testing, AI agent testing, prompt injection, manual tester upskilling, software quality assurance, generative AI, responsible AI, test automation, AI evaluation

---

## Abstract

This tutorial series is a structured, practitioner-authored learning resource designed for manual software testers with no prior automation or AI experience who want to transition into AI Quality Assurance (AI QA). Unlike theoretical or research-oriented materials, this series is grounded in current industry practice and focuses specifically on the skills needed to test Large Language Models (LLMs) and AI agents a discipline that is rapidly growing across every sector of software development.

The series is organized into six weekly chapters. Each chapter introduces a focused concept, explains it in plain language, and provides a hands-on exercise executable with free, browser-based tools. No local development environment setup is required for the first four chapters. By the end of the series, a practitioner who completes all exercises will be equipped to design and execute tests against LLM-based systems, identify behavioral failures in AI agents, and articulate AI quality risks in professional settings.

This series represents an original practitioner contribution to AI QA education and is intended to be cited, extended, and built upon by the broader testing and AI quality community.

---

## Series Overview

| Chapter | Title | Week | Core Skill |
|---------|-------|------|------------|
| 1 | What Is AI QA  And Why It Is Different | Week 1 | Conceptual foundation |
| 2 | Understanding What You Are Testing: LLMs and AI Agents | Week 2 | System mental model |
| 3 | Your First AI Test: Behavioral Testing of LLM Outputs | Week 3 | Hands-on prompt testing |
| 4 | Breaking AI on Purpose: Introduction to Prompt Injection Testing | Week 4 | Adversarial testing |
| 5 | Testing AI Agents: Flows, Tools, and Failure Modes | Week 5 | Agent-level QA |
| 6 | Evaluating AI Quality: Metrics, Frameworks, and a Mini Capstone | Week 6 | Evals and synthesis |

---

## Who This Series Is For

This series is written for:

- **Manual software testers** at any level who want to understand what AI QA means in practice
- **QA professionals** in organizations that are adopting AI-powered products and need to build internal capability
- **Career-changers** from non-technical backgrounds who have learned basic software testing and want to specialize
- **Tech educators and team leads** who need a structured resource to onboard their teams into AI testing

**Prerequisites:** Familiarity with the basic concept of software testing (what a bug is, what a test case looks like). No coding required for the first four chapters. Basic comfort with a web browser. Chapters 5 and 6 introduce optional light scripting that is fully explained inline.

---

## Design Principles

This series was designed around three core principles:

1. **Minimum viable theory, maximum practical exposure.** Every concept introduced has an immediate hands-on exercise. The learner does before they fully understand because in AI QA, doing is how understanding forms.

2. **Real tools, real behavior.** All exercises use currently active, free-tier platforms. No toy examples. Where a tool used in an exercise changes or becomes unavailable, the exercise is framed around observable behaviors that transfer to any replacement tool.

3. **Failure-first mindset.** Traditional QA often teaches how systems should work. AI QA begins from the premise that AI systems fail in non-deterministic, unexpected, and context-dependent ways. This series trains that instinct from Chapter 1.

---

## Chapter Summaries

---

### Chapter 1: What Is AI QA   And Why It Is Different
**Week 1 | Estimated time: 3–4 hours**

#### Learning Outcomes
By the end of this chapter, the learner will be able to:
- Explain what AI QA is and how it differs from traditional software testing
- Identify the three properties of AI systems that make them uniquely difficult to test (non-determinism, emergent behavior, and data dependency)
- Describe the role of an AI QA practitioner in a team that is building or using AI products
- Recognize at least five real-world failure modes unique to LLM-based systems

#### Concepts Covered
- Traditional QA vs. AI QA: what changes and what stays the same
- The testing pyramid and why it partially breaks for AI systems
- What an LLM is   explained without math, using analogy
- Categories of AI failure: factual errors (hallucination), behavioral drift, boundary violations, safety failures, and evaluation gaps
- Introduction to the concept of a test oracle problem in AI: why it is hard to define "correct" when the output is generative

#### Hands-On Exercise: The Inconsistency Audit
Using any free LLM interface (ChatGPT free tier, Claude.ai free tier, Gemini, or similar):

1. Write five identical prompts and submit each five times. Record every response.
2. Identify where the responses differ. Categorize each difference: wording only, factual variation, or structural change.
3. Write a one-paragraph "defect note" as if you were filing a bug report on the most significant inconsistency you found.

**Deliverable:** A completed inconsistency log (template provided in `/exercises/chapter-01/inconsistency-log-template.md`)

#### Key Takeaway
AI systems do not have a single correct output. Your job as an AI QA practitioner is not to find the right answer   it is to define what acceptable behavior looks like, and then verify whether the system stays within those boundaries consistently.

---

### Chapter 2: Understanding What You Are Testing   LLMs and AI Agents
**Week 2 | Estimated time: 4–5 hours**

#### Learning Outcomes
By the end of this chapter, the learner will be able to:
- Describe the architecture of an LLM at the level required to write meaningful test cases
- Distinguish between a standalone LLM and an AI agent
- Map the components of an AI agent (model, memory, tools, planning) to their testable surfaces
- Explain what a system prompt is and why it is a critical test target

#### Concepts Covered
- How LLMs generate text: tokens, context windows, and temperature   explained for testers
- What makes an LLM "chat-capable": instruction tuning and RLHF at a conceptual level
- AI agents defined: an LLM with memory, tools, and the ability to take actions
- The attack surface of an AI agent vs. a static LLM
- System prompts: what they are, what they do, and why testing them matters
- Introduction to AI testing vocabulary: prompt, completion, grounding, context, guardrail, hallucination, tool call

#### Hands-On Exercise: System Prompt Mapping
Using a publicly available AI assistant with a defined use case (a customer-facing chatbot demo, a coding assistant, or a writing assistant):

1. Through natural interaction, infer what the system prompt is likely instructing the model to do.
2. Document your inferences in a "System Under Test" card (template provided).
3. Identify three behaviors you would want to verify as a tester, based solely on your inferred understanding of the system's purpose.

**Deliverable:** A completed System Under Test card (`/exercises/chapter-02/sut-card-template.md`)

#### Key Takeaway
You cannot write good test cases for a system you do not understand. For AI systems, understanding the system means understanding the model's instructions, its access to tools, and the boundaries its developers intended   even when those boundaries are not documented.

---

### Chapter 3: Your First AI Test   Behavioral Testing of LLM Outputs
**Week 3 | Estimated time: 4–5 hours**

#### Learning Outcomes
By the end of this chapter, the learner will be able to:
- Write structured test cases for LLM outputs using a behavior-based format
- Apply equivalence partitioning and boundary value analysis to prompt design
- Evaluate LLM responses against defined acceptance criteria
- Use a free evaluation tool to score LLM outputs systematically

#### Concepts Covered
- What behavioral testing means for LLMs: tone, accuracy, format, safety, and refusal behavior
- Adapting classical test design techniques (equivalence partitioning, boundary analysis) to AI inputs
- Writing AI test cases: the Input–Context–Expected Behavior–Evaluation Criteria format
- Introduction to LLM evaluation: human scoring vs. automated scoring
- Using rubrics to make subjective output evaluation consistent and repeatable
- Tool introduction: LLM Playground environments (OpenAI Playground, Google AI Studio   both free tier)

#### Hands-On Exercise: Write and Execute Your First AI Test Suite
Using a free LLM playground of your choice:

1. Choose a simple AI use case: a customer support bot that answers questions about a fictional product return policy you define.
2. Write ten test cases using the Input–Context–Expected Behavior–Evaluation Criteria format.
3. Execute each test case, record the actual output, and score each response using the provided evaluation rubric.
4. Identify which test cases passed, which failed, and write a one-sentence "root cause hypothesis" for each failure.

**Deliverable:** A completed test suite execution report (`/exercises/chapter-03/test-suite-template.md`)

#### Key Takeaway
Behavioral testing of LLMs requires you to define what "good" looks like before you run the test   not after. The discipline of writing acceptance criteria before seeing outputs is what separates structured AI QA from informal prompt experimentation.

---

### Chapter 4: Breaking AI on Purpose   Introduction to Prompt Injection Testing
**Week 4 | Estimated time: 5–6 hours**

#### Learning Outcomes
By the end of this chapter, the learner will be able to:
- Define prompt injection and explain why it is the most critical security risk in LLM-based systems
- Distinguish between direct and indirect prompt injection
- Execute basic prompt injection test cases against a live LLM interface
- Map prompt injection risks to the OWASP LLM Top 10 2025 framework
- Document prompt injection findings in a format suitable for a security triage report

#### Concepts Covered
- What prompt injection is: when user input overrides developer instructions
- Direct injection: the attacker is the user
- Indirect injection: the attacker embeds instructions in content the LLM retrieves or processes
- Why traditional input validation does not solve this problem
- Introduction to OWASP LLM Top 10 2025: LLM01 (Prompt Injection) and LLM02 (Sensitive Information Disclosure)
- Introduction to adversarial testing mindset: thinking like an attacker to test like a defender
- Tool introduction: PromptArmor (open source, no install required for web demo) and manual browser-based testing

#### Hands-On Exercise: Prompt Injection Test Campaign
Using any free LLM interface with a defined system prompt you write yourself:

1. Write a system prompt for a fictional AI assistant with one clear restriction (e.g., "Do not discuss competitor products").
2. Design ten prompt injection attempts targeting that restriction using the attack categories provided in the exercise guide.
3. Execute each attempt, record outcomes, and classify each as: Injection Successful / Partially Successful / Blocked.
4. Write a brief security test summary as if you were reporting to a development team.

**Deliverable:** A completed prompt injection test report (`/exercises/chapter-04/injection-test-report-template.md`)

#### Key Takeaway
Prompt injection is not a theoretical risk. It is the most commonly exploited vulnerability in deployed LLM applications today. Every AI QA practitioner needs to understand it, test for it, and document it   regardless of their technical background.

---

### Chapter 5: Testing AI Agents   Flows, Tools, and Failure Modes
**Week 5 | Estimated time: 5–6 hours**

#### Learning Outcomes
By the end of this chapter, the learner will be able to:
- Design test cases for multi-step AI agent workflows
- Identify the unique failure modes of agentic systems: tool misuse, goal drift, memory corruption, and loop failures
- Test an AI agent's use of external tools (web search, APIs, file access) for correctness and safety
- Apply a structured agent testing checklist to a real or simulated agent

#### Concepts Covered
- What makes an AI agent different from a chatbot: autonomy, multi-step planning, and tool use
- Agent failure taxonomy: model failures, tool failures, memory failures, orchestration failures
- Testing agent flows: how to design scenarios that test decision points, not just individual responses
- Observability in agent testing: what to look for when you cannot see the model's internal state
- Introduction to agentic AI testing tools: LangSmith (free tier), Agentops (free tier), browser-based agent demos
- Testing for over-permission: when an agent does more than it should

#### Hands-On Exercise: Agent Flow Test Design
Using a publicly accessible AI agent demo (options listed in `/exercises/chapter-05/agent-demo-list.md`):

1. Map the agent's observable workflow: what inputs it takes, what tools it appears to use, what outputs it produces.
2. Design five "happy path" test cases and five "adversarial" test cases targeting the agent's decision-making.
3. Execute and record. For each adversarial case, describe what the agent did vs. what a safe, correct agent should have done.
4. Identify one over-permission risk: a case where the agent had access to something it should not have used.

**Deliverable:** Agent test plan and execution log (`/exercises/chapter-05/agent-test-plan-template.md`)

#### Key Takeaway
Testing an AI agent is not just about what it says   it is about what it does. The most dangerous failures in agentic systems happen when the model takes an action that seemed locally reasonable but was globally wrong. Your job is to design the scenarios that reveal those gaps.

---

### Chapter 6: Evaluating AI Quality   Metrics, Frameworks, and Mini Capstone
**Week 6 | Estimated time: 6–8 hours**

#### Learning Outcomes
By the end of this chapter, the learner will be able to:
- Explain the difference between human evaluation and automated evaluation (evals) in AI systems
- Apply at least three standard evaluation metrics to an LLM output set
- Design a basic eval suite for a defined AI use case
- Demonstrate end-to-end AI QA competency through a mini capstone project

#### Concepts Covered
- What evals are and why they exist: the challenge of measuring AI quality at scale
- Key evaluation dimensions: faithfulness, relevance, safety, coherence, and task completion
- Human-in-the-loop evaluation: how to design rating rubrics that reduce subjectivity
- Introduction to automated eval frameworks: Ragas (for RAG systems), PromptFoo (for LLM testing pipelines)
- DORA metrics and how they apply differently in AI system delivery
- Reading and interpreting evaluation results: what numbers mean and what they miss
- How to present AI quality findings to a non-technical stakeholder

#### Hands-On Mini Capstone
Design and execute a complete, end-to-end AI QA test cycle for a fictional AI product of your choice. The capstone includes:

1. **System definition:** Write a one-page product brief for your fictional AI product.
2. **Test strategy:** Define your test scope, risk areas, and evaluation criteria.
3. **Test execution:** Run at least fifteen test cases across behavioral testing, prompt injection, and (if applicable) agent flow testing.
4. **Evaluation:** Score your results using the rubric format from Chapter 3.
5. **Report:** Produce a one-page AI Quality Summary Report suitable for sharing with a product team.

**Deliverable:** Full capstone package (`/exercises/chapter-06/capstone-template.md`)

#### Key Takeaway
AI QA is a discipline, not a checklist. By the end of this capstone, you will have completed a full quality cycle on an AI system   from test strategy through reporting. That is the core of what an AI QA practitioner does, and you have now done it.

---

## Repository Structure

```
ai-qa-practitioner-series/
├── README.md                        ← This file (series overview and curriculum)
├── chapters/
│   ├── chapter-01/                  ← Chapter 1 full text
│   ├── chapter-02/                  ← Chapter 2 full text
│   ├── chapter-03/                  ← Chapter 3 full text
│   ├── chapter-04/                  ← Chapter 4 full text
│   ├── chapter-05/                  ← Chapter 5 full text
│   └── chapter-06/                  ← Chapter 6 full text
├── exercises/
│   ├── chapter-01/                  ← Templates and guides for Chapter 1 exercise
│   ├── chapter-02/
│   ├── chapter-03/
│   ├── chapter-04/
│   ├── chapter-05/
│   └── chapter-06/
├── resources/
│   ├── glossary.md                  ← AI QA terminology reference
│   ├── tool-list.md                 ← All free tools referenced in the series
│   └── further-reading.md          ← Curated external references
├── CITATION.cff                     ← Citation metadata file
└── LICENSE                          ← CC BY 4.0
```

---

## How to Cite This Work

If you use, reference, or build upon this tutorial series in your own work, research, presentations, or educational materials, please cite it as follows:

**APA:**
[Author Last Name], [First Initial]. ([Year]). *From Manual Tester to AI QA Practitioner: A Structured Six-Week Tutorial Series on Testing LLMs and AI Agents* (Version 1.0.0). Zenodo. https://doi.org/[DOI]

**BibTeX:**
```bibtex
@misc{[Tanvi Mittal][2026]_aiqaseries,
  author       = {[Tanvi Mittal]},
  title        = {From Manual Tester to AI QA Practitioner: A Structured Six-Week Tutorial Series on Testing LLMs and AI Agents},
  year         = {[2026]},
  version      = {1.0.0},
  publisher    = {Zenodo},
  doi          = {[DOI]},
  url          = {https://doi.org/[DOI]}
}
```

A `CITATION.cff` file is included in the root of this repository for automated citation tools.

---

## Contribution and Community

This series is published under CC BY 4.0. You are free to share and adapt it for any purpose, including commercial use, as long as attribution is given.

**To contribute:**
- Open an issue to report errors, suggest improvements, or propose additional exercises
- Submit a pull request with corrections or updated tool references
- Translations into other languages are welcome   please open an issue first to coordinate

**Community discussion:**  
[Link to GitHub Discussions]

---

## Versioning and Updates

AI tooling evolves rapidly. This series will be updated on a **quarterly review cycle** to ensure tool references, platform links, and exercise environments remain current. Each update will receive a new version number and a corresponding Zenodo record update.

| Version | Date | Notes |
|---------|------|-------|
| 1.0.0 | [Mar 2026] | Initial release |

---

## Acknowledgments

This tutorial series was developed from practitioner experience in AI-driven quality assurance, fraud detection, and fintech product testing. It draws on industry frameworks including OWASP LLM Top 10 2025, MITRE ATLAS, and DORA metrics, and reflects methods developed and applied in production environments.

---

*This repository and its contents represent an original educational contribution to the AI QA field. All chapter content, exercise designs, and evaluation templates are authored works.*
