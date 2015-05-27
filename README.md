# Fusepool Stanbol Launcher

A custom Apache Stanbol Launcher for the Fusepool Plattform.

This Launcher includes

* Apache Stanbol core modules
* Apache Stanbol Enhancer component
    * All common Stanbol Enhancement Engines
    * [Data TXT Enhancement Engine](https://github.com/fusepoolP3/p3-datatxt-stanbol)
    * [FISE to FAM transformation Engine](https://github.com/fusepoolP3/p3-stanbol-engine-fam)
* Apache Stanbol Entityhub component
* Open NLP Language Models for Danish (`da`), German (`de`), English (`en`), Spanish (`es`), French (`fr`), Dutch (`nl`), Portuguese (`pt`) and Swedish (`sv`).
* [Fusepool Transformer Adapter](https://github.com/fusepoolP3/p3-stanbol-enhancer-adapter/tree/master/service)
* [Fusepool Configuration Service](https://github.com/fusepoolP3/p3-stanbol-enhancer-adapter/tree/master/config)


## Installation

Just

    mvn install

After the build succeeds you can find the runnable JAR under

   launcher/target/stanbol-launcher-1.0.0-SNAPSHOT.jar

Copy this launcher to your working directory and start it using

    java -jar -Xmx1g stanbol-launcher-1.0.0-SNAPSHOT.jar -p 8304

_NOTE:_ The `-p 8304` option sets the HTTP port to `8304` the port for the Stanbol Transformer as defined [here](https://github.com/fusepoolP3/overall-architecture/blob/master/default-ports.md). This needs to be parsed explicitly until [SLING-4672](https://issues.apache.org/jira/browse/SLING-4672) gets release.

