# Copilot access cost comparison

A single-page calculator that compares the monthly cost of Copilot Business or
Copilot Enterprise with the Copilot access billing model GitHub announced on
28 October 2026.

Everything is in `index.html`. There is no build step and no dependency other
than a web font loaded from Google Fonts.

## Publish with GitHub Pages

1. Put `index.html` in the root of a repository.
2. In the repository, open Settings, then Pages.
3. Under "Build and deployment", choose "Deploy from a branch", pick `main` and
   `/ (root)`, and save.

The page is then served at `https://<account>.github.io/<repository>/`.

## Updating the rates

List prices live in one object near the top of the script in `index.html`:

```js
var LIST = { bp: 19, ba: 1900, ep: 39, ea: 3900, sf: 10, cv: 0.01 };
```

| Key  | Meaning                                    |
|------|--------------------------------------------|
| `bp` | Copilot Business seat, USD a month         |
| `ba` | Copilot Business AI credits per user       |
| `ep` | Copilot Enterprise seat, USD a month       |
| `ea` | Copilot Enterprise AI credits per user     |
| `sf` | Copilot Standalone, USD per user a month   |
| `cv` | Value of one AI credit, USD                |

When you change them, also update the "checked" date in the Rates panel and the
figures quoted in the "What GitHub has published" notes.

Sources, last checked 5 November 2026:

- https://docs.github.com/en/copilot/get-started/whats-changing-with-github-enterprise-and-copilot
- https://docs.github.com/en/copilot/get-started/plans
- https://docs.github.com/en/copilot/reference/copilot-billing/models-and-pricing

## How the comparison is worked out

- Today: seats × seat price, plus any credits used beyond the pooled allowance
  (seats × credits per user) at the credit value.
- Copilot access: users without a GitHub Enterprise Cloud licence × the Copilot
  Standalone price, plus all credits used at the credit value.

## Shareable links

The inputs are stored in the URL after `#`, so a link reproduces an estimate.
Nothing is sent to a server.
