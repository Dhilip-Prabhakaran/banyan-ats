# Stakeholders & Personas — Banyan ATS

> **Status: REVISED v0.2** — first draft by Dhilip, reworked together on 2026-07-05.
> Guidance blockquotes are retained as a learning record; delete them once a section
> has real content.
>
> **Key idea:** a *stakeholder* is anyone who cares about the system (affected by it,
> funds it, constrains it, judges it). A *user* is the narrower group who actually
> touches the software. Every user is a stakeholder; not every stakeholder is a user.
> Part A lists everyone (wide + shallow); Part B goes deep on only the people who
> actually use it.

---

## Part A — Stakeholder register

> Cast a wide net. List everyone who cares, whether or not they log in. For each:
> their main interest, their influence (High/Medium/Low), and whether they actually
> touch the software. The "Is a user?" column is the hinge — it decides who gets a
> persona in Part B.

| Stakeholder | Main interest | Influence | Is a user? |
|-------------|---------------|-----------|------------|
| Founder / co-founders | Fast, correct hires; value for money | High | Rarely — views summary reports only |
| Director | Correct hires; reviews recruitment reports | High | Rarely |
| Department Head | A candidate with the right skillset for a vacancy | High | Rarely |
| HR Manager (Admin) | Configure and oversee the whole flow; records & activity logs | High | **Core user** |
| Hiring Manager | Publish jobs; assign candidates to recruiters; approve key stages | High | **Core user** |
| HR Executive / Recruiter | Work the board daily; move candidates; schedule; communicate | Medium | **Core user** |
| Panel Member | Interview and score candidates | Medium | Limited — scorecard entry page only |
| Candidate | Apply; track progress; (later) self-schedule | Low | Limited — application form |
| Employee Referrer | Refer known candidates; referral bonus | Low | Limited — referral page (later version) |
| Accounts / Finance | Salary budget for open roles | Low | Not a user |
| Background Verification Team | Verify certificates of hired candidates | Low | Not a user — Recruiter records the outcome |
| 3rd-party Assessment Team | Conduct written / mass assessments | Low | Not a user |

> **Resolved contradiction:** the Background Verification Team does *not* type into
> Banyan in v1 — the Recruiter records their outcome. That keeps them a stakeholder,
> not a user. (Integrating them directly is a later-version decision.)
>
> The rows marked **Core user** are the ones that earn a full persona below. Everyone
> else is satisfied through features and reports, not screens designed for them.

---

## Part B — Personas

> A deep profile for each person who actually uses the system, drawn from real people
> observed (or been). Names use matching initials to their role so they stay memorable
> (Arthi/Admin-ish, Mani/Manager, Rachel/Recruiter, Cathy/Candidate).

### Persona 1 — Arthi, HR Manager (Admin)

- **Snapshot:** HR Manager at a ~100-employee firm; comfortable with software; owns the hiring system end to end.
- **In the hiring process, they:** hold all permissions; create job openings from department requirements; design each job's process (stages + scoring) with the department head and leadership; assign whole jobs or individual candidates to hiring managers; use override permission to resolve discrepancies; export reports for the director and founders.
- **Goals:** a well-defined, consistent process for every job; live visibility of progress.
- **Frustrations today:**
  - Candidates apply through several HRs at once, with no single place to see them all.
  - Every job needs a different flow, but rushing it all into one day causes poor selection.
- **What they need from Banyan ATS:**
  - A predefined flow (stages + scoring) attached to each job *at posting time*.
  - Progress reports, and automation wherever possible.
- **Telling detail:** She has been burned by two recruiters unknowingly chasing the same candidate, so she instinctively wants to see *everything* herself — which makes her the bottleneck she resents being.

### Persona 2 — Mani, Hiring Manager

- **Snapshot:** manages a team of recruiters; accountable for filling his department's roles.
- **In the hiring process, they:** assign candidates to recruiters; approve candidates at key stages; form interview / demo / group-discussion panels; invite panel members with schedules; balance recruiter workloads.
- **Goals:** smoothly monitor recruitment and balance his team's workload.
- **Frustrations today:** hard to centralize and follow different processes for different jobs at the same time.
- **What they need from Banyan ATS:** a clear workflow and automation to manage workloads and monitor recruiter activity live.
- **Telling detail:** Mani lives in back-to-back meetings; his real fear is that a strong candidate goes cold while he's away from his desk, so he wants the system to nudge him when *his* approval is the thing holding a candidate up.

### Persona 3 — Rachel, Recruiter (HR Executive)

- **Snapshot:** executes the day-to-day recruitment; lives in the board.
- **In the hiring process, they:** enter scores at each stage; move candidates between stages; manually record outcomes from the assessment and background-verification teams; handle email with candidates and panel members; build interview schedules, create slots, allocate panel members.
- **Goals:** move candidates stage by stage and complete the process cleanly.
- **Frustrations today:** tracking every candidate in Excel is hard; each recruiter keeps their own data; coordination is painful.
- **What they need from Banyan ATS:** a smooth interface to move candidates through stages; less dependence on managers by working to a preset flow; easy scheduling and communication.
- **Telling detail:** Rachel is often the scapegoat when an unplanned process goes wrong for a candidate or the team — so she wants the process visible and enforced, to share the accountability rather than carry it alone.

### Persona 4 — Cathy, Candidate

- **Snapshot:** applies expecting a clear JD, a seamless application, visibility of the major stages, and no unnecessary waiting.
- **In the hiring process, they:** apply via web portal (or hard copy); fill the form; upload documents; *(later version)* self-schedule interview slots; move through each stage; accept the offer.
- **Goals:** a smooth process with zero unnecessary waiting, clear communication, hassle-free scheduling.
- **Frustrations today:** made to wait for hours because interview planning is poor.
- **What they need from Banyan ATS:** an application portal, two-way communication, and *(later)* self-scheduling — especially for candidates travelling a distance.
- **Telling detail:** Cathy once lost a whole day to a disorganized, uncommunicative process — with no clear schedule she couldn't plan her travel, and she now judges a company's professionalism by how it runs its hiring.

> **v1 scope note on Cathy:** in v1 she is a user of *one* screen — the application
> form (apply + upload). Self-scheduling and online offer acceptance are deferred to
> a later version (see problem statement §7).

---

## Part C — What this tells us (design implications)

- **Primary persona (optimise for first): Admin (Arthi).** Admin and Recruiter share
  the same core board; Admin is a superset with extra config/override screens. We
  optimise the shared board for the high-frequency daily flow, and keep admin-only
  controls on *separate* screens so the board stays fast. *(Watch out: don't let
  override controls clutter the daily board — that's the trap this choice risks.)*
- **A stakeholder who is NOT a user but must still be satisfied: the Founder.** A
  mis-hire costs 3–6 months of salary plus training. Satisfy through a transparent
  report: recruitment funnel, filtering steps, candidate–JD match, and time-to-hire.
- **What writing this surfaced:** the three internal personas map cleanly onto three
  permission tiers — **Admin / Hiring Manager / Recruiter**. In other words, the
  product needs **Role-Based Access Control (RBAC)**. We discovered a standard design
  pattern by profiling real people, not by copying a template.
