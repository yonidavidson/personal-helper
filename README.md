# personal-helper
My personal Helper

## GitHub Action: Daily Email Notification

This GitHub Action sends an email every morning at 0800.

### Configuration

To configure the email recipient, follow these steps:

1. Open the `.github/workflows/email-action.yml` file.
2. Locate the `recipient_email` environment variable.
3. Replace the placeholder email address with the desired recipient's email address.

### Example

```yaml
name: Daily Email Notification

on:
  schedule:
    - cron: '0 8 * * *'

jobs:
  send-email:
    runs-on: ubuntu-latest
    steps:
      - name: Send Email
        run: |
          curl -s --url 'smtps://smtp.example.com:465' --ssl-reqd \
            --mail-from 'sender@example.com' \
            --mail-rcpt 'recipient@example.com' \
            --user 'username:password' \
            -T <(echo -e "From: sender@example.com\nTo: recipient@example.com\nSubject: Daily Notification\n\nThis is your daily notification.")
        env:
          recipient_email: 'recipient@example.com'
          sender_email: 'sender@example.com'
          smtp_server: 'smtp.example.com'
          smtp_username: 'username'
          smtp_password: 'password'
```

### Exec Now Button

To manually trigger the email notification, follow these steps:

1. Open the GitHub repository.
2. Navigate to the "Actions" tab.
3. Select the "Daily Email Notification" workflow.
4. Click on the "Run workflow" button to execute the action immediately.
