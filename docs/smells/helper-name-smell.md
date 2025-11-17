# The "Helper" Name Smell

## Why "Helper" Is a Red Flag

Names like `WidgetHelper`, `GizmoHelper`, or `SomethingHelper` often obscure the class' actual
purpose and can lead to several problems:

- **Lack of Clarity and Responsibility**: A "Helper" class doesn't clearly communicate what it does
  or what its responsibilities are. This makes it difficult for developers to understand
  its role in the system.
- **Violation of Single Responsibility Principle**: "Helper" classes often become *dumping groups*
  for unrelated methods, violating the SRP (Single Responsibility Principle). That leads to lower
  cohesion, harder reasoning, and difficulty seeing where the logic belongs.

## What to Prefer

- **Descriptive Naming**: Name the class based on its specific function or the domain concept it
  represents. For example, instead of `StringHelper`, consider `StringFormatter`, `StringValidator`,
  `TextProcessor` and so on.
- **Refactoring into Smaller, Focused Classes**: I a "Helper" class contains diverse
  functionalities (it often does), refactor it into multiple, smaller classes, each with a single,
  well-defined responsibility. If you can't find a better name than "Helper", that's usually a hint
  that the responsibilities of the class are rather fuzzy.
- **Utilize Design Patterns**: Consider if a specific design pattern (example, Builder, Strategy,
  Factory) can be applied to better structure the code and give the class a more meaningful name.
- **Module-Level Functions**: For genuine generic, stateless utility functions, consider placing them
  at the module level (in languages that support this) rather than within a class, or in a dedicated
  utility modules with clear, descriptive names.

## Why It Matters

- **Improves readability:** Clearer names reduce mental load during review and maintenance.
- **Encourages cohesion:** Responsibilities crystallize around a single purpose.
- **Reveals boundaries:** Makes it easier to see which layer or domain owns what.
- **Prevents hoarding:** Avoids the slow accumulation of unrelated functions in a catch-all bin.

## Quick Heuristic

> **If you can't name it precisely, the responsibilities might not be precise.**

Clear names lead to clear designs.


## When "Helper" *might* be acceptable

Very rarely, for:

- Small one-off *local* lambdas
- Extremely narrow-scope helpers inside a `.cpp` file, not exported from a module
- Generated code or boilerplate where naming is irrelevant

But for any exported type or shared abstraction, prefer descriptive, responsibility-centered names.
