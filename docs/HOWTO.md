# HOWTO do all this stuff

## Directory [Structure][4]

```
project_root/
├── docs/
│   ├── index.md
│   └── other_pages.md
├── mkdocs.yml
```

## Useful [Commands][2]

1. Create a new project: `mkdocs new .`
2. Serve the documentation locally: `mkdocs serve`
3. Build the static site: `mkdocs build`
4. Deploy to GitHub Pages: `mkdocs gh-deploy`

## Pushing to GitHub with Material Theme

1. Ensure your `mkdocs.yml` includes the Material theme configuration.
   See parent directory.

2. Commit your changes:
```bash
git add .
git commit -m "Add Material theme and documentation"
```

3. Push to GitHub:
```bash
git push origin master
```

4. Deploy to GitHub Pages:
```bash
mkdocs gh-deploy
```

This command builds your site and pushes it to the `gh-pages` branch, making it available on [GitHub Pages][3] with the [Material theme][6].

[1]: https://timvink.github.io/mkdocs-table-reader-plugin/howto/project_structure/
[2]: https://www.mkdocs.org/user-guide/cli/
[3]: https://workbook.craftingdigitalhistory.ca/supporting%20materials/gh-pages/
[4]: https://realpython.com/lessons/create-mkdocs-project-structure/
[5]: http://yakworks.github.io/docmark/cheat-sheet/
[6]: https://github.com/marketplace/actions/deploy-mkdocs
[7]: https://www.mkdocs.org/user-guide/configuration/
[8]: https://www.mkdocs.org/getting-started/
