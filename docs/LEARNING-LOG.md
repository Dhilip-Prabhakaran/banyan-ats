# Learning Log

A few lines after every work session or completed slice: what was built, what I understood, what surprised me. Raw material for LinkedIn posts.

---

## 2026-07-04 — Project setup

- Created the repo with `git init -b main`: a plain folder becomes a repository when Git adds its hidden `.git` directory — the history recorder.
- Decided to document the product cycle, not just code: BA artifacts, decision records (ADRs), and this log all live in the repo.
- Learnt about the difference between git and github. Understood distributed version control, commit the changes to local, git push to github, git pull from github to local.

## 2026-07-04 - Stakeholder and Personas

- Every User is stakeholder and they actually touches the software
- Stakeholders are all involved in the process, funds it, manges it, controls it,constraint it, judges it.Many stakeholder never logs in.
- Design features for users but satisfy stakeholders
- The primary persona is the one who cannot be satisfied by an interface designed for any other persona, and around whose core task the main screens are optimized

## 2026-07-10 - Process Flow

- The difference between the as-is and to-be is your product's entire value. 
- Placed side by side, every place the to-be is simpler, faster, or safer is a feature justified
- flowchart TD
    A([Application arrives]) --> B[Recruiter reviews]
    B --> C{Qualified?}
    C -->|Yes| D[Schedule interview]
    C -->|No| E([Reject])