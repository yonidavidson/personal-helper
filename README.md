# Daily Health Email Notification GitHub Action

## Overview

This GitHub Action sends a daily health reminder email with:
- Latest health news headline
- An AI-generated inspirational health quote
- Key health tips
- Formatted in both plain text and HTML

## Prerequisites

Before using this action, you'll need to set up the following secrets in your GitHub repository:

1. `NEWS_API_KEY`: API key from NewsAPI for fetching health headlines
2. `OPEN_AI_TOKEN`: OpenAI API token for quote generation
3. `SMTP_PASSWORD`: Password for SMTP service
4. `RECIPIENT_EMAIL`: Email address of the recipient

## Workflow Configuration

The action is scheduled to run daily at 5:00 AM UTC using a cron job.

```yaml
on:
  schedule:
    - cron: '0 5 * * *'  # Daily at 5:00 AM UTC
  workflow_dispatch:     # Allow manual triggering
```

## Email Content

- General health reminders
- Daily inspirational quote
- Motivational closing message

## API Services Used

- NewsAPI: Retrieve latest health headlines
- OpenAI: Generate contextual health quotes
- Mailtrap SMTP: Send emails