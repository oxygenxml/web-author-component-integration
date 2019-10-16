# web-author-component-integration
A sample Maven project using the Web Author Component.

This project generates a .war by overlaying the Web Author Component and adding frameworks and plugins to it.

## Migrating ``oxygen-sdk-samples`` project to use ``web-author-component`` and ``web-author-framewors`` 
A step by step procedure can be found [here](migration-procedure.md) 

## Prerequisites

Before running the  XML Web Author Component, you need to register for the Oxygen XML SDK at https://www.oxygenxml.com/oxygen_sdk/download.html and ask for a development license from support@oxygenxml.com.

## Plugins


Plugins added as Maven dependencies:

* web-author-webdav-plugin
* web-author-webdav-server-plugin
* web-author-charpicker-plugin
* web-author-svg-plugin
* web-author-mathml-plugin
* web-author-rest-plugin

### Adding new plugins

The project bundles all it's Maven dependencies that have the `plugin` classifier. So, if the plugin you want to add can be found on a Maven repository and it has this classifier, you just need to declare a dependency on it. You can use the plugins declared in the `pom.xml` file as examples.

To add the additional **File comparison plugin**, you should add the following dependency in the `pom.xml` file:  

    <dependency>
      <artifactId>web-author-diff-plugin</artifactId>
      <groupId>com.oxygenxml</groupId>
      <version>${oxygen.version}</version>
      <classifier>plugin</classifier>
      <scope>provided</scope>
    </dependency>
    
Note that this plugin requires a separate license. For more details, contact the Oxygen sales team at sales@oxygenxml.com. 

The application also automatically bundles all the folders from the `web-author-component-integration/plugins/` directory (you will have to create it) as plugins so that you can copy the desired plugin(s) in it.


## Frameworks

Frameworks already added through Maven dependencies:

* dita
* dockbook
* mathml
* svg
* tei
* xhtml
* xhtml11

### Adding new frameworks

The project bundles all the frameworks from the  `web-author-frameworks` artifact. To add a new framework that is a Maven artifact, you just need to unpack it in the `${project.build.directory}/frameworks/` directory during the `generate-resources` Maven phase (this is what is done with `web-author-frameworks`).

The application also automatically bundles all the content of the `web-author-component-integration/frameworks/` directory (you will have to create it) as frameworks so that you can copy the desired framework(s) in it.

Copyright and License
---------------------
Copyright 2018 Syncro Soft SRL.

This project is licensed under [Apache License 2.0](https://github.com/oxygenxml/web-author-component-integration/blob/master/LICENSE)
