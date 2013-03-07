ember-rhino-precompiler
=======================

In Java based environments where adding non-Java dependencies is not possible, developers can use this script to precompile Handlebar templates for Ember.js applications.

Dependencies
=======
env.js v1.2
jquery v1.9.1
handlebars v1.0.0-rc.3
ember v1.0.0-RC.1
rhino v1.7R4

Usage
========
In a shell where the Rhino jar file is on the classpath, you can call the script like so:

<code>java -jar rhino-1.7R.jar org.mozilla.javascript.tools.shell.Main ember-rhino-precompiler.js --templatesDir /path/to/templates --outputFile /path/to/compiledfile.js</code>

Two additional arguments are required for this script to execute

--templatesDir, this specifies where your Handlebars templates are located

--outputFile, this specifies what file the generated code should be written to

The URIs to the JavaScript dependencies can be overridden from the shell as well. See the options object to see what other variables you can override.
