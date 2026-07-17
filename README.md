# Resume JS Presentation

Slidev deck for the NorfolkKS talk on Build Your Resume with JavaScript.

## Presentation Overview

This presentation walks through the idea, learning process, project structure, refactor decisions, bugs, and takeaways from building a JavaScript resume.

Topics covered include:

- Why a live resume can support a traditional resume
- Using one data source to drive a web page
- Fetching JSON with JavaScript
- Rendering sections dynamically
- Refactoring into modules
- Separation of concerns
- Debugging common beginner JavaScript issues
- Lessons learned from building and presenting a real project

## Pre-Talk Checklist

Use this checklist before publishing or presenting the deck.

### Content Review

- [ ] Review every slide in presentation mode.
- [ ] Confirm slide order matches the planned talk flow.
- [ ] Replace placeholder text in the Takeaways slide.
- [ ] Confirm the live demo URL is correct.
- [ ] Confirm the GitHub repository URL is correct.
- [ ] Check all dates, event names, and title text.
- [ ] Review speaker notes in `NOTES.md`.
- [ ] Make sure the final slide is ready for audience questions.

### Demo Readiness

- [ ] Test the live demo before the talk.
- [ ] Prepare a backup screenshot or recording.
- [ ] Keep a local fallback ready in case the deployed site is unavailable.

### Build Check

- [ ] Run a production build with `pnpm run build`.
- [ ] Confirm the build completes without errors.
- [ ] Verify the background image loads correctly.

### Delivery Prep

- [ ] Practice the talk against the 35-minute target.
- [ ] Rehearse transitions between slides.
- [ ] Practice the live demo path.
- [ ] Prepare a short intro for yourself and the project.
- [ ] Prepare a recovery line if the demo fails.
- [ ] Leave time for questions at the end.

## Day-Of Checklist

Use this checklist shortly before presenting.

### Local Setup

- [ ] Run the deck locally with `pnpm run dev`.
- [ ] Open the presentation at `http://localhost:3030`.
- [ ] Open the live demo URL.
- [ ] Open the GitHub repository URL.
- [ ] Confirm all links load correctly.

### Room and Display Check

- [ ] Test the deck in the browser you will present from.
- [ ] Confirm presenter display, projector, or screen sharing works.
- [ ] Check text size and contrast on the presentation screen.
- [ ] Confirm audio/video setup if needed.
- [ ] Confirm internet access is available.
- [ ] Keep the local fallback ready.

### Final Prep

- [ ] Close unnecessary browser tabs and apps.
- [ ] Disable notifications.
- [ ] Put your phone on silent or Do Not Disturb.
- [ ] Have water nearby.
- [ ] Start on the opening slide before the audience is ready.
- [ ] Take a breath before beginning.

## Getting Started

### Prerequisites

Install Node.js and pnpm before running the project.

This project is designed to run as a Slidev deck and uses pnpm scripts for local development, production builds, and exports.

### Install Dependencies

```bash
pnpm install
```

### Start the Development Server

```bash
pnpm run dev
```

Then visit:

```text
http://localhost:3030
```

The development command opens the presentation automatically in your browser.

## Available Scripts

### Development

```bash
pnpm run dev
```

Starts the local Slidev development server.

### Production Build

```bash
pnpm run build
```

Builds the presentation for production and outputs the static site to:

```text
dist/
```

### Export

```bash
pnpm run export
```

Exports the Slidev deck using Slidev’s export tooling.

> Note: Exporting may require additional browser tooling depending on the selected export format.

## Deploy

This project includes configuration for both Netlify and Vercel.

### Netlify

Netlify builds the project with:

```bash
pnpm run build
```

The production output is served from:

```text
dist/
```

### Vercel

Vercel builds the project with:

```bash
pnpm run build
```

The production output directory is:

```text
dist/
```

## Recommended Workflow

Install dependencies:

```bash
pnpm install
```

Start development:

```bash
pnpm run dev
```

Make edits in `slides.md`, then build before deployment:

```bash
pnpm run build
```
