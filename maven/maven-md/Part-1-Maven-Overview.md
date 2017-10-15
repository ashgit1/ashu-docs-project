# Maven Tutorial:

>Apache Maven is a software project management tool. Based on the concept of a project object model (POM), Maven can manage a project's build, reporting and documentation.
>A POM file is an XML representation of project resources like source code, test code, dependencies (external JARs used) etc. 

### The POM contains references to all of these resources:
| Element | Description |
| ------ | ------ |
| project | It is the root element of pom.xml file |
| modelVersion | It is the sub element of project. It specifies the modelVersion. It should be set to 4.0.0. since it matched Maven version 2 and 3|
| groupId | It is the sub element of project. It specifies the id for the project group |
|artifactId| It is the sub element of project. It specifies the id for the artifact (project). An artifact is something that is either produced or used by a project. Examples of artifacts produced by Maven for a project include: JARs, source and binary distributions, and WARs.|
|version|It is the sub element of project. It specifies the version of the artifact under given group.|

Sample pom.xml
```
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
                      
  <modelVersion>4.0.0</modelVersion>
    <groupId>com.ashish</groupId>
    <artifactId>java-web-app</artifactId>
    <version>1.0.0</version>
  
</project>
```

# Maven pom.xml file with additional elements:

Here we are going to add other elements in pom.xml file such as:  

| Element | Description |
| ------ | ------ |
|packaging|defines packaging type such as jar, war etc|
|name|defines name of the maven project|
|url|defines url of the project|
|dependencies | defines dependencies for this project|
|dependency   | defines a dependency. It is used inside dependencies|
|scope      | defines scope for this maven project. It can be compile, provided,   runtime, test and system.|

Sample pom.xml with above elements:
```
<project xmlns="http://maven.apache.org/POM/4.0.0"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0   
http://maven.apache.org/xsd/maven-4.0.0.xsd">  
  
  <modelVersion>4.0.0</modelVersion>  
  
  <groupId>com.ashish</groupId>  
  <artifactId>java-web-app</artifactId>  
  <version>1.0.0</version>  
  <packaging>war</packaging>  
  
  <name>Maven Java Web App</name>  
  <url>http://maven.apache.org</url>  
  
  <dependencies>  
    <dependency>  
      <groupId>junit</groupId>  
      <artifactId>junit</artifactId>  
      <version>4.8.2</version>  
      <scope>test</scope>  
    </dependency>  
  </dependencies>  
  
</project>
```

### In a Nutshell:
>The `modelVersion` element sets what version of the POM model you are using. Use the one matching the Maven version you are using. Version 4.0.0 matches Maven version 2 and 3.

>The groupId element is a unique ID for an organization, or a project (an open source project, for instance). The group ID `com.ashish` would then be located in a directory called `MAVEN_REPO/com/ashish`. The `MAVEN_REPO` part of the directory name will be replaced with the directory path of the Maven repository. 

>The `artifactId` element contains the name of the project you are building. 
In the case of my Java Web App project, the artifact ID would be `java-web-app`. 
The artifact ID is used as name for a subdirectory under the group ID directory in the Maven repository. 
The artifact ID is also used as part of the name of the JAR file produced when building the project. 

>The output of the build process, the build result that is, is called an `artifact` in Maven. Most often it is a JAR, WAR or EAR file, but it could also be something else. 

>The `versionId` element contains the version number of the project. If your project has been released in different versions, for instance an open source API, then it is useful to version the builds. That way users of your project can refer to a specific version of your project.  `The version number is used as a name for a subdirectory under the artifact ID directory. The version number is also used as part of the name of the artifact built.` 

### Output:

The above `groupId`, `artifactId` and `version` elements would result in a `WAR` file being built and put into the local Maven repository at the following path (directory and file name):
`MAVEN_REPO/com/ashish/java-web-app/1.0.0/java-web-app-1.0.0.war`

