# AI Job Hunter (n8n)

n8n workflows that look for remote jobs in Spain, score them with an LLM and send the
good ones to Discord.

- `ai-job-hunter-merged-9-sources-discord-fixed.json` job sources (Jooble, Adzuna, RemoteOK,
  Remotive, Arbeitnow, We Work Remotely, NoDesk, Himalayas, Jobicy), dedup in workflow static
  data, Groq scoring, Discord digest, run lock so runs do not overlap
- `ats-direct-poll-spain-job.json` polls company career boards directly (Greenhouse, Lever,
  Ashby, SmartRecruiters, Workable), dedup in an n8n Data table, DeepSeek scoring, Discord
- `ats-detector-v4-strict-non-empty-check.json` checks a list of company names against the
  ATS URL patterns and finds which companies use which ATS

## Setup

1. Import the JSON files in n8n (Workflows, Import from File).
2. Create the credentials the nodes ask for (Groq, DeepSeek). Every credential in the
   export is named `YOUR_CREDENTIAL`, select your own one in each node.
3. Replace `https://discord.com/api/webhooks/YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN` and other
   `YOUR_...` / `REPLACE_ME` placeholders with your values (search the workflow for them).
4. Data table nodes often lose their settings on import: open them, pick the table and the
   operation again.

Secrets are not part of this repository.
