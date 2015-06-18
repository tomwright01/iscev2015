# Reveal.js Template

This repository can be used to kickstart [Reveal.js](http://lab.hakim.se/reveal-js/)
presentations and host them on [Github Pages](http://pages.github.com/).

It also uses [Jinja](http://jinja.pocoo.org/) in order to split up the
`index.html` into smaller sub-files (i.e. one file per slide) and it uses
[Fabric](http://docs.fabfile.org/) to render your Jinja templates and publish
them to Github.


## Installation

In order to start a new presentation, do the following:

    git clone git@github.com:mbrochh/reveal-template.git
    cd reveal-template
    rm -rf .git
    git init
    git add .
    git commit -am "Initial commit"
    mkvirtualenv -p python2.7 reveal-template
    workon reveal-template
    pip install -r requirements.txt

Now you should have all necessary Python software installed.

The [Reveal.js](http://lab.hakim.se/reveal-js/) files are included as a submodule,
they are not downloaded when you cloned this repository. To download the files, do the following:

    git submodule init
    git submodule update

For further convenience you should install [observr](https://github.com/kevinburke/observr/)


## Usage

In order to build your presentation you will create and manipulate files in
the `source` folder. If you want to use Jinja templates to split up your
presentation, it would be cool to render the template into the `presentation`
folder every time you change something.

In order to run the file system watcher, execute:

    ./source-watcher.sh

If you don't want to use the file system watcher, you can trigger a build via

    fab build

Now make your changes in the source directory. When you are done, review your
changes:

    fab build
    open presentation/index.html

If all looks good, publish to Github:

    fab publish

## Update to the latest version of reveal.js

This project is pegged to reveal.js v3.0.0. To update to the latest version:

    cd presentation/reveal.js
    git submodule update --remote

## LICENSE

This repository is licensed under the [MIT license](https://github.com/hakimel/reveal.js/blob/master/LICENSE).
