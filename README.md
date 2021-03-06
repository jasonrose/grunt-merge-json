# grunt-merge-json-to-js

Grunt Task for Merging Multiple JSON Files into JS


## Getting Started

This plugin requires Grunt `~0.4.0`

If you haven't used [Grunt](http://gruntjs.com/)
before, be sure to check out the [Getting
Started](http://gruntjs.com/getting-started) guide, as it explains how
to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as
install and use Grunt plugins. Once you're familiar with that process,
you may install this plugin with this command:

```shell
npm install grunt-merge-json-to-js --save-dev
```

Once the plugin has been installed, it may be enabled inside your
Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-merge-json-to-js');
```

## Task Options

- `replacer`: (default `null`) the replacer argument for `JSON.stringify()` (second argument).
- `space`: (default `\t`) the space argument for `JSON.stringify()` (third argument).

## Merge JSON Task

_Run this task with the `grunt merge-json-to-js` command._

Task targets, files and options may be specified according to the Grunt
[Configuring tasks](http://gruntjs.com/configuring-tasks) guide.

## Usage Example

Assuming we have the following types of source JSON files:

- `src/foo/foo-en.json`:

```json
{
    "foo": {
        "title": "The Foo",
        "name":  "A wonderful component"
    }
}
```

- `src/bar/bar-en.json`:

```json
{
    "bar": {
        "title": "The Bar",
        "name":  "An even more wonderful component"
    }
}
```

Assuming we want to generate the following destination JS file:

```js
var translations = window.translations || {}; translations.en = {
    "foo": {
        "title": "The Foo",
        "name":  "A wonderful component"
    },
    "bar": {
        "title": "The Bar",
        "name":  "An even more wonderful component"
    }
}
```

### Single file per target variant

```js
grunt.initConfig({
    "merge-json-to-js": {
        "en": {
            src: [ "src/**/*-en.json" ],
            dest: "www/en.json"
        },
        "de": {
            src: [ "src/**/*-de.json" ],
            dest: "www/de.json"
        }
    }
});
```

### Multiple files per target variant

```js
grunt.initConfig({
    "merge-json-to-js": {
        "i18n": {
            files: {
                "www/en.json": [ "src/**/*-en.json" ],
                "www/de.json": [ "src/**/*-de.json" ]
            }
        }
    }
});
```

