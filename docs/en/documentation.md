# Contribute to the documentation

Documentation is written in markdown and the website is statically built using [Mkdocs material](https://squidfunk.github.io/mkdocs-material/)

NOTE: New languages, better wording, new sections, more visuals, any fixes even small ones are welcome!

## How to contribute ?
- Create a Github account
- Fork the Agorakit repository
- Edit the documentation files in the /docs/ directory
- Create a pull request to ask your changes to be merged

TIP: Using [Visual Studio Code](https://code.visualstudio.com/) to work on code and markdown files is a reasonably simple option. You additionaly get a built in user interface for git and github integration, which is nice for beginners.

## How to build the docs ?
Install mkdocs material and a few plugins. 


    pip install mkdocs-material
    pip install markdown-callouts
    pip install mkdocs-static-i18n


Then start the built-in webserver to preview your work on the documentation.

    mkdocs serve


The documentation is currently served by github pages. The workflow for publication is localted here : https://github.com/agorakit/documentation/actions/workflows/ci.yml

How this works ?
Each time a commit is made on main or master branch, the doc are built using https://github.com/mhausenblas/mkdocs-deploy-gh-pages
(this is a git action that does the work for us)

The resulting files are put into the GH-branch of the documentation repository which is then serbed using the github "pages" feature.

It's a bit painful to configure but it seems that once done, it works.


See https://squidfunk.github.io/mkdocs-material/getting-started/ for more informations on how the documentation builder works.



