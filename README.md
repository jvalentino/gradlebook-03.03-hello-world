## 3.3  Hello World

The following is the standard “Hello World” for Gradle. It is a single **build.gradle** file that can be run using either local Gradle or the Gradle Wrapper, and results in “Hello World!!!” bring written to the command-line.

#### build.gradle

```groovy
task hello {
    group 'custom'
    description 'This is an example of how to make a custom task'
    doLast {
        println "Hello World!!!"
    }
}
```

Usage:

```bash
$ gradlew hello
:hello
Hello World!!!
```

### Eclipse IDE Support

If you are using one of the later versions of the Eclipse IDE, it comes with the Buildship plugin that handles working with Gradle. It is also recommended that you install the Jspresso Spock Plugin (https://marketplace.eclipse.org/content/spock-plugin) for better Spock syntax highlighting. Additionally, you will be required to add Groovy support using the Eclipse Groovy Development Tools (https://marketplace.eclipse.org/content/groovy-development-tools).

With all these tools though, there isn’t a “New Gradle Project” option that gives an actual blank Gradle build that doesn’t do anything. It is for that reason I hand-constructed the Eclipse configuration files. These configuration files will later be extended for better Groovy-based Gradle plugin support.

#### .project

```xml
<?xml version="1.0" encoding="UTF-8"?>
<projectDescription>
	<name>hello-world</name>
	<comment></comment>
	<projects>
	</projects>
	<buildSpec>
	<buildCommand>
	<name>org.eclipse.buildship.core.gradleprojectbuilder</name>
	<arguments>
	</arguments>
	</buildCommand>
	<buildCommand>
	<name>org.eclipse.jdt.core.javabuilder</name>
	<arguments>
	</arguments>
	</buildCommand>
	</buildSpec>
	<natures>
	<nature>org.jspresso.contrib.sjsplugin.spock.nature</nature>
	<nature>org.eclipse.jdt.core.javanature</nature>
	<nature>org.eclipse.jdt.groovy.core.groovyNature</nature>
	<nature>org.eclipse.buildship.core.gradleprojectnature</nature>
	</natures>
</projectDescription>
```

The **.project** file defined the name of the projects, and the available language support. Specifically:

·   **projectDescription.name** is the name used for the project in Eclipse

·   The build specification of **gradleprojectbuilder** makes this a project that supports a Gradle based build

·   The build specification of **javabuilder** adds the support for general Java

·   The nature of **spock.nature** it was adds the syntax highlighting for Spock based tests

·   The nature of **javanature** handles Java

·   The nature of **groovyNature** handles Groovy

·   The nature of **gradelprojectnature** handles Gradle

#### .classpath

```xml
<?xml version="1.0" encoding="UTF-8"?>
<classpath>
	<classpathentry kind="con" path="org.eclipse.jdt.launching.JRE_CONTAINER/org.eclipse.jdt.internal.debug.ui.launcher.StandardVMType/JavaSE-1.8/"/>
	<classpathentry kind="con" path="org.eclipse.buildship.core.gradleclasspathcontainer"/>
	<classpathentry exported="true" kind="con" path="GROOVY_DSL_SUPPORT"/>
	<classpathentry kind="output" path="bin"/>
</classpath>
```

The **.classpath** file handles setting up what is compiled, how, and where:

·   The entry for **JavaSE-1.8** is reference to the internal Java Runtime Environment used within Eclipse

·   The entry for **gradleclasspathcontainer** is what delegates dependency management, meaning runtime, compile time, and others, to the Gradle Container

·   The entry of **GROOVY_DSL_SUPPORT** is what allows the use of Groovy syntax



