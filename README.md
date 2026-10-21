# Developer Portfolio (v5)

A single-page personal portfolio: a home hero, an about section, services, an education and experience flip-book, a GitHub-backed project list, a blog list and a contact form.

**Status:** In progress. The page builds, and a GitHub Actions workflow deploys it to Firebase Hosting on each push to `main`. But the contact form only logs to the console, the chat widget is commented out of the app, the blog entries are placeholder text, and the Clients section is also commented out.

## The problem

A developer needs a portfolio that presents who they are, what they have built and how to reach them. This version uses Create React App and pulls project data from GitHub, so the list stays current without manual edits.

## What it does

- About section with the GitHub profile of the owner, fetched from `api.github.com` (`src/components/About.js`).
- Project section that lists the owner's public repositories from the GitHub API, with a filter and cards (`Portfolio.js`, `PortfolioFilter.js`, `ProjectCard.js`).
- Education and experience displayed as a flip-book with `react-pageflip` (`src/components/Book.js`).
- Services section (`Services.js`, `ServicesCard.js`) and a blog list (`Blog.js`, `BlogCard.js`).
- Contact form with name, email and subject fields and a submit handler (`Contact.js`).

## How it's built

- React 18 with Create React App (`react-scripts` 5). Components are function components in `src/components/`, with one stylesheet in `src/index.scss`.
- `react-github-calendar`, `react-reveal` and `react-typewriter-effect` provide the GitHub activity grid and the animations.
- Shared helpers, such as the scroll-to-bottom function used by the chat widget, live in `src/utils/function.js`.
- Deployment is a GitHub Actions workflow (`.github/workflows/deploy.yml`). It runs `npm ci` and `npm run build`, then deploys hosting to Firebase with a `FIREBASE_TOKEN` repository secret.

## Running it locally

```bash
npm install
npm start      # http://localhost:3000
npm run build  # production bundle in build/
```

Other scripts: `npm test` (react-scripts test runner) and `npm run eject`.

## What's left

- The contact form's `handleSubmit` only calls `preventDefault` and logs the fields. Nothing is sent.
- The chatbot component exists in `src/components/Chatbot.js` but its render is commented out in `App.js`, and it does not respond to input.
- The Clients section is commented out in `App.js`.
- Blog entries are a hard-coded array of placeholder text ("Blog name Lorem ipsum...").
- Testing libraries are installed but there are no test files.
- Both `package-lock.json` and `pnpm-lock.yaml` are committed, so the package manager is not settled.
