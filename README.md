# GitHub Workflows

Shared GitHub Actions workflows for the OpenSwiftUI Project organization.

## Workflows

### claude.yml
Workflow that enables Claude Code to interact with pull requests and issues when triggered.

### issue-triage.yml
Automated issue triage workflow that uses Claude to analyze and label new issues.

### pr-triage.yml
Automated PR triage workflow that uses Claude to analyze and label new pull requests.

## Usage

These workflows are designed to be used as reusable workflows across all repositories in the OpenSwiftUIProject organization.

### Using claude.yml

Create `.github/workflows/claude.yml` in your repository:

```yaml
name: Claude Code

on:
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]
  issues:
    types: [opened, assigned]
  pull_request_review:
    types: [submitted]

permissions:
  contents: read
  pull-requests: read
  issues: read
  id-token: write
  actions: read

jobs:
  claude:
    uses: OpenSwiftUIProject/github-workflows/.github/workflows/claude.yml@main
    secrets: inherit
```

### Using issue-triage.yml

Create `.github/workflows/issue-triage.yml` in your repository:

```yaml
name: Issue Triage

on:
  issues:
    types: [opened]

permissions:
  contents: read
  issues: write

jobs:
  triage-issue:
    uses: OpenSwiftUIProject/github-workflows/.github/workflows/issue-triage.yml@main
    secrets: inherit
```

### Using pr-triage.yml

Create `.github/workflows/pr-triage.yml` in your repository:

```yaml
name: PR Triage

on:
  pull_request:
    types: [opened]

permissions:
  contents: read
  pull-requests: write

jobs:
  triage-pr:
    uses: OpenSwiftUIProject/github-workflows/.github/workflows/pr-triage.yml@main
    secrets: inherit
```

## Requirements

The following secrets are required:
- `CLAUDE_CODE_OAUTH_TOKEN`: OAuth token for Claude Code functionality
  - **Already configured** at the organization level for all OpenSwiftUI Project repositories
  - No per-repository configuration needed
  - To obtain a new token (for org admins), run `claude setup-token` in your terminal
- `GITHUB_TOKEN`: Automatically provided by GitHub Actions
