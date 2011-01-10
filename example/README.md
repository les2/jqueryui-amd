## jquery-amd example

This is an example that includes a sample web project, in the **webapp** directory, along with the RequireJS optimizer, in the **requirejs** directory. Load the webapp/app.html file in the browser to see the example in action.

To run the optimizer for this example, if you are in the directory that contains this file:

    requirejs/build/build.sh webapp/scripts/app.build.js

That will generate a **webapp-build** directory that is a sibling to **webapp-build** which will include an optimized scripts/main.js file. The Datepicker and its French localization will still be loaded on demand as separate files.