# Super POM:
>All Maven POM files inherit from a super POM. If no super POM is specified, the POM file inherits from the base POM.
>You can make a POM file explicitly inherit from another POM file. That way you can change the settings across all inheriting POM's via their common super POM.
>Default location of super pom in version 3.3.9: `lib/maven-model-builder-3.3.9.jar:org/apache/maven/model/pom-4.0.0.xml`

# Effective POM: 
>This command will make Maven write out the effective POM to the command line prompt
`mvn help:effective-pom`

# Maven Settings File:
>You can configure settings for Maven across all Maven POM files. 
>The settings files is called `settings.xml`. 
For instance, you can configure:

- Location of local repository
- Active build profile

##### The two settings files are located at:
- The Maven installation directory: `$M2_HOME/conf/settings.xml`
- The user's home directory: `${user.home}/.m2/settings.xml`

```
Both files are optional. If both files are present, the values in the user home settings file overrides the values in the Maven installation file. 
```

# Maven Directory Structure:
```
- src
  - main
    - java
    - resources
    - webapp
  - test
    - java
    - resources

- target
```

>If you follow that directory structure for your project, you do not need to specify the directories of your source code, test code etc.

>The `src` directory is the root directory of your source code and test code. The `main` directory is the root directory for source code related to the application itself (not test code). 

>The `test` directory contains the test source code. The `java` directories under main and test contains the Java code for the application itself (under main) and the Java code for the tests (under test).

>The `resources` directory contains other resources needed by your project. This could be `property files used for internationalization of an application`, or something else.

>The `webapp` directory contains your Java web application, if your project is a web application. The webapp directory will then be the root directory of the web application. 
`Thus the webapp directory contains the WEB-INF directory etc.`

>The `target` directory is created by Maven. It contains all the compiled classes, JAR files etc. produced by Maven. 

>When executing the `clean` build life cycle, it is the target directory which is cleaned.  
# Project Dependencies:
>Unless your project is small, your project may need external Java APIs or frameworks which are packaged in their own JAR files. These JAR files are needed on the classpath when you compile your project code. 

> Maven has built-in dependency management. You specify in the POM file what external libraries your project depends on, and which version, and then Maven downloads them for you and puts them in your local Maven repository. 

>If any of these external libraries need other libraries, then these other libraries are also downloaded into your local Maven repository. 

##### You specify your project dependencies inside the dependencies element in the POM file:

```
<dependencies>
        <dependency>
          <groupId>org.jsoup</groupId>
          <artifactId>jsoup</artifactId>
          <version>1.7.1</version>
        </dependency>

        <dependency>
          <groupId>junit</groupId>
          <artifactId>junit</artifactId>
          <version>4.8.1</version>
          <scope>test</scope>
        </dependency>
</dependencies>
```

>Each dependency element describes an external dependency. 
Each dependency is described by its groupId, artifactId and version. You may remember that this is also how you identified your own project in the beginning of the POM file. The example above needs the org.jsoup group's jsoup artifact in version 1.7.1, and the junit group's junit artifact in version 4.8.1. 

>When this POM file is executed by Maven, the two dependencies will be downloaded from a central Maven repository and put into your local Maven repository. 

>If the dependencies are already found in your local repository, Maven will not download them. `Only if the dependencies are missing will they be downloaded into your local repository.`

# Missing Dependencies:
>Sometimes a given dependency is not available in the central Maven repository. You can then download the dependency yourself and put it into your local Maven repository. 
Remember to put it into a subdirectory structure matching the groupId, artifactId and version. `Replace all dots (.) with / and separate the groupId, artifactId and version with / too.` 
Then you have your subdirectory structure.

>The two dependencies downloaded by the example above will be put into the following subdirectories:
`MAVEN_REPOSITORY_ROOT/junit/junit/4.8.1`
`MAVEN_REPOSITORY_ROOT/org/jsoup/jsoup/1.7.1`

# External Dependencies:
>An external dependency in Maven is a dependency (JAR file) which is not located in a Maven repository (neither local, central or remote repository). It may be located somewhere on your local hard disk, for instance in the lib directory of a webapp, or somewhere else.

