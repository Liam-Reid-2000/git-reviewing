# Git Reviewing
Github / Slack job to remind users that there are PR's awaiting their review.
<img width="495" height="154" alt="image" src="https://github.com/user-attachments/assets/6f822093-aeab-4391-82c8-3d99c94f23f3" />

Runs every hour, 8:30am to 4:30pm, Monday to Friday.

## Setup
Key setup elements:
- Slack App
- Github Token
- Github Secrets Configuration
- Github Action

### Slack App
1. Go to https://api.slack.com/apps
2. Click “Create New App”
3. Choose “From scratch”
4. App name can be anything. (Git Reviewing).
5. Pick your workspace

Configuration
1. Go to "Incoming Webhooks" in settings sidebar
2. Click “Add New Webhook to Workspace”
3. Choose channel, e.g: #dev
4. Slack will generate a webhook URL, we need this for the Github secret

### Github Token
1. Go to user settings
2. Developer settings
3. Personal Access Tokens > Tokens (classic)
4. Generate a new Classic Token
5. Give it Repo access
6. Copy the Github secret

### Secrets Configuration
1. Go to your repository
2. Go to `Settings`
3. Go to "Secrets and Variables" > "actions"
4. Add 2 repository secrets:
  - `GH_TOKEN` -> token generated in user settings
  - `SLACK_WEBHOOK_URL` -> URL from the slack app
<img width="518" height="120" alt="image" src="https://github.com/user-attachments/assets/3211cd86-e6c0-4cbd-bb4f-ea414084950a" />

### Github Action
1. Copy [this file](https://github.com/Liam-Reid-2000/git-reviewing/blob/main/.github/workflows/pr-review-reminder.yml) into `.github/workflows/`
2. Adjust the cron job as necessary
3. Push to Github
4. Go to Github actions tab
5. Select the workflow
6. Manually trigger the workflow
7. The slack message should be sent to the desired channel
