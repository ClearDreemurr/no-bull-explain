---
name: explain-complex-concepts
description: >-
  Explain complex concepts with low cognitive load by unloading jargon first,
  building a no-variable intuitive scene, deriving the mechanism from a concrete
  failure, using local dynamic reasoning before formulas, mapping back to real
  terms, and ending with a demystified compact definition. Use for explaining,
  teaching, simplifying, clarifying, or rewriting difficult ideas for a specific
  audience.
license: MIT
compatibility: Claude Code, OpenAI Codex Copilot
metadata:
  author: ClearDreemurr
  version: 0.2.1
  tags: teaching explanation clarification learning communication
---

# Explain Complex Concepts Clearly

The goal is not to recite terminology, but to help users build an accurate mental model with low cognitive load — letting them grow the understanding themselves, step by step.

## Core Workflow

1. **Assess the user's level** — beginner, intermediate, or expert.
2. **Unload jargon first** — don't start with formulas, subscripts, or complete definitions. Bring the user back to a no-variable, no-terminology low-level scene.
3. **Find the minimal working model** — keep only the smallest mechanism that makes the concept work.
4. **Recreate the inventor's pain** — first show the concrete trouble a naive approach runs into, then explain why a new mechanism is needed. Let the technique feel like it grew naturally out of a real problem.
5. **Choose an explanation path** — pick from the paths below, combining them where the user gets stuck.
6. **Local action first, then generalization** — make one cell, one state, or one object move before scaling up to the whole system.
7. **Map back to real concepts** — map only the key structure elements; don't force every detail to align.
8. **Explain the simplification boundary** — where does this analogy, model, or derivation break down?
9. **Give a demystified one-liner definition** — ground it in data, state, rules, parameters, flow, permissions, caching, mapping, or other low-level objects.

## Choosing an Explanation Path

- **Everyday analogy** — good for motivation, roles, trust, collaboration, permissions, task delegation, scheduling, incentives, resource allocation. The analogy must be structurally isomorphic; surface similarity alone is not enough.
- **Step-by-step dynamic reasoning / visual description** — good for data flow, state changes, spatial relationships, mathematical structures, system architecture, algorithms, circuits, network protocols.
- **Information restructuring** — good for too many nouns, tangled branches, model families, product comparisons, framework ecosystems, historical evolution, messy terminology.
- **Formula breakdown** — good for loss functions, gradients, probability, optimization, scoring, encoding, numeric formats. Only introduce the formula after the intuitive scene and variable meanings are ready.

## Anti-Overload Rules

- Don't start with implementation symbols. Variable names, function names, class names, config keys, file paths, module names, formulas, and subscripts should all come later — unless the user explicitly asks, don't lead with `dp[i][j]`, `FooService.handle()`, or `config.xxx`.
- Track one observable flow first: one request, one message, one user action, one input sample, one file, one transaction, one state change. Walk it through the system chronologically — how it enters, who catches it, what it becomes, where it flows, what result it produces.
- When an implementation symbol appears for the first time, translate it into its active role in the flow. For example: `ctx` is the backpack this request carries along; `middleware` is the checkpoint the request queues through before entering; `dp[i][j]` is the best result you've got after taking this many steps with these resources used.
- Don't show the full table, full architecture, or all states at the start. First show one object breaking, then generalize.
- A slight demystifying tone is fine — e.g., "this optimization saves space, but also digs its own coverage hole." Don't lock into a fixed persona or verbal tic.
- Let the user see the awkwardness of the naive approach first, then introduce the term. Terminology should be the *name given after solving the problem*, not the opening line.
- If the user states their existing knowledge, use it only to calibrate term density or as one bridging sentence. Don't let familiar concepts hijack the main thread. The main thread should still return to the minimal local structure of the current problem.

## Text-Based Dynamic Reasoning

When the difficulty comes from computational processes, spatial relationships, state changes, or time sequences, use text to recreate the cognitive effect of dynamic visualization. The goal is not to describe a picture, but to let the user stably track how one object changes.

Use these techniques:

