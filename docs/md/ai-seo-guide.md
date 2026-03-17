# How to Create AI SEO for Your Website

**Published by Bermuda LLC** | https://www.thebermuda.us/ai-seo-guide
**Category:** AI Visibility, GEO, InsurTech

AI search engines — ChatGPT, Perplexity, Claude, and Grok — are now primary entry points for business discovery. Traditional SEO gets you found on Google. AI SEO (also called Generative Engine Optimization, or GEO) gets your business cited inside AI-generated answers. This guide covers the exact steps to make your website readable, discoverable, and citable by AI systems.

---

## Why AI SEO Matters Now

- 95 out of 100 Google AI Mode queries end without a click — but the 5 that click are high-intent
- ChatGPT sends 12 million clicks per month in Germany alone; the top-cited site captured 2% of that
- AI crawlers (GPTBot, PerplexityBot, Claude-Web) actively index your site — but only if you let them
- An HTML page takes 16,180 tokens for an AI to process; the same content in markdown takes 3,150 — an 80% reduction
- AI systems prefer structured, declarative content over marketing language

The opportunity: fewer visitors, but higher intent. AI-cited businesses win trust before the user ever visits.

---

## Step 1: Create llms.txt

`llms.txt` is the AI equivalent of `robots.txt`. Proposed by Jeremy Howard (Answer.AI), it tells LLMs what your site is about and where to find structured content.

**Place it at:** `https://yourdomain.com/llms.txt`

**Format:**
```
# Company Name

> One-sentence description of who you are and what you do.

## Core Pages
- [Product Name](https://yourdomain.com/docs/product.md): brief description
- [FAQs](https://yourdomain.com/docs/faqs.md): common questions

## Optional
- [Full Content](https://yourdomain.com/llms-full.txt): all content merged
```

**Key rules:**
- Lead with a clear `>` blockquote description — AI uses this to decide relevance
- Link to markdown files, not HTML pages (markdown is 80% more token-efficient)
- Include an `llms-full.txt` link for AI agents that want everything in one fetch
- Keep the index concise — AI agents parse this before deciding what to retrieve

---

## Step 2: Create robots.txt (Allow AI Crawlers)

Many sites accidentally block AI crawlers with aggressive `Disallow` rules. Check yours and explicitly allow key bots.

**Place it at:** `https://yourdomain.com/robots.txt`

**Crawlers to allow:**

| Bot | Platform |
|-----|----------|
| `GPTBot` | ChatGPT (training) |
| `OAI-SearchBot` | ChatGPT (search/RAG) |
| `PerplexityBot` | Perplexity |
| `Claude-Web` | Claude |
| `anthropic-ai` | Anthropic crawlers |
| `Google-Extended` | Gemini training |
| `cohere-ai` | Cohere |
| `Meta-ExternalAgent` | Meta AI |

**Minimum robots.txt:**
```
User-agent: *
Allow: /

User-agent: GPTBot
Allow: /

User-agent: PerplexityBot
Allow: /

Sitemap: https://yourdomain.com/sitemap.xml
```

---

## Step 3: Create Markdown Content Files

AI agents prefer markdown over HTML. HTML pages contain navigation bars, scripts, ads, and wrappers that add zero semantic value but cost thousands of tokens. Markdown delivers only the content.

**Create a `docs/md/` directory with one file per topic:**
- `README.md` — company overview, key stats, quick links
- `products.md` — what you sell, features, how it works
- `faqs.md` — Q&A format (AI loves FAQ structure)
- `pricing.md` — declarative pricing facts
- `integrations.md` — what connects with your platform

**Best practices for AI-optimized markdown:**
- Use `##` headings for every major section — AI uses these as chunk boundaries
- Write declarative statements: "Bermuda processes 50,000 quotes per month" not "we're industry-leading"
- Put the most important fact in the first sentence of each section
- Use bullet lists for features — AI extracts these as structured facts
- Include the canonical URL at the top of each file: `**Page:** https://yourdomain.com/product`

**Also create `llms-full.txt`** at the root — merge all markdown files into one. AI agents that want a complete picture can get it in a single HTTP request instead of 8.

---

## Step 4: Create sitemap.xml

`sitemap.xml` tells all crawlers (including AI) which pages exist and when they were last updated. Without it, AI crawlers may miss your content entirely.

**Include your markdown files in the sitemap**, not just HTML pages:
```xml
<url>
  <loc>https://yourdomain.com/docs/md/products.md</loc>
  <lastmod>2026-03-17</lastmod>
  <priority>0.7</priority>
</url>
```

Freshness matters: Perplexity heavily cites content less than one year old. Keep `<lastmod>` current.

---

## Step 5: Set Proper Content-Type Headers for Markdown

AI agents that send `Accept: text/markdown` request headers (Claude Code, OpenCode, and others do this) should receive markdown with the correct MIME type.

**If you use Vercel**, add to `vercel.json`:
```json
{
  "headers": [
    {
      "source": "/(.*\\.md)",
      "headers": [
        { "key": "Content-Type", "value": "text/markdown; charset=utf-8" }
      ]
    }
  ]
}
```

