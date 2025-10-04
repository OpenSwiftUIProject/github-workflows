# GitHub Workflows

Shared GitHub Actions workflows for the OpenSwiftUI Project organization.

## Workflows

### claude.yml
Workflow that enables Claude Code to interact with pull requests and issues when triggered.

### issue-triage.yml
Automated issue triage workflow that uses Claude to analyze and label new issues.

## Usage

These workflows are designed to be used as reusable workflows across all repositories in the OpenSwiftUIProject organization.

To use these workflows in your repository, reference them in your workflow files:

```yaml
jobs:
  call-shared-workflow:
    uses: OpenSwiftUIProject/github-workflows/.github/workflows/claude.yml@main
    secrets: inherit
```

## Requirements

The following organization or repository secrets must be configured:
- `ANTHROPIC_API_KEY`: API key for Claude Code functionality
