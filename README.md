# Clearpath Accessibility — GitHub Action

Run accessibility checks on every commit and get a per-deploy regression diff
posted straight to your pull request. Merge-blocking is configurable per project
in your Clearpath dashboard.

```yaml
# .github/workflows/accessibility.yml
name: Accessibility
on: [pull_request]

jobs:
  clearpath:
    runs-on: ubuntu-latest
    steps:
      - uses: qashift/clearpath-action@v1
        with:
          urls: ${{ env.PREVIEW_URL }}        # or a comma-separated list
          token: ${{ secrets.CLEARPATH_INGEST_TOKEN }}
```

Add your project's ingest token (from the Clearpath dashboard) as the
`CLEARPATH_INGEST_TOKEN` repository secret. Set the merge-blocking policy
(off / new / new-or-worsened) in the project's settings.

The check runs in **your** runner, so usage stays flat and unlimited.
