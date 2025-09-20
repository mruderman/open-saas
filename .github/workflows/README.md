# GitHub Workflows

This directory contains GitHub Actions workflows for the Open SaaS repository.

## Workflows

### sync-upstream.yml

**Purpose**: Automatically syncs this fork with the upstream repository (`wasp-lang/open-saas`)

**Triggers**:

- **Scheduled**: Runs daily at 2 AM UTC
- **Manual**: Can be triggered manually via GitHub Actions UI (workflow_dispatch)

**What it does**:

1. Checks if the upstream repository has new commits
2. If changes are detected, creates a new branch with the upstream changes
3. Attempts to merge the upstream changes
4. Creates a Pull Request with:
   - Summary of changes
   - Number of new commits
   - Merge status (clean merge or conflicts detected)
   - Instructions for next steps

**Benefits**:

- Keeps the fork up-to-date with the latest improvements from upstream
- Creates PRs for review rather than pushing directly to main
- Handles merge conflicts gracefully
- Provides clear information about what changed

**Security**: Uses the default `GITHUB_TOKEN` with minimal required permissions (contents: write, pull-requests: write)

### e2e-tests.yml

**Purpose**: Runs end-to-end tests using Playwright

**Triggers**: Push to main, Pull Requests to main

### blog-deployment.yml

**Purpose**: Deploys the blog/documentation to Netlify

**Triggers**: Changes to `opensaas-sh/blog/**` path on main branch or PRs