# The "Manager" Name Smell

## Why "Manager" Is a Red Flag

Names like `GizmoManager`, `ConnectionManager`, or `StateManager` sound convenient, but they rarely
communicate anything. Almost every class "manages" something: data, resources, state,
invariants, or behavior.

By that logic, even a `std::string` could be called a `StringManager` — and the
name would tell you nothing.

Because "managing" is so universal and so vague, Manager classes often grow into:

- mixed responsibility objects
- high-coupling hubs
- vague orchestration layers
- "god-lite" objects that sit ambiguously between domains

This doesn't automatically mean the design is wrong. It's simply a signal that
the abstraction may benefit from a more precise, meaningful name.

## What to Prefer

- **Descriptive Naming**: Choose a name that describes **the specific role or operation** the type
  owns: Examples:

  - `JobScheduler` instead of `JobManager`
  - `SessionRegistry` instead of `SessionManager`
  - `UploadCoordinator` instead of `UploadManager`
  - `WorkerPool` instead of `ThreadManager`
  - `RetryPolicy` instead of `RetryManager`

- **Utilize Design Patterns**: Consider if a specific design pattern (example, Builder, Strategy,
  Factory) can be applied to better structure the code and give the class a more meaningful name.

A precise name forces a precise responsibility.

## Why It Matters

- **Improves clarity:** Intent becomes obvious to reviewers and maintainers.
- **Strengthens cohesion:** Responsibilities stay centered around a single idea.
- **Reduces coupling:** Avoids one "authority hub" that everything depends on.
- **Reveals boundaries:** You can see which domain owns what.

When names sharpen, architecture sharpens.

## Quick Heuristic

> **If any class could plausibly be named "XyzManager" then "XyzManage" tells you nothing.**

When the name forces you to confront what the class *really* does, the design improves.

## Questions to Ask

- What exactly is this class responsible for?
- Can that responsibility be summarized with a more precise noun or verb?
- Would renaming it reveal unclear or mixed responsibilities?
- Is the class becoming a dumping ground because "Manager" doesn't constrain it?

If these questions feel hard to answer, it's usually a sign the abstraction needs sharpening.

## When "Manager" *Can* Be Appropriate

Sometimes "Manager" isn't a design crutch. If the term matches a real concept in the product or
system domain, it can be accurate.

In this case, "Manager" is part of the established terminology for the field. The name then
communicates a **clear, industry-recognized responsibility*.

Even then, it should have narrow, explicit responsibilities — not a catch-all mandate.