You configure an external dependency like this:
```
<dependency>
  <groupId>mydependency</groupId>
  <artifactId>mydependency</artifactId>
  <scope>system</scope>
  <version>1.0</version>
  <systemPath>${basedir}\war\WEB-INF\lib\mydependency.jar</systemPath>
</dependency>
```

>The groupId and artifactId are both set to the name of the dependency. The name of the API used, that is. 
`The scope element value is set to system. The systemPath element is set to point to the location of the JAR file containing the dependency. `
The ${basedir} points to the directory where the POM is located. The rest of the path is relative from that directory

# Snapshot Dependencies:
>Snapshot dependencies are dependencies (JAR files) which are under development.
Snapshot versions are always downloaded into your local repository for every build, even if a matching snapshot version is already located in your local repository. 

>Always downloading the snapshot dependencies assures that you always have the latest version in your local repository, for every build.

>You can tell Maven that your project is a snapshot version simply by appending -SNAPSHOT to the version number in the beginning of the POM (where you also set the groupId and artifactId). Here is a version element example:
`<version>1.0-SNAPSHOT</version>`

>Depending on a snapshot version is also done by appending the -SNAPSHOT after the version number when configuring dependencies. 
Here is an example:
```
<dependency>
    <groupId>com.ashish</groupId>
    <artifactId>java-web-app</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
```
>The -SNAPSHOT appended to the version number tells Maven that this is a snapshot version.
You can configure how often Maven shall download snapshot dependencies in the Maven Settings File.

# Maven Repositories:

>Maven repositories are directories of packaged JAR files with extra meta data. 
The meta data are POM files describing the projects each packaged JAR file belongs to, including what external dependencies each packaged JAR has. 

> It is this meta data that enables Maven to download dependencies of your dependencies recursively, until the whole tree of dependencies is download and put into your local repository.

##### Maven has three types of repository:
- Local repository
- Central repository
- Remote repository

>Maven searches these repositories for dependencies in the above sequence. 
First in the local repository, then in the central repository, and third in remote repositories if specified in the POM.

## Local Repository:

>A local repository is a directory on the developer's computer. This repository will contain all the dependencies Maven downloads. 
The same Maven repository is typically used for several different projects. 
Thus Maven only needs to download the dependencies once, even if multiple projects depends on them (e.g. Junit).

>Your own projects can also be built and installed in your local repository, using the `mvn install` command.  That way your other projects can use the packaged JAR files of your own projects as external dependencies by specifying them as external dependencies inside their Maven POM files.

>By default Maven puts your local repository inside your user home directory on your local computer. However, you can change the location of the local repository by setting the directory inside your Maven settings file. 

>Your Maven settings file is also located in your `user-home/.m2` directory and is called `settings.xml`. 

Here is how you specify another location for your local repository:
```
<settings>
    <localRepository>
        d:\data\java\products\maven\repository
    </localRepository>
</settings>
```

# Central Repository:
>The central Maven repository is a repository provided by the Maven community. 
By default Maven looks in this central repository for any dependencies needed but not found in your local repository. 

>Maven then downloads these dependencies into your local repository. 
`You need no special configuration to access the central repository.`

# Remote Repository:
>A remote repository is a repository on a web server from which Maven can download dependencies, just like the central repository. 
A remote repository can be located anywhere on the internet, or inside a local network.

>A remote repository is often used for hosting projects internal to your organization, which are shared by multiple projects. For instance, a common security project might be used across multiple internal projects. 

>This security project should not be accessible to the outside world, and should thus not be hosted in the public, central Maven repository. Instead it can be hosted in an internal remote repository.

>You can configure a remote repository in the POM file. 
`Dependencies found in a remote repository are also downloaded and put into your local repository by Maven.`

Put the following XML elements right after the <dependencies> element:
```
<repositories>
   <repository>
       <id>ashish.code</id>
       <url>http://maven.ashish.com/maven2/lib</url>
   </repository>
</repositories>
```

# Maven Build Life Cycles, Phases and Goals:

>When Maven builds a software project it follows a build life cycle. 
The build life cycle is divided into build phases, and the build phases are divided into build goals.

### Build Life Cycles:
Maven has 3 built-in build life cycles. These are:
- default
- clean
- site

