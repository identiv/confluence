A Github action to generate a markdown file into a Confluence page.

This uses the tool in repo `https://github.com/kovetskiy/mark`

The 'secret sauce' that makes it work are `md` tags **that github does not render**

Here is the raw content for the Enterphone Hardware `hardware.md` - you can now see the meta

```
<!-- Space: APD -->
<!-- Parent: About the Engineering Project Documentation Space -->
<!-- Parent: Physical Access Control (Mark A.) -->
<!-- Parent: Viscount Access Control -->
<!-- Parent: Enterphone -->
<!-- Title: Enterphone Hardware -->
<!-- Attachment: ./identiv_iQ_back.pdf -->
<!-- Attachment: ./identiv_iQ_front.pdf -->
<!-- Attachment: ./identiv_mesh19_back.pdf -->
<!-- Attachment: ./identiv_mesh19_front.pdf -->
<!-- Attachment: ./enterphone_19_mounting.svg -->
<!-- Attachment: ./enterphone_iq_mounting.svg -->
<!-- Attachment: ./enterphone_19_mounting.png -->
<!-- Attachment: ./enterphone_iq_mounting.png -->
<!-- Attachment: ./Enterphone_Mounting_Requirements.pdf -->
<!-- Attachment: ./Enterphone_19.pdf -->
<!-- Attachment: ./Enterphone_IQ.pdf -->

# Enterphone Hardware

## Drawings 
### Enterphone IQ 
* [Back](./identiv_iQ_back.pdf)
* [Front](./identiv_iQ_front.pdf)
* [Inside](./Enterphone_IQ.pdf)
* Mounting:
  * [PNG](./enterphone_iq_mounting.png)
  * [SVG](./enterphone_iq_mounting.svg)

### Enterphone 19"
* [Back](./identiv_mesh19_back.pdf)
* [Front](./identiv_mesh19_front.pdf)
* [Inside](./Enterphone_19.pdf)
* Mounting:
  * [PNG](./enterphone_19_mounting.png)
  * [SVG](./enterphone_19_mounting.svg)

### Mounting

* [Mounting Requirements](./Enterphone_Mounting_Requirements.pdf) -- see also above
```


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
