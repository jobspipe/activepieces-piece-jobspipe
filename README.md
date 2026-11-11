# @jobspipe/piece-jobspipe

JobsPipe piece for Activepieces - Search live job postings and company profiles from 30+ job boards and ATS platforms.

## About

This package provides a custom Activepieces piece for integrating [JobsPipe](https://jobspipe.dev) into your Activepieces workflows. Search normalized job postings from LinkedIn, Indeed, Greenhouse, Workday, Lever, Ashby, and 25+ other sources, or look up enriched company profiles—all through one unified API.

## Installation

### For Activepieces Self-Hosted Users

1. Log in to your Activepieces instance as an admin
2. Navigate to **Platform Admin > Pieces**
3. Click **Install piece from npm**
4. Enter the package name: `@jobspipe/piece-jobspipe`
5. Click **Install**

The piece will be available to all users in your workspace immediately.

### For Activepieces Cloud Users

Custom pieces are not currently supported on Activepieces Cloud. You'll need to use a self-hosted instance.

## Getting Started

### 1. Get Your API Key

Sign up for a free JobsPipe account at [jobspipe.dev](https://jobspipe.dev) and get 1,000 free credits (no credit card required). Your API key is available in the dashboard after signup.

### 2. Configure Authentication

When adding a JobsPipe action to your flow:

1. Click on the authentication field
2. Select **Add new connection**
3. Paste your JobsPipe API key
4. The connection will be validated automatically against the JobsPipe API

## Available Actions

### Search Jobs

Search live job postings from 30+ sources with advanced filters.

**Filters:**
- **Job Titles** - Match any of these role keywords (e.g. "data engineer", "senior developer")
- **Company Names** - Filter by company (partial match)
- **Country Codes** - ISO alpha-2 codes (e.g. "US", "GB", "DE")
- **Cities** - Exact city names
- **Locations** - Match city or region (partial)
- **Remote Only** - Filter for remote positions
- **Seniority Levels** - entry, junior, mid, senior, lead, staff, principal, director, vp, c-level, intern
- **Posted Within (Days)** - Only recent postings (max 365 days)
- **Minimum Salary (USD)** - Filter by annual salary
- **Description Keywords** - Match terms in job descriptions
- **Skills** - Technology/skill slugs (e.g. "python", "kubernetes", "react")
- **Sources** - Target specific sources (linkedin, indeed, greenhouse, workday, etc.)
- **Max Results** - Limit the number of results (1-500, default 25)

**Example Output:**
```json
{
  "data": [
    {
      "id": "...",
      "title": "Senior Software Engineer",
      "company": "Acme Corp",
      "location": "San Francisco, CA",
      "remote": true,
      "posted_at": "2024-11-08T12:34:56Z",
      "url": "https://...",
      "salary": {
        "min": 150000,
        "max": 200000,
        "currency": "USD"
      }
    }
  ],
  "metadata": {
    "total_results": 234,
    "credits_charged": 1,
    "credits_remaining": 999
  }
}
```

### Get Company Profile

Look up enriched company data by domain, email, or name.

**Input:**
- **Company Key** - Domain (e.g. "stripe.com"), careers URL, email, or exact company name

**Example Output:**
```json
{
  "key": "stripe.com",
  "name": "Stripe",
  "domain": "stripe.com",
  "url": "https://stripe.com",
  "logo": "https://...",
  "employee_count": 8000,
  "linkedin_url": "https://linkedin.com/company/stripe",
  "description": "...",
  "location": {
    "city": "San Francisco",
    "region": "CA",
    "country": "US"
  },
  "founded": "2010"
}
```

### Custom API Call

Make authenticated requests to any JobsPipe API endpoint for advanced use cases not covered by the standard actions. See the [JobsPipe API documentation](https://docs.jobspipe.dev) for available endpoints.

## Credits & Pricing

- **Free tier**: 1,000 credits (no credit card required)
- **Search Jobs**: 1 credit per search (regardless of result count)
- **Get Company Profile**: 1 credit per successful lookup (404s are free)
- **Custom API Call**: Varies by endpoint

Check your remaining credits in any action response under `metadata.credits_remaining`.

For more credits or higher limits, see [pricing](https://jobspipe.dev/pricing).

## Resources

- **Documentation**: [docs.jobspipe.dev](https://docs.jobspipe.dev)
- **Dashboard**: [jobspipe.dev](https://jobspipe.dev)
- **Support**: [support@jobspipe.dev](mailto:support@jobspipe.dev)
- **GitHub**: [github.com/jobspipe](https://github.com/jobspipe)

## Development

### Building from Source

```bash
npm install
npm run build
```

### Testing the Build

```bash
npm run test:load
```

This verifies the piece exports correctly and can be loaded by Activepieces.

## License

MIT © JobsPipe

## Contributing

This piece was originally developed as a contribution to the Activepieces community repository but was published separately after upstream paused community PRs. Issues and PRs are welcome at [github.com/jobspipe/activepieces-piece-jobspipe](https://github.com/jobspipe/activepieces-piece-jobspipe).
