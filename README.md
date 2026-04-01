# Google Code Review Plugin

Claude Code plugin for automated PR code review following [Google's Engineering Practices](https://google.github.io/eng-practices/review/).

## What it does

Provides a `review-pr` skill that evaluates pull requests across 11 dimensions:

1. **Design** — Does the change integrate well with the system?
2. **Functionality** — Edge cases, concurrency, user impact
3. **Complexity** — Over-engineering, readability
4. **Tests** — Appropriate tests included and correct
5. **Naming** — Clear, descriptive names
6. **Comments** — Explain "why" not "what"
7. **Style** — Follows project conventions
8. **Documentation** — Updated where needed
9. **Every Line** — All human-written code reviewed
10. **Context** — Broader system impact
11. **Good Things** — Acknowledges what's done well

Findings are posted as inline GitHub review comments categorized by severity: Bug, Issue, Suggestion, Clarify, Nit.

## Usage in GitHub Actions

```yaml
- uses: anthropics/claude-code-action@v1
  with:
    anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
    prompt: "Review this pull request using the review-pr skill."
    plugins: |
      google-code-review
    plugin_marketplaces: |
      sebastianTostado/google-code-review-plugin
```

## Local installation

```
/plugin marketplace add sebastianTostado/google-code-review-plugin
/plugin install google-code-review
```
