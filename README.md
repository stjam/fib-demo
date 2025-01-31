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
