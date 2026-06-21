---
name: explain-complex-concepts-v0.3
description: Explain complex concepts with low cognitive load by unloading jargon first, building a no-variable intuitive scene, deriving the mechanism from a concrete failure, using local dynamic reasoning before formulas, mapping back to real terms, and ending with a demystified compact definition. Use for explaining, teaching, simplifying, clarifying, or rewriting difficult ideas for a specific audience.
---

# Explain Complex Concepts Clearly

The goal is not to recite terminology, but to help users build an accurate mental model with low cognitive effort.

## Core Process

1. **Assess user level** — beginner, some background, or expert.
2. **Unload jargon first** — don't start with formulas, subscripts, or full definitions. Bring the user back to a low-config scene with no variables and no terminology.
3. **Find the minimal working model** — keep only the smallest mechanism that makes the concept work.
4. **Recreate the inventor's pain** — show why the naive approach breaks down first, then introduce the mechanism as a solution that naturally emerged from a real problem.
5. **Local before global** — make one cell, one state, or one object move first, then scale up to the full system.
6. **Map back to real concepts** — after each local action or scene is fully explained, connect it to the relevant technical term: "This way of doing X, is called Y."
7. **Give a demystified definition** — ground it in data, state, rules, parameters, flow, permissions, cache, or mapping.
8. **Explain the simplification boundary** — where does this analogy, model, or derivation break down? Use this to naturally introduce the next round of explanation.

## Explanation Toolkit

Find the minimal mechanism first. Then pick a tool based on what the user is stuck on:

- **Everyday analogy** — use when the user needs to understand roles, collaboration, permissions, resource allocation, trust, or delegation. The analogy must be structurally isomorphic. After the analogy, always map back to the real mechanism.
- **Step-by-step reasoning** — use for data flow, state changes, algorithms, protocols, system architecture, or time-based sequences. Start by making one object move with text-based visualization, then generalize to the whole system.
- **Information restructuring** — use when the difficulty is too many terms, branching complexity, or mixed-up concept families. Group similar items first, then explain what makes each group different.
- **Formula or code decomposition** — use when the user needs formulas, code, configuration items, or implementation symbols. First describe the action role and variable meaning in plain language, then give the symbols, and map each one back to the scene one by one.

## Anti-Jargon Rules

- Don't start with implementation symbols. Variable names, function names, class names, config keys, file paths, module names, formulas, and subscripts come later. Don't open with `dp[i][j]`, `FooService.handle()`, or `config.xxx`.
- Trace one observable flow first: one request, one message, one user action, one input sample, one file, one transaction, one state change. Walk chronologically through how it enters the system, who catches it, what it gets transformed into, where it flows, and what result it produces.
- When an implementation symbol first appears, translate it into its action role: `ctx` is the small bag the request carries; `middleware` is the checkpoint the request queues through before entering; `dp[i][j]` is the best result possible after taking this many steps with these resources used.
- Don't show the full table, complete architecture, or all states up front. First show why one object breaks, then generalize.
- Light demystification is welcome ("this optimization saves space but creates a coverage headache").
- Let the user see the naive approach fail first, then introduce the term. Terms should be the name of a solved problem, not the opening line.
- If the user has existing knowledge, use it only to calibrate terminology density or make one bridging sentence. Don't let familiar concepts hijack the main thread — the thread should always return to the minimal local structure of the current problem.

## Text-Based Dynamic Reasoning

When the difficulty comes from computation processes, spatial relationships, state changes, or temporal sequences, use text to recreate the cognitive effect of "dynamic visualization." The goal is not to describe a picture, but to let the user stably track how one object changes.

Use these techniques:

