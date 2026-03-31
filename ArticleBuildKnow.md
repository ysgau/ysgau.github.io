## AIMS Fellows Article Build Knowledge

This file defines how new articles should be added to this repository.

## Site Structure

- `index.html`
	homepage / research portal
- `articles/`
	article summary / landing pages
- `SAHRE_html/`
	full rendered article pages
- `SHARE_md/`
	source markdown files

### Important rule
- `index.html` is not a full article page.
- Do not paste complete article bodies into the homepage.
- Even though `SAHRE_html` looks like a typo, treat it as the canonical directory name.

## Homepage Contract

The homepage should function as:
- brand entry
- topic explorer
- featured research gateway
- latest article list
- about / publishing note

### Homepage article card minimum fields
Every article shown on the homepage should have this content contract, even if implemented directly in static HTML:
- `title`
- `summary`
- `publishedDate`
- `topics[]`
- `summaryUrl`
- `fullArticleUrl`
- `featured` boolean

### Homepage linking rule
- Main CTA should prefer the summary page in `articles/`
- Secondary CTA may link directly to the full article in `SAHRE_html/`

## Summary Page Contract

Files in `articles/` are summary pages, not full article pages.

Each summary page must include:
- article title
- short abstract / summary
- 3-5 key takeaways
- use cases / applicable scenarios
- keyword tags
- link back to homepage
- CTA to the full article in `SAHRE_html/`

### Summary page metadata rule
- `canonical` must point to the public `articles/...html` URL
- `og:url` must point to the public `articles/...html` URL
- Summary pages may use `og:type=article`
- The visible page copy must make it clear that the page is a summary / abstract page

## Full Article Page Contract

Files in `SAHRE_html/` are the full rendered reading pages.

Each full article page must:
- load or render the complete article content
- retain article metadata
- use its own `SAHRE_html/...html` public URL for `canonical` and `og:url`

## Metadata Standard

### Homepage
- `title`
- `meta description`
- `meta keywords`
- `meta robots`
- `canonical`
- Open Graph:
	`og:locale`, `og:type=website`, `og:site_name`, `og:title`, `og:description`, `og:url`
- Twitter:
	`twitter:card`, `twitter:title`, `twitter:description`
- JSON-LD:
	`WebSite`, and when needed `mainEntity` as `ScholarlyArticle`

### Article and summary pages
- `title`
- `meta description`
- `meta keywords`
- `meta robots`
- `canonical`
- Open Graph:
	`og:locale`, `og:type=article`, `og:site_name`, `og:title`, `og:description`, `og:url`
- Twitter:
	`twitter:card`, `twitter:title`, `twitter:description`
- JSON-LD:
	`Article` + `ScholarlyArticle`

### Metadata writing rules
- Use Traditional Chinese as the primary language
- Use `AIMS Fellows` as default `author` and `publisher`
- `inLanguage = zh-TW`
- `meta description` should summarize:
	topic, scope, and application context
- `meta keywords` should mix Chinese and English keywords
- Do not stuff unrelated keywords

### JSON-LD minimum fields
- `headline`
- `alternativeHeadline` when useful
- `description`
- `url`
- `mainEntityOfPage`
- `inLanguage`
- `datePublished`
- `dateModified`
- `author`
- `publisher`
- `about`
- `keywords`
- `isPartOf`

## Workflow For New Articles

1. Add the markdown file to `SHARE_md/`
2. Create the summary page in `articles/`
3. Create the full rendered page in `SAHRE_html/`
4. Apply metadata to both pages
5. If the article is featured, update homepage metadata and homepage article card
6. Validate `canonical`, `og:url`, dates, and page links

## URL Mapping Rule

- Markdown:
	`SHARE_md/<article-file>.md`
- Summary page:
	`articles/<article-file>.html`
- Full article page:
	`SAHRE_html/<article-file>.html`
- Public summary URL:
	`https://aimsfellows.ai/articles/<article-file>.html`
- Public full article URL:
	`https://aimsfellows.ai/SAHRE_html/<article-file>.html`

## Short Prompt For AI Agent

```text
請依據 ArticleBuildKnow.md 與 README 的規則，為新文章同時處理：
1. `articles/` 摘要頁
2. `SAHRE_html/` 全文頁
3. 若為 featured article，更新 `index.html` 的 metadata 與首頁文章卡

請直接修改檔案，不只給建議，並檢查：
- canonical
- og:url
- datePublished
- dateModified
- 首頁導流是否先到摘要頁
```
﻿
