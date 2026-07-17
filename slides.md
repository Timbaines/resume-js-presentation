---
theme: seriph
background: ./resume-js-bg.webp
title: Build Your Resume with JavaScript
info: |
  ## Build Your Resume with JavaScript
  Expand Your Online Presence Beyond LinkedIn

  NorfolkJS

  July 27, 2026
class: text-left
drawings:
  persist: false
transition: fade-out
comark: true
duration: 35min
---

<!---------- SLIDE 1 | OPENING BANNER ---------->

# Build Your Resume with JavaScript

Expand Your Online Presence Beyond LinkedIn

<div class="mt-4 text-lg text-left opacity-70">
  July 27, 2026
</div>

<!---------- SLIDE 2 | THE PROBLEM ---------->

---
transition: fade-out
---

# The Problem

<div class="mt-6">

- Developers in Hampton Roads navigating layoffs
- Job searching in a market most of us have never faced
- PDF resumes and LinkedIn profiles have limits
- Online presence beyond a static document matters now

</div>

<!---------- SLIDE 3 | LIVE RESUME BENEFITS ---------->

---
transition: slide-up
---

# Live Resume Benefits

<div class="mt-6">

- Proves how you communicate — not just what you built
- Contact info, projects and profile links all in one place
- Stands out in a stack of identical PDFs
- Represents you before you walk in the room

</div>

<div v-click class="mt-6 p-4 border border-yellow-400/50 rounded-lg bg-yellow-400/10">
  This does not replace your ATS resume. It does support it.
</div>

<!---------- SLIDE 4 | THE IDEA ---------->

---
transition: fade-out
layout: center
class: text-center
---

# The Idea

<div class="mt-8 text-2xl">

One JSON file.

One JavaScript file.

One live URL.

</div>

<div v-click class="mt-8 text-xl text-primary font-mono">
  Update the data → the page updates.
</div>

<div v-click class="mt-4 text-lg opacity-70">
  Without having to touch the HTML file.
</div>

<!---------- SLIDE 5 | MY LEARNING CURVE ---------->

---
transition: fade-out
--- 

# Learning Curve

<div class="text-sm mt-2">

| Day | Milestone |
|---|---|
| **Day 1** | Structured the project and pushed the first commit |
| **Day 4** | Fetched live data and logged it to the console |
| **Day 7** | Rendered dynamic lists with `.map()` and `.join()` |
| **Day 13** | Handled errors with `try/catch` |
| **Day 14** | Refactored into modules using `import/export` |
| **Day 19** | Built design system with CSS custom properties |


</div>

<!---------- SLIDE 6 | PROJECT STRUCTURE ---------->

---
transition: fade-out
---

# Project Structure

<div class="grid grid-cols-2 gap-8 mt-4">
<div class="text-xs">

```
resume-js/
├── assets/
│   └── fonts/
├── css/
│   └── style.css
├── data/
│   └── resume.json
├── src/
│   ├── sections/
│   │   ├── achievements.mjs
│   │   ├── certifications.mjs
│   │   ├── education.mjs
│   │   ├── experience.mjs
│   │   ├── footer.mjs
│   │   ├── header.mjs
│   │   ├── projects.mjs
│   │   ├── skills.mjs
│   │   └── summary.mjs
│   ├── index.mjs
│   └── render.mjs
├── index.html
├── package.json
└── README.md
```

</div>
<div v-click class="flex flex-col justify-center text-sm">

### Why This Structure?

- **`assets/fonts/`** Locally loaded fonts for performance
- **`data/`** Single source of truth
- **`src/sections/`** Individual file with one job
- **`render.mjs`** Coordinates all sections
- **`index.mjs`** Fetches data, starts the process
- **`index.html`** Intentionally empty shell

<div class="mt-4 p-3 border border-primary/30 rounded bg-primary/5 text-sm">
  Each file has one job.
</div>

</div>
</div>

<!---------- SLIDE 7 | PROJECT REFACTOR ---------->

---
transition: fade-out
---

# Project Refactor

<div class="grid grid-cols-2 gap-8 mt-6">
<div class="text-xs">

