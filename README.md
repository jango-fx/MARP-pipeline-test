---
marp: true
---

# MARP to GHPages
## publishing web slideshows from Markdown
thanks to [GitHub Marp CLI Action](https://github.com/marketplace/actions/marp-cli-action) by [KoharaKazuya](https://github.com/KoharaKazuya)

***
## 1. Create a Repo
### with MARP-formatted Markdown files

***
## 2. Add the Github Action
- `Actions` → `set up a workflow yourself`
- add the following code:
    ```
    name: MARP
    on:   
    push:
        branches: [ "main" ]
    jobs:
    publish:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v3
        - name: Convert Markdown into HTML and PDF
            uses: KoharaKazuya/marp-cli-action@v2
        - name: Deploy to GitHub Pages
            uses: peaceiris/actions-gh-pages@v3
            with:
            github_token: ${{ secrets.GITHUB_TOKEN }}
            publish_dir: ./
    ```

***
## 3. Grant writing permissions
- Repo-`Settings` → `Actions` → `General` → `Workflow permissions`
- enable `Read and write permissions`

***
## First Test
- push an update to the repository and 
- see if the action creates a new `gh-pages` branch

***
## 4. Activate Github Pages
- Repo-`Settings` → `Pages` → `Deploy from Branch`
- Select `gh-pages`

## Test your slideshow
under https://USERNAME.github.io/REPO