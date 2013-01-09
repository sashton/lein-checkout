# lein-checkout

A Leiningen plugin to manage your checkouts without setting your hair on fire.

## Usage

Put `[lein-checkout "0.1.0-SNAPSHOT"]` into the `:plugins` vector of your
`:user` profile, or if you are on Leiningen 1.x do `lein plugin install
lein-checkout 0.1.0-SNAPSHOT`.

`checkout` searches the parent directory of the current project for projects by default. If you need fancier logic than that (i.e. you store your projects across multiple directories), you'll need to specify a `:checkout` key in your `project.clj` (for project by project configuration), or in your `:user` profile (for system wide configuration) which maps to a vector containing the absolute paths of directories which house your projects so that `checkout` can search there as well.

If your project tree looks like this

    .   
    `-- projects
        |-- a
        |-- b
        `-- c

And you're currently in project `a`, adding a checkout to project `b` would look like:

    $ lein checkout ln b

Adding a checkout to all projects would be:

    $ lein checkout ln .*

`PATTERN` arguments are passed directly to `re-matches`

Other tasks include:

    rm        [pattern]: Remove all checkouts. If PATTERN is specified, only checkouts matching that pattern will be removed
    enable    Enable checkouts.
    disable   Disable all checkouts for a moment.

## License

Copyright © 2013 Tim Visher

Distributed under the Eclipse Public License, the same as Clojure.
