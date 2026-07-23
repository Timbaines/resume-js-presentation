<!---------- SLIDE 1 | OPENING BANNER ---------->

<!--
Begin by setting the context:

- This talk is about building a resume with JavaScript
- The goal is to expand an online presence beyond LinkedIn
- This is both a learning project and a practical tool
- The project is intentionally simple: data, JavaScript, HTML, and CSS

Opening line idea:
I wanted to build something practical while also testing what I actually understood about JavaScript.
-->

<!---------- SLIDE 2 | THE PROBLEM ---------->

<!--
Use this slide to explain the real-world motivation.

Key points:
- The job market is competitive, especially for developers breaking in, transitioning, or recovering from layoffs
- A PDF resume still matters, but it is not always enough
- LinkedIn and GitHub are important, but a personal web presence can show initiative
- I wanted to build something useful for jobseekers, early-career developers like myself, and anyone who wants a simple digital resume
- I also wanted to measure my current JavaScript understanding honestly
- I wanted another experienced developer to solve the same problem so I could compare approaches, tradeoffs, and problem-solving decisions

Ask:
How many of you have updated your resume in the last two years?

Then transition:
A traditional resume is still important, but a live resume can support it in ways a PDF cannot.
-->

<!---------- SLIDE 3 | LIVE RESUME BENEFITS ---------->

<!--
Explain that a live resume is not meant to replace an ATS-friendly resume.

It supports the traditional resume by giving people:
- A link they can visit
- A better sense of your technical ability
- A more flexible and searchable version of your professional story
- A place to show initiative beyond LinkedIn and GitHub

Emphasize:
Use the ATS resume for job applications and automated screening.
Use the live resume for networking, sharing project links, and telling your story.

Possible line:
A live resume is not the replacement. It is the companion.
-->

<!---------- SLIDE 4 | THE IDEA ---------->

<!--
This is the thesis slide.

Say it slowly and let the audience absorb it:

One JSON file.
One JavaScript file.
One live URL.

The key idea:
Update the data, and the page updates without touching the HTML.

Emphasize:
This was the point where the project became more than a static page. The data started driving the content.
-->

<!---------- SLIDE 5 | MY LEARNING CURVE ---------->

<!--
Walk through this like a story, not a list.

Each milestone represents an intentional step in the learning process.

Emphasize:
- Fetching data was a major turning point
- Rendering lists helped connect data to the DOM
- Error handling made the project more reliable
- Refactoring into modules made the project easier to reason about
- CSS custom properties helped create a consistent design system
- The print button connected JavaScript behavior to a practical resume feature

Mention:
I wrote every CSS rule by hand. I used AI to suggest the color palette so I could stay focused on the JavaScript architecture, similar to how I would use a design system from a designer on a real team.

Transition:
Once the project worked, the next challenge was making it easier to maintain.
-->

<!---------- SLIDE 6 | PROJECT STRUCTURE & REFACTOR ---------->

<!--
Explain the difference between the early version and the refactored version.

Before:
- One file handled too much
- Rendering logic was grouped together
- The project worked, but it was harder to maintain

After:
- index.mjs starts the process
- render.mjs coordinates the sections
- Each section module has one job

Say:
This file structure is not just organization. It is separation of concerns.

Each module only knows how to render its own section. It does not need to know how the whole app works.

Main point:
This is the best practice I did not just read about. I built it, broke it, and refactored toward it.
-->

<!---------- SLIDE 7 | FINAL PROJECT STRUCTURE ---------->

<!--
Point to each folder and explain its role.

Give the audience a moment to look at the structure before moving on.

Emphasize:
- assets/fonts contains locally loaded fonts
- css contains screen and print styling
- data/resume.json is the single source of truth
- src/sections contains individual modules
- render.mjs coordinates the modules
- index.mjs fetches the data and starts the render process
- index.html stays intentionally simple

Main takeaway:
Each file has one job.

Transition:
This structure helped, but it did not prevent mistakes. It made the mistakes easier to understand.
-->

<!---------- SLIDE 8 | BUGS & MISTAKES ---------->

<!--
Walk through the table as lessons, not failures.

Keep the tone honest and practical.

Emphasize:
- Scope errors taught me where data actually lives
- Fetch path issues taught me how project structure affects paths
- Silent fetch failures taught me why response.ok matters
- Copy and paste errors taught me to slow down and review
- Unused CSS reminded me that removing a feature means checking HTML, JavaScript, CSS, and data together

Possible line:
Every bug became a map of what I did not understand yet.

Do not spend too long here. Pick two or three examples and move forward.
-->

<!---------- SLIDE 9 | LIVE DEMO ---------->

<!--
Walk through the flow:

index.mjs
→ render.mjs
→ section modules
→ DOM

Keep the demo focused.

Show:
- The JSON data file
- The fetch process
- render.mjs coordinating section modules
- One simple section render, such as header or skills
- A small data change if time allows

Have a backup screenshot or local copy ready if anything breaks.

If something breaks live, stay calm and say:
This is exactly why we write error handling.

Transition:
After building and debugging the project, these were the resources that helped me keep learning.
-->

<!---------- SLIDE 10 | RESOURCES ---------->

<!--
Use this slide to point people toward anything that helped you build and understand the project.

Mention:
- MDN Web Docs for JavaScript, fetch, DOM methods, and browser APIs
- JavaScript.info for async JavaScript and fundamentals
- Scrimba for interactive JavaScript practice and project-based learning
- Eloquent JavaScript for deeper JavaScript concepts and problem solving
- GitHub for version history, commits, and project review
- Community feedback for improving structure, clarity, and presentation flow
- AI tools for support, review, and design suggestions, not as a replacement for understanding

Suggested wording:
AI was helpful as a support tool, but I still had to understand what the code was doing.

Keep this section brief so there is enough time for takeaways and project links.
-->

<!---------- SLIDE 11 | KEY TAKEAWAYS ---------->

<!--
Let each takeaway land before moving to the next.

Connect each takeaway back to a specific part of the project:

- Data drives the page:
  The JSON file became the source of truth.

- Structure affects everything:
  File organization changed paths, imports, debugging, and maintainability.

- Scope lives where data lives:
  The ReferenceError helped me understand where variables actually exist.

- Async code teaches you to think in steps:
  Requests and promises changed how I thought about execution order.

- Modular code is easier to maintain:
  Section files made the project easier to reason about and refactor.

- Clean code is a process:
  Reviewing, refactoring, and fixing mistakes are part of building real projects.

Closing thought:
This project did not make me an expert overnight, but it gave me a real way to measure progress.
-->

<!---------- SLIDE 12 | LIVE DEMO LINK ---------->

<!--
Let the audience see the live demo link and QR code.

Mention:
- This is the deployed version of the resume project
- The live page shows the final result
- The page is powered by structured data and JavaScript rendering

Give people a moment to scan the QR code.

Suggested line:
If you want to see the finished resume as a user would see it, this is the live page.
-->

<!---------- SLIDE 13 | GITHUB REPO LINK ---------->

<!--
Let the audience see the GitHub repo link and QR code.

Mention:
- The GitHub repo shows the source code
- The commit history reflects the learning process
- The repo shows the project structure, modules, data file, and refactor history

Suggested line:
The live demo shows the result. The repo shows the process.

Handoff to Ryan to share his approach for solving the same problem.

Leave time for Q/A after Ryan finishes.
-->