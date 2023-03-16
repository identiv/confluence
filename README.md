A Github action to generate a markdown file into a Confluence page.

This uses the tool in repo `https://github.com/kovetskiy/mark`

The 'secret sauce' that makes it work are `md` tags **that github does not render**

[HERE](https://raw.githubusercontent.com/identiv/enterphone-hardware/main/Hardware.md?token=GHSAT0AAAAAAB2JUOJ2TMHAOQ34345DE4TUZASWRGQ) is the raw content for the Enterphone Hardware `Readme.md` - you can now see the meta


Example usage

```
jobs:
  generate-confluence-page:
    runs-on: ubuntu-latest
    name: Generate Confluence pages
    steps:
    - name: Publish docs
      uses: identiv/confluence@v1
      with:
        source: '*.md'
        url: https://identivegroup.atlassian.net/wiki
        conf-account: 'your identiv email addr'
        conf-api-key: ${{ secrets.CONFLUENCE_TOKEN }}
```

You can generate a `confluence_token` [here](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/)
