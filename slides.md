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

# Build Your Resume with JavaScript

Expand Your Online Presence Beyond LinkedIn

<div class="mt-4 text-lg text-left opacity-70">
  July 27, 2026
</div>

<!--
Slide 1 Notes
-->

---
transition: fade-out
---

# Why I Built This Project

<div class="mt-6">

- The 2026 job market is competitive, especially for developers breaking in, transitioning, or recovering from layoffs
- A resume PDF still matters, but it is not always enough
- LinkedIn and GitHub are important, but a personal web presence shows initiative
- I wanted to build something useful for jobseekers, early-career developers like myself, and anyone who wants a simple digital resume
- I also wanted to measure my current JavaScript understanding honestly
- While learning and practicing how to think like a developer, I wanted to give another experienced developer the opportunity to share their approach, perspective, and practical tradeoffs when solving the same problem

</div>

<!--
Slide 2 Notes
-->

---
transition: slide-up
---

# Live Resume Benefits

<div class="mt-6">

1. Easier to update
2. Shareable with a link
3. Expands your online presence
4. Shows technical ability
5. More flexible than a static PDF
6. Makes it easier for recruiters and community connections to learn about you
7. If hosted publicly, a live resume can be indexed by search engines
8. Easier to customize based on different goals
9. Encourages better data organization

</div>

<div v-click class="mt-6 p-4 border border-yellow-400/50 rounded-lg bg-yellow-400/10">
  A live resume complements your ATS resume, but it does not replace it. Use your ATS resume for job applications and automated screening. Use your live resume for networking, sharing project links, and telling your story.
</div>

<!--
Slide 3 Notes
-->

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

| Day        | Milestone                                                             |
|------------|-----------------------------------------------------------------------|
| **Day 1**  | Structured the project and pushed the first commit                    |
| **Day 4**  | Used `fetch()` and `response.json()` to load resume data              |
| **Day 5**  | Targeted sections with `document.getElementById()`                    |
| **Day 7**  | Rendered dynamic lists with `.map()` and `.join()`                    |
| **Day 13** | Handled errors with `try/catch`, `response.ok`, and `response.status` |
| **Day 14** | Refactored into ES modules using `import` and `export`                |
| **Day 19** | Built a design system with CSS custom properties                      |
| **Day 21** | Added print button with `addEventListener()` and `window.print()`     |

</div>

<!---------- SLIDE 6 | PROJECT STRUCTURE & REFACTOR ---------->

---
transition: fade-out
---

# Project Structure & Refactor

<div class="grid grid-cols-2 gap-8 mt-6">
<div class="text-xs">

### Before - Day 13

```javascript
// index.demo.mjs

const data = await (await fetch('../data/resume.json')).json()
console.log(data)

// MONOLITHIC FILE STRUCTURE:
// 1. Fetching data
// 2. Selecting DOM elements
// 3. Building section markup
// 4. Rendering every resume section
// 5. Handling UI behavior
```

</div>
<div v-click class="text-xs">

### After - Day 17

```javascript
// index.mjs

import { renderResume } from './render.mjs'

const response = await fetch('data/resume.json')
const data = await response.json()

renderResume(data)

// render.mjs coordinates the section modules
// each module renders one part of the resume
```

</div>

<div v-click class="col-span-2 mt-1 p-3 border border-primary/30 rounded bg-primary/5">
  Refactoring into modules helped separate responsibilities.
Each file handles one part of the page, which makes the project easier to understand, debug, and maintain.
</div>
</div>

<!---------- SLIDE 7 | PROJECT STRUCTURE ---------->

---
transition: fade-out
---

# Final Project Structure

<div class="grid grid-cols-[1.1fr_0.9fr] gap-6 mt-3">
<div class="text-[0.55rem] leading-none">

