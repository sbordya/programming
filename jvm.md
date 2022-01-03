[JVM](https://www.youtube.com/watch?v=QHIWkwxs0AI):
1. Class loader - 3 phases:
    1. Loading
        1. Bootstrap class loader - load .class file from RT.jar (runtime jar) to runtime memory; loads precompiled pretrusted System.class file (/jre/lib)
        2. Extension class loader - additional class files load (/jre/lib/ext): IBM MQ, OJDBC (3rd party jar files)
        3. Application class loader - load class files from the app specific jar
    2. Linking
        1. Verify - bytecode class files are verified if they conform to standards (after class files are loaded to the memory)
        2. Prepare - memory is allocated for the static variables and default values are assigned
        3. Resolve - all the symbolic references are replaced with the actual references
            *  In Java , a java class will be compiled into a class file. At compile time, the java class does not know the actual address of the referenced class, so symbolic references can only be used instead. For example, the org.simple.People class refers to the org.simple.Language class. The People class does not know the actual memory address of the Language class at compile time, so it can only use the symbol org.simple.Language to represent the address of the Language class.
    3. Initialisation - all the static variables are assigned with the actual values, static initializers are executed
2. Runtime data area:
    1. Method area - class data (static fields and methods)
    2. Heap area - object data (instances)
    3. Stack memory:
        1. Local variable - local variables within the module
        2. Operand stack - operands used within a method
        3. Frame data - any catch block information if any exception occurs within method
    4. PC register - current execution instructions
    5. Native method stack - native method information
3. Execution engine - converts the bytecode to machine code and executes the instructions:
    1. Interpreter - reads the class file or bytecode and executes it one by one. The problem - when a method is called multiple times, lines of code are interpreted again and again
    2. JIT compiler - helps in overcoming the problem of the interpreter. When repeated method calls occur, JIT compiler compiles bytecode to native code that will be used. JIT compiler contains few components to achieve this feature:
        1. Intermediate code generator - generates intermediate code
        2. Code optimizer - optimizes the intermediate code for the better performance
        3. Target code generator - converts intermediate code to the native machine code
        4. Profiler - responsible for finding the hotspots, methods which are called repeatedly
    3. Garbage collector - destroying the objects that are no longer used
    4. Java native method interface - interacting with native libraries and makes it available for the JVM execution engine