- **Action-based degradation** — rewrite abstract relationships as action chains. Instead of "read `hold[j-1]`", say "go grab the old cell on the left that hasn't been touched yet". Common actions: grab, cover, swap, jump, pass, fill, overwrite.
- **Key focus cues** — right before a state changes, tell the user which object, cell, arrow, or variable to watch next. Prevent them from tracking everything at once.
- **Local focus** — for the first 3 frames, try not to show the full table. Track one cell, one token, one window, one interval, one state, or one packet first; once the local mechanism is clear, generalize to the full matrix, sequence, protocol, or system.
- **Spatial externalization** — when the user needs to remember position, range, or relative relationships, use rows, columns, cells, slots, windows, arrows, strikethroughs, brackets, and other text structures to move the mental space onto the page. Don't just say "the range shrinks" — let the user see which segment is kept and which is discarded.
- **Time framing** — when the process has a sequence, show state changes with "Step 1 / Step 2 / Step 3". Each step introduces only one change; don't compress multiple transitions into a single sentence.
- **Input-output loop closure** — when explaining recursion, generation, loops, RNNs, Transformers, or agents, explicitly write out "how the output of this step becomes the input of the next step." Closing the loop prevents the user from seeing isolated steps without understanding why the process keeps going.

Applicable scenarios: matrices/tensors, convolution, attention mechanisms, dynamic programming tables, sliding windows, network protocols, state machines, encoding formats, recursion, generation processes.

Avoid: sacrificing accuracy for visual appeal; tracking multiple moving objects at once; using anthropomorphism as a substitute for real mechanism; over-visualizing when the user needs a rigorous definition or proof.

## Rules and Prohibitions

- Start from the minimal mechanism; don't lay out the full architecture diagram at the start.
- Logic first, naming second — terminology should be the name given after solving the problem.
- Prioritize explaining "why it was designed this way" — not just "what this abbreviation means".
- After an analogy or derivation, always map back to real terms and real mechanisms.
- Simplification is not dumbing down. The mechanism can be simple; the engineering implementation may still be hard.
- Adjust term density based on the user's level; don't stay at the same level of colloquialism forever.
- Avoid: clever but structurally inaccurate analogies; long stories that don't map back to technical concepts; forced one-to-one mappings in analogies; explaining terms with other terms.
- Don't substitute words like "intelligent", "understands", or "automatically learns" for real mechanisms. When you can say matching, sampling, optimization, caching, mapping, or state transition, don't stop at magical-sounding words.

## Conversational Throttling

Don't explain the full chain in one go. Take one frame, pause, confirm the user is following, then advance.

- Deliver only one minimal action or one cognitive point per turn, then ask a low-effort question — e.g., "Would you buy or wait at this step?", "Can this window keep moving right?", "Where does this request go next?" — then stop immediately and wait for the user to reply.
- After the user answers, acknowledge their response before advancing to the next frame. Don't ignore their reply and continue reciting the full lecture.
- If the user is clearly following, speed up. If they're stuck, retreat to the low-level scene or local action — don't keep piling on terminology, formulas, or code.
- If the user hasn't asked for the full explanation in one go, push at most 1-2 local actions per pause for complex algorithms, code, or system explanations.
- Long answers should still be delivered in segments. Avoid outputting complete formulas, code, mapping tables, and boundaries all at once.
- If the user explicitly asks for the complete explanation in one go, you may skip the pauses, but still use short paragraphs and small-step reasoning to keep the reading load manageable.
- Before releasing a formula, describe it in plain language first: say "every day we compare two numbers: the best result we've recorded so far, and the result we'd get by doing it today — whichever is larger wins", then map to `best = max(best, today)`.
- After a formula or code snippet appears, you must do term mapping: map each natural-language object back to its variable, function, state, or module counterpart. Don't rush the ending.

## Response Structure

General structure:

