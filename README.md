# Fusepool Stanbol Launcher

A custom Apache Stanbol Launcher for the Fusepool Plattform.

This Launcher is based on the `1.0.0-SNAPSHOT` (trunk) version of Apache Stanbol. It includes the following Features:

* Apache Stanbol core modules
* Apache Stanbol Enhancer component
    * All common Stanbol [Enhancement Engines](http://stanbol.apache.org/docs/trunk/components/enhancer/engines/). See this [list](http://stanbol.apache.org/docs/trunk/components/enhancer/engines/list.html) for an overview about the available options.
    * [Data TXT Enhancement Engine](https://github.com/fusepoolP3/p3-datatxt-stanbol) supporting entity linking to [DBPedia.org](http://wiki.dbpedia.org/) including support for disambiguation. This engine is based on the [DataTXT service[(http://dandelion.eu/datatxt/) provided by [Spaziodati](http://www.spaziodati.eu/). Users will neet to aquire an Application key to use this engine.
    * [FISE to FAM transformation Engine](https://github.com/fusepoolP3/p3-stanbol-engine-fam) required to transform Enhancement Results using the Stanbol Enhancement Structure to the [Fusepool Annotation Model](https://github.com/fusepoolP3/overall-architecture/blob/master/wp3/fp-anno-model/fp-anno-model.md) (FAM)
* Apache Stanbol Entityhub component used for the management of Controlled Vocabularies for entity linking.
* Open NLP Language Models for Danish (`da`), German (`de`), English (`en`), Spanish (`es`), French (`fr`), Dutch (`nl`), Portuguese (`pt`) and Swedish (`sv`). Those are provided by the [eu.fusepool.p3.stanbol-launcher:stanbol-data-opennlp-pos](/fusepoolP3/p3-stanbol-launcher/tree/master/data/opennlp-pos) module part of this repository.
* [Fusepool Transformer Adapter](https://github.com/fusepoolP3/p3-stanbol-enhancer-adapter/tree/master/service) allowing to use Stanbol Enhancer Chains and Engines as Fusepool Transformers.
* [Fusepool Configuration Service](https://github.com/fusepoolP3/p3-stanbol-enhancer-adapter/tree/master/config) allowing to configure a Stanbol Instance for a Fusepool Plattrom during the installation process of Fusepool.


## Installation

Just

    mvn install

After the build succeeds you can find the runnable JAR under

    launcher/target/stanbol-launcher-1.0.0-SNAPSHOT.jar

Copy this launcher to your working directory and start it using

    java -jar -Xmx1g stanbol-launcher-1.0.0-SNAPSHOT.jar -p 8304

_NOTE:_ The `-p 8304` option sets the HTTP port to `8304` the port for the Stanbol Transformer as defined [here](https://github.com/fusepoolP3/overall-architecture/blob/master/default-ports.md). This needs to be parsed explicitly until [SLING-4672](https://issues.apache.org/jira/browse/SLING-4672) gets release.
