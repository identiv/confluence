# Confluence GHA

This is a reusable GitHub Action which translates a Markdown file into a Confluence
page.

This makes it simple to translate code documentation into public or internal pages
in Confluence. This is an example of usage:

```
jobs:
  generate-confluence-page:
    runs-on: ubuntu-latest
    name: A job to generate Confluence page
    steps:
    - name: Generate confluence page
      uses: identiv/confluence@v1
      with:
        source: README.md
        url: https://identivegroup.atlassian.net/wiki
        conf-account: ${{ secrets.CONFLUENCE_ACCOUNT }}
        conf-api-key: ${{ secrets.CONFLUENCE_API_KEY }}
```
