# Security

At GitNotebooks, we take the security of your data and code seriously. This document outlines our security practices and explains the permissions we request.

## Code Privacy

**Your code never touches our servers.**

Here's how it works:

- All files are fetched directly from GitHub to your browser
- Diffs are performed client-side in your browser
- We do not fetch, store, or process your code on our servers

## GitHub Permissions

We request certain GitHub permissions to provide GitNotebooks functionality. Here's why we need each permission:

- Repository (Read)

  - Generate access tokens that allow your browser to fetch pull request files directly from GitHub
  - Enable viewing and diffing of code within GitNotebooks

- Repository (Write)

  - Enable resolving conversations in pull requests
  - We never write to your repositories for any other purpose

  **Note:** We're actively tracking [GitHub's progress](https://github.com/orgs/community/discussions/12961) on creating a separate, more limited permission for this functionality.

- Pull Request (Write)

  - Post comments on pull requests
  - Submit reviews

- Metadata (Read)
  - Fetch pull request information (e.g., who opened it, current status)
  - Display relevant context within GitNotebooks

## Questions or Concerns?

If you have any questions about our security practices or the permissions we request, please don't hesitate to contact us at `support@gitnotebooks.com`.
