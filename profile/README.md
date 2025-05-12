# GitHub Workflow Guidelines

## Core Principles

1. **Quality Over Quantity**
   - Remember that one merged PR is more valuable than many pending PRs
   - Follow the KISS principle (Keep It Simple, Stupid): https://en.wikipedia.org/wiki/KISS_principle
   - All code and documentation must be in English for universal understanding

2. **Collaborative Development**
   - Reviewing is learning - reading others' code helps you understand different approaches and solutions
   - Pull Requests help improve code quality as no developer is perfect
   - Code isn't done until it's merged - local implementations aren't production-ready

## Branch Management

1. **Main Branch as the Source of Truth**
   - Use the "main" branch as your base branch for all work
   - The main branch should always contain stable, deployable code
   - All work must be done on separate branches branched from main

2. **No Direct Commits to Main**
   - All work must be done on separate branches
   - The main branch is protected - changes can only be made through Pull Requests
   - Merges to the main branch are the only way to deploy to production

3. **Branch Synchronization**
   - Keep your working branches updated with the main branch
   - Regularly pull changes from main into your branch to reduce merge conflicts
   - Resolve conflicts early and often rather than waiting until PR time

## Pull Request Process

1. **Creating Pull Requests**
   - Keep PRs as small as possible for easier review
   - Use draft PRs when work is still in progress to avoid notification spam
   - Convert to a regular PR only when ready for review
   - Break large features into smaller, logically separable PRs when possible

2. **PR Quality Requirements**
   - Include descriptive PR names and meaningful commit messages
   - PR descriptions must summarize changes, dependencies, deployment instructions, etc.
   - Resolve all issues identified by GitHub Action "AI Codium" before requesting review

3. **Self-Review**
   - The PR creator must review their own PR first before requesting others' reviews
   - Check for code quality, documentation, and potential issues

## Code Review Process

1. **Review Requirements**
   - Each PR requires at least 2 approvals before merging to main
   - Cross-team reviews are necessary to ensure code quality
   - Reviewers must actually review the code before approving - "blind" approvals are not acceptable

2. **Review Standards**
   - Follow conventional comments when reviewing: https://conventionalcomments.org/
   - Reviewers share responsibility as contributors to the codebase
   - Reviews should be constructive, not adversarial

## Code Organization and Quality

1. **Branch and Commit Management**
   - Use descriptive branch names that reflect the feature or fix (e.g., `feature/user-authentication` or `fix/login-timeout`)
   - Write atomic commits that focus on a single logical change
   - Consider using conventional commits format (https://www.conventionalcommits.org/) for better clarity

2. **Code Standards**
   - Include appropriate tests with all code changes
   - Document new features, APIs, or significant changes
   - Ensure code matches established project style guides and patterns

## Security Best Practices

1. **Protecting Sensitive Information**
   - NEVER commit secrets, API keys, credentials, or sensitive configuration directly to the repository
   - Use environment variables and secure secret management tools
   - Implement and enforce `.gitignore` to prevent accidental commits of sensitive files
   - Immediately rotate credentials if they are accidentally exposed

2. **Secrets and Credentials Management**
   - Use GitHub Secrets for storing sensitive information in CI/CD workflows
   - Avoid hardcoding any credentials in code or configuration files
   - Regularly audit and rotate access tokens and secrets

### If you accidentally commit a secret:
  1. Do NOT just delete the commit
  2. Immediately rotate all exposed credentials
  3. Remove the secret from the entire Git history using `git filter-branch`
  4. Notify the team

**Warning**: A single exposed secret can compromise entire systems. Always treat credentials and sensitive information with the highest level of care and caution.

## Additional Information

- These guidelines are mandatory for critical projects
- Balance thoroughness with development speed based on project requirements
- For more detailed information on Git usage: https://www.w3schools.com/git/
- For detailed information on GitHub PRs: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests
