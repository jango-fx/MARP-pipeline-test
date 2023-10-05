---
marp: true
---

# MARP to GHPages
## publishing web slideshows from Markdown
thanks to [GitHub Marp CLI Action](https://github.com/marketplace/actions/marp-cli-action) by [KoharaKazuya](https://github.com/KoharaKazuya)

***
## 1. Create a Repo
### with the MARP-formatted Markdown files

***
## 2. Add Github Action
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
## 3. Activate Github Pages
1. Repo-`Settings` → `Pages` → `Deploy from Branch`
2. Select `gh-pages`