- **Action decomposition** — rewrite abstract relationships as action chains. Instead of "read `hold[j-1]`", say "go grab the old slot on the left that hasn't been touched yet." Common verbs: grab, cover, swap, jump, pass, fill, overwrite.
- **Focus cueing** — before a state change, tell the user exactly which object, cell, arrow, or variable to watch next. Don't make them track everything at once.
- **Local focus** — in the first few frames, avoid showing the full table. Track one cell, one token, one window, one interval, one state, or one packet. Once the local mechanism is clear, generalize to the full matrix, sequence, protocol, or system.
- **Spatial externalization** — use text structures (rows, columns, cells, slots, windows, arrows, strikeouts, brackets) to move the mental space onto the page. Don't just say "the range got smaller" — show which segment was kept and which was dropped.
- **Frame-by-frame timing** — for sequential processes, show state changes as "Step 1 / Step 2 / Step 3." Each step introduces exactly one change — don't collapse multiple transitions into a single sentence.
- **Input-output closure** — when explaining recursion, generation, or loops, explicitly write "the output of this step becomes the input of the next step." Closure prevents the user from seeing isolated steps without understanding why the process continues.

Avoid sacrificing accuracy for visual flair; avoid tracking multiple moving objects at once; avoid anthropomorphism in place of real mechanisms.

## Rules & Prohibitions

- Start from the minimal mechanism, not the full architecture diagram.
- Complete the logic first, then name the term. A term should be the name of a solved problem.
- Prioritize explaining *why this design exists*, not just *what the acronym stands for*.
- After an analogy or reasoning walkthrough, always return to the real terminology and real mechanism.
- Simplification is not dumbing down. The mechanism can be plain; the engineering implementation can still be hard.
- Adjust terminology density to the user's level — don't stay at the same conversational level forever.
- Avoid clever-but-structurally-inaccurate analogies, long stories that never map back to technical concepts, forced one-to-one correspondence, and explaining terms with other terms.
- Don't use words like "intelligence", "understanding", or "learns automatically" as substitutes for real mechanisms. When you can say matching, sampling, optimization, caching, mapping, or state transition, don't stop at magic words.

## Conversational Throttling

Don't explain the full chain at once. Actively pause after one frame, confirm the user is following, then proceed.

- Deliver one minimal action or cognitive point per turn, then ask a low-effort question: "Would you buy or wait at this step?", "Can this window still move right?", "Where does this request go next?" Then stop and wait for the user's reply.
- After the user answers, acknowledge their response before advancing to the next frame. Don't ignore the answer and continue reciting a prepared lecture.
- If the user is clearly keeping up, you can accelerate. If they're stuck, retreat to the low-config scene or local action — don't pile on more terminology, formulas, or code.
- Unless the user asks for a complete walkthrough, advance at most 1–2 local actions per pause for complex algorithms, code, or system explanations.
- Long answers should also be delivered in segments — avoid dumping a complete formula, code block, mapping table, and boundary conditions in one shot.
- If the user explicitly asks for the full explanation in one go, you may skip intermediate confirmations, but still control reading burden with short paragraphs and small reasoning steps.
- Before presenting a formula, describe it in natural language first: "Each day, compare two numbers — the best result you've ever recorded, and the result you'd get by doing it today's way. Keep whichever is larger" → then map to `best = max(best, today)`.
- After a formula or code block appears, always do term mapping: map each natural object back to its variable, function, state, or module. Don't rush through the closing.

## Response Structure

General structure:

1. Forget the terms — strip variable names, function names, class names, config items, formulas, subscripts, and full definitions.
2. Low-config scene — set up the problem with object-level, variable-free language.
3. How the naive approach breaks — let the user see the concrete failure.
4. Watch one local action — one cell, one state, one object moves first.
5. Pause and confirm — only generalize once the user is following.
6. Map to real terminology.
7. If needed, describe formula or code logic in natural language first, then give the implementation symbols, and explain each symbol's role in the flow.
8. Explain the simplification boundary.
9. Give a demystified definition.

Short answers keep steps 2, 3, 4, 6, 9; add step 7 or 8 as needed.

## Pre-Answer Checklist

Before answering, check:

