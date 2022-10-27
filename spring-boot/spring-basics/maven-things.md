---
description: Everything related to maven
---

# Maven Things

### Missing pom.xml version

#### If version in pom.xml isnt mentioned, then how does spring boot know which version to use ?

The version belonging the parent module will be referenced. Spring Boot starter comes with a lot of libraries in-built, with is referenced as a parent in the pom.xml file of your project&#x20;

```
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.7.0</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
```

* Click on `spring-boot-starter-parent` and to open its' pom.xml and then open  `spring-boot-dependencies` and you will find the list of version of each dependencies mentioned in it, used the specific spring-boot version you are using.

Now, if we have a child module in our spring application, and if we dont specify the version number, we either need to mention the parent pom or specify the version there.

```
<!-- referencing parent pom.xml -->
        <parent>
        <groupId>com.example</groupId>
        <artifactId>spring-demo</artifactId>
        <version>0.0.1</version>
        <relativePath>../pom.xml</relativePath>
    </parent>
```

or you can the specify the version inside the dependency tag or in the properties tag

```
	<properties>
		<java.version>17</java.version>
		<lombok.version>1.18.18</lombok.version> <!-- example -->
	</properties>
```

You can also exclude the child module ( if you want to use another implementation ) from the parent pom.

Example : Excluding the artifactedId hamcrest-core from junit.

```
<dependencyManagement>
		<dependencies>
			<dependency>
				<groupId>junit</groupId>
				<artifactId>junit</artifactId>
				<version>4.12</version>
				<scope>test</scope>
				<exclusions>
					<exclusion>
						<groupId>org.hamcrest</groupId>
						<artifactId>hamcrest-core</artifactId>
					</exclusion>
				</exclusions>
			</dependency>
		</dependencies>
	</dependencyManagement>
```

* Check the maven tab, you will find that `hamcrest-core` is no longer a sub-dependency of junit and will also find the exact version.

### Maven Build Phases

* `validate` - validate the project is correct and all necessary information is available
* `compile` - compile the source code of the project
* `test` - test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed
* `package` - take the compiled code and package it in its distributed format, such as a JAR.
* `verify` - run any checks on results of integration tests to ensure quality criteria are met
* `install` - install the package into the local repository, for use as a dependency in other projects locally
* `deploy` - done in the build environment, copies the final package to the remote repository for sharing with other developers and projects.
