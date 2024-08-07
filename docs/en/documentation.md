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


See https://squidfunk.github.io/mkdocs-material/getting-started/ for more informations on how the documentation builder works.