**If you use Cloudflare**, enable "Markdown for Agents" in the dashboard (Beta, free for Pro+). Cloudflare will automatically convert any HTML page to markdown when an AI agent requests it with `Accept: text/markdown`.

**If you use Nginx:**
```nginx
location ~* \.md$ {
    add_header Content-Type "text/markdown; charset=utf-8";
}
```

---

## Step 6: Content Strategy for AI Citation

AI systems cite content that is authoritative, structured, and specific. To increase your citation rate:

### Write for RAG, Not Just Readers

RAG (Retrieval-Augmented Generation) is how ChatGPT and Perplexity work — they search the web live, pull chunks of your content, and feed it into the AI model. Your content competes to be retrieved and selected.

**What gets selected:**
- Specific facts with numbers ("reduces manual work by 40 hours/month")
- Clear H2/H3 hierarchy that defines chunk boundaries
- FAQ format — AI loves direct Q&A structure
- Summary sentences at the top of each section
- Lists over long paragraphs

**What gets ignored:**
- Vague marketing claims ("industry-leading," "best-in-class")
- Long unbroken paragraphs
- Content buried under navigation and scripts

### Build Presence on Sources AI Cites Most

Your website alone is not enough. AI systems pull from:
- **Wikipedia / Crunchbase / G2** — complete these profiles thoroughly
- **LinkedIn** — publish thought leadership articles
- **Reddit** — participate genuinely in relevant communities
- **YouTube** — create transcribed video content
- **Industry publications** — digital PR and editorial mentions

Consistent brand descriptions across all platforms accelerate AI visibility. Use identical company descriptions on LinkedIn, Crunchbase, X, and GitHub.

### Track Query Fanout

When a user asks ChatGPT a question, the AI generates 2-5 related search queries behind the scenes. Optimize for the real questions your customers ask, not just your product name.

Export your top Google Search Console queries, convert them to conversational questions, and test each in ChatGPT/Perplexity to see if your site appears.

---

## Step 7: Add JSON-LD Structured Data

Structured data in JSON-LD format helps both traditional search engines and AI systems understand your content type, author, and organization.

**Add to every HTML page:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Your Company",
  "url": "https://yourdomain.com",
  "description": "What your company does in one sentence.",
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+1-000-000-0000",
    "email": "info@yourdomain.com"
  }
}
</script>
```

**For blog/guide pages, add Article schema:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Your Article Title",
  "author": { "@type": "Organization", "name": "Your Company" },
  "datePublished": "2026-03-17"
}
</script>
```

---

## Quick Checklist

- [ ] `llms.txt` at root with company summary and markdown links
- [ ] `llms-full.txt` at root with all content merged
- [ ] `robots.txt` explicitly allowing GPTBot, PerplexityBot, Claude-Web
- [ ] `sitemap.xml` including markdown doc URLs
- [ ] `docs/md/` directory with topic-specific markdown files
- [ ] Content-Type headers set for `.md` files
- [ ] JSON-LD structured data on key pages
- [ ] Consistent brand presence on Crunchbase, LinkedIn, G2
- [ ] FAQ content written in declarative Q&A format
- [ ] Google Analytics segment for AI traffic (ChatGPT, Perplexity, Claude)

---

## Frequently Asked Questions

**What is the difference between SEO and GEO?**
SEO (Search Engine Optimization) targets Google's ranking algorithm to get blue links. GEO (Generative Engine Optimization) targets AI language models to get cited inside AI-generated answers. Both matter — but GEO requires structured, machine-readable content rather than keyword density.

**Does llms.txt replace robots.txt?**
No. `robots.txt` controls crawler access (which bots can crawl which pages). `llms.txt` provides AI-readable content about your site's structure and purpose. You need both.

**Will this work for ChatGPT?**
ChatGPT uses RAG (web search) for current information. Allowing GPTBot and OAI-SearchBot in robots.txt, having a sitemap, and providing structured content increases the probability of being retrieved and cited in ChatGPT answers.

**How long does AI SEO take to show results?**
RAG-based systems (Perplexity, ChatGPT search) can reflect changes within days to weeks. Foundation model training data has cutoffs — influence there is longer-term and requires external citation building.

**Is markdown required, or can HTML work?**
AI systems can process HTML, but it costs 5–10x more tokens. Clean HTML with good semantic structure (proper H1/H2, no excessive wrappers) performs better than average, but dedicated markdown files give AI agents the most efficient path to your content.

---

## About Bermuda LLC

Bermuda is an InsurTech company specializing in insurance automation — real-time rating, agentic AI workflows, and carrier data integration for insurance agencies.

This guide reflects the exact GEO implementation we applied to thebermuda.us. See our implementation: [llms.txt](https://www.thebermuda.us/llms.txt) | [llms-full.txt](https://www.thebermuda.us/llms-full.txt)

**Contact:** info@thebermuda.us | (512) 428-8740 | https://www.thebermuda.us
