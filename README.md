# jqueryui-amd

A conversion script for translating jQuery UI files into the style used by the [AMD API proposal](http://wiki.commonjs.org/wiki/Modules/AsynchronousDefinition). This API is usable in script loaders like [RequireJS](http://requirejs.org).

## How to Run It

The script requires Node 0.2.x (not tested on 0.3.x). Run the following command to generate the modules:

    node r.js convert.js path/to/jqueryui/source ./outputdir

## What happens

It is assumed a full source directory of jQuery UI is given to the conversion script. So, the directory should have a **ui** directory inside of it with the .js files for jQuery UI.

The example's jQueryUI directory was created with the following command (run from this directory):

    node r.js convert.js path/to/jquery-ui-1.8.7 ./example/webapp/scripts/jqueryui-1.8.7

Once the conversion script runs, it will create a few new files and directories. Taking the example above, the **example/webapp/scripts/jqueryui-1.8.7** directory above would have the following contents (items that can be deleted if you do not use them -- they are not strictly part of making the example work -- are marked with a (d) below):

* jqueryui-1.8.7
    * AUTHORS.txt
    * demos (d)
    * docs (d)
    * external (d)
    * GPL-LICENSE.txt
    * jquery-1.4.4.js (d)
    * jqueryui (directory created by convert)
    * jqueryui.js (file created by convert)
    * jqueryui-i18n.js (file created by convert)
    * MIT-LICENSE.txt
    * tests (d)
    * themes
    * ui (d)
    * version.txt

The conversion process transformed the following files:

* jqueryui-1.8.7/ui/jquery-ui.js --> jqueryui-1.8.7/jqueryui.js
* jqueryui-1.8.7/ui/jquery.ui.*.js --> jqueryui-1.8.7/jqueryui/*.js
* jqueryui-1.8.7/ui/jquery.effects.*.js --> jqueryui-1.8.7/jqueryui/effects/*.js
* jqueryui-1.8.7/ui/i18n/jquery.ui.datepicker-*.js --> jqueryui-1.8.7/jqueryui/datepicker-*.js
* jqueryui-1.8.7/ui/i18n/jquery-ui-i18n.js --> jqueryui-1.8.7/jqueryui-i18n.js

These file/path name changes were done to fit better with module path expectations, and to make it easier/less typing to load the files.

## Example

The **example** directory contains an example that includes a sample web project, in the **webapp** directory, along with the RequireJS optimizer, in the **requirejs** directory. Run the webapp/app.html file to see the example in action.

## Downloads

* [A zip file of theconverted 1.8.7 release](http://requirejs.org/jquery-amd/jquery-amd-1.8.7.zip).
* [A zip file of this complete directory, including conversion script and example project](http://requirejs.org/jquery-amd/jquery-amd.zip).


## Constraints

This script assumes a directory for jQuery UI contains a directory inside of it that has a jquery-ui.js file.

This script will need to be revisited if:

* the jquery-ui.js name changes.
* the naming convention of jquery.something.plugin.js changes.
* the i18n approach changes.
* more i18n files appear that are not for datepicker.
