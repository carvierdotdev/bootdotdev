# Key takeways

- Use **Option 1 (single branch, course folders)** for clarity.
- Layer **Option 3 (branches for projects)** when you hit guided/portfolio projects.
- Keep Obsidian vault inside the repo (`/notes`) so everything is versioned together.


## 🗂 Repo Organization Strategy

### 1. **Single Main Branch + Course Folders**

- **Structure:**
    
    ```
    bootdotdev/
      python/
        01-learn-to-code/
        04-bookbot-project/
        05-oop/
        ...
      typescript/
        13-learn-js/
        14-learn-ts/
        16-pokedex-project/
        ...
      linux/
      git/
      c/
      sql/
      docker/
      rabbitmq/
    ```
    
- **Pros:**
    - Easy to navigate by language/tech.
    - Keeps everything in one branch, so you don’t have to constantly switch.
    - Works well with Obsidian vault linking (each folder can have notes + code).
- **Cons:**
    - Repo can get large over time.
    - Harder to isolate experiments without clutter.

---

### 2. **Hybrid: Monorepo with Branches for Projects**

- **Structure:**
    - `main` → all course folders (like option 1).
    - Feature branches for **guided projects** (Bookbot, Asteroids, Pokedex, Blog Aggregator, etc.).
- **Pros:**
    - Keeps your learning path linear in `main`.
    - Each project can have its own branch history, so you can track iterations cleanly.
    - Easy to showcase projects later (merge into portfolio repo).
- **Cons:**
    - Slightly more Git overhead.
    - Requires discipline to merge project branches back into main.

---

## 📓 Obsidian Integration

Since you’re using Obsidian as your “hub”:

- Create a **note per course** with backlinks to code folders.
- Use **Dataview plugin** to track progress (`completed lessons`, `projects done`).
- Keep a `README.md` in each course folder with:
    - Summary of what you learned.
    - Links to Obsidian notes.
    - Commands/env setup (so future you can rerun easily).

---
