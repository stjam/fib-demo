# fib-demo

Repository for paperwork about Jit-compiler

**Build project**

```mvn clean install```

**To run without JIT compiler**

```
java -jar target/benchmark.jar -jvmArgs='-Xint -Xlog:compilation*=debug:file=compilation.log:time,uptime,level,tags'
```

**To run with C2 compiler**

```
java -jar target/benchmark.jar -jvmArgs='-XX:-TieredCompilation -Xlog:compilation*=debug:file=compilation.log:time,uptime,level,tags'
```

**To run with C1 compiler**

```
java -jar target/benchmark.jar -jvmArgs='-XX:+TieredCompilation -XX:TieredStopAtLevel=1 -Xlog:compilation*=debug:file=compilation.log:time,uptime,level,tags'
```

**To run in tired mode**
```
java -jar target/benchmark.jar -jvmArgs='-Xlog:compilation*=debug:file=compilation.log:time,uptime,level,tags'
```

**My environment**
```
Apache Maven 3.9.9 (8e8579a9e76f7d015ee5ec7bfcdc97d260186937)
Java version: 23.0.1, vendor: Homebrew, runtime: /opt/homebrew/Cellar/openjdk/23.0.1/libexec/openjdk.jdk/Contents/Home
OS name: "mac os x", version: "14.5", arch: "aarch64", family: "mac"
```

**Results that I've got:**

```
TieredCompilation
Benchmark               Mode  Cnt    Score    Error  Units
Main.measureFibonacci  thrpt    5  406,206 ± 44,724  ops/s
```

```
Without JIT
Benchmark               Mode  Cnt   Score   Error  Units
Main.measureFibonacci  thrpt    5  18,821 ± 0,055  ops/s
```

```
When use only C1
Benchmark               Mode  Cnt    Score    Error  Units
Main.measureFibonacci  thrpt    5  376,382 ± 53,193  ops/s
```

```
When use only C2
Benchmark               Mode  Cnt    Score   Error  Units
Main.measureFibonacci  thrpt    5  416,779 ± 4,059  ops/s
```
