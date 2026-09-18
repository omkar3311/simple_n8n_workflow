# Simple n8n Workflow

This repository contains an n8n automation that generates a daily programming learning note using an LLM and commits it back into the GitHub repository.

It is designed to help maintain a habit of learning by automatically creating short, useful programming notes and storing them in a Markdown file (`test.md`).

## What this workflow does

When the workflow runs, it:

- triggers either manually or on a scheduled time
- calls a Groq-hosted LLM model
- asks it to generate a short daily programming concept/note
- processes the returned content
- reads the current GitHub file contents
- prepares the updated Markdown content
- commits the change back to the repository via the GitHub API

This is a simple example of combining n8n, GitHub, and LLM-powered automation.

## Repository contents

- `daily_commit_with_trigger.json` — workflow configured with a scheduled trigger
- `daily_commit_without_trigger.json` — workflow version that runs only when manually executed
- `test.md` — sample generated learning notes stored in Markdown

## Example workflow behavior

The workflow uses:

- GitHub API to fetch and update repository content
- Groq API / OpenAI-compatible chat completions endpoint to generate notes
- n8n Code node to parse LLM output and prepare file updates
- GitHub credentials configured inside n8n

The generated content includes short learning topics such as:

- closures
- variable scope
- immutability
- DRY principle
- async/await
- SQL injection prevention
- testing edge cases

## Prerequisites

Before importing or running the workflow, make sure you have:

- n8n installed and running
- a GitHub account and personal access token or OAuth credential configured in n8n
- a Groq account and API key
- permission to write to this repository

## Setup instructions

1. Open n8n and import one of the workflow JSON files:
   - `daily_commit_with_trigger.json` for scheduled execution
   - `daily_commit_without_trigger.json` for manual execution
2. Configure the GitHub credential in n8n.
3. Configure the Groq API credential in n8n.
4. Verify the repository path in the workflow is correct:
   - `omkar3311/simple_n8n_workflow`
   - file target: `test.md`
5. Save and activate the workflow if using the scheduled version.
6. Run the workflow manually or wait for the configured schedule.

## Scheduling

The scheduled workflow uses an `n8n-nodes-base.scheduleTrigger` node.

It is currently configured to run at a specified hour, which you can modify in n8n based on your preferred daily schedule.

## Notes

- This project is intended as a lightweight automation example.
- The generated content is stored as plain Markdown for easy review in GitHub.
- The workflow is flexible and can be adapted to different repository paths, file names, or LLM prompts.

## Use cases

This pattern can be adapted for:

- daily AI-generated development notes
- automated knowledge logs
- repository documentation updates
- scheduled content generation in GitHub repos

## Summary

This repository is a compact n8n automation that turns a GitHub repository into a daily learning journal powered by an LLM. It demonstrates how to automate documentation generation and commit updates directly back to a repository.
