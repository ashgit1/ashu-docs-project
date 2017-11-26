https://tekslate.com/build-and-release-engineer-interview-questions

What is the purpose of continuous integration for a development team?:
The primary purpose of CI is to provide regular, fast feedback to developers as they commit 
changes to the shared code repository (VCS).
The idea being that we’re always integrating our code on commit, so that when conflicts arise, 
they can be addressed more quickly and easily than if the changes had been made days, week, or even months ago.

Difference between CI/C-Del/C-Dep?:
What's your opinion?:

CI: Code is integarted at least once
C-Delivery: Code is continously delivered to lower environments as per our will
C-Deployment: Because of C-Delivery I have code that can be deployed to production.	

What technologies have you worked with for build management?:
Ant and Maven [mostly]

Difference between jar, war and ear?:
Jar is Java Archieve i.e compressed Class or Class / Java files.
War comprises of compressed Servlet class files,JSP FIles,supporting files, GIF and HTML files.
Ear comprise of compressed Java and web module files (was files).

Which version control system you are using in your current project?:
We are using SVN and Git Hub.

What's the heart of any version control system.? What is Repository?:
Repository is the heart of any version control system. 
It is central place where developers store all their work. 
Repository not only stores files but also history. Repository is accessed over a network, 
with repository acting as a sever and version control tool acting as a client. 
Client can connect to repository, and then they can store/retrieve their changes to/from repository.

What is a transitive dependency?:
Transitive dependency is the dependencies not defined directly in the current POM but the POM of the dependent projects.

Can we override Transitive Dependency version and If Yes, how?:
Yes, we can override transitive dependency version by specifying the dependency in the current POM.

What is the use of !! command? Can I use it with conjunction to some other string to complete a command?:
It’s used to execute last command. Yes, this can be used with other string to execute new command. 
For eg – if ls was the last command, we can execute !! -l for having the long listing.

What is the best practice configuration usage for files – pom.xml or settings.xml?:
configurations in settings.xml must be specific to the current user and that 
pom.xml configurations are specific to the project.

Maven Build Life Cycle, build phases and goals?:
default, clean and site

Ant Build Life Cycle? What are task, tagets and so on?:
Tasks, targets, depends, <javac> tag and so on

What is jacoco, how it is specified in build.xml?:
ResourceLocator project

Code Quality metrics, how sonar is configured in ant?:
ResourceLocator project

How can I change the default location of the generated jar when I command “mvn package”?:
By default, the location of the generated jar is in ${project.build.directory} or in your target directory. 
We can change this by configuring the outputDirectory of maven-jar-plugin.
on command line:
-DoutputDirectory=<path>
and in pom.xml:
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-jar-plugin</artifactId>
      <version>2.3.1</version>
      <configuration>
        <outputDirectory>/my/path</outputDirectory>
      </configuration>
    </plugin>
  </plugins>
</build>

What is Maven’s order of inheritance?:
parent pom
project pom
settings
CLI parameters

Maven CLI options:
http://maven.apache.org/ref/3.1.0/maven-embedder/cli.html
-X,--debug	Produce execution debug output
-f,--file <arg>	Force the use of an alternate POM file (or directory with pom.xml)
-e,--errors	Produce execution error messages
-h, --help produces help information

How do I determine which POM contains missing transitive dependency?:
run --> mvn -X

What is the difference between compile and install?:
Compile compiles the source code of the project
whereas
Install installs the package into the local repository, for use as a dependency in other projects locally
Install will run -> validate, compile, test, package and install

What is Jenkins?:
It is a continuous integration tool written in Java.

What is the difference between Maven, Ant and Jenkins?:
Maven and Ant Are Build Technologies whereas Jenkins is a continuous integration tool.

Which SCM or version control tools Jenkins supports?:
AccuRev, CVS, Subversion, Git, Mercurial, Perforce, Clear case and RTC

What are the various ways in which build can be scheduled in Jenkins?:
Builds can be triggered by source code management commits.
Can be triggered after completion of other builds.
Can be scheduled to run at specified time (crons)
Manual Build Requests


Maven skip test and ignore build failures:
-Dmaven.test.failure.ignore=true
-Dmaven.test.skip=true

mvn -rf and -pl options:?
rf (i.e. resume) from which you can resume your build from the module where it failed. 
So, if your build failed at myproject-commons you can run the build from this module by 
typing: mvn -rf myproject-commons clean install

pl Maven option helps you build specified reactor projects instead of building all projects.
if you need to build only two of your modules myproject-commons and myproject-service, 
you can type: mvn -pl myproject-commons, myproject-service clean install  

