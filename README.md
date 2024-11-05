# Explanation

This project can be run by setting your java home to a GraalVM JDK.

`./gradlew clean nativeRun` is all that's needed to perform the graalvm test.
Look for the following sections in the output:

`Finished generating 'demo' in 1m 19s.` and `Started DemoApplication in 0.207 seconds`

JDK tests can be run using `./gradlew clean compileJava` and `./gradlew clean bootRun`

The compileJava is the total time and the bootRun is the startup time, e.g:

`BUILD SUCCESSFUL in 654ms` and for bootRun, `Started DemoApplication in 1.387 seconds`

| System           | JDK Compile Time | JDK Startup Time | Native Compile Time | Native Startup Time |
|------------------|------------------|------------------|---------------------|---------------------|
| 2019 Macbook Pro |                  |                  |                     |                     |
| M1 Pro  8c 32GB  | 1000ms           | 2.071s           | 140s                | 207ms               |
| M3 Pro 12c 36GB  | 650ms            | 1.490s           | 79s                 | 20.5ms              |
| M3 Max xxxxx     |                  |                  |                     |                     |