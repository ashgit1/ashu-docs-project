# Advance Maven Commands:

##### Super pom:

>The super pom contains the configuration details like where the source code is kept for compiling and so on(like default source directory, default test directory, default target directory and so on).

>The super pom also contains plugins like 'compiler plugin', 'sure-fire plugin' which we get for free.

>The most important section is the repository section which defines the Central maven repo from where the dependencies are downloaded.
`It's just like the Object class in java which is the super class of all the classes.`

##### Effective pom:
>The effective pom is the combination of `super pom and our pom`.
`mvn help:effective-pom`
--> displays the effective pom

example:
>`mvn help:effective-pom -Doutput=effective-pom.xml`
--> stores the effective pom in the file effective-pom.xml

##### Effective settings:
>`mvn help:effective-settings`
display the effective settings on the console

example:
>`mvn help:effective-settings -Doutput=effective-settings.xml`
stores the effective settings in to a file effective-settings.xml
`The most important settings in this file is the <localRepository> which defines the path where dependencies are stored after download.`

### Plugins:
>Plugins helps you to customize your build. 
If you want to compile your code by using java 1.8 rather than the default 1.5 in eclipse you can override the `maven-compiler-plugin` which comes in the effective pom and add that plugin in your project pom.

example:
```
<build>
	<plugins>
		<plugin>
			<artifactId>maven-compiler-plugin</artifactId>
    		<version>3.2</version>
    		<configuration>
    			<source>1.8</source>
    			<target>1.8</target>
    		</configuration>
		</plugin>
	</plugins>
</build>
```

>Another important tag in the plugin section is the <phase> tag which tells during which build phase the plugins are invoke.
ex: `<phase>compile</phase>, <phase>test</phase>`

### Run Tomat configured in pom.xml:
> `mvn tomcat7:run`
<contextReloadable>true</contextReloadable>
--> Reloads the content instantly witout restarting the server.

### How to skip tests:
>`mvn clean install -DskipTests=true`

### How to run maven in debug mode:
>`mvn -X clean install`

>To troubleshoot save the output of debug in a txt file incase you are not able to figure out the problem.
`mvn -X clean install > maven-debug.txt`

### Dependency tree for a project:
>`mvn dependency:tree`
This shows the entire dependency tree for a project.

### Download the source code for the dependencies:
>`mvn dependency:sources`

### Help Command:
>`mvn --help`

### Maven rf option:
>Most of us work in a multi-module environment and it happens very often that a build fails at some module. It's a big pain to rerun the entire build. To save you from going through this pain, Maven has an option called rf (i.e. resume) from which you can resume your build from the module where it failed. So, if your build failed at `myproject-commons` you can run the build from this module by typing:
`mvn -rf myproject-commons clean install`

### Maven pl option:
>The `pl` Maven option helps you build specified reactor projects instead of building all projects. For example, if you need to build only two of your modules `myproject-commons` and `myproject-service`, you can type:
`mvn -pl myproject-commons, myproject-service clean install`
This command will only build commons and service projects.

### Maven Classifiers:
>We all know about qualifiers `groupId`, `artifactId`, `version` that we use to describe a dependency but there is fourth qualifier called `classifier`. 
It allows distinguishing two artifacts that belong to the same POM but were built differently, and is appended to the filename after the version. 

>For example, if you want to build two separate jars, one for Java 5 and another for Java 6, you can use classifier. It lets you locate your dependencies with the further level of granularity.

```
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <scope>test</scope>
    <classifier>jdk16</classifier>
</dependency>
```

### Dependency Version Ranges:
>Have you ever worked with a library that releases too often when you want that you should always work with the latest without changing the pom. It can be done using dependency version changes. 

>So, if you want to specify that you should always work with the version above a specified version, you will write:
`<version>[1.1.0,)</version>`
`This line means that the version should always be greater than or equal to 1.1.0`

