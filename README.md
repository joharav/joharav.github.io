Hello!

This is a repository oriented to serve as a academic page, based on the template of  https://academicpages.github.io/

This is an interactive process and maybe this page will be changing during a span of time and I will be improving it recurrently.

Thank you!

## Publishing and indexing

The public academic content lives in `_pages/about.md`, which generates `/`.
Its canonical URL is `https://joharav.github.io/`. Keep the homepage content,
styles, research descriptions, external links, and downloads unchanged when
maintaining indexing settings.

- The former CV, publications, research, teaching, coauthors, and terms pages
  have `published: false`. Their Markdown is retained as source material.
- Research, publications, teaching, and portfolio collections have
  `output: false`; they no longer generate standalone pages.
- `_posts` is empty (the old example posts were removed previously). Posts,
  drafts, `markdown_generator`, and the unused talk map and authoring scripts
  are excluded from production. The remaining template draft has been deleted.
- Navigation uses the existing `/#research-projects` anchor and the current CV
  PDF. The homepage continues to hide its masthead.
- `/sitemap/` stays available for the existing homepage footer link. It lists
  only intended published pages and has `noindex, follow`, as does the custom
  404 page. The SEO include now honors `noindex`.
- `jekyll-sitemap` generates `/sitemap.xml` with only the homepage. Downloads
  remain accessible, but `assets/files` is excluded from the sitemap using
  front matter defaults. The generated `robots.txt` advertises the sitemap
  without blocking crawling.
- Removed pages and former `/about/`, `/about.html`, and `/resume` aliases have
  no redirect replacements. GitHub Pages can serve `/404.html` with a 404 status
  for missing URLs. Do not add a catch-all homepage redirect or block these
  URLs in `robots.txt`.

### Retired URLs

These standalone routes are absent from the cleaned build (including their
generated `.html` or `index.html` variants):

```text
/cv/
/publications/
/research/
/teaching/
/coauthors/
/terms/
/publications/Nowcasting
/publications/TransactionalDedollarization
/research/Nowcasting
/research/TransactionalDedollarization
/research/TurnoverInnovation
/teaching/Graduate
/teaching/Undergraduate
/markdown_generator/
/talkmap/map.html
/about/
/about.html
/resume
```

The indexed “Jupyter notebook markdown generator” heading comes from
`markdown_generator/readme.md`, which was published at `/markdown_generator/`.
Older template routes such as `/markdown/`, `/markdown.html`, `/md/`, and the
sample `/posts/.../blog-post-.../` URLs also remain absent.

### Build and deployment checks

```sh
JEKYLL_ENV=production bundle exec jekyll build --safe
```

The intended HTML output is `index.html`, `sitemap/index.html`, and `404.html`.
The sitemap should contain exactly `https://joharav.github.io/`. Keep the CV,
papers, slides, images, CSS, and JavaScript available at their existing paths.
Deploy a fresh build so obsolete files are removed from the published output.

Cleanup validation compared production builds before and after the change:
the homepage HTML was byte-for-byte identical, all 74 generated asset and image
files were unchanged, every local HTML link and resource resolved, and 51
obsolete URL variants returned HTTP 404 without redirects on a local Jekyll
server. These local checks do not verify a deployment.

### Google Search Console after deployment

1. Confirm that the live homepage and downloads return 200, retired URLs return
   404, and the live sitemap contains only the homepage.
2. In the `https://joharav.github.io/` property, inspect the homepage, run
   **Test live URL**, and select **Request indexing**.
3. Under **Sitemaps**, submit or resubmit `sitemap.xml`.
4. Inspect a few exact obsolete URLs using **Test live URL** to confirm Google
   sees the 404. Monitor the **Page indexing** report as Google recrawls them;
   a retired URL reported as **Not found (404)** is expected.
5. For faster temporary hiding, optionally use **Removals → New request →
   Temporarily remove URL** for each exact obsolete URL. Keep the permanent 404
   in place; temporary removals alone do not permanently remove a page. Do not
   submit the homepage or retained PDF downloads for removal.

Google controls sitelinks and recrawl timing. Deploying this cleanup or
requesting indexing does not guarantee when search results will change.

References: [Google recrawl requests](https://developers.google.com/search/docs/crawling-indexing/ask-google-to-recrawl),
[Search Console removals](https://support.google.com/webmasters/answer/9689846),
[Google sitelinks](https://developers.google.com/search/docs/appearance/sitelinks),
and [GitHub Pages custom 404 pages](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-custom-404-page-for-your-github-pages-site).
