# Fusepool Stanbol Launcher  [![Build Status](https://travis-ci.org/fusepoolP3/p3-stanbol-launcher.svg)](https://travis-ci.org/fusepoolP3/p3-stanbol-launcher)

Modules under this folder provide Stanbol Launchers including extensions required to use Stanbol with the Fusepool P3 Plattform. Currently their are two Launcher version available

1. __Core Stanbol Launcher:__ This only include the software modules required to use Stanbol together with the Fuespool P3 Plattform. This launcher includes the Stanbol Enhancer and Entityhub component as well as all Fusepool Extensions. See below for a more detailed list of included components and links to their documentation
2. __Default Stanbol Launcher:__ This is the core launcher plus a set of data, default configuration and demos. This launcher packs NLP modles, often used Thesauri and configuration that allows users to directly use the packed features as Fusepool Transformers.


### Included Software Components:

This Launcher is based on the `1.0.0-SNAPSHOT` (trunk) version of Apache Stanbol. It includes the following Features:

* Apache Stanbol core modules
* Apache Stanbol Enhancer component
    * All common Stanbol [Enhancement Engines](http://stanbol.apache.org/docs/trunk/components/enhancer/engines/). See this [list](http://stanbol.apache.org/docs/trunk/components/enhancer/engines/list.html) for an overview about the available options.
    * [Data TXT Enhancement Engine](https://github.com/fusepoolP3/p3-datatxt-stanbol) supporting entity linking to [DBPedia.org](http://wiki.dbpedia.org/) including support for disambiguation. This engine is based on the [DataTXT service](http://dandelion.eu/datatxt/) provided by [Spaziodati](http://www.spaziodati.eu/). Users will need to aquire an Application key to use this engine.
    * [FISE to FAM transformation Engine](https://github.com/fusepoolP3/p3-stanbol-engine-fam) required to transform Enhancement Results using the Stanbol Enhancement Structure to the [Fusepool Annotation Model](https://github.com/fusepoolP3/overall-architecture/blob/master/wp3/fp-anno-model/fp-anno-model.md) (FAM)
* Apache Stanbol Entityhub component used for the management of Controlled Vocabularies for entity linking.
* [Fusepool Transformer Adapter](https://github.com/fusepoolP3/p3-stanbol-enhancer-adapter/tree/master/service) allowing to use Stanbol Enhancer Chains and Engines as Fusepool Transformers.
* [Fusepool Configuration Service](https://github.com/fusepoolP3/p3-stanbol-enhancer-adapter/tree/master/config) allowing to configure a Stanbol Instance for a Fusepool Platform during the installation process of Fusepool.

### Included Data Bundles

_Note:_ The core Launcher does not include any of those data bundles.

* Open NLP Language Models for Danish (`da`), German (`de`), English (`en`), Spanish (`es`), French (`fr`), Dutch (`nl`), Portuguese (`pt`) and Swedish (`sv`). Those are provided by the [eu.fusepool.p3.stanbol-launcher:stanbol-data-opennlp-pos](/fusepoolP3/p3-stanbol-launcher/tree/master/data/opennlp-pos) module part of this repository.
* OpenNLP Named Entity Extraction (NER) Models for English (`en`), Spanish (`es`), French (`fr`) and Dutch (`nl`). Those are provided by the [eu.fusepool.p3.stanbol-launcher:stanbol-data-opennlp-ner](/fusepoolP3/p3-stanbol-launcher/tree/master/data/opennlp-ner) module part of this repository
* [IXA Pipe Nerc](https://github.com/ixa-ehu/ixa-pipe-nerc/) Named Entity Recognition Models for English (`en`), German (`de`), Spanish (`es`), Italian (`it`), Dutch (`nl`) and Basque (`eu`). The included models are taken from the [1,5.0 Release](http://ixa2.si.ehu.es/ixa-pipes/models/nerc-models-1.5.0.tgz) and are provided by the [eu.fusepool.p3.stanbol-launcher:stanbol-data-ixa-nerc](/fusepoolP3/p3-stanbol-launcher/tree/master/data/ixa-nerc) module part of this repository.

## Try it out

First, obtain the latest [release](https://github.com/fusepoolP3/p3-stanbol-launcher/releases/latest).

Currently their are two launcher configuration - _(1) core_ and _(2) default_. For most users it is recommended to use the default launcher as it includes data and configurations useful for typical usage scenarios.

Next, start the transformer:

    java -jar -Xmx8g stanbol-p3-*.jar -p 8304

You can then access the Stanbol webinterface (including links to the Fusepool-transformers) using a webbrowser pointing to [http://localhost:8304/](http://localhost:8304/)

## Compiling and Running

To build the runnable jar, issue the following maven-command:

    mvn install

After the build succeeds you can find the runnable JARs for the two launchers at the following locations:

    launcher/core/target/stanbol-launcher-core-{version}.jar
    launcher/default/target/stanbol-launcher-{version}.jar

To use the default launcher copy `launcher/default/target/stanbol-launcher-{version}.jar` to your working directory and start it by assigning at lease 8 GByte ram to the process.

    java -jar -Xmx8g stanbol-launcher-{version}.jar -p 8304

_NOTES:_ 

* The `-p 8304` option sets the HTTP port to `8304` the port for the Stanbol Transformer as defined [here](https://github.com/fusepoolP3/overall-architecture/blob/master/default-ports.md). This needs to be parsed explicitly until [SLING-4672](https://issues.apache.org/jira/browse/SLING-4672) gets release.
* The default launcher needs about 8 GByte ram because of the IXA Pipe Nerc models. The core launcher (without any data) will only require about 500 MByte ram.
_NOTE:_ The `-p 8304` option sets the HTTP port to `8304` the port for the Stanbol Transformer as defined [here](https://github.com/fusepoolP3/overall-architecture/blob/master/default-ports.md). This needs to be set explicitly until [SLING-4672](https://issues.apache.org/jira/browse/SLING-4672) gets released.
