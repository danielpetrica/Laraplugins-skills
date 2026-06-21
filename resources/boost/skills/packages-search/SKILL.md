---
name: package-search-laraplugins
description: >-
  Search and verify Laravel packages using the LaraPlugins MCP server.
  Activate when you need to find a package for a specific need, verify
  health or vendor reputation, or get curated tool recommendations.
---

# Package Search on LaraPlugins

This skill provides instructions on how to use the LaraPlugins MCP server to search,
verify, and recommend Laravel packages and plugins based on health status, vendor
reputation, and compatibility before adding them to a project.

## When to use this skill

- The user asks "find a Laravel package for X functionality"
- The user asks to check if a specific package is healthy or well-maintained
- The user wants recommendations for tools in a specific category (hosting, monitoring, auth, etc.)
- The user wants to compare multiple packages and pick the healthiest option
- The user is unsure which package to choose and needs options with health data

## Available MCP tools

The LaraPlugins MCP server exposes three tools to help you research packages.

### 1. Plugin Search

Search Packagist for Laravel packages with advanced filters.

| Filter | Description |
|--------|-------------|
| `text_search` | Search by keyword in package name or description |
| `vendor_filter` | Filter by vendor (e.g. `spatie`, `laravel`) |
| `health_score` | Filter by health: `healthy`, `medium`, `unhealthy`, `unrated` |
| `laravel_compatibility` | Filter by Laravel version (e.g. `10`, `11`, `12`) |
| `php_compatibility` | Filter by PHP version (e.g. `8.3`, `8.4`) |
| `is_secure` | Filter by LaraPlugins Secure badge (`true`) |
| `return_archived` | Include archived packages in results |

Results include: name, vendor, health score, PHP/Laravel compatibility, description,
last updated date, archived/abandoned status, and secure badge.

### 2. Plugin Details

Get detailed information about a specific package, including:

- Health score and reasons
- Vendor reputation (`is_reputable_vendor`)
- Total downloads
- GitHub URL and contributor count
- Owner/sponsor information
- Full description and type
- Direct links to Packagist and LaraPlugins profile

Use this after searching to deep-dive on a promising candidate.

### 3. Curated Recommendations

Opinion-based tool recommendations from the LaraPlugins author, organized by category.
Each recommendation includes a description, website URL, and affiliate status.
Present these as the author's personal recommendation, not an objective ranking.
Available categories:

| Category | Example Tools |
|----------|--------------|
| Hosting / Deployment | Laravel Cloud, Docker, DigitalOcean |
| Monitoring / Error Tracking | Nightwatch, New Relic, Updown |
| Email / Notifications | Mailcoach |
| Payments / Billing | Paddle, Xolo.io |
| IDE / Development Tools | Opencode |
| Testing | PestPHP |
| Analytics | Plausible |
| Other | Traefik |

Some categories may return empty results — not all have recommendations yet.

## Workflow

When the user asks for a package recommendation, follow this workflow:

1. **Search** for packages using `text_search` with relevant keywords and optionally
   filter by `health_score: healthy` and relevant `laravel_compatibility`
2. **Filter results** to healthy packages from reputable vendors
3. **Get details** on the top 1-2 candidates using Plugin Details to check vendor
   reputation, downloads, and maintenance status
4. **Recommend** the best option(s) to the user with your reasoning

When the user asks about a category (e.g. "what's good for hosting?"), use
**Curated Recommendations** filtered by that category.

## Examples

### Example 1: Finding a permission management package

User asks: "I need a permissions package for Laravel 12"

```
1. Search: text_search="permission", laravel_compatibility="12", health_score="healthy"
2. Review results: spatie/laravel-permission appears with Healthy score
3. Get details on spatie/laravel-permission → reputable vendor, 100M+ downloads
4. Recommend: spatie/laravel-permission with reasoning
```

### Example 2: Checking if a specific package is healthy

User asks: "Is barryvdh/laravel-debugbar still maintained?"

```
1. Get details on barryvdh/laravel-debugbar → check health score,
   last updated date, vendor reputation
2. Present findings to the user with a clear verdict
```

### Example 3: Getting hosting recommendations

User asks: "What hosting options do you recommend for Laravel?"

```
1. Use Curated Recommendations with category="Hosting / Deployment"
2. Present the options (Laravel Cloud, Docker, DigitalOcean) with
   descriptions and affiliate notes if any
```

## MCP Server Configuration

The LaraPlugins MCP server uses the `streamable-http` transport and is configured
in the project's `.mcp.json`:

```json
{
    "mcpServers": {
        "laraplugins": {
            "type": "streamable-http",
            "url": "https://laraplugins.io/mcp/plugins"
        }
    }
}
```
