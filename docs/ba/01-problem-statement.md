# Problem Statement — Banyan ATS

> **Status: REVISED DRAFT v0.2** — first draft by Dhilip, revised together in review
> on 2026-07-05. Guidance blockquotes are intentionally retained as a learning record
> of how each section was approached.

**Product angle (decided 2026-07-05):** An applicant tracking system for small and
growing companies, differentiated by per-job configurable hiring pipelines — the same
product a software firm, a sales team, or a school can shape to its own process.
(Originally scoped to teaching-staff hiring; widened to horizontal with configurability
as the flexibility mechanism. Teaching hires remain our showcase configuration.)

## 1. The problem

> In 3–5 sentences: what goes wrong today when a small company without dedicated HR
> tooling needs to hire? Draw on what you've SEEN — at your EdTech employer, at
> institutes you worked with. Probing questions: Where do applications land today
> (email inbox? WhatsApp? job-portal messages)? Who loses track of which candidate
> is at which step? What happens when the one person tracking it all goes on leave?
> How does a candidate experience the silence?

When a small company hires without a dedicated tool, applications arrive scattered
across email inboxes, WhatsApp chats, and job-portal messages — there is no single
place where anyone can see every candidate for a role. Under time pressure the whole
process is often compressed into a single day of walk-in interviews ending in
same-day offers, with necessary stages skipped along the way; steps that cannot be
rushed, like certificate verification with a university, take unpredictable time
that nobody tracks. HR and management have no shared view of who applied, who was
called, or who decided what — the hiring status lives in one person's head or
spreadsheet. Candidates experience the disorder directly: hours of waiting on
interview day, and silence afterwards.

## 2. Who feels the pain

> One line of specific pain per role. Not "users" — real people: the founder/director
> who hires rarely but urgently, the office manager or HR-of-everything who tracks
> candidates in a spreadsheet, the department head pulled in to interview, and the
> candidate refreshing their inbox.

- **The founder/director** — hires rarely but urgently, and personally absorbs the
  cost of a wrong hire; in a startup, one bad selection is money the company cannot
  recover.
- **The HR / office manager** — tracks every candidate in a private spreadsheet,
  chases panel members and universities by phone, and becomes a single point of
  failure; where trust between HR and management is thin, the lack of a shared
  record turns into suspicion and politics.
- **The interview panel member / department head** — pulled in ad hoc around their
  real job; their availability silently dictates the entire recruitment schedule,
  because nothing can move without the expert in the room.
- **The candidate** — waits hours on interview day, then refreshes an inbox that
  never rings; they judge the whole company by the disorder of its hiring.

## 3. The cost of the problem

> Why does this deserve software? Estimate honestly: what does a slow or bad hire
> cost a 20-person company? Lost candidates who accepted elsewhere during the delay?
> Founder hours burned on coordination? A mis-hire's salary and redo cost?

- **A mis-hire costs 4–6 months of salary** with no fruitful return, plus the full
  cost of running the hiring round again.
- **In education, the cost compounds into reputation:** a wrong teaching hire shows
  up in student results and placement outcomes — damage that outlasts the employee.
- **Repeated ad hoc hiring has a hidden cost:** someone senior must run product
  training for every replacement, effectively dedicating a trainer the startup
  cannot afford to lose.
- **Slow, uncoordinated processes lose the best candidates,** who accept faster
  offers elsewhere while the panel's calendars are being aligned.

## 4. How they cope today (current alternatives)

> What do small companies actually use — shared inboxes, Excel, Google Forms, job
> portals' built-in trackers, sticky notes? Why do these break down? And the key
> question for OUR angle: why do the big ATSs (Workday, Greenhouse) not fit — price,
> complexity, rigidity? Also: where does a company with a NON-standard process
> (like a school needing a demo class) fit in generic tools?

Today the work is done with shared inboxes, Excel sheets, and Google Forms. These
hold data but give nothing back: no analytics or insight into how hiring is going,
no collaboration — the spreadsheet is one person's private tool, invisible to
management and panel members — and no traceable history of who moved which candidate,
when, and why. When the person who owns the sheet is on leave, hiring stops.

At the other extreme, enterprise ATSs (Workday, Greenhouse and the like) are priced
and designed for companies with dedicated HR departments: they demand formal
implementation, ongoing administration, and HR expertise that a 20-person company
does not have. At small hiring volumes, the cost cannot justify the returns.

And even where a generic tool is affordable, it is rigid: a school's demo class, a
sales team's role-play call, a startup founder's culture conversation have no place
in a fixed pipeline. Companies end up bending their hiring process to fit the tool —
the opposite of what a tool is for.

## 5. The vision

> 2–3 sentences: the world after Banyan ATS. Written for a company owner, not a
> developer — outcomes, no feature names. The word "pipeline" may appear; the word
> "database" may not.

Banyan ATS gives a small or growing company one place where hiring runs in the open:
every vacancy, every candidate, and every decision visible to everyone involved, from
founder to panel member. Each job runs its own pipeline shaped to how that role is
really hired — a coding test for a developer, a demo class for a teacher — so the
company's process fits the company, not the tool. Hiring becomes swift for the team,
transparent for management, and respectful for the candidate.

*(Later versions add AI assistance on top of this foundation; the vision above must
stand on its own without it.)*

## 6. What success looks like for v1

> 3–5 measurable statements. Example shape: "A company can go from posting a vacancy
> to recording an offer decision entirely inside the system, with every candidate's
> current stage visible at a glance." These become the yardstick for every scoping
> decision later.

1. A company can go from posting a vacancy to recording an offer decision **entirely
   inside the system** — no step of the flow requires falling back to email or Excel.
2. Every application submitted against a posted job **lands directly in that job's
   pipeline** — no application exists only in someone's personal inbox.
3. Before opening a job, an admin can **shape its pipeline** — add, remove, rename,
   and reorder stages — so two different jobs can run two different processes.
4. Anyone with access can answer **"where is candidate X, and whose action is
   next?" in under 10 seconds** from a board view of the pipeline.
5. Every stage move is **recorded with who and when**, so any candidate's full
   journey can be reconstructed after the fact.

## 7. Explicitly out of scope (for now)

> As important as everything above. Candidates for this list: payroll, onboarding,
> background checks, a public job board, resume search across companies, email
> automation, multi-language UI, AI features (later version by design). Decide too:
> is pipeline configurability itself v1 or v1.5? Write the call down either way.

**Decided IN v1:** pipeline configurability (add/remove/rename/reorder stages per
job) — it is the product's differentiator, so it cannot wait. Limited strictly to
stage structure: no per-stage automation rules, triggers, or approvals in v1.
Each job gets a shareable public application link (otherwise nothing can enter the
pipeline), but that is a form, not a job board.

**Deferred to v1.5/v2:**

- Email notifications to candidates and panel members (v1: status is visible in the
  system; nobody is notified automatically)
- Automated recruiter assignment (v1: candidates are assigned manually)
- Assessments/tests: configuration, delivery, and scoring (v1: an "Assessment" stage
  can exist, but the test itself happens outside the system)
- Certificate/document verification workflow (v1: verification can be a stage; the
  chasing of universities stays manual)
- A public careers page / job board listing all openings

**Out entirely (this product cycle):**

- Payroll and onboarding
- Background checks performed by the system itself
- Resume search across companies
- Multi-language UI
- All AI features — resume parsing, matching, summarization — reserved by design
  for the final phase of this project
