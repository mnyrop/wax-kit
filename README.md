# wax-kit

> *NOTE: some things are not yet implemented, including:*
> - *Search build*
> - *Clobber individual item*
> - *Build individual item*

## Test Drive

1. Clone the repo
    ```sh 
    gh repo clone mnyrop/wax-kit && cd wax-kit
    ```
2. Run `bundle install`, which pulls in `wax_theme` and `wax_cli` via remote ruby gems.
3. Run `bundle exec wax --help` to see available commands and subcommands.
4. Run `bundle exec wax clobber demo` to remove demo derivatives (pages, images, wax json).
5. Replace the demo collection data your own `assets`, `records.csv`, and `dictionary.yml` that live in the `wax` folder within the project root:
    ```sh 
    .
    ├── Gemfile
    ├── README.md
    ├── _config.yml
    ├── _site
    └── source # the jekyll site source lives tidied here
        └── _data # the un-processed wax input data lives here
            └── demo
                ├── assets
                ├── dictionary.yml
                └── records.csv
    ```
    ~~>
    ```sh 
    .
    ├── .wax-cache
    ├── Gemfile
    ├── README.md
    ├── _config.yml
    ├── _site
    └── source # the jekyll site source lives tidied here
        └── _data
            └── my_collection # renamed!
                ├── assets # replaced!
                ├── dictionary.yml # replaced!
                └── records.csv # replaced!
    ```
6. Update your repo's config to reference your new collection `my_collection`:
    ```yaml
    collections:
      demo:
        output: true
        build:
          simple_images:
          iiif:
          pages: 
          search:
    ```
    ~~>
    ```yaml
    collections:
      my_collection: # renamed! that's it!
        output: true
        build:
          simple_images:
          iiif:
          pages: 
          search:
    ```
7. Run `bundle exec wax lint my_collection` to check for errors & warnings with my collection data & configuration. (e.g., missing id, invalid csv, unallowed column header/key, etc.)
8. Run `bundle exec wax build collection my_collection` which will run *all* the build tasks specified in the collection `build` config (in this case `simple_images`, `iiif`, `pages` and `search`) for the jekyll site to use.  It will also create/update the collection's `wax.json` state file with information about what's been done.
9. Later, if you want to (re)build a specific output for the collection (e.g., the pages), you can run the command with a flag, e.g.,
    ```sh
    bundle exec wax build collection my_collection --pages
    ```
    or
    ```
    bundle exec wax build collection my_collection --search
    ```
    which will build only that output type
    see:
    ```sh
      bundle exec wax build collection --help

      Usage:
        wax build collection NAME

      Options:
                  [--search], [--no-search]                # If true, builds a search index for the collection.
                  [--iiif], [--no-iiif]                    # If true, builds IIIF resources.
                  [--pages], [--no-pages]                  # If true, builds markdown page for each item.
                  [--simple-images], [--no-simple-images]  # If true, builds simple image derivatives.

      Build the wax collection named NAME
    ```
10. You can then build and serve my site with jekyll normally:
    ``` sh
    bundle exec jekyll serve
    ```
11. Look for includes and references to the `demo` collection in the kit source. Replace them with your new collection to get the galleries, banners, and more looking the way you want.

## Develop

The best way to rapidly develop `wax_cli` and/or `wax_theme` is to clone them locally, checkout the proper branch, and update `wax-kit`'s Gemfile to look for the local paths to load the gem(s) instead of the github branche(s). E.g., 

```rb
# gem 'wax_theme',  github: 'mnyrop/wax_theme',  branch: 'chore/wax_cli'
gem 'wax_theme',  path: 'wax_theme'
```

You'll need to rerun `bundle`. Make sure to avoid committing `wax-kit` with references to local gems! you'll need to put the original refs back when you're done.