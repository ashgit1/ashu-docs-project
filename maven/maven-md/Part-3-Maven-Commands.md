# Maven Commands:
>Maven contains a wide set of commands which you can execute. 
`Maven commands are a mix of build life cycles, build phases and build goals, and can thus be a bit confusing.`
Therefore we will describe the common Maven commands as well as explain which build life cycles, build phases and build goals they are executing.

### Maven Command Structure:
A Maven command consists of two elements:
   - mvn
   - One or more build life cycles, build phases or build goals

### Here is a Maven command example:
`mvn clean`
>This command consists of the `mvn` command which executes Maven, and the `build life cycle named clean`.

### Here is another Maven command example:
`mvn clean install`
>This maven command executes the `clean build life cycle` and the `install build phase` in the `default build life cycle.`

You might wonder how you see the difference between a build life cycle, build phase and build goal. 

### Build Life Cycles, Phases and Goals:
>Maven contains three major build life cycles:

   - clean
   - default
   - site

>Inside each `build life cycle` there are `build phases`, and inside each `build phase` there are `build goals`.
You can execute either a `build life cycle, build phase or build goal`. 

>When executing a build life cycle you execute all build phases (and thus build goals) inside that build life cycle.

>When executing a build phase you execute all build goals within that build phase. `Maven also executes all build phases earlier in the build life cycle of the desired build phase`.

>Buid goals are assigned to one or more buid phases. When the build phases are executed, so are all the goals in that build phase. `You can also execute a build goal directly`. 

### Executing Build Life Cycles, Phases and Goals:
>When you run the mvn command you pass one or more arguments to it. These arguments specify either a build life cycle, build phase or build goal. 

>For instance to execute the `clean build life cycle` you execute this command:
`mvn clean`

>To execute the site build life cycle you execute this command:
`mvn site`

### Executing the Default Life Cycle:
>The `default` life cycle is the build life cycle which `generates, compiles, packages etc. your source code`.
`You cannot execute the default build life cycle directly, as is possible with the clean and site`. 
Instead you have to execute a specific build phase within the default build life cycle.

#### The most commonly used build phases in the default build life cycle are: 
|Build Phase| Description|
|-------|-------|
| validate | Validates that the project is correct and all necessary information is available. This also makes sure the dependencies are downloaded.
| compile | Compiles the source code of the project.|
| test | Runs the tests against the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed. |
| package | Packs the compiled code in its distributable format, such as a JAR/WAR. |
| install | Install the package into the local repository, for use as a dependency in other projects locally. |
| deploy | Copies the final package to the remote repository for sharing with other developers and projects. |

>Executing one of these build phases is done by simply adding the build phase after the mvn command, like this:
`mvn test`

>This Maven command executes the `test` build phase of the `default` build life cycle. 
`This Maven command also executes all earlier build phases in the default build life cycle, meaning the validate and complie build phases`

### Executing Build Phases:
>You can execute a build phase located inside a build life cycle by passing the name of the build phase to the Maven command. 

Here are a few build phase command examples:
- mvn pre-clean
- mvn compile
- mvn package

>Maven will find out what `build life cycle` the `specified build phase` belongs to, so you don't need to explicitly specify which build life cyle the build phase belongs to. 
