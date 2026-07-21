# 11 — Interview Questions Bank

## Introduction

This chapter is a **timed drill book**. Answer out loud. Aim for structure: definition → internals → trade-offs → production example → pitfalls. For lead roles, add people/process impact.

## Definition

An **interview question bank** for Senior Java / Tech Lead loops spanning core language, concurrency, JVM, Spring, and design judgment — with model answer outlines (not scripts to memorize).

## Internal Working

How to use this file:

```mermaid
flowchart LR
  Q[Pick question] --> T[Timer 3–5 min]
  T --> A[Answer aloud]
  A --> C[Compare to model]
  C --> N[Note gaps]
  N --> R[Restudy chapter]
```

## Why it exists

Interviews reward **retrieval under pressure**. Studying chapters builds knowledge; drills build delivery.

## Advantages

- Covers breadth + depth signals
- Model answers encode senior structure
- Separates IC vs lead framing

## Disadvantages

- Memorization without understanding fails follow-ups
- Real interviews adapt — don’t recite

## Time Complexity

N/A as algorithms — but practice **time-boxing**:

| Round type | Target answer length |
|------------|----------------------|
| Warm-up | 60–90s |
| Core technical | 3–5 min |
| Deep dive follow-up | Until whiteboard done |
| Lead behavioral | STAR 2–3 min |

## Memory Considerations

N/A.

## Code Examples

Use snippets from chapters 01–10 when illustrating. Prefer short, compilable mental models over long code dumps on a whiteboard.

## Common Interview Questions

### Core Java

**Q1. Explain equals/hashCode contract with a production bug story.**  
**Model:** Contract rules → HashMap bucket → mutable key bug → immutability / records fix.

**Q2. How does HashMap work in Java 8+?**  
**Model:** hash, bins, treeify threshold, load factor, resize; compare ConcurrentHashMap.

**Q3. Checked vs unchecked exceptions — your team policy?**  
**Model:** Trade-offs; wrapping at boundaries; observability; try-with-resources.

**Q4. Generics erasure and PECS?**  
**Model:** Erasure why; `? extends`/`? super`; API example `copy`.

**Q5. How do records differ from Lombok @Value?**  
**Model:** Language-level; constraints; serialization; JPA caveats.

### Concurrency & JVM

**Q6. What does happens-before guarantee?**  
**Model:** JMM edges; volatile/sync; data race definition.

**Q7. Design a thread pool for a mixed workload.**  
**Model:** Separate CPU vs IO pools; queue bounds; rejection; metrics; VT on 21.

**Q8. Diagnose a production deadlock.**  
**Model:** jstack/JFR; lock order; fix; prevention standards.

**Q9. G1 vs ZGC — when?**  
**Model:** Pause goals, heap size, CPU overhead, measure.

**Q10. Virtual threads pinning — what/why/how detect?**  
**Model:** synchronized/native; JFR; ReentrantLock.

### Spring / Design / Lead

**Q11. Bean scopes and pitfalls of prototype in singleton?**  
**Model:** Injection timing; Provider/ObjectFactory; request scope proxies.

**Q12. How do you design idempotent payment APIs?**  
**Model:** Idempotency keys; dedupe store; exactly-once illusion; at-least-once + dedupe.

**Q13. Walk through a design review you led that changed direction.**  
**Model:** STAR; trade-offs; data; stakeholder alignment.

**Q14. How do you set SLOs for a new service?**  
**Model:** User journeys; latency/error; burn rates; capacity.

**Q15. Mentoring: engineer stuck on mid-level plateau — your plan?**  
**Model:** Goals; stretch tasks; feedback cadence; measurable outcomes.

### Rapid-fire (30–60s each)

1. `volatile` vs `AtomicInteger`  
2. `ArrayList` vs `LinkedList`  
3. `Comparable` vs `Comparator`  
4. `Callable` vs `Runnable`  
5. `Optional` misuse  
6. `String` immutability reasons  
7. Metaspace vs heap  
8. `synchronized` vs `ReentrantLock`  
9. `map` vs `flatMap`  
10. Sealed class purpose  

## Senior Engineer Notes

- Lead with **trade-offs**, end with **production judgment**.
- If stuck: state assumptions, propose how you’d verify with tools.
- Prefer diagrams for concurrency/JVM/system design.

## Technical Lead Perspective

Expect meta-questions:

- How do you review designs?  
- How do you handle incidents?  
- How do you say no to scope?  
- How do you raise the team’s engineering bar?  

Tie technical answers to **standards, mentoring, and risk**.

## Best Practices

1. Structure: Answer → Why → Example → Pitfall → Measure.  
2. Ask clarifying questions on design prompts.  
3. Quantify: QPS, p99, data size.  
4. Admit unknowns; describe validation plan.  
5. Keep code whiteboard-sized.

## Common Mistakes

| Mistake | Better |
|---------|--------|
| Reciting docs | Teaching with examples |
| Ignoring follow-ups | Check interviewer cues |
| Over-optimizing early | Correctness → measure → optimize |
| Blaming others in behavioral | Ownership + learning |
| Silent thinking too long | Narrate trade-offs |

## Summary

Drill until your answers are **structured, accurate, and production-anchored**. Use this bank weekly until delivery is automatic.

## Cheat Sheet — Answer Skeleton

```
1. One-sentence definition
2. Internals / mechanism
3. Pros / cons / alternatives
4. Real example
5. Pitfalls + how to verify
```

## Exercises with Answers

**E1.** Record yourself answering Q6 in 4 minutes. Compare to model.  
**A1.** Self-grade on hb edges, race definition, sync/volatile, one prod story.

**E2.** Whiteboard HashMap get/put.  
**A2.** Include treeify and resize; mention nulls.

**E3.** Explain VT to a mid-level engineer in 3 minutes.  
**A3.** Cheap threads, blocking OK, don’t pool, watch pinning, vs reactive.

**E4.** Lead question: prioritize reliability vs features for a quarter.  
**A4.** Risk framework: user impact, error budget, dependency criticality, sequencing.
