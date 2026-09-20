# Academic website review — 20 September 2026

## Implemented
- Preserved Astro, portrait, navy/teal identity, responsive sidebar, light/dark mode, publication filters, citation copying, BibTeX, print, canonical URL and GitHub Pages.
- Unified the hero and CV name as AHMED IQDYMAT with restrained weight and spacing; reduced phone hero spacing.
- Broadened the biography and research themes. Professional experience now precedes research interests and publications.
- Added Languages and Academic Profiles sections; numbering and navigation share one data source.
- Added Python (Basic), consistent with the supplied CV, and Systems Engineering to expertise.
- Added the authorised personal/professional email beside the existing institutional email, with mailto links and explicit labels.
- Linked official university names and Al Jebrini. Kept the existing direct Scopus Author ID link unchanged.
- Verified and added the 2023 DOI, 10.1109/CSCS59211.2023.00011, from IEEE. Added the direct IEEE publisher page for the sim-to-sim paper. Ordered the September 2025 conference before the January 2025 journal paper.
- Replaced long publication DOI controls with concise actions. Full identifiers remain in citations, structured data and printed output. Journal and software DOIs remain separate.
- Retained scientific limitations beside the relevant papers, including the separate fake-hardware pipeline. No physical UR3e validation or SAC superiority claimed.
- Prepared `profile.cvPdf` (null) for a reviewed public PDF at `/cv/Ahmed-Iqdymat-Academic-CV.pdf`; no broken download or private PDF was published.
- Added a reusable AcademicProfileLinks component and explicit allowlist packaging script.

## Evidence and unresolved conflicts
- The supplied academic identity document supports the broad academic/engineering biography.
- The supplied CV supports the historical degrees, industrial positions, dates, and Python at Basic level. Employment descriptions were preserved without inflation.
- PhD: supplied CV says 2022–Present under education but December 2021–Present under research. The proposed 2021 start was not imposed; existing In progress remains. An authoritative enrolment record or clarification is needed to resolve the discrepancy.
- French: supplied CV says Intermediate, while the proposal says Basic. Under the requested evidence hierarchy, Intermediate is displayed. Arabic Native and English Advanced are also in the CV; Romanian Basic is newly supplied by the owner. German is not published.
- Journal metadata was checked against supplied publisher PDFs. Direct publisher access through the research tool was unavailable, so no new unsupported metadata was added.
- The proposed TB Lock technical page visibly contains unrelated pharmaceutical advertising. Employer identity matches, but linking that page would be poor visitor UX. Employer text remains without a link.

Sources:
- https://ieeexplore.ieee.org/document/10214750/ — 2023 title and DOI
- https://ieeexplore.ieee.org/document/11322052/ — sim-to-sim title, 4–6 September 2025 conference
- https://upb.ro/ — institutional identity
- https://www.univ-dbkm.dz/en/home/ — university identity
- https://www.al-jebrini.com/about — employer identity
- https://tblock.ps/en/Technical-Info — employer identity, inappropriate unrelated content observed

## Second review and additional repairs
- Light-theme teal contrast against the page background was 4.47:1. Darkened it slightly from #087f83 to #08797d to exceed 4.5:1 while retaining the visual identity.
- Added a lighter focus outline on navy navigation for visibility.
- Escape previously moved focus to the menu even when closed; limited this to an open mobile menu.
- Made CV DOI references actual links, not plain URL text.
- Kept full DOI text available for print after shortening screen controls.
- Updated the privacy test to allow only the two approved emails, rather than prohibit personal email categorically.
- Updated publication checks to support future records instead of hard-coded record counts.
- Corrected stale portrait documentation. Removed the temporary viewport harness before building the upload.

## Validation before deployment
- `npm ci`: PASS.
- `npm run build`: PASS.
- `npm test`: PASS; all HTML routes, local links and section targets, citation exports, metadata JSON, sitemap, robots, approved emails, private-data guards and PDF-control state.
- Browser: homepage and CV at 390, 768, 1024 and 1440px frame widths; content widths 375, 753, 1009, 1425px respectively. No horizontal overflow within any tested page viewport.
- Mobile menu opens, closes on a link and dismisses with Escape. Journal/conference filters each show two items; all shows four. Theme toggle changes light/dark state.
- Desktop hero, mobile hero, mobile publications, contact area and HTML CV visually inspected.
- Contrast checked for principal text, links, button and dark-theme colours. Semantic headings, portrait alt text, focus rules, reduced-motion and print rules reviewed. This is not a full WCAG certification or Lighthouse score.
- Browser console included extension-origin metadata messages; these were not site JavaScript failures.
- External URLs compared with owner-supplied identifiers and authoritative records. Some academic sites restrict automated retrieval (Scopus, LinkedIn, DOI resolver and direct MDPI pages); their reachability is not represented as independently passed. Google Scholar search resolves Ahmed's matching profile. ORCID resolves; its dynamic record was not fully readable.

## Source structure and deployment decision
The archive contains all editable source and the portrait. Conventional Git source would improve diffs, but the GitHub integration returns a write-permission 403 and local Git has no push credential. Preserve the existing atomic archive upload and working deployment workflow rather than perform a partial source migration. No token, permission expansion, force push or self-modifying workflow was introduced. The separate research repository was not modified.

Deployment and live verification are reported with the final run result after upload; a local PASS alone is not a deployment claim.

## Free URL investigation
| Option | Advantages | Disadvantages / decision |
| --- | --- | --- |
| Existing ahmed-iqdymat.github.io | Already deployed, name-based, HTTPS, free for this public repository, independent of university affiliation | Hosting-provider suffix; retained and recommended |
| A name-based pages.dev subdomain | Free Pages plan supports static sites; HTTPS; familiar static deployment | New hosting setup and public-address migration without an academic identity advantage; name availability not reserved or assumed |
| Institutional profile/address | Clear university association if the institution provides one | No verified entitlement to a personal hosting address, and continuity depends on affiliation; not a replacement recommendation |

Official documentation:
- https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages
- https://developers.cloudflare.com/pages/platform/limits/
- https://developers.cloudflare.com/pages/configuration/custom-domains/

No address change, domain purchase, subscription or hosting migration was performed. A personally owned custom domain could provide future provider portability and a shorter address, but adds renewal cost and is optional.

## Privacy
Only the two authorised emails are public. No telephone, residential address, credentials, private CV, source academic documents or correspondence included in the website/source archive. Portrait preserved; its visible appearance is unchanged. Structured data uses only the institutional email. No analytics added.

## Owner confirmation and PDF update workflow — 20 September 2026
The owner has now confirmed 2021 as the PhD start year and Intermediate French. This resolves the earlier factual uncertainties; the website displays 2021–Present, In progress.

Added `/cv/update/`, accessible from the Academic CV page, with an authenticated GitHub upload action and instructions. Uploading the consistently named public PDF to the repository root triggers the existing deployment and activates the stable download URL automatically. The PDF remains independent of the source archive. No private source CV was uploaded. PDF signature, size and completeness checks reject obviously invalid uploads; they do not certify document content.
