# Glossary

Concepts explained in my own words as I meet them. Each entry: what it is, what the alternatives are, and when you'd pick which.

---

## jQuery vs. React (ways to update a web page)

Both solve the same problem: updating what the user sees when data changes.

- **jQuery (imperative):** you manipulate the page directly — "find this element, change its text, hide that div." Fine for small pages; becomes a tangle in large apps because *you* are responsible for keeping the page in sync with the data everywhere it appears.
- **React (declarative):** you describe what the UI should look like for a given state ("if there are 5 candidates, show 5 rows"). When state changes, React works out what to update. You write the *what*, not the *how*.

**When which:** jQuery-style DOM manipulation still appears in legacy systems and tiny scripts. New apps of any size use a declarative framework (React, Vue, Angular, Svelte) because manual sync doesn't scale with app complexity.

---

## Git vs. GitHub (version control vs. hosting)

- **Git** is a program on my machine. The hidden `.git` folder inside the project *is* the repository — the full database of every commit, fully usable offline. Committing is a local act.
- **GitHub** is a company hosting a second full copy of the repository, with a website on top (rendered README, pull requests, issues). Alternatives: GitLab, Bitbucket — same Git underneath.
- The copies do **not** sync automatically: `git push` uploads my new commits to GitHub; `git pull` downloads commits I don't have. `origin` is just the conventional nickname for the bookmark pointing at the hosted copy.
- This is "distributed" version control: every copy is complete. Daily rhythm: edit → `git add` (stage) → `git commit` (snapshot locally) → `git push` (share).

---

## Line endings: LF vs. CRLF

Typewriter heritage: ending a line = carriage return (CR, `\r`) + line feed (LF, `\n`). Unix/Linux/Mac use LF alone; Windows uses the CRLF pair — so the "same" text file is different bytes per platform.

- Git's "LF will be replaced by CRLF" warning is not an error: it's Git narrating that it stores the neutral form (LF) in the repository and hands Windows its native form (CRLF) in the working copy.
- The per-machine setting (`core.autocrlf`) works but isn't shared; the professional fix is a **`.gitattributes`** file with `* text=auto`, committed to the repo, so every contributor's machine follows the same policy.
- Why care: apps are developed on any OS but usually deployed to Linux, where stray CRLF in scripts/configs causes confusing failures.
