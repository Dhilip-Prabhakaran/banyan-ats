# Glossary

Concepts explained in my own words as I meet them. Each entry: what it is, what the alternatives are, and when you'd pick which.

---

## jQuery vs. React (ways to update a web page)

Both solve the same problem: updating what the user sees when data changes.

- **jQuery (imperative):** you manipulate the page directly — "find this element, change its text, hide that div." Fine for small pages; becomes a tangle in large apps because *you* are responsible for keeping the page in sync with the data everywhere it appears.
- **React (declarative):** you describe what the UI should look like for a given state ("if there are 5 candidates, show 5 rows"). When state changes, React works out what to update. You write the *what*, not the *how*.

**When which:** jQuery-style DOM manipulation still appears in legacy systems and tiny scripts. New apps of any size use a declarative framework (React, Vue, Angular, Svelte) because manual sync doesn't scale with app complexity.
