# Sayan Khutia — Portfolio

Personal portfolio of Sayan Khutia, a Software Engineer focused on backend and full stack development (Python, FastAPI, Next.js, TypeScript).

**Live:** [i-sayankh.github.io/portfolio](https://i-sayankh.github.io/portfolio)

## Sections

- **Hero** — intro with animated roles and a resume link
- **Skills** — grouped into Frontend, Backend and Others
- **Experience** and **Education** — timeline cards
- **Projects** — filterable project cards with a details view (GitHub and live links)
- **Contact** — email form powered by [EmailJS](https://www.emailjs.com/), with validation and duplicate-submit protection

## Tech stack

- [React 18](https://react.dev) (Create React App)
- [styled-components](https://styled-components.com) for styling, with a dark theme
- [Material UI](https://mui.com) for the alert/snackbar and icons
- [@emailjs/browser](https://www.npmjs.com/package/@emailjs/browser) for the contact form
- [react-router-dom](https://reactrouter.com), [react-scroll](https://www.npmjs.com/package/react-scroll), [typewriter-effect](https://www.npmjs.com/package/typewriter-effect)
- [gh-pages](https://www.npmjs.com/package/gh-pages) for deployment to GitHub Pages

## Project structure

```
src/
  components/     # Hero, NavBar, Skills, Experience, Education, Projects, ProjectDetails, Contact, Footer, Cards
  data/
    constants.js  # all portfolio content (bio, skills, experience, education, projects)
  utils/          # theme definitions
  images/         # local images
public/           # static assets and index.html
```

## Getting started

```bash
npm install
npm start
```

Open [http://localhost:3000](http://localhost:3000). The page reloads as you edit.

## Updating the content

Everything shown on the site comes from [`src/data/constants.js`](src/data/constants.js):

| Export | Controls |
| --- | --- |
| `Bio` | name, roles, description, resume and social links |
| `skills` | skill groups and their icons |
| `experiences` | work experience cards |
| `education` | education cards |
| `projects` | project cards (title, date, description, image, tags, `github`, `webapp`) |

To add a project, add an object to the top of `projects` with a unique `id`. Use a direct image URL (for example a raw GitHub screenshot) and leave `webapp` as `null` if there is no live demo.

## Contact form (EmailJS)

The form in [`src/components/Contact/index.js`](src/components/Contact/index.js) sends mail through EmailJS. Its service ID, template ID and public key are set in that file. The public key is safe to expose, but you should protect the account:

- In the EmailJS dashboard, restrict allowed domains to `localhost` and `i-sayankh.github.io`, and consider enabling reCAPTCHA.
- The template must use the variables `from_email`, `from_name`, `subject` and `message`.
- If sending fails with `412 Invalid grant`, the Gmail connection has expired. Reconnect it under **Email Services** in the EmailJS dashboard.

## Scripts

| Script | Description |
| --- | --- |
| `npm start` | Start the dev server |
| `npm run build` | Build for production into `build/` |
| `npm run deploy` | Build and publish `build/` to the `gh-pages` branch |
| `npm test` | Run the test runner |

## Deployment

The site is hosted on GitHub Pages from the `gh-pages` branch. Pushing to `master` does not update it. After merging changes, run:

```bash
npm run deploy
```

It usually takes a minute or two to go live. Hard-refresh (Ctrl+Shift+R) to bypass the browser cache.
