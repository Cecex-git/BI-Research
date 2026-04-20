---
description: |
  This workflow performs research to provide industry insights and competitive analysis.
  Reviews recent code, issues, PRs, industry news, and trends to create comprehensive
  research reports. Covers related products, research papers, market opportunities,
  business analysis, and new ideas. Creates GitHub issues with findings to inform
  strategic decision-making.

on:
  schedule:
    - cron: "47 11 * * *"
  workflow_dispatch:

permissions: read-all

network: defaults

safe-outputs:
  create-issue:
    title-prefix: "${{ github.workflow }}"

tools:
  github:
    toolsets: [all]
    min-integrity: none # This workflow is allowed to examine and comment on any issues or PRs
  web-fetch:

timeout-minutes: 15

source: githubnext/agentics/workflows/weekly-research.md@96b9d4c39aa22359c0b38265927eadb31dcf4e2a
---

# Weekly Research

## Job Description

Do a deep research investigation in ${{ github.repository }} repository, and the related industry in general.

- Read selections of the latest code, issues and PRs for this repo.
- Read latest trends and news from the software industry news source on the Web.

Create a new GitHub issue with title starting with "${{ github.workflow }}" containing a markdown report with

- Interesting news about the area related to this software project.
- Related products and competitive analysis
- Related research papers
- New ideas
- Market opportunities
- Business analysis
- Enjoyable anecdotes

Only a new issue should be created, no existing issues should be adjusted.

At the end of the report list write a collapsed section with the following:
- All search queries (web, issues, pulls, content) you used
- All bash commands you executed
- All MCP tools you used
