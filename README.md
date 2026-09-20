# Ahmed Iqdymat — Academic & Research Website

A personal academic profile for an Automation & Control Systems Engineer and PhD Candidate in Systems Engineering. The website centres on qualifications, research interests, publications, and professional experience. Research implementations remain in their separate GitHub repositories.

## Technology stack
Astro static generation, semantic HTML, responsive CSS, and small client-side scripts. No backend, analytics, external fonts, or runtime API dependencies. Node.js 24 and npm are used in CI.

## Source delivery and local development
The complete editable source remains in `website-source.zip`. Extract it without replacing the working root deployment workflow:
```sh
unzip -o website-source.zip -x '.github/*'
```
The archive-based workflow is intentionally retained. The current GitHub connector lacks source-write permission and local Git has no push credentials. A conventional source migration should use an authenticated Git checkout, preserve the archive through a verified deployment, and remove the runner extraction step only when all editable files and assets are committed together.

## Local development
```sh
npm ci
npm run dev
```
## Build and checks
```sh
npm run build
npm test
npm run preview
```
Production output is `dist/`. Checks cover internal routes and anchors, metadata, citation files, and accidental inclusion of private contact details.

## Deployment
Target public repository: `AHMED-IQDYMAT/AHMED-IQDYMAT.github.io`.
Target URL: https://ahmed-iqdymat.github.io/

The included GitHub Actions workflow builds and validates the site and deploys the `dist` directory with the official Pages actions. In repository Settings → Pages, select **GitHub Actions** as the build source. Push to `main` or run the workflow manually. The existing root workflow has `contents: read`, `pages: write`, and `id-token: write`; it never commits source files back to the repository.

## Content structure
- `src/data/profile.js`: identity, affiliation, education, industrial experience, research themes, technical expertise, profile links, and software identifier.
- `src/data/publications.js`: publication records and shared citation/BibTeX functions.
- `src/components/`: reusable section and publication components.
- `src/layouts/Layout.astro`: navigation, metadata, structured data, and interactions.
- `src/styles/global.css`: light/dark palettes, responsive layout, and print styles.
- `src/pages/`: academic profile, public CV, 404, sitemap, and generated citation exports.

## Add a publication
Add an object to `publications` with a unique `id`, `year`, `type` (`Journal Article` or `Conference Paper`), `title`, `authors` array, and `venue`. Optional fields are `doi`, `url`, `volume`, `issue`, `article`, `published`, `note`, and `software`. Keep newest records first. Do not invent missing metadata. Citation downloads and structured data update automatically.

## Add a research project
Keep project documentation and source code in the appropriate separate repository. To connect research software to a publication, update the `software` record in `profile.js` and set the matching publication's `software` flag. For additional software records, convert this record into a keyed collection and reference its key from each publication. Do not add project showcase pages unless the scope changes.

## Update profile information
Edit `src/data/profile.js`, then build and test. Education dates must match verified records. The PhD start year is intentionally omitted because the supplied CV has differing education and research dates; status is **In progress**. Never use Dr. or imply the degree has been awarded.

## Portrait
The supplied image is at `public/images/ahmed-iqdymat.jpeg`, referenced by `profile.portrait`. Preserve the authorised photograph when updating the source. It displays at 176px on desktop and 104px on small phones.

## CV and privacy
`/cv/` is an English academic CV with Print / Save as PDF. `profile.cvPdf` is `null`, so no PDF download is rendered. When an approved public PDF is supplied, place it at `public/cv/Ahmed-Iqdymat-Academic-CV.pdf`, set `profile.cvPdf` to `/cv/Ahmed-Iqdymat-Academic-CV.pdf`, and update `profile.updated`. The build check should then require the real PDF rather than the currently disabled button.

Only the two explicitly authorised email addresses are published. Do not publish the original private CV, telephone numbers, residential information, credentials, or correspondence. Languages and Python proficiency follow reviewed records; unresolved factual conflicts are documented in REVIEW.md.

## Publish content updates
Run the build and tests, then `python3 scripts/package-source.py`. Upload the resulting `website-source.zip` to the repository root. The existing workflow extracts it into its temporary workspace, builds, tests, and deploys. This packaging script uses an explicit source allowlist and excludes private documents, dependencies, build output, and temporary QA files.

## Academic integrity
The UR3e research is described as simulation-based evaluation and sim-to-sim integration. The ROS 2 fake-hardware study is distinct from physical robot validation. Journal DOI `10.3390/info17090885` and software DOI `10.5281/zenodo.22817235` remain separate. No citation metrics, awards, grants, teaching, supervision, or memberships are inferred.

## Accessibility and maintenance
Keyboard focus, skip link, semantic headings, labelled navigation, publication-filter state, copy feedback, system/manual dark mode, reduced-motion support, and print styles are included. Regularly review external profile links and update the lockfile deliberately. Do not include source CVs, private correspondence, credentials, or unpublished documents in the public repository.
