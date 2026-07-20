---
name: scrapling
description: "Use when extracting data from websites — HTTP requests, browser automation, Cloudflare bypass, and crawling with anti-detection techniques."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [web-scraping, crawling, data-extraction, automation]
    related_skills: [blogwatcher, youtube-content]
---

# Scrapling — Web Scraping Toolkit

## Overview

Scrapling provides web scraping capabilities for extracting data from websites that may have anti-bot protections. Includes HTTP clients, browser automation via Playwright, Cloudflare challenge bypass, recursive crawling, and schema-based extraction.

## When to Use

- Extracting data from public websites without an API
- Monitoring competitor pricing or content changes
- Collecting training data from the web
- Automating form submissions on sites without APIs

Do NOT use for: sites with clear terms of service prohibiting scraping, login-gated content you don't have permission to access, or high-frequency requests that would degrade the target site.

## Setup

```python
import httpx
# Or for JavaScript-heavy sites
from playwright.sync_api import sync_playwright
```

## Basic HTTP Scraping

```python
import httpx
from parsel import Selector

# Simple request with headers
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36",
    "Accept": "text/html,application/xhtml+xml",
}
resp = httpx.get("https://example.com/products", headers=headers, timeout=30)

# Parse with CSS/XPath selectors
sel = Selector(text=resp.text)
titles = sel.css("h2.product-title::text").getall()
prices = sel.xpath("//span[@class='price']/text()").getall()
```

## JavaScript Rendering

```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch(headless=True)
    page = browser.new_page()
    page.goto("https://example.com/dynamic-page", wait_until="networkidle")
    
    # Wait for dynamic content to load
    page.wait_for_selector(".product-grid")
    
    # Extract rendered content
    content = page.content()
    items = page.eval_on_selector_all(".product-item", 
        "els => els.map(el => el.textContent)")
    
    browser.close()
```

## Common Pitfalls

1. **Cloudflare/WAF** — Rotate User-Agent, use residential proxies, add realistic delays between requests
2. **Rate limiting** — Always add `time.sleep(random.uniform(1, 3))` between requests
3. **Legal compliance** — Check robots.txt and terms of service before scraping
4. **Page structure changes** — CSS selectors break when the site updates; monitor for changes
5. **Session management** — Maintain cookies across requests for sites that require sessions

## Verification Checklist

- [ ] Test request returns expected HTML
- [ ] CSS/XPath selectors extract correct data
- [ ] Rate limiting and delays are implemented
- [ ] Error handling for 403, 429, and timeout responses
- [ ] Robots.txt has been checked for disallowed paths
