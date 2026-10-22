# Samuel Dolle — Portfolio

## Stack

- React and Vite
- Tailwind CSS 4 for layout, spacing, and responsive utilities
- Bootstrap 5 and React Bootstrap for the accessible modal, mobile offcanvas navigation, forms, alerts, and buttons
- Bootstrap Icons, original transparent frontend artwork, and custom CSS animations
- Optional EmailJS integration

Tailwind utilities use the `tw:` prefix. Bootstrap and custom styles have explicit cascade layers, and Tailwind Preflight is omitted so the two frameworks do not apply competing resets.

The transparent frontend artwork was created with built-in image generation; its saved prompt and provenance are in [assets/frontend-art.prompt.txt](assets/frontend-art.prompt.txt).

## Run

Use Node.js 22.12+ (Node 24 LTS recommended).

```sh
npm ci
npm run dev
```

`npm run build` creates the production site in `dist/`. Use `npm run preview` to check it locally. Vite uses relative asset paths, so the build can be served at the repository subpath on GitHub Pages or the root of another static host.

## Content

Edit `src/content.js` to update the introduction, contact links, skills, and projects:

1. Marvel Champions Digital — community build with a Windows download link to GitHub Releases
2. Netflix Clone
3. Summarist
4. NFT Marketplace
5. Skinstric

The Marvel image comes from the project's repository documentation. The other four images are screenshots of the actual live projects; Netflix uses Sam's supplied homepage screenshot. Marvel's description credits the original Irefrixs project, Summarist's account/subscription flows are described as a demo, NFT Marketplace credits the supplied Ultraverse design and Frontend Simplified course, and Skinstric's results are described as simulated.

Marvel's featured statistics were verified on October 22, 2026: 29 GitHub stars and 644 cumulative Windows ZIP downloads, excluding artwork and checksum assets. The site uses the conservative “600+ Windows downloads” label; this counts downloads, not unique players.

The original starter assets remain in Git for reference. Its sample resume and placeholder project links are not displayed. Set `profile.resume` to a real resume URL to enable the resume link.

## Contact

Without EmailJS configuration, the validated contact form's **Compose email** button opens the visitor's email application with a draft to `sam_dolle@outlook.com`. A direct email link is available beneath the button. The site does not claim the draft was sent.

To enable direct sending, copy `.env.example` to `.env.local` and set the EmailJS service ID, template ID, and public key. Configure the template recipient in EmailJS and use the form variables `user_name`, `user_email`, and `message`. These are public browser integration identifiers; do not put email account passwords or private service credentials in Vite environment variables.

## Interaction and accessibility

- Staggered hero entrance, original frontend artwork with a slide-in entrance, gentle floating, pointer-responsive tilt, hover lift, and scroll indicator
- Full-colour project screenshots in window frames, with alternating image/text columns on desktop
- Project descriptions, technology lists, and links always visible; stacked layouts on tablets and phones
- Light/dark preference saved in local storage
- Focus-trapped, keyboard-dismissible Bootstrap dialog and mobile navigation
- Form labels, input validation, status announcements, and honest email-draft fallback
- Decorative hero artwork is hidden from assistive technology and omitted on phone layouts
- Reduced-motion preference respected; hero artwork motion and hover transforms are disabled

## Checks

`npm run build` is run in GitHub Actions on pushes and pull requests. Browser QA covers desktop and phone layouts, image loading, modal open/close, focus restoration, theme persistence, project details, and form validation.

## Deployment

The live portfolio is hosted on GitHub Pages at [samdolle.dev](https://samdolle.dev/). The original [sdolle1775.github.io/Portfolio](https://sdolle1775.github.io/Portfolio/) URL redirects to the custom domain.

Every push to `main` builds and deploys `dist/` to GitHub Pages. The workflow can also be run manually from GitHub Actions. Other branches and pull requests only run the build check. Repository Settings → Pages uses **GitHub Actions** as its publishing source.

The custom domain is configured in GitHub Pages settings. Porkbun DNS uses an apex `ALIAS` and a `www` `CNAME`, both pointing to `sdolle1775.github.io`. Keep the `_github-pages-challenge-sdolle1775` TXT record to preserve GitHub's domain ownership verification. The Actions deployment does not require a `CNAME` file in the repository.
