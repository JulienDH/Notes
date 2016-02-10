
### Git basic commands

#### How to add a new mkdocs note in your GitHub repository

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

More information about mkdocs are available [here](http://www.mkdocs.org).