>Each of these build life cycles takes care of a different aspect of building a software project. Thus, each of these build life cycles are executed independently of each other. 

>You can get Maven to execute more than one build life cycle, but they will be executed in sequence, separately from each other, as if you had executed two separate Maven commands.

>The default life cycle handles everything related to compiling and packaging your project. 

>The clean life cycle handles everything related to removing temporary files from the output directory, including generated source files, compiled classes, previous JAR files etc.

>The site life cycle handles everything related to generating documentation for your project. In fact, site can generate a complete website with documentation for your project.

# Build Phases:
>Each build life cycle is divided into a sequence of build phases, and the build phases are again subdivided into goals. 
`Thus, the total build process is a sequence of build life cycle(s), build phases and goals.`

>You can execute either a whole build life cycle like `clean` or `site`, a build phase like `install` which is part of the `default` build life cycle, or a build goal like `dependency:copy-dependencies`.

##### Note:
>`You cannot execute the default life cycle directly. You have to specify a build phase or goal inside the default life cycle.`

>When you execute a build phase, all build phases before that build phase in this standard phase sequence are executed. 
`Thus, executing the install build phase really means executing all build phases before the install phase, and then execute the install phase after that.`

>The default life cycle is of most interest since that is what builds the code. 
`Since you cannot execute the default life cycle directly, you need to execute a build phase or goal from the default life cycle.`

#### The most commonly used build phases of 'default' life cycle are:

|Build Phase| Description|
|-------|-------|
| validate | Validates that the project is correct and all necessary information is available. This also makes sure the dependencies are downloaded.
| compile | Compiles the source code of the project.|
| test | Runs the tests against the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed. |
| package | Packs the compiled code in its distributable format, such as a JAR/WAR. |
| install | Install the package into the local repository, for use as a dependency in other projects locally. |
| deploy | Copies the final package to the remote repository for sharing with other developers and projects. |

You execute one of these build phases by passing its name to the mvn command. 
ex: `mvn package`

>This example executes the package build phase, and thus also all build phases before it in Maven's predefined build phase sequence.

>`If the standard Maven build phases and goals are not enough to build your project, you can create Maven plugins to add the extra build functionality you need.`

# Build Goals:
>Build goals are the finest steps in the Maven build process. 
A goal can be bound to one or more build phases, or to none at all. 
If a goal is not bound to any build phase, you can only execute it by passing the goals name to the mvn command. 
`If a goal is bound to multiple build phases, that goal will get executed during each of the build phases it is bound to.`

# Maven Build Profiles:
>Maven build profiles enable you to build your project using different configurations. 
Instead of creating two separate POM files, you can just specify a profile with the different build configuration, and build your project with this build profile when needed.

>Maven build profiles are specified inside the POM file, inside the profiles element. 
Each build profile is nested inside a `profile` element. 

Here is an example:
```
<groupId>com.ashish</groupId>
  <artifactId>java-web-app</artifactId>
  <version>1.0.0</version>

  <profiles>
      <profile>
          <id>test</id>
          <activation>...</activation>
          <build>...</build>
          <modules>...</modules>
          <repositories>...</repositories>
          <pluginRepositories>...</pluginRepositories>
          <dependencies>...</dependencies>
          <reporting>...</reporting>
          <dependencyManagement>...</dependencyManagement>
          <distributionManagement>...</distributionManagement>
      </profile>
  </profiles>
```

>A build profile describes what changes should be made to the POM file when executing under that build profile. This could be changing the applications configuration file to use etc. The elements inside the profile element will override the values of the elements with the same name further up in the POM.

>`Inside the profile element you can see a 'activation' element. 
This element describes the condition that triggers this build profile to be used.`

>One way to choose what profile is being executed is in the settings.xml file.  There you can set the active profile. 
`Another way is to add -P profile-name to the Maven command line.`

# Maven Plugins:
>Maven plugins enable you to add your `own actions to the build process.`
You do so by creating a simple Java class that extends a special Maven class, and then create a POM for the project. 
The plugin should be located in its own project.