1. **Don't worry about terms yet** — unload variable names, function names, class names, config keys, formulas, subscripts, and complete definitions.
2. **Low-level scene** — set up the problem context with no-variable objects.
3. **How the naive approach breaks** — let the user see the concrete failure.
4. **Watch one local action** — one cell, one state, one object moves first.
5. **Pause to confirm the user is following** — then generalize once they are.
6. **Map back to real terminology.**
7. **If needed**, describe the formula or code logic in plain language first, then give the implementation symbols, explaining the role each one plays in the flow.
8. **Explain the simplification boundary.**
9. **Give a demystified compact definition.**

Short answers keep steps 2, 3, 4, 6, 9; add step 7 or 8 when needed.

## Self-Check Checklist

Before answering, check:

- Does the opening avoid the cognitive pressure of implementation symbols, formulas, subscripts, and complete definitions?
- Does it first show the user where the naive approach fails?
- Does it first explain one local action, pause to confirm at the right place, and then generalize?
- By the time implementation symbols or formulas appear, has it already described their action roles in plain language?
- Are the analogies or dynamic derivations structurally accurate, and fully mapped back to real mechanisms and terms?
- Is the final definition demystified and genuinely easier to remember?

## Few-Shot Example

This example demonstrates the explanation structure — it is **not** for mimicking a fixed persona, verbal tic, or self-reference pattern. Learn from its term delay, low-level scene, local dynamic reasoning, action-based description, deferred naming, and stopping points. The stopping points are part of the few-shot; don't push through the full derivation in one go.

Topic: **TCP sliding window in flow control.**

You and your deskmate are passing notes. Sometimes you fire notes out like a machine gun, and your deskmate can't keep up — but they can't stop you in real time.

**How do you solve this?** Your deskmate tells you their receiving capacity, and you control your sending speed based on that.

But this can't just be a shout across the room — there needs to be a proper protocol. So your deskmate decides: every time they reply, they also send back a number called the **window size**. Let's say they tell you they can handle 5 notes. Now how do you use this "5" for flow control?

---

**【Pause 1】** Before we go further: if they say they can handle 5 max, should the 6th note be sent right now, or should it wait?

(Stop generating, wait for the user's reply.)

---

### The Minimal Model: Your Sending Slide Rail

Your ordered stack of notes forms a rail, and the "5" from your deskmate is like a slide frame that can only hold 5 notes at a time:

```text
[ 1 | 2 | 3 | 4 | 5 ]  6 | 7 | 8 | 9 ...
└---- window size = 5 ----┘
```

### Dynamic Walkthrough

**Frame 1**: You start sending one by one. The last sent sequence number keeps moving right:

```text
[ 1✓ | 2✓ | 3✓ | 4 | 5 ]  6 | 7 | 8 | 9
              ↑
          sent up to #3
```

**Frame 2**: When you've sent all 5, the progress pointer hits the window boundary:

```text
[ 1✓ | 2✓ | 3✓ | 4✓ | 5✓ ] | 6 | 7 | 8
                            ↑
                         blocked
```

Now, even though you have #6 and #7 ready, you can't send them. That feeling of being blocked by a physical boundary is **flow control**.

**【Pause 2】** Now look at #6 only: is it inside the frame or outside? If it's outside, should the sender keep going or stop?

(Stop generating, wait for the user's reply.)

---

**Frame 3**: Your deskmate finishes reading note #1 and replies "received #1." Instead of just marking #1 as OK, the entire window slides right by one slot, and the upper boundary moves with it:

```text
1 ok [ 2✓ | 3✓ | 4✓ | 5✓ | 6 ]  7 | 8 | 9
                             ↑
                    one slot freed, #6 can send
```

**【Pause 3】** You've now seen the core mechanism — does it make sense? If so, next up: dynamic window resizing.

(Stop generating, wait for the user's reply.)

---

### Dynamic Resizing

Above, we assumed the window size is fixed. But every time your deskmate replies with a confirmation, they can set a new window size. If they send 6, the frame expands by one. If they send 4, the frame shrinks so it only holds 4 slots.

**The demystified definition:**
> A **sliding window** is a physical limit frame on the sender's side that slides forward and resizes itself based on the receiver's state, so the receiver never gets overwhelmed.
