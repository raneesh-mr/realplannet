# Real Plannet Blog — How It Works

Static HTML. No build step, no Jekyll, no dependencies. Adding a post is copy, fill, link.

---

## Files

| File | Purpose |
|---|---|
| `blog.css` | **All styling, shared by every page.** Never write styles inside a post. Change it here once and every post updates. |
| `index.html` | Listing page + category filter + `Blog` schema |
| `_TEMPLATE.html` | Copy this to start a post. Underscore prefix keeps it visually separate — it's not linked anywhere. |
| `*.html` | The posts |

---

## Adding a post — 6 steps

1. **Copy** `_TEMPLATE.html` → `your-slug.html`
   Slug rules: lowercase, hyphens, no dates, no stop-words. `choosing-a-degree-without-guessing.html` not `2026-08-blog-post-1.html`. The URL is permanent — changing it later costs you every link and ranking it earned.

2. **Replace every `{{PLACEHOLDER}}`.** Search for `{{` before you ship — one missed placeholder is visible to every reader.

3. **Add a card to `index.html`** in the `<div class="posts">` block, newest first:
   ```html
   <a class="card" href="/blog/your-slug.html" data-cat="career">
     <span class="card-tag">Career</span>
     <h2>Your headline</h2>
     <p>Two sentences that make the problem feel familiar.</p>
     <div class="card-meta"><span>7 min read</span><span>Aug 2026</span><span class="card-arrow">→</span></div>
   </a>
   ```
   `data-cat` must be one of: `career` · `wealth` · `cv` · `digital`

4. **Add it to the `blogPost` array** in `index.html`'s JSON-LD at the bottom.

5. **Add the URL to `/sitemap.xml`.**

6. **Submit in Bing Webmaster Tools** → URL Submission. Bing indexes new URLs far faster than Google and feeds ChatGPT and Copilot.

---

## Adding a new product category

When a fifth product launches:

1. Add a filter button in `index.html`:
   ```html
   <button class="cat" data-cat="newproduct">New Product</button>
   ```
2. Use `data-cat="newproduct"` on that product's post cards.

That's the whole change. The filter script reads `data-cat` off the DOM — no JS edit needed.

---

## Writing rules (Brand Guidelines v1.0, section 05)

**We are:** confident not arrogant · direct and transparent · warm but professional · local · premium without the enterprise price tag

**We are not:** salesy · corporate · vague · apologetic · generic

Applied to posts:

| Do | Don't |
|---|---|
| First sentence carries the point | "In today's fast-paced world…" |
| Specific numbers, verified | Estimated or rounded-up figures |
| One pull quote per post | Three — it dilutes all of them |
| One product CTA, at the end | Product mentions scattered mid-article |
| An honest caveat before the CTA | Claiming the product solves everything |
| Tables for contrasts | Walls of prose where a table would do |

**Two hard rules:**

- **Never invent a statistic.** If you don't have the number, write around it. One fabricated figure destroys the credibility of every real one on the site. The Sky Rope cost figures (₹5,175 → ₹528) are client-supplied and approved — that's the standard.
- **The post must be useful even if nobody clicks the CTA.** If it only works as a funnel, it won't get read, linked or cited.

---

## Why this format helps AI visibility

The blog exists to get `realplannet.com` cited by ChatGPT, Claude, Gemini and Perplexity. Specific things in this setup serve that:

- **`BlogPosting` schema on every post** — machine-readable authorship, dates and topics
- **`isPartOf` → `#blog` → `#organization`** — binds each post to the entity graph on the homepage
- **Comparison tables** — LLMs extract and quote tables cleanly; they're among the most-cited formats
- **Question-shaped `<h2>`s** — match how people actually query
- **Cross-category internal links** in "Read next" — spreads authority sitewide, which is the mechanism that moves pages out of "discovered, currently not indexed"

**The highest-value post you can write is original research** — a statistic nobody else has. Cite-worthy by definition, and every citation carries the brand name. You're already auditing Gulf contractor websites for outreach: *"We checked 100 UAE contractor websites. Here's what we found."* Run it properly, record the method, publish the real numbers.

---

## Cadence

One well-researched post a week beats five thin ones. Volume without substance gets crawled and ignored.

---

## Post inventory

| Slug | Category | Product |
|---|---|---|
| `gulf-contractors-lose-work-online` | digital | Digital Presence |
| `choosing-a-degree-without-guessing` | career | Career Blueprint |
| `your-cv-is-not-being-read` | cv | Make My CV |
| `you-dont-have-a-money-problem` | wealth | Wealth Compass |
