ProceduralTextureMaker
========================

### Introduction
ProceduralTextureMaker generates texture images in arbitrary sizes based on graphs of nodes that take other nodes' output as input and transform them into new images.  

Nodes are added dynamically and connected to each other graphically.  
Custom UI widgets are created for each node based on the texture generator's available settings, making it easy to try out new configuration and watch how changes affect the output.  
The project files with texture graphs can be saved to and loaded from XML files, and images can be exported to PNG files.  

A number of texture generators written in C++ and Javascript are included with the project.  

For more general information about procedural textures, see https://en.wikipedia.org/wiki/Procedural_texture

### Technical Details
The application is written in C++ and uses the Qt framework.  
It has been tested on Mac OS 10.13 and Windows 10 with Qt 5.9.1 and 5.10.  
It uses multiple threads on multiple CPU cores where supported, so that CPU intensive texture calculations don't affect the UI performance.  
It's easy to extend the application by adding new generators, especially ones written in Javacript as those are loaded dynamically from external files.

### Javascript
The external Javascript texture generators are parsed and run using the QtScript engine.  
As the QtScript module is listed as deprecated and not installed by default by the Qt installer there is also support for running the scripts with the QJSEngine class.  
However QJSEngine is not enabled by default as there were some strange unresolved bugs related to QJSEngine's memory management encountered during development. It's easy though to change which engine should be used by adding or removing a `#define USE_QJSENGINE` in _generators/javascript.cpp_.  
One example Javascript texture generator is included in the directory _JavascriptTextureGenerators_.

### How to build
Install and configure Qt 5.10, available at http://www.qt.io/qt5-10.  
If Qt Creator was installed, use it to open and build the project file `ProceduralTextureMaker.pro`.  
If Qt Creator isn't available, use a terminal to browse to the project root directory and run `qmake && make && make install`.  
If you're compiling with the QScript engine (see the Javascript section above) make sure that the Qt installation includes that module.

### License
Released under GPL version 3.

### Author
Johan Lindqvist  
johan.lindqvist@gmail.com  
https://github.com/johanokl

Icon from https://www.iconfinder.com/icons/28730/