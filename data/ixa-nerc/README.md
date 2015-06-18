# Fusepool IXA Pipe Nerc models

[IXA Pipe Nerc](https://github.com/ixa-ehu/ixa-pipe-nerc/) provides good quality Named Entity Recognition Models for English (`en`), German (`de`), Spanish (`es`), Italian (`it`), Dutch (`nl`) and Basque (`eu`). 

This modules provides those models so that they can be loaded by the [Apache Stanbol Datafile Provider](http://stanbol.apache.org/docs/trunk/utils/datafileprovider) Infrastructure.

This model also provides a default configuration of the Apache Stanbol [OpenNLP Custom NER engine](http://stanbol.apache.org/docs/trunk/components/enhancer/engines/opennlpcustomner) that loads the included models as well as en Enhancement Chain with the name `ixa-ner` that can be directly used as Fusepool Transformer for Named Entity Recognition in the listed languages.

Extracted Named Entities will use the following `fam:entity-type` values:

* `dbo:Person` for persons
* `dbo:Organisation` for organizations
* `dbo:Place` for locations
* `skos:Concept` for misc

This configuration makes the results compatible with the default configuration of the Fusepool [Literal Extraction Transformer](https://github.com/fusepoolP3/p3-literal-extraction-transformer) (version `1.1+`)

__NOTE:__ The IXA NER models are rather resource intensive. Loading the models requires about 6 GByte of RAM. Therefore it is recommended to start a Stanbol Launcher that includes those models with at least 8 GByte of RAM (`-Xmx8g`)
