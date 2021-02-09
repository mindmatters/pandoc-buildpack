# Pandoc Buildpack

A Heroku buildpack for [pandoc](http://pandoc.org).

It reads the requested pandoc version from the file `.pandoc-version` in the
app directory.

It is based on https://github.com/illustrativemathematics/pandoc-buildpack .

## Installation

To install this buildpack run:
```
heroku buildpacks:add https://github.com/mindmatters/pandoc-buildpack.git -a your-app-name
```
The buildpack will be installed on your next push to the app.

## What It Does

* The buildpack script downloads a prebuilt tar archive
from the [pandoc repository](https://github.com/jgm/pandoc/releases).
    * If the tar archive already exists in the heroku buildpack cache, the cached
      version will be used instead.
* The script then extracts the `pandoc` binary from this archive into `/app/vendor/pandoc`.
* Finally, the script adds `/app/vendor/pandoc` to the `PATH`.

For details, see the script in [bin/compile](https://github.com/mindmatters/pandoc-buildpack/blob/master/bin/compile).
