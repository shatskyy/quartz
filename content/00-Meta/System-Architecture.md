
# 🏗️ Wiki System Architecture

This document outlines the pipeline for the **shatskyy-wiki**. It is inspired by the Karpathy LLM-Wiki pattern.

## 1. The Core Components
- **The Body (Obsidian)**: Local Markdown storage on macOS.
- **The Memory (GitHub)**: `shatskyy/my-wiki` (Private Repo).
- **The Brain (Claude Routines)**: Hosted by Anthropic. Processes ingestions.
- **The Gateway (Vault-Inbox)**: Vercel-hosted web app for mobile submissions.
- **The Display (Quartz)**: Vercel-hosted static site for public viewing.

## 2. The Data Flow
1. **Input**: Text/URLs are dropped into the `Vault-Inbox` (phone/browser).
2. **Trigger**: Vercel sends a POST request to the Claude Routine Webhook.
3. **Synthesis**: Claude clones the repo, reads `CLAUDE.md`, and creates a new branch.
4. **Approval**: A Pull Request (PR) is opened on GitHub.
5. **Deployment**: Once merged to `main`, Vercel rebuilds the Quartz site.
6. **Sync**: Obsidian-Git pulls the new files to the local machine every 5 minutes.

## 3. Critical Keys & Secrets
- **Vercel Env Vars**: `CC_ROUTINE_ENDPOINT`, `CC_ROUTINE_TOKEN`, `SUBMIT_SECRET`.
- **GitHub Secrets**: `QUARTZ_DEPLOY_TOKEN` (if using GitHub Actions).
- **Obsidian Plugins**: `Obsidian Git`, `Copilot` (connected to Gemini 2.5-Flash).

## 4. Maintenance Tasks
- **Daily**: Review and merge pending Pull Requests.
- **Weekly**: Run a "Lint" command via Claude to fix dead links.
- **Monthly**: Rotate the `SUBMIT_SECRET` if the URL is leaked.
