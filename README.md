# Hire Heroes (Astro)

Fiverr affiliate blog. Static site, no database, minimal JavaScript.

## Before you publish (required)
1. `src/config/affiliate.ts`: paste your verified Fiverr affiliate URL(s). Until then links show a yellow "not configured" marker and go nowhere.
2. `src/config/site.ts`: set `contactEmail`. Optional: `gaMeasurementId` (GA4; loads only after the visitor accepts).
3. `src/pages/privacy-policy.astro` and `terms.astro` are TEMPLATES (noindex). Write real content, then delete `noindex` on the `<Base ...>` line.
4. Set `SITE_URL` (Vercel > Settings > Environment Variables) or edit `astro.config.mjs` to your real domain. Sitemap, canonicals and robots.txt depend on it.
5. Hosting: confirm Vercel's current Hobby plan terms allow a commercial/affiliate site. If not, use Cloudflare Pages (build `npm run build`, output `dist`) after checking its terms.

## Run locally
    npm install
    npm run dev       # http://localhost:4321
    npm run build     # production build into dist/

## Deploy
1. Create a GitHub repo and upload this folder (GitHub web: Add file > Upload files; or `git push`).
2. Vercel > Add New Project > import the repo. Framework: Astro (auto-detected). Deploy.
3. Every commit to `main` redeploys automatically.

## Create an article (works in the GitHub mobile browser)
1. Repo > `src/content/blog/` > Add file > Create new file.
2. Name it `your-article-slug.mdx` (the name becomes the URL: `/blog/your-article-slug/`).
3. Start with this frontmatter:

       ---
       title: "Title under 70 characters"
       description: "50 to 160 characters."
       category: seo-digital-marketing
       pubDate: 2026-10-20
       hasAffiliateLinks: true
       draft: false
       ---
       import AffiliateLink from '../../components/AffiliateLink.astro';

4. Write in Markdown. Add an affiliate link with `<AffiliateLink to="seo">link text</AffiliateLink>`.
5. Commit. The site redeploys in about a minute. If the build fails, Vercel's Deployments tab shows the error (usually a frontmatter typo).
Set `draft: true` to hide an article. Add `updatedDate` only when you really update it.

## Update an affiliate link
Edit the matching key in `src/config/affiliate.ts`. All articles using that key update.
Article-specific link: `<AffiliateLink href="https://your-verified-url">text</AffiliateLink>`.

## Change a category
Change `category:` in the article to one of the slugs in `src/data/categories.ts`. Edit names/descriptions there.

## Limitations
- Phone editing is text-only; images go in `public/images/` via Upload files and are referenced as `/images/name.jpg`.
- The GitHub mobile editor has no live preview; check the Vercel preview URL.
- This project has NOT been built or Lighthouse-tested yet; run `npm run build` and fix any error before launch.

## Not included yet
Images/OG images, the remaining 10 articles, the 30-day roadmap, and the post-launch SEO checklist.
