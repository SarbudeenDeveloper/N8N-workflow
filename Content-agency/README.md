# Content Agency — n8n Workflow

Automate social media content generation using **n8n**, **GraphyCards API**, **Google Sheets**, and **Google Drive**. Define your content plan in a spreadsheet, and the workflow generates branded designs and uploads them automatically.

## How It Works

1. **Schedule Trigger** — Polls the Google Sheet every 3 minutes
2. **Google Sheets** — Reads rows with status `process it`
3. **GraphyCards API** — Generates branded PDFs from the sheet data (supports multilingual content)
4. **Wait & Poll** — Waits for the job to complete, then downloads the result
5. **Google Drive** — Uploads the generated file to a specified folder
6. **Update Sheet** — Sets status to `ready` and adds a preview link

## Google Sheet Columns

| Column | Description |
|--------|-------------|
| Input | Content text or topic |
| Type | Input type for GraphyCards |
| Customer | Brand kit ID |
| Render Format | Output format (e.g., carousel) |
| Mode | Content style |
| Theme | Design theme |
| Language | Output language |
| Status | `process it` → `ready` |
| Preview Link | Auto-filled Google Drive link |

A sample spreadsheet (`Customer Social Media Plan.xlsx`) is included in the repo.

## Setup

1. **Import** `Content Agency.json` into your n8n instance
2. **Google Sheets / Drive** — Add OAuth2 credentials and connect both nodes
3. **GraphyCards API Key** — Sign up free at [graphycards.com](https://graphycards.com) (includes 3 free generations). Go to **Settings → API** tab and create an API key. Then in n8n, go to Credentials → Add → Header Auth:
   - Name: `X-API-Key`
   - Value: your GraphyCards API key
4. **Google Sheet** — Copy `Customer Social Media Plan.xlsx` to your Google Sheets and update the node references
5. **Google Drive** — Choose the destination folder for generated files
6. **Activate** the workflow

## Demo

See `Google Sheet - Content Agency.mp4` included in the repo.

## Examples

The `examples/` folder contains sample generated outputs in multiple languages (English, Italian, French, Arabic, Chinese).

## Repository

[github.com/SarbudeenDeveloper/N8N-workflow](https://github.com/SarbudeenDeveloper/N8N-workflow)
