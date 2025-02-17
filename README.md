# gfc-time [![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.gilt/gfc-time_2.12/badge.svg?style=plastic)](https://maven-badges.herokuapp.com/maven-central/com.gilt/gfc-time_2.12) [![Build Status](https://travis-ci.org/gilt/gfc-time.svg?branch=master)](https://travis-ci.org/gilt/gfc-time) [![Coverage Status](https://coveralls.io/repos/gilt/gfc-time/badge.svg?branch=master&service=github)](https://coveralls.io/github/gilt/gfc-time?branch=master) [![Join the chat at https://gitter.im/gilt/gfc](https://badges.gitter.im/gilt/gfc.svg)](https://gitter.im/gilt/gfc?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)


A library that contains time related scala utility classes. Part of the [Gilt Foundation Classes](https://github.com/gilt?q=gfc).

## Getting gfc-time

The latest version is 0.0.7, which is cross-built against Scala 2.10.x, 2.11.x and 2.12.x.

If you're using SBT, add the following line to your build file:

```scala
libraryDependencies += "com.gilt" %% "gfc-time" % "0.0.7"
```

For Maven and other build tools, you can visit [search.maven.org](http://search.maven.org/#search%7Cga%7C1%7Ccom.gilt%20gfc).
(This search will also list other available libraries from the gilt fundation classes.)

## Contents and Example Usage

### com.gilt.gfc.time.Timer

Various utilities for timing & reporting on blocks of code and scala Futures.

* Format a nanosecond timespan into a human-readable string, like "37 us" or "45 days 08:55:01".

    val start = System.nanoTime()
    doSomething()
    val elapsed = Timer.pretty(System.nanoTime() - start)
    println(s"doSomething() took $elapsed")

* Report ns result (Long value)

    val result = Timer.time(l => println(s"Operation took $l ns")) {
      // timed function, returning a
      result
    }

* Report formatted result. The result String is using the best suitable time unit
  (e.g. "10 ns", "456 ms", "45 days 08:55:01" etc.)

    val result = Timer.time(s => println(s"Operation took ${s}")) {
      // timed function, returning a
      result
    }

* Time the body, then calls pretty on the elapsed time to get a more human-friendly time
  String, then passes that to the "format" method.

    val result = Timer.time("Operation took %s", println _)) {
      // timed function, returning a
      result
    }

* Similar functions as above are available to time scala Future completions.


### com.gilt.gfc.time.Timestamp

A immutable lightweight wrapper around a millisecond timestamp.

## License
Copyright 2019

Licensed under the Apache License, Version 2.0: http://www.apache.org/licenses/LICENSE-2.0