### Before - Day 13

```javascript
// index.demo.mjs

const data = await (await fetch('../data/resume.json')).json();
console.log(data);

// SECTIONS RENDERED
// 1. HEADER
// 2. SUMMARY
// 3. SKILLS
// 4. EXPERIENCE
// 5. PROJECTS
// 6. EDUCATION
// 7. CERTIFICATIONS
// 8. ACHIEVEMENTS
// 9. FOOTER
```

</div>
<div v-click>

### After - Day 17

```javascript
// index.mjs

import { renderResume } from './render.mjs'
const data = await fetch('../data/resume.json')
renderResume(data)

// render.mjs coordinates 9 modules
// each module has one job
// each module only knows itself
```

<div class="mt-4 p-3 border border-primary/30 rounded bg-primary/5">
  Refactoring into individual modules is separation of concerns in practice. 
  Each file has one job and only knows how to do that one thing.
</div>

</div>
</div>

<!---------- SLIDE 8 | THE BUGS ---------->

---
transition: fade-out
---

# Bugs & Mistakes

<div class="text-sm mt-2">

| Issue                                 | Cause                                      | What I Learned                      |
|---------------------------------------|--------------------------------------------|-------------------------------------|
| `ReferenceError: data is not defined` | `data` referenced outside `.then()`        | Scope lives where data lives        |
| `404` on `fetch()`                    | Wrong relative path from inside `src/`     | File structure affects every path   |
| Wrong `<h2>` title rendered           | Copy paste without reviewing               | Always review before committing     |
| Silent fetch failure                  | `fetch()` alone does not throw HTTP errors | `response.ok` check is not optional |
| Swapped file contents                 | `education.mjs` had certifications code    | Fresh eyes before every commit      |

</div>

<!---------- SLIDE 9 | LIVE DEMO ---------->

---
transition: fade-out
layout: center
class: text-center
---

# Live Demo

<div class="mt-8 font-mono text-xl">
  index.mjs → render.mjs → section modules → DOM
</div>

<div class="mt-8 text-lg opacity-70">
  Change One File & Update The Entire Page
</div>

<!---------- SLIDE 10 | WHAT I LEARNED ---------->

---
transition: fade-out
---

# What I Learned

<div class="grid grid-cols-2 gap-4 mt-6">

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  Scope lives where data lives.
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  Async code does not run top to bottom.
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  Separation of concerns improves maintainability, degbugging and collaboration.
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  Reviewing your own code is a skill.
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  The data should drive the decision.
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  Clean code is not always written clean the first time.
</div>

</div>

<!---------- SLIDE 11 | TAKEAWAYS ---------->

---
transition: fade-out
layout: center 
class: text-left
---

# Takeaways

<div class="mt-6 p-4 border border-primary/30 rounded-lg bg-primary/5">
  Takeaway 1
</div>

<div v-click class="mt-6 p-4 border border-primary/30 rounded-lg bg-primary/5">
  Takeaway 2
</div>

<div v-click class="mt-6 p-4 border border-primary/30 rounded-lg bg-primary/5">
  Takeaway 2
</div>

<div v-click class="mt-6 p-4 border border-primary/30 rounded-lg bg-primary/5">
  Takeaway 4
</div>

<!---------- SLIDE 12 | PROJECT LINKS ---------->

---
layout: two-cols
class: text-left
---

# Project Links / QR Code

<div class="flex flex-col justify-center h-full gap-6 pb-34">

  <div class="text-xl">
    <strong>Live Demo</strong>
    <div class="font-mono mt-2 text-primary">your-github-pages-url.com</div>
  </div>

  <div class="text-xl">
    <strong>GitHub Repo</strong>
    <div class="font-mono mt-2 text-primary">https://github.com/Timbaines/resume-js</div>
  </div>

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-4">
  <div class="w-48 h-48 border-1 border-primary/30 rounded-lg bg-primary/5 flex items-center justify-center">
    <span class="text-sm opacity-50">QR Code</span>
  </div>
  <p class="text-sm opacity-70">Scan for repo</p>
</div>


