# n8n templates

Three workflows that call these Apify Actors from [n8n](https://n8n.io) with the official Apify node (`@apify/n8n-nodes-apify`). On self-hosted n8n, install that community node first.

| Workflow | Actor | What it does |
| --- | --- | --- |
| [`keyword-tracking-google-sheets.json`](keyword-tracking-google-sheets.json) | [Keyword Research API](https://apify.com/gaelasao/keyword-research-api) | Every Monday, appends one row per keyword to Google Sheets: search volume, CPC, competition, keyword difficulty, intent, AI search volume and whether Google shows an AI Overview. |
| [`building-permits-weekly-digest.json`](building-permits-weekly-digest.json) | [Building Permits API](https://apify.com/gaelasao/planning-data-au-nz-fr) | Every Monday, sends the building permits a US city issued in the last 7 days in your ZIP codes, by Gmail and Slack: address, type, work, declared value and contractor. |
| [`ai-visibility-weekly-report.json`](ai-visibility-weekly-report.json) | [AI Visibility Tracker](https://apify.com/gaelasao/ai-visibility-tracker) | Every Monday, asks ChatGPT, Perplexity, Gemini and Google AI Overviews your questions, appends one row per question and engine to Google Sheets and posts a summary to Slack: brand named, rank, site cited, competitors. |

## Use

1. Import the JSON file into a new n8n workflow.
2. Add your Apify API token to the Apify credential, then connect Google Sheets, Gmail or Slack.
3. Edit the Set node: your keywords and country, your city, ZIP codes and recipients, or your brand, competitors and questions.

## Costs

- Keywords: $3 per 1,000 keywords with data, plus $0.01 per run. 100 keywords a week cost about $0.31. The Apify node stops a run at $1.
- Permits: $5 per 1,000 permits. The Set node asks for 100 permits at most, and the Apify node stops a run at $0.50.
- AI visibility: $0.02 per check (a Perplexity answer counts as 2), plus $0.01 per run. 10 questions on the 4 engines cost about $1.01 a week. The Apify node stops a run at $2.
