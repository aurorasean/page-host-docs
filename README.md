# page-host-docs

This is a simplification of the 1 click deployment process using Github Pages as the artifacts and hosted result

![How page host works](<docs/page-host-How Page host works.drawio.png>)
## How the Page host works

You create a template with the template repo https://github.com/aurorasean/page-host-product-template

Fill in the secret PAT_TOKEN (this is not ideal but it's a demo)

When the resulting repo builds, it will make commits against the page-host repo https://github.com/aurorasean/page-host

And when that builds it will upload to Github Pages


# How 1ClickDeploy can work with almost anything

In a real setting, you wouldn't use Github Pages, you would have infrastructure requirements

![alt text](<docs/page-host-1CD in github with common action.drawio.png>)

## You need to reduce your deployment to it's simplest method

- If you have containers, reduce it to `docker tag`
  - Use Flux CD as an example with ImageReflection

- If you have a bucket, reduce it to `upload zip` 
  - Use Piral.io as your MFE host

- If you have a helm chart, reduce it to `helm upgrade`
  - Create an artifact of your helm chart, put it in a registry
  - then setup creds in your vault storage per asset, that lets that asset deploy to it's helm namespace

## When you team clicks deploy:

- Call a common action repo
- That contains the same instructions for all assets
- Pull creds for the given asset
- If you deploy with containers, `docker tag`

