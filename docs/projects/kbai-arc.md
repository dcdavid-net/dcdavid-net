# Project: ARC-AGI Solver

**Course:** Knowledge-Based AI (CS7637)

## **The Challenge**
The Abstraction and Reasoning Corpus (ARC-AGI) is a benchmark designed to measure Artificial General Intelligence. It consists of visual grid puzzles where an agent must infer a transformation rule from a few "training" examples and apply it to a "test" input. The challenge is that the rules are never explicitly stated; the agent must deduce concepts like "gravity," "color matching," or "object movement" purely from visual patterns.

## **The Approach**
I designed a **Production System** agent, prioritizing Procedural Knowledge over Episodic Memory.

1.  **Vectorized Operations**: To handle the computational load of analyzing grid pixels, I utilized **NumPy** for vectorized operations. This allowed for efficient shape recognition rather than slow iterative pixel comparisons.
2.  **Logic Chain (Production System)**: The agent utilized a flexible chain of `if-then` heuristics:
    * **Condition Check (`is_some_condition`)**: The agent inspects the input grid for specific patterns (e.g., "Is this a rectangle split?", "Is there a single non-black pixel?", "Is this a rotation?").
    * **Transformation Action (`do_some_operation`)**: If a condition is met, a corresponding transformation is triggered (e.g., "Split array," "Draw diagonal intersection," "Rotate 90 degrees").
3.  **Efficiency**: By relying on `O(C)` (linear time) operations for most transformations, the agent maintained an average runtime of under **70ms** per problem.

## **The Results**
The agent successfully solved **54 out of 96** problems in the final evaluation.

* **Strengths**: It excelled at problems requiring rigid geometric transformations (cropping, rotation, axis mirroring) and pattern completion.
* **Limitations**: Without a "learning" component (Episodic Memory), the agent struggled with novel problems that required generalizing rules it had not been explicitly programmed to recognize, such as complex object enclosure detection.