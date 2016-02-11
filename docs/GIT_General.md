
## Git basic commands

### How to add a new mkdocs note in your GitHub repository

From your docs folder, type:
```bash
vi example.md
git add example.md
git commit -m "my example note on GitHub"
git push
cd ..
mkdocs gh-deploy
```

Please find [here](https://guides.github.com/features/mastering-markdown/) the specific markdown syntax for GitHub.

More information about mkdocs are available:
* [Official Website](http://www.mkdocs.org)
* Customize the color of [code blocs](https://highlightjs.org/static/demo/) with some [CSS](https://github.com/isagalaev/highlight.js/tree/master/src/styles)
