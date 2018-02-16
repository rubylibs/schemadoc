# schemadoc

schemadoc gem - document your database schemas (tables, columns, etc.)

* home  :: [github.com/schemadoc/schemadoc](https://github.com/schemadoc/schemadoc)
* bugs  :: [github.com/schemadoc/schemadoc/issues](https://github.com/schemadoc/schemadoc/issues)
* gem   :: [rubygems.org/gems/schemadoc](https://rubygems.org/gems/schemadoc)
* rdoc  :: [rubydoc.info/gems/schemadoc](http://rubydoc.info/gems/schemadoc)



## Usage Command Line

The `schemadoc` gem includes a command line tool
named - surprise, surprise - `schemadoc`. Try:

```
$ schemadoc --help
```

resulting in:

```
schemadoc 1.0.0 - Lets you document your database tables, columns, etc.

Usage: schemadoc [options]
    -o, --output PATH            Output path (default is '.')
    -v, --verbose                Show debug trace

Examples:
  schemadoc                # defaults to ./schemadoc.yml
  schemadoc football.yml
```


## Configuration

The `schemadoc` command line tool
requires a configuration file (defaults to `./schemadoc.yml` if not
passed along).

**Database Connection Settings - `database` Section**

Use the `database` section to configure you database connection settings.
Example:

```
database:
  adapter:  sqlite3
  database: ./football.db
```

**Schema Sections**

All other sections are interpreted as database schemas.
The first section is the "default" schema,
that is, all tables not listed in other schemas will get auto-added
to the "default" schema.


**Example - `schemadoc.yml`**

```
## connection spec

database:
  adapter:  sqlite3
  database: ./football.db


## main tables

football:
  name: Football


## world tables

world:
  name: World
  tables:
    - continents
    - countries
    - regions
    - cities
    - places
    - names
    - langs
    - usages
```


## Outputs

The `schemadoc` tool writes out two json files:

- `database.json`  - includes all schemas, tables, columns, etc.
- `symbols.json`   - includes all symbols from a to z


**Examples.**
See the football.db -
[`database.json`](https://github.com/openfootball/schema/blob/master/_data/database.json),
[`symbols.json`](https://github.com/openfootball/schema/blob/master/_data/symbols.json)
or beer.db -
[`database.json`](https://github.com/openbeer/schema/blob/master/_data/database.json),
[`symbols.json`](https://github.com/openbeer/schema/blob/master/_data/symbols.json)
live examples.


## Reports 'n' Templates

To generate web pages from you json files use a static site generator and
a template pack (theme). For example, to use the `schemadoc/schemadoc-theme` theme
copy your json files in the `_data/` folder and rebuild the site (e.g. $ `jekyll build`).
That's it. Enjoy your database schema docu.

**Examples.**
See the [football.db](http://openfootball.github.io/schema/)
or [beer.db](http://openbeer.github.io/schema/) live examples.


## Free Schemadoc Template Packs / Themes

- [`schemadoc/schemadoc-theme`](https://github.com/schemadoc/schemadoc-theme) - free schemadoc theme; works w/ Jekyll (and GitHub Pages) static site generator


## Install

Just install the gem:

```
$ gem install schemadoc
```

In addition, install `Active Record` and your database adapter's gem such as `mysql2`

```
$ gem install activerecord
$ gem install mysql2
```


## License

![](https://publicdomainworks.github.io/buttons/zero88x31.png)

The `schemadoc` scripts are dedicated to the public domain.
Use it as you please with no restrictions whatsoever.
