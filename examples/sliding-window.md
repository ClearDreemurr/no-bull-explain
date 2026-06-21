# TCP Sliding Window — Explained with This Skill

This is the few-shot example from the skill itself, extracted as a standalone walkthrough.

## The Setup

You and your deskmate are passing notes. Sometimes you fire notes so fast your deskmate can't keep up — but there's no way for them to stop you in real time.

**The problem:** How does the sender know when to slow down?

## The Solution

Your deskmate starts telling you their receiving capacity every time they reply. They send back a number: **window size**. Say they tell you they can handle 5 notes. Now what?

### The Sender's Slide Rail

Think of your ordered stack of notes as a rail that can only hold 5 at a time:

```
[ 1 | 2 | 3 | 4 | 5 ]  6 | 7 | 8 | 9 ...
└---- window size = 5 ----┘
```

### Frame 1: Sending

You start sending one by one. The last sent sequence number moves right:

```
[ 1✓ | 2✓ | 3✓ | 4 | 5 ]  6 | 7 | 8 | 9
              ↑
          sent up to #3
```

### Frame 2: Blocked

When you've sent all 5, the progress pointer hits the window boundary:

```
[ 1✓ | 2✓ | 3✓ | 4✓ | 5✓ ] | 6 | 7 | 8
                            ↑
                         blocked
```

Even though you have notes #6, #7, #8 ready, you can't send them. That physical boundary is **flow control**.

### Frame 3: Window Slides

Your deskmate finishes reading note #1 and replies "received #1". The entire window slides right by one slot:

```
1 ok [ 2✓ | 3✓ | 4✓ | 5✓ | 6 ]  7 | 8 | 9
                             ↑
                    slot freed, #6 can send
```

### Dynamic Resizing

The window size isn't fixed. Every time your deskmate replies, they can set a new size. If they send 6, the frame expands. If they send 4, it shrinks.

## The Demystified Definition

**Sliding window** = a physical limit frame on the sender's side that slides forward and resizes itself based on the receiver's state, so the receiver never gets overwhelmed.
