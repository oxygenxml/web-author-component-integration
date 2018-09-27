# web-author-component-integration
A sample Maven project using the Web Author Component

This project generates a .war by overlaying the Web Author Component and adding frameworks and plugins to it.

## Plugins


Plugins added as Maven dependencies:

* web-author-webdav-plugin
* web-author-webdav-server-plugin
* web-author-charpicker-plugin
* web-author-svg-plugin
* web-author-mathml-plugin
* web-author-rest-plugin
* web-author-frameworks

### Adding new plugins

The project bundles all it's dependencyes that have the `plugin` classifier so if the plugin has this classifier you just have to declare a dependency on it. You can use the plugins already added as examples.

The application also bundles automatically as plugins all the folders from the `web-author-component-integration/plugins/` directory (you will have to create it) so you can copy the desired plugin(s) in it.



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

The project bundles all the frameworks from the  `web-author-frameworks` artifact. To add a new framework that is a Maven artifact you just have to unpack it in the `${project.build.directory}/frameworks/` directory during the `generate-resources` Maven phase (This is what we do with  `web-author-frameworks`).

The application also bundles automatically as frameworks all the content of the `web-author-component-integration/frameworks/` directory (you will have to create it) so you can copy the desired framework(s) in it.
