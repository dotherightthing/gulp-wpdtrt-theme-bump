# gulp-wpdtrt-theme-bump

[![GitHub release](https://img.shields.io/github/release/dotherightthing/gulp-wpdtrt-theme-bump.svg?branch=master)](https://github.com/dotherightthing/gulp-wpdtrt-theme-bump/releases) [![Build Status](https://travis-ci.org/dotherightthing/gulp-wpdtrt-theme-bump.svg?branch=master)](https://travis-ci.org/dotherightthing/gulp-wpdtrt-theme-bump) [![GitHub issues](https://img.shields.io/github/issues/dotherightthing/gulp-wpdtrt-theme-bump.svg)](https://github.com/dotherightthing/gulp-wpdtrt-theme-bump/issues)

Updates a fixed selection of files in either [dotherightthing/wpdtrt](https://github.com/dotherightthing/wpdtrt/), or a [generated child](https://github.com/dotherightthing/generator-wp-theme-boilerplate), using the version information in `package.json`.

## Installation

```
yarn add https://github.com/dotherightthing/gulp-wpdtrt-theme-bump --dev
```

## Usage

As used in [wpdtrt's gulpfile.js](https://github.com/dotherightthing/wpdtrt/blob/master/gulpfile.js):

```
var wpdtrtThemeBump = require('gulp-wpdtrt-theme-bump');

var themeName = process.cwd().split("/").pop();

gulp.task("bump_replace", function () {

    "use strict";

    taskheader(
        "Version",
        "Bump",
        "Replace version strings"
    );

    // if run from wpdtrt:
    // gulp bump
    var root_input_path = "";
    var wpdtrt_theme_boilerplate_input_path = "";

    // if run from a child theme:
    // gulp bump
    // --gulpfile ./vendor/dotherightthing/wpdtrt/gulpfile.js --cwd ./
    if (themeName !== "wpdtrt") {
        root_input_path = "";
        wpdtrt_theme_boilerplate_input_path = "vendor/dotherightthing/wpdtrt/";
    }

    return wpdtrtThemeBump({
        root_input_path: root_input_path,
        wpdtrt_theme_boilerplate_input_path: wpdtrt_theme_boilerplate_input_path
    });
});
```

## Tests

```
// install test dependencies
yarn install

// run tests
yarn test
```