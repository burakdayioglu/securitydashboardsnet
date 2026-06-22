# securitydashboards.net — content map

15 pages. Each markdown file has YAML front matter with its `url`, `title`, `description`, `target_keyword`, and `internal_links`. Internal links inside the body use site relative URLs (e.g. `/security-kpi-system-of-record/`) so they work once deployed.

## File → URL

| File | URL | Target keyword |
|------|-----|----------------|
| content/index.md | / | security dashboards |
| content/what-is-a-security-dashboard.md | /what-is-a-security-dashboard/ | security dashboard |
| content/what-is-a-ciso-dashboard.md | /what-is-a-ciso-dashboard/ | CISO dashboard |
| content/security-dashboard-examples.md | /security-dashboard-examples/ | security dashboard examples |
| content/security-dashboard-vs-siem.md | /security-dashboard-vs-siem/ | security dashboard vs SIEM |
| content/how-to-build-a-security-dashboard.md | /how-to-build-a-security-dashboard/ | how to build a security dashboard |
| content/best-security-dashboard-tools-2026.md | /best-security-dashboard-tools-2026/ | best security dashboard tools 2026 |
| content/tools/grafana-security-dashboard.md | /tools/grafana-security-dashboard/ | Grafana security dashboard |
| content/tools/power-bi-security-dashboard.md | /tools/power-bi-security-dashboard/ | Power BI security dashboard |
| content/tools/servicenow-security-dashboard.md | /tools/servicenow-security-dashboard/ | ServiceNow security dashboard |
| content/tools/splunk-security-dashboard.md | /tools/splunk-security-dashboard/ | Splunk security dashboard |
| content/the-data-layer-beneath-the-dashboard.md | /the-data-layer-beneath-the-dashboard/ | security dashboard data layer |
| content/security-dashboard-data-problem.md | /security-dashboard-data-problem/ | security dashboard data problem |
| content/security-kpi-system-of-record.md | /security-kpi-system-of-record/ | security KPI system of record |
| content/about.md | /about/ | about securitydashboards |

## The three clusters

**Education (traffic engine):** what-is-a-security-dashboard, what-is-a-ciso-dashboard, security-dashboard-examples, security-dashboard-vs-siem, how-to-build-a-security-dashboard

**Comparison (commercial intent, authority):** best-security-dashboard-tools-2026 + the four /tools/ pages

**Bridge (conversion):** the-data-layer-beneath-the-dashboard, security-dashboard-data-problem, security-kpi-system-of-record

## Link flow

Every education and comparison page links down into the bridge cluster. The bridge cluster links out to metricmaestro.com. Only two pages link to metricmaestro.com directly (security-kpi-system-of-record and about), so the outbound link to MM stays focused and credible rather than spammed across every page.

```
education ─┐
           ├─→ bridge cluster ─→ metricmaestro.com
comparison ┘
```

## The one outbound rule

Keep the metricmaestro.com link confined to the bridge cluster (and the about disclosure). If every page links out to MM, the site reads as an ad and both trust and rankings suffer. The education and comparison pages earn the traffic and the authority; the bridge pages convert it.

## Publish order (recommended)

1. what-is-a-ciso-dashboard + security-dashboard-examples (fastest traffic)
2. best-security-dashboard-tools-2026 (commercial intent)
3. the-data-layer-beneath-the-dashboard + security-kpi-system-of-record (the conversion bridge)
4. everything else fills in

## llms.txt

`llms.txt` is included at the project root. It must be served at the web root so it resolves at `https://securitydashboards.net/llms.txt`. In Hugo, drop it in `static/llms.txt` and it deploys to the root automatically. It lists every page grouped by cluster with absolute URLs, so LLMs can discover and scan the whole site from one file. Update it whenever you add or rename a page.

## Notes for deployment

- These are Hugo compatible front matter blocks. If you use a different generator, the `url` field tells you where each page goes.
- Keep `robots.txt` permissive for the crawlers you want, and submit a sitemap.xml; `llms.txt` complements these, it does not replace them.
- Set up matching corroboration on metricmaestro.com: a page there that links back to /security-kpi-system-of-record/ with "security KPI system of record" anchor text (two way signal).
- Add Organization + Article schema sitewide; ItemList schema on the comparison page; SoftwareApplication is better placed on metricmaestro.com than here.
- De-prioritize any future /resources/ or /guides/ sections in crawl priority, same as the MM main site.
