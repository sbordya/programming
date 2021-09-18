Gradle - modern, flexible, customisable build automation tool
   * supports single project (single build output) and multi-project build structures (multiple build outputs)
1. build.gradle
    * plugins (configures project in curtain way and adds additional tasks)
    * build metadata (build info like group and version)
    * repositories (like maven central)
    * dependencies
2. task - unit of work to be executed in the build (like code compiling and deploying to repo)
    * ./gradlew build - compiles and tests the project
    * ./gradlew tasks - all tasks
    * custom tasks can be created
    * tasks can have dependencies on other tasks
    * task graph
3. wrapper - script used to invoke Gradle and run tasks
    * always commited into version control system
    * no gradle installation required for anyone building the project
    * contains a specific version of gradle for the project
4. simple gradle project structure:
    * build.gradle
    * gradle
        * wrapper
            * gradle-wrapper.jar
            * gradle-wrapper.properties
    * gradlew
    * gradlew.bat
    * settings.gradle (project name and more)
5. gradle init - setup wizard (for new project)
6. java project requirements:
    * compile java classes from .java into .class files
    * manage resources that live alongside code
    * package everything into a jar file
    * easily run tests
    * define dependencies
7. java plugin
    * adds a task compileJava - ./gradlew compileJava
        * uses java installation to compile .java into .class files
        * outputs .class files into build directory
    * manage resources - ./gradlew processResources
        * copies contents of resources directories into build directory
    * package into jar file - ./gradlew jar
        * adds compiled classes and resources from build folder to jar archive
        * jar file named <project-name>-<version>.jar
    * easily run tests - ./gradlew test
        * compiles tests, processes resources, runs test
        * creates a test report in the build directory
    * define dependencies
8. Dependency configuration:
    * implementation - dependencies required during the compilation or execution of the code
    * testImplementation - dependencies required during the compilation or execution of the tests
    * dependency configuration used to generate classpath
9. gradle java project layout:
    * src/main/java -> build/classes/java/main
    * src/main/resources -> build/resources/main
    * src/test/java -> build/classes/java/test
    * src/test/resources -> build/resources/test
10. Groovy
    * jvm scripting language
    * brackets are optional
    * supports closures
11. Tasks
    * some tasks are actions, some aggregations
    * aggregate tasks combine multiple tasks using task dependencies
    * java plugin tasks
        * assemble/jar - assemble + creates jar
        * check/test
        * build - assemble + check
        * classes - compiles .java to .class
        * clean - removes build directory
