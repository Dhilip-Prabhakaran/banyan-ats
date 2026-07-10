# Process Flows — Banyan ATS

> **Status: TEMPLATE — as-is worked as an example; to-be to be drafted by Dhilip.**
> Guidance blockquotes are retained for learning; delete them as sections firm up.
>
> **The idea:** draw hiring as a sequence of steps TWICE — once as it happens today
> (*as-is*, the problem) and once as it happens with Banyan (*to-be*, the solution).
> The DIFFERENCE between the two maps is the product's value. Diagrams are written in
> Mermaid (text that GitHub renders into a picture) so they live in the repo and diff
> like code.

---

## Notation legend

> The shared visual vocabulary. In Mermaid:

- `([ text ])` → **rounded box** = a start or end point
- `[ text ]` → **rectangle** = an action / step
- `{ text }` → **diamond** = a decision (branches labelled `-->|Yes|`)
- `-->` → **arrow** = flow direction
- `subgraph` → a **swimlane** grouping the steps owned by one actor

> `flowchart TD` = top-down layout; `flowchart LR` = left-to-right. Use TD for long
> flows (scrolls vertically), LR for short ones.

---

## Part A — As-is: hiring today, WITHOUT Banyan  *(worked example — study the syntax)*

> This is the problem from `01-problem-statement.md`, drawn. Notice how the diagram
> makes the pain visible: scattered entry points, a manual compile step, stages that
> get skipped, and verification happening AFTER the offer.

```mermaid
flowchart TD
    A1([Vacancy arises]) --> A2[Dept head tells HR verbally / on chat]
    A2 --> A3[HR posts job on portals, WhatsApp, email]

    A3 --> B1([Candidate applies])
    B1 --> B2{Where does it land?}
    B2 -->|Email| C1[Sits in an inbox]
    B2 -->|WhatsApp| C2[Sits in a chat]
    B2 -->|Walk-in| C3[Paper form on a desk]

    C1 --> D1[HR manually compiles a list in Excel]
    C2 --> D1
    C3 --> D1

    D1 --> E1{Time pressure?}
    E1 -->|Yes - common| F1[Screening skipped or rushed]
    E1 -->|No| F2[Résumé screened]
    F1 --> G1
    F2 --> G1

    G1[Interview scheduled around panel availability] --> G2{Panel free today?}
    G2 -->|No| G3[Candidate waits / comes another day]
    G2 -->|Yes| H1[All rounds crammed into one day]
    G3 --> H1

    H1 --> I1{Selected?}
    I1 -->|No| I2([Rejected - often no reply])
    I1 -->|Yes| J1[Verbal offer, same day]

    J1 --> K1[Certificate verification with university]
    K1 --> K2{Comes back clean?}
    K2 -->|Unpredictable delay| K3([Hire confirmed... eventually])
    K2 -->|Problem found| K4([Offer unwound - after the fact])
```

> **Read the pain in the picture:** three entry points that never meet until a manual
> Excel step (D1); a decision (E1) whose common branch SKIPS screening; verification
> (K1) happening *after* the offer, so problems surface too late. Every one of these
> is something the to-be flow should fix.

---

## Part B — To-be: hiring WITH Banyan  *(your turn to design)*

> Now draw the improved flow. Don't just "add software" to the old steps — rethink
> them. Prompts drawn from your personas and problem statement:
>
> - Where does Arthi's work now happen (configuring the job + pipeline UP FRONT)?
> - Do the three entry points still exist, or does one application link replace them?
> - Where does screening sit now so it can't be skipped?
> - Where does verification move to, so problems surface BEFORE the offer?
> - What does the candidate (Cathy) see instead of silence?
>
> A scaffold to get you started — replace the placeholders and extend it. Keep the
> `mermaid` fence so it renders.

```mermaid
flowchart TD
    T1([Vacancy arises]) --> T2[Admin creates job + configures pipeline stages & scoring]
    T2 --> T3[Job posted with one application link]

    T3 --> T4([Candidate applies via link])
    T4 --> T5[Application lands directly in the job's pipeline]

    %% --- your design continues here ---
    T5 --> T6[Assigned to a recruiter]
    T6 --> T7{ ... your next step ... }
    %% Think: screening as a stage, moving across the kanban board,
    %% scoring at each stage, where verification happens, what the candidate sees.
```

> Build out T6 onward. Aim to show: the pipeline stages as steps, scoring at stages,
> verification positioned BEFORE the offer, and the candidate kept informed. It's fine
> to be rough — we'll refine in review.

---

## Part C — What changed (the delta = the value)

> Fill LAST, after both diagrams exist. One line per meaningful improvement, each
> tracing to a step that changed between as-is and to-be. This section turns two
> pictures into an argument.

- **Scattered entry points → one pipeline:** *...*
- **Manual Excel compile → automatic intake:** *...*
- **Skippable screening → a stage that can't be bypassed:** *...*
- **Verification after offer → verification before offer:** *...*
- **Candidate silence → candidate visibility:** *...*
- *(add any others your to-be flow reveals)*
