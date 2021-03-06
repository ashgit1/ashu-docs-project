# Maven Archetypes:
>Maven archetypes are project templates which can be generated for you by Maven. 
In other words, when you are starting a new project you can generate a template for that project with Maven. 
`In Maven a template is called an archetype.` 
Each Maven archetype thus corresponds to a project template that Maven can generate.

### Available Maven Archetypes:
>Maven contains a lot of archetypes, so this Maven archetype tutorial will just show you some of the most commonly used archetypes. 
To see a full list of Maven archetypes, simply run this command: `mvn archetype:generate`

>This command actually intends to generate a Maven archetype for you, but since you have not specified in the command which archetype to build, Maven will output all its available archetypes to the command prompt. 
At the end Maven will ask you which Maven archetype to generate. 
If you know the number of the archetype to generate, you can type in the number in the command prompt and press enter.

>The list contains more than 1000 Maven archetypes, so it is not really that easy to find the archetype you need. 
To look at the list of available Maven archetypes, you can pipe the output into a file, and open that file in a editor like Notepad++/Sublime or so. 
You pipe the available Maven archetypes into a file using this Maven command:
`mvn archetype:generate > archetypes.txt`

##### Note:
>You may have to cancel the command at the point where it asks you to enter the archetype number. 
You can do so on Windows with CTRL-C. The archetypes will still be written into the file. 

### Named Archetypes:
>Maven contains a set of named archetypes which you can create. We will list a few of these archetypes in the following sections. 

##### Eclipse:
>This is a Maven archetype which can generate a new Java project including files for the Eclipse IDE. 
You can generate that archetype using this Maven command:
`mvn eclipse:eclipse`

>`Before you can generate this Maven archetype though, you need to have a POM file in the project root directory into which you want to generate the archetype.`

##### IDEA Archetype:
>Similar to the Eclipse archetype, Maven contains an IntelliJ IDEA archetype. 
You can generate the IDEA archetype using this Maven command:
`mvn idea:idea`

##### Example of a Simple Maven Web App:
> cd /tmp/web-app-using-archetype/Spring-Web_MVC
$ `mvn archetype:generate -DgroupId=com.ashish -DartifactId=WebApp -DarchetypeArtifactId=maven-archetype-webapp`
