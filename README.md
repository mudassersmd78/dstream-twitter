# Twitter data source for DStream (Spark Streaming)

A library for reading data from Twitter to [Spark Streaming](http://spark.apache.org/docs/latest/streaming-programming-guide.html).

[![Build Status](https://travis-ci.org/spark-packages/dstream-twitter.svg?branch=master)](https://travis-ci.org/spark-packages/dstream-twitter)
[![codecov.io](http://codecov.io/github/spark-packages/dstream-twitter/coverage.svg?branch=master)](http://codecov.io/github/spark-packages/dstream-twitter?branch=master)

## Requirements

This documentation is for Spark 2.0.0+. For old Spark versions, please use the old versions published with Spark.

## Linking

You can link against this library (for Spark 2.0.0+) in your program at the following coordinates:

Using SBT:

```
libraryDependencies += "org.spark-project" %% "dstream-twitter" % "0.1.0"
```

Using Maven:

```xml
<dependency>
    <groupId>org.spark-project</groupId>
    <artifactId>dstream-twitter_2.10</artifactId>
    <version>0.1.0</version>
</dependency>
```

This library can also be added to Spark jobs launched through `spark-shell` or `spark-submit` by using the `--packages` command line option.
For example, to include it when starting the spark shell:

```
$ bin/spark-shell --packages org.spark-project:dstream-twitter_2.10:0.1.0
```

Unlike using `--jars`, using `--packages` ensures that this library and its dependencies will be added to the classpath.
The `--packages` argument can also be used with `bin/spark-submit`.

This library is cross-published for Scala 2.11, so 2.11 users should replace 2.10 with 2.11 in the commands listed above.

## Examples

`TwitterUtils` uses Twitter4j to get the public stream of tweets using 
[Twitter's Streaming API](https://dev.twitter.com/docs/streaming-apis). Authentication information
can be provided by any of the [methods](http://twitter4j.org/en/configuration.html) supported by
Twitter4J library. You can import the `TwitterUtils` class and create a DStream with `TwitterUtils.createStream` as shown below.

### Scala API

```Scala
import org.apache.spark.streaming.twitter._

TwitterUtils.createStream(ssc, None)
```

### Java API

```Java
import org.apache.spark.streaming.twitter.*;

TwitterUtils.createStream(jssc);
```

You can also either get the public stream, or get the filtered stream based on a
keywords. See examples ([TwitterPopularTags](https://github.com/spark-packages/dstream-twitter/tree/master/examples/src/main/scala/org/apache/spark/examples/streaming/twitter/TwitterPopularTags.scala)
and [TwitterAlgebirdCMS](https://github.com/spark-packages/dstream-twitter/tree/master/examples/src/main/scala/org/apache/spark/examples/streaming/twitter/TwitterAlgebirdCMS.scala)).

## Building From Source
This library is built with [SBT](http://www.scala-sbt.org/0.13/docs/Command-Line-Reference.html),
which is automatically downloaded by the included shell script. To build a JAR file simply run
`build/sbt package` from the project root.

## Testing

Just Run `build/sbt test examples/test`.