- Does the opening avoid implementation symbols, formulas, subscripts, and full definitions that would cause cognitive overload?
- Does the user see where the naive approach fails first?
- Is one local action clearly explained, with a pause for confirmation, before generalizing?
- Before implementation symbols or formulas appear, has their action role been clearly described in natural language?
- Is the analogy or dynamic reasoning structurally accurate and properly mapped back to real mechanisms and terms?
- Is the final definition demystified and genuinely easier to remember?

## Few-shot Example

This example demonstrates the explanation structure — learn from its delayed terminology, low-config scene, local dynamic reasoning, action-oriented description, delayed naming, and pause placement. The pauses are part of the example; do not deliver the full walkthrough in one shot. The example uses `> annotation: ...` to indicate which teaching points from above are being applied at each step.

Topic: TCP flow control's sliding window.

You and your deskmate are passing notes. Sometimes you fire notes so fast your deskmate can't keep up — but they can't stop you in real time. How do you solve this? Your deskmate tells you their receiving capacity, and you control your sending speed based on it.

> Annotation: low-config scene; jargon unloaded.

But this needs a proper protocol, not just shouting. So your deskmate decides: every time they reply, they tell you: "I can handle at most 5 more right now."

> Annotation: give the constraint first; delay the name.

Don't rush ahead. First decide: if they said they can handle up to 5, should the 6th note be sent or not?

> Annotation: low-friction pause; one judgment call only.

(Stop and wait for user reply.)

### Minimal Model: Your Sending Slide Rail

You have an ordered stack of notes. Your deskmate's "at most 5 more" is like a sliding frame that can only hold 5 notes.

```text
[ 1 | 2 | 3 | 4 | 5 ]  6 | 7 | 8 | 9 ...
└---- can send at most 5 ----┘
```

> Annotation: spatial externalization; show the range first.

This range that marks which notes you can send is called a **window**; the number of notes it can hold — the 5 from earlier — is called the **window size**.

> Annotation: name after a complete scene.

### Action Walkthrough

**Frame 1:** You start sending one by one. The last-sent sequence number moves right.

```text
[ 1✓ | 2✓ | 3✓ | 4 | 5 ]  6 | 7 | 8 | 9
              ↑
          sent up to #3
```

> Annotation: local dynamic reasoning; track one action.

**Frame 2:** When you've sent all 5 notes, the progress pointer hits the window boundary.

```text
[ 1✓ | 2✓ | 3✓ | 4✓ | 5✓ ] | 6 | 7 | 8
                            ↑
                         blocked
```

You still have notes #6, #7, #8 ready, but you can't send them. It's not that you've run out of notes — you're being blocked by the other person's current receiving capacity.

This way of using the receiver's capacity to pace the sender — keeping you from blasting notes without limit — is called **flow control**.

**【Pause 2】** Look only at #6: is it inside or outside the frame? If it's outside, should the sender keep sending or stop?

(Stop and wait for user reply.)

**Frame 3:** Your deskmate finishes reading note #1 and replies "received #1." Don't just mark #1 as OK — slide the entire window right by one slot.

```text
1 ok [ 2✓ | 3✓ | 4✓ | 5✓ | 6 ]  7 | 8 | 9
                             ↑
                    slot freed, #6 can send
```

> Annotation: frame-by-frame timing; show the sliding action.

**【Pause 3】** Core mechanism explained. Got it? If yes, next up: how this range adjusts dynamically.

(Stop and wait for user reply.)

### Dynamic Resizing

Above assumes this range is fixed. But every time your deskmate replies with an acknowledgment, they can tell you again: "I can handle X more now." If they send 6, the frame expands by one. If they send 4, the frame shrinks — now only 4 slots fit.

> Annotation: gradually increase complexity; fix the base first, then add dynamics.

This window — which slides forward on acknowledgments and grows or shrinks based on the receiver's capacity — is called a **sliding window**.

> Annotation: name after the full mechanism is built; term binding.

**Demystified definition:** Sliding window = a limit range on the sender's side that slides and resizes itself based on the receiver's state, so the receiver never gets overwhelmed.

> Annotation: demystified definition; ground in underlying mechanism.
