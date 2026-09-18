# Ahmed Iqdymat — Academic & Research Website

A personal academic profile for an Automation & Control Systems Engineer and PhD Candidate in Systems Engineering. The website centres on qualifications, research interests, publications, and professional experience. Research implementations remain in their separate GitHub repositories.

## Technology stack
Astro static generation, semantic HTML, responsive CSS, and small client-side scripts. No backend, analytics, external fonts, or runtime API dependencies. Node.js 24 and npm are used in CI.

## Repository delivery format
The complete editable Astro source is in `website-source.zip`. The GitHub Pages workflow unpacks it only inside its temporary build workspace and deploys the validated output. It has read-only repository access and does not modify repository files.

Clone or download the repository, then extract the archive before development:
```sh
unzip -o website-source.zip
```
The archive includes the data files, components, styles, scripts, lockfile, and supplied portrait.

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

The included GitHub Actions workflow builds and validates the site and deploys the `dist` directory with the official Pages actions. In repository Settings → Pages, select **GitHub Actions** as the build source. Push to `main` or run the workflow manually. `configure-pages` attempts initial Pages enablement; if the repository token cannot enable Pages, an owner must select GitHub Actions in Settings once.

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

## Update a personal portrait
Place an authorised portrait at `public/images/ahmed-iqdymat.webp`, then set `profile.portrait` to `/images/ahmed-iqdymat.webp`. The layout displays it at 176 × 176 on desktop and 120 × 120 on mobile. The supplied portrait is currently stored at `public/images/ahmed-iqdymat.jpeg`. No stock or generated identity photo is used.

## CV and privacy
`/cv/` provides an English academic CV with a print/save-as-PDF button. The original supplied CV is not published because it includes personal contact details. No nonexistent download is linked. A reviewed public PDF can be added to `public/` later.

## Academic integrity
The UR3e research is described as simulation-based evaluation and sim-to-sim integration. The ROS 2 fake-hardware study is distinct from physical robot validation. Journal DOI `10.3390/info17090885` and software DOI `10.5281/zenodo.22817235` remain separate. No citation metrics, awards, grants, teaching, supervision, or memberships are inferred.

## Accessibility and maintenance
Keyboard focus, skip link, semantic headings, labelled navigation, publication-filter state, copy feedback, system/manual dark mode, reduced-motion support, and print styles are included. Regularly review external profile links and update the lockfile deliberately. Do not include source CVs, private correspondence, credentials, or unpublished documents in the public repository.

## Publish content updates
After extracting the source, edit the structured data and run the build and checks above. Recreate `website-source.zip` from the source files, excluding `node_modules`, `dist`, `.git`, and private documents. Upload the replacement archive to the repository root. The existing root `.github/workflows/deploy.yml` builds and deploys it automatically. For conventional Git maintenance, extract the source into the repository, remove the temporary unpack step from the workflow, and commit the individual source files instead.
