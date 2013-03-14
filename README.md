ember-rhino-precompiler
=======================

In Java based environments where adding non-Java dependencies is not possible, developers can use this script to precompile Handlebar templates for Ember.js applications.

The inspiration for this script came from Yehuda Katz's reply to this
StackOverflow question: http://stackoverflow.com/questions/12054452/ember-js-helpers-and-handlebars-js-runtime-only-build/12336249#12336249

Dependencies
=======
* env.js v1.2
* jquery v1.9.1
* handlebars v1.0.0-rc.3
* ember v1.0.0-RC.1
* rhino v1.7R4

Usage
========
In a shell where the Rhino jar file is on the classpath, you can call the script like so:

<code>java -jar rhino-1.7R.jar org.mozilla.javascript.tools.shell.Main ember-rhino-precompiler.js --templatesDir /path/to/templates --outputFile /path/to/compiledfile.js</code>

Two additional arguments are required for this script to execute

--templatesDir, this specifies where your Handlebars templates are located

--outputFile, this specifies what file the generated code should be written to

The URIs to the JavaScript dependencies can be overridden from the shell as well. See the options object to see what other variables you can override.

Maven
========
<pre>
&lt;dependencies&gt;
  &lt;dependency&gt;
		&lt;groupId&gt;org.mozilla&lt;/groupId&gt;
		&lt;artifactId&gt;rhino&lt;/artifactId&gt;
		&lt;version&gt;1.7R4&lt;/version&gt;
	&lt;/dependency&gt;
&lt;/dependencies&gt;

&lt;plugins&gt;
  &lt;plugin&gt;
		&lt;groupId&gt;org.codehaus.mojo&lt;/groupId&gt;
		&lt;artifactId&gt;exec-maven-plugin&lt;/artifactId&gt;
		&lt;version&gt;1.1&lt;/version&gt;
		&lt;executions&gt;
			&lt;execution&gt;
				&lt;phase&gt;compile&lt;/phase&gt;
				&lt;goals&gt;
					&lt;goal&gt;java&lt;/goal&gt;
				&lt;/goals&gt;
			&lt;/execution&gt;
		&lt;/executions&gt;
		&lt;configuration&gt;
			&lt;mainClass&gt;org.mozilla.javascript.tools.shell.Main&lt;/mainClass&gt;
			&lt;classpathScope&gt;compile&lt;/classpathScope&gt;
			&lt;arguments&gt;
				&lt;argument&gt;https://raw.github.com/locnguyen/ember-rhino-precompiler/master/ember-rhino-precompiler.js&lt;/argument&gt;
				&lt;argument&gt;--envjs&lt;/argument&gt;
				&lt;argument&gt;src/main/webapp/resources/handlebars/env.rhino.1.2.js&lt;/argument&gt;
				&lt;argument&gt;--jquery&lt;/argument&gt;
				&lt;argument&gt;src/main/webapp/resources/jquery/jquery.min.js&lt;/argument&gt;
				&lt;argument&gt;--ember&lt;/argument&gt;
				&lt;argument&gt;src/main/webapp/resources/ember/ember-1.0.0-rc.1.js&lt;/argument&gt;
				&lt;argument&gt;--handlebars&lt;/argument&gt;
				&lt;argument&gt;src/main/webapp/resources/handlebars/handlebars-1.0.0-rc.3.js&lt;/argument&gt;
				&lt;argument&gt;--templatesDir&lt;/argument&gt;
				&lt;argument&gt;src/main/webapp/resources/javascripts/templates/&lt;/argument&gt;
				&lt;argument&gt;--outputFile&lt;/argument&gt;
				&lt;argument&gt;src/main/webapp/resources/javascripts/compiled-templates.js&lt;/argument&gt;
			&lt;/arguments&gt;
		&lt;/configuration&gt;
	&lt;/plugin&gt;
&lt;/plugins&gt;	
</pre>
  
