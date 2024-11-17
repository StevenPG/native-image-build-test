# Explanation

The goal here isn't the first execution, nor is it for the most optimized run. Just a couple reruns and the average/best value.
These systems have real performance differences, so we're just looking for a ballpark difference between them.

NOTE: Rerun the first gradle run, since it'll probably download gradle as part of the run! And pulling dependencies! We only care about CPU, no download variances!

This project can be run by setting your java home to a GraalVM JDK.

`./gradlew clean nativeRun` is all that's needed to perform the graalvm test.
Look for the following sections in the output:

`Finished generating 'demo' in 1m 19s.` and `Started DemoApplication in 0.207 seconds`

JDK tests can be run using `./gradlew clean compileJava` and `./gradlew clean bootRun`

The compileJava is the total time and the bootRun is the startup time, e.g:

`BUILD SUCCESSFUL in 654ms` and for bootRun, `Started DemoApplication in 1.387 seconds`

| System           | JDK Compile Time | JDK Startup Time | Native Compile Time | Native Startup Time | Spec Notes                  | OS                  |
|------------------|------------------|------------------|---------------------|---------------------|-----------------------------|---------------------|
| 2015 Macbook Pro | 3000ms           | 3.849s           | 436s (7m 16s)       | 320ms               |                             | MacOS               |
| 2020 Lemur Pro   | 4000ms           | 8.052s           | 657s (10m 57s)      | 938ms               | System76, i5 10210U 4c 40GB | Ubuntu Server 21.04 |
| 2019 Macbook Pro | 2000ms           | 3.786s           | 230s (3m 50s)       | 413ms               | 2.6GHz 6c i7                | MacOS               |
| M1 Pro           | 1000ms           | 2.071s           | 140s (2m 20s)       | 207ms               | M1 Pro 8c 32GB              | MacOS               |
| M2 Air           | 1000ms           | 1.687s           | 205s (3m 25s)       | 180ms               | M2 16GB                     | MacOS               |
| M2 Pro  xxxxxxx  |                  |                  |                     |                     |                             | MacOS               |
| M3 Pro           | 650ms            | 1.490s           | 79s (1m 19s)        | 20.5ms              | M3 Pro 12c 36GB (6p,6e)     | MacOS               |
| M3 Max           | 620ms            | 1.429s           | 66s (1m 6s)         | 20.4ms              | M3 Max 16c 48GB             | MacOS               |
| M4               | 668ms            | 1.29s            | 137s (2m 17s)       | 16ms                | M4 10c 32GB (4p,6e)         | MacOS               |
| M4 Pro           | 607ms            | 1.281s           | 81s (1m 41s)        | 17.2ms              | M4 Pro 14c 48GB (10p,4e)    | MacOS               |
| ITX Computer     | 1000ms           | 2.410s           | 186s (2m 46s)       | 17.2ms              | Ryzen 5700g 8c 16t 32GB     | Pop!\_OS 22.04 LTS  |