```text
resume-js/
├── assets/
│   └── fonts/
├── css/
│   ├── print.css
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
│   │   ├── printButton.mjs
│   │   ├── projects.mjs
│   │   ├── skills.mjs
│   │   └── summary.mjs
│   ├── index.mjs
│   └── render.mjs
├── index.html
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

<!---------- SLIDE 8 | BUGS & MISTAKES ---------->

---
transition: fade-out
---

# Bugs & Mistakes

<div class="text-sm mt-2">

| Issue | Cause | What I Learned |
|---|---|---|
| `ReferenceError: data is not defined` | Data was referenced outside the scope where it existed | Scope matters, especially with fetched data |
| `404` on `fetch()` | Wrong relative path to `resume.json` | File paths depend on where the page is loaded |
| Silent fetch failure | `fetch()` does not throw for failed HTTP responses by itself | Check `response.ok` before calling `response.json()` |
| Wrong section title rendered | Copy/paste without a full review | Small UI mistakes are easy to miss |
| Unused CSS selector | Removed markup but left old CSS behind | Removing a feature means checking HTML, JS, CSS, and data |

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

<!---------- SLIDE 10 | RESOURCES ---------->

---
transition: fade-out
class: text-left
---

# Resources

<div class="mt-6 text-md">

- **MDN Web Docs** for JavaScript, `fetch()`, DOM methods, and browser APIs
- **JavaScript.info** for async JavaScript and fundamentals
- **Scrimba** for interactive JavaScript practice and project-based learning
- **Eloquent JavaScript** for deeper JavaScript concepts and problem solving
- **GitHub** for version history, commits, and project review
- **Community feedback** for improving structure, clarity, and presentation flow
- **AI tools** for support, review, and design suggestions. Not as a replacement for understanding

</div>

<!---------- SLIDE 11 | KEY TAKEAWAYS ---------->

---
transition: fade-out
---

# Key Takeaways

<div class="grid grid-cols-2 gap-4 mt-6">

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  <strong>Data drives the page.</strong>
  <div class="mt-2 text-sm opacity-80">
    A single JSON file can power the content without rewriting HTML.
  </div>
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  <strong>Structure affects everything.</strong>
  <div class="mt-2 text-sm opacity-80">
    File organization changes paths, imports, debugging, and maintainability.
  </div>
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  <strong>Scope lives where data lives.</strong>
  <div class="mt-2 text-sm opacity-80">
    Understanding where data exists helped me fix JavaScript errors.
  </div>
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  <strong>Async code teaches you to think in steps.</strong>
  <div class="mt-2 text-sm opacity-80">
    Code does not always run top to bottom when requests and promises are involved.
  </div>
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  <strong>Modular code is easier to maintain.</strong>
  <div class="mt-2 text-sm opacity-80">
    Separation of concerns improves maintainability, debugging, and collaboration.
  </div>
</div>

<div v-click class="p-4 border border-primary/20 rounded-lg bg-primary/5">
  <strong>Clean code is a process.</strong>
  <div class="mt-2 text-sm opacity-80">
    Reviewing, refactoring, and fixing mistakes are part of building real projects.
  </div>
</div>

</div>


<!---------- SLIDE 12 | LIVE DEMO LINK ---------->

---
layout: two-cols
class: text-left
---

<script setup>
import QrcodeVue from 'qrcode.vue';
const liveDemoUrl = 'https://timbaines.github.io/resume-js/'
</script>

# Live Resume Demo

<div class="flex flex-col justify-center h-full gap-6 pb-34">

  <div class="text-xl">
    Scan the QR code to view the deployed project.
  </div>

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-4">
  <div class="w-48 h-48 border-1 border-primary/30 rounded-lg bg-white p-3 flex items-center justify-center">
    <QrcodeVue :value="liveDemoUrl" :size="168" level="M"></QrcodeVue>
  </div>

  <p class="text-xs font-mono opacity-70">
    {{ liveDemoUrl.replace('https://', '') }}
  </p>
</div>

<!---------- SLIDE 13 | GITHUB REPO LINK ---------->

---
layout: two-cols
class: text-left
---

<script setup>
import QrcodeVue from 'qrcode.vue';
const githubRepoUrl = 'https://github.com/Timbaines/resume-js'
</script>

# GitHub Repo

<div class="flex flex-col justify-center h-full gap-6 pb-34">

  <div class="text-xl">
    Scan the QR code to view the source code.
  </div>

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-4">
  <div class="w-48 h-48 border-1 border-primary/30 rounded-lg bg-white p-3 flex items-center justify-center">
    <QrcodeVue :value="githubRepoUrl" :size="168" level="M"></QrcodeVue>
  </div>

  <p class="text-xs font-mono opacity-70">
    {{ githubRepoUrl.replace('https://', '') }}
  </p>
</div>

<!--
Slide 13 Notes
-->

---
transition: fade-out
layout: center
class: text-center
---

# Same Problem, Different Target

<div class="mt-8 text-2xl">

Tim built the live resume.

</div>

<div v-click class="mt-4 text-2xl">

I went down the rabbit hole on the PDF.

</div>

<div v-click class="mt-8 text-lg opacity-70">
  Same goal underneath: a resume that works like code — versioned, themed, one source of truth.
</div>

<!--
Callback to Tim's project.

I went a different direction with the same ultimate goal.
-->

---
transition: fade-out
---

# Getting to Typst: Three Dead Ends

<div class="text-sm mt-4">

| Attempt | The Appeal | Why I Binned It |
|---|---|---|
| **LaTeX** | Battle-tested, decades of templates | Clunky and awkward to write, and the output still wasn't amazing for the effort |
| **Markdown → PDF** | Write in plain text, stay in your editor | No clean converter with great templating at the time* |
| **Website + print CSS** | Modern site *and* a printable resume from one source | Firefox gives you no clean way to drop the printer header/footer |

</div>

<div v-click class="mt-6 p-4 border border-yellow-400/50 rounded-lg bg-yellow-400/10 text-sm">
  *The Markdown story has improved since — Quarkdown looks really clean today. Tooling moves fast; re-check your dead ends occasionally.
</div>

<!--
Outline 3 previous attempts.

LaTeX blows (old, clunky).
Markdown getting better.
Website + Print good but no universal support.
-->

---
transition: fade-out
---

# Typst: Where It Clicked

<div class="grid grid-cols-2 gap-6 mt-4">
<div class="text-xs">

```typ
// resume.typ — just content
#import "template.typ": *
#show: resume

