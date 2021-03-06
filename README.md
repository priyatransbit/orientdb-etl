# Project MOVED

OrientDB ETL has been moved to OrientDB core modules: https://github.com/orientechnologies/orientdb/tree/develop/etl

 






# ETL

The OrientDB-ETL module is an amazing tool to move data from and to OrientDB by executing an [ETL process](http://en.wikipedia.org/wiki/Extract,_transform,_load). It's super easy to use. OrientDB ETL is based on the following principles:
- one [configuration file](http://www.orientechnologies.com/docs/last/Configuration-File.html) in [JSON](http://en.wikipedia.org/wiki/JSON) format
- one [Extractor](http://www.orientechnologies.com/docs/last/Extractor.html) is allowed to extract data from a source
- one [Loader](http://www.orientechnologies.com/docs/last/Loader.html) is allowed to load data to a destination
- multiple [Transformers](http://www.orientechnologies.com/docs/last/Transformer.html) that transform data in pipeline. They receive something in input, do something, return something as output that will be processed as input by the next component

## How ETL works
```
EXTRACTOR => TRANSFORMERS[] => LOADER
```
Example of a process that extract from a CSV file, apply some change, lookup if the record has already been created and then store the record as document against OrientDB database:

```
+-----------+-----------------------+-----------+
|           |              PIPELINE             |
+ EXTRACTOR +-----------------------+-----------+
|           |     TRANSFORMERS      |  LOADER   |
+-----------+-----------------------+-----------+
|   FILE   ==>  CSV->FIELD->MERGE  ==> OrientDB |
+-----------+-----------------------+-----------+
```

The pipeline, made of transformation and loading phases, can run in parallel by setting the configuration ```{"parallel":true}```.

## Installation
Starting from OrientDB v2.0 the ETL module will be distributed in bundle with the official release. If you want to use it, then follow these steps:
- Clone the repository on your computer, by executing:
 - ```git clone https://github.com/orientechnologies/orientdb-etl.git```
- Compile the module, by executing:
 - ```mvn clean install```
- Copy ```script/oetl.sh``` (or .bat under Windows) to $ORIENTDB_HOME/bin
- Copy ```target/orientdb-etl-2.0-SNAPSHOT.jar``` to $ORIENTDB_HOME/lib

## Usage

```
$ cd $ORIENTDB_HOME/bin
$ ./oetl.sh config-dbpedia.json
```

## Available Components
- [Blocks](http://www.orientechnologies.com/docs/last/Block.html)
- [Sources](http://www.orientechnologies.com/docs/last/Source.html)
- [Extractors](http://www.orientechnologies.com/docs/last/Extractor.html)
- [Transformers](http://www.orientechnologies.com/docs/last/Transformer.html)
- [Loaders](http://www.orientechnologies.com/docs/last/Loader.html)

Examples:
- [Import DBPedia](http://www.orientechnologies.com/docs/last/Import-from-DBPedia.html)
- [Import from a DBMS](http://www.orientechnologies.com/docs/last/Import-from-DBMS.html)


Look to the [Documentation](http://www.orientechnologies.com/docs/last/Introduction.html) for more information.
