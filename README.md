GraphiteContext
===============

Like the GangliaContext for Hadoop 2, you can use this to sends metrics to Graphite.

### Compiling

    $ mvn install

### Installing

To install, you only need to drop the compiled jar (from `target/`) into your hadoop classpath. This can vary, but the `hadoop classpath` command line tool is your friend.

### Setting everything up

Once installed, you'll need to update the `hadoop-metrics.properties` configuration file, something like the below will get you started.

    mapred.class=org.apache.hadoop.metrics.graphite.GraphiteContext
    mapred.period=60
    mapred.serverName={graphite_host}
    mapred.port=2013

    jvm.class=org.apache.hadoop.metrics.graphite.GraphiteContext
    jvm.period=60
    jvm.serverName={graphite_host}
    jvm.port=2013

    dfs.class=org.apache.hadoop.metrics.graphite.GraphiteContext
    dfs.period=60
    dfs.serverName={graphite_host}
    dfs.port=2013

    ugi.class=org.apache.hadoop.metrics.graphite.GraphiteContext
    ugi.period=60
    ugi.serverName={graphite_host}
    ugi.port=2013

By default, metrics will be prefixed with `Platform.Hadoop`. You can changed this prefix using the `path` attribute of each metric. For example...

    mapred.path=hadoop.test