= Experience

#job("Trader Interactive", "Software Engineer",
     "2022 – 2026")[
  - Migrated a legacy frontend to Nuxt/TypeScript
  - Built the company's first image cropping API
]
```

```typ
// template.typ — all the styling
#let job(company, title, date, body) = {
  block(breakable: false, ...)
}
```

</div>
<div class="text-sm">

### Why It Stuck

- Reads like JavaScript — functions, arguments, imports
- `typst watch` recompiles instantly as you type
- Documentation is genuinely excellent
- Templating is first-class: one file styles, one file is content
- Output is a pixel-perfect PDF, every time, on every machine

<div v-click class="mt-4 p-3 border border-primary/30 rounded bg-primary/5">
  Sound familiar? It's Tim's architecture: <code>resume.json</code> + render modules. Here it's <code>resume.typ</code> + <code>template.typ</code>.
</div>

</div>
</div>

<!--
Typst stuck cause it's JS.
Modular setup.
Replicatable outcome.
Solid docs.
-->

---
transition: fade-out
---

# Choosing Your Tool

<div class="text-sm mt-4">

| Tool | Pick It When… | Watch Out For… |
|---|---|---|
| **JavaScript + JSON** | You want a live URL and to learn the web platform | The PDF side is a print job, not the product |
| **LaTeX** | You're in its ecosystem already (academia) | Steep syntax, slow feedback loop |
| **Markdown** | You just want words on a page, fast | Templating is the weak spot (Quarkdown is changing this) |
| **HTML + print CSS** | One source for site *and* PDF | The browser's print dialog owns your output |
| **Typst** | You want code-like control and a perfect PDF | Younger ecosystem, far fewer ready-made templates |

</div>

<div v-click class="mt-6 p-4 border border-primary/30 rounded-lg bg-primary/5 text-sm">
  There's no wrong answer here — every one of these beats hand-nudging a Word doc, because your resume becomes data you can version, diff, and reuse.
</div>

<!--
Highlight that all listed tools have a valid place.

My tool might already be deprecated due to Quarkdown & AI Markdown integration.
-->

---
transition: fade-out
---

# One Master File to Feed Them All

<div class="grid grid-cols-2 gap-8 mt-6">
<div class="text-sm">

### `master-resume.md`

- A plain-Markdown **superset** of everything I've done
- Source of truth for *facts* — new accomplishments land here first
- Each tailored Typst resume is a curated subset of it

</div>
<div v-click class="text-sm">

### What It Feeds

- The base resume variants I maintain in Typst
- AI drafting & tailoring — the model knows every real fact, so it doesn't need to invent any
- Any other AI workflow that needs my full history

</div>
</div>

<div v-click class="mt-8 p-4 border border-primary/30 rounded-lg bg-primary/5 text-sm">
  Tim's <code>resume.json</code> drives a web page. My <code>master-resume.md</code> drives the AI that helps me maintain the resumes. Either way: structure your data once, render it anywhere.
</div>

<!--
Yet another reason Quarkdown might be the future for me.
Ultimately the same general structure as Tim's project, in a different coat.
-->

---
layout: two-cols
class: text-left
---

<script setup>
import QrcodeVue from 'qrcode.vue';
const templateRepoUrl = 'https://github.com/TekGadgt/resume-template'
</script>

# Typst Resume Template

<div class="flex flex-col justify-center h-full gap-6 pb-34">

  <div class="text-xl">
    Scan the QR code to grab the template. Fork it, edit <code>resume.typ</code>, run <code>typst compile</code>.
  </div>

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-4">
  <div class="w-48 h-48 border-1 border-primary/30 rounded-lg bg-white p-3 flex items-center justify-center">
    <QrcodeVue :value="templateRepoUrl" :size="168" level="M"></QrcodeVue>
  </div>

  <p class="text-xs font-mono opacity-70">
    {{ templateRepoUrl.replace('https://', '') }}
  </p>
</div>

<!--
Just a link to my Typst template if anyone wants to try it.
-->
