---
title: Web Quality Skills by Addy Osmani - Lighthouse & Core Web Vitals Auditing
anchor: Agent skills for comprehensive web page auditing based on Lighthouse and Core Web Vitals
tags: [ai, web, auditing, lighthouse, core-web-vitals, accessibility, seo, performance, agent-skill]
description: 150+ Lighthouse audits across Performance, Accessibility, SEO, and Best Practices. Stack-agnostic skills for AI agents.
source_url: https://skills.sh/addyosmani/web-quality-skills
repo_url: https://github.com/addyosmani/web-quality-skills
---

## My Reference

### Summary
Agent Skills collection for optimizing web projects based on Google Lighthouse guidelines and Core Web Vitals. Works with any framework (React, Vue, Angular, Svelte, Next.js, Nuxt, Astro, plain HTML).

### Installation
```bash
npx skills add addyosmani/web-quality-skills
# or
npx add-skill addyosmani/web-quality-skills
```

### Available Skills

| Skill | Description | Trigger Phrases |
|-------|-------------|-----------------|
| **web-quality-audit** | Comprehensive quality review | "Audit my site", "Review this for quality", "Check web quality" |
| **performance** | Loading speed, runtime efficiency | "Optimize performance", "Speed up my site", "Fix slow loading" |
| **core-web-vitals** | LCP, INP, CLS optimizations | "Improve Core Web Vitals", "Fix LCP", "Reduce CLS", "page experience" |
| **accessibility** | WCAG compliance, a11y | "Improve accessibility", "WCAG audit", "a11y review" |
| **seo** | Search engine optimization | "Optimize for SEO", "Improve search ranking", "Fix meta tags" |
| **best-practices** | Security, modern APIs | "Apply best practices", "Security audit", "Code quality" |

### Coverage
- **150+ Lighthouse audits** across Performance, Accessibility, SEO, Best Practices
- **Core Web Vitals:** LCP ≤2.5s, INP ≤200ms, CLS ≤0.1
- **Performance budgets:** Total <1.5MB, JS <300KB, CSS <100KB
- **Lighthouse targets:** Perf ≥90, A11y 100, Best Practices ≥95, SEO ≥95

### Framework Notes
- **React/Next.js:** next/image, React.lazy(), Suspense, useCallback/useMemo
- **Vue/Nuxt:** nuxt/image, async components, computed properties
- **Svelte:** await blocks, reactive statements
- **Astro:** <Image>, partial hydration, view transitions
- **Static HTML:** native lazy loading, <picture>, preconnect hints

### Resources
- **Skills.sh:** https://skills.sh/addyosmani/web-quality-skills
- **GitHub:** https://github.com/addyosmani/web-quality-skills
- **Lighthouse Docs:** https://developer.chrome.com/docs/lighthouse/
- **Core Web Vitals:** https://web.dev/articles/vitals
