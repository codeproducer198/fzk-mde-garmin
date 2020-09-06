fzk-mde-garmin
==============

<strong>F</strong>rei<strong>z</strong>eit<strong>k</strong>arte <strong>M</strong>ap <strong>D</strong>evelopment <strong>E</strong>nvironment for <strong>G</strong>armin

Branch fenix
------------

**This branch "fenix" is optimized for Garmin Fenix 6 pro's and based on the great work of [Cryptomilks FZK pull request](https://github.com/cryptomilk/fzk-mde-garmin).**

General
-------
The 'Freizeitkarten' maps are based on data of the OpenStreetMap-Project and are provided as general maps for

* your leisure time
* and for outdoor activities

This repository contains the development environment used for creating the 'Freizeitkarte' maps.

### More Information

EN:
* [Freizeitkarte Main Page](https://www.freizeitkarte-osm.de/garmin/en/index.html)
* [Freizeitkarte Map Development](https://www.freizeitkarte-osm.de/garmin/en/development.html)

DE:
* [Freizeitkarte Hauptseite](https://www.freizeitkarte-osm.de/garmin/de/index.html)
* [Freizeitkarte Karten Entwicklung](https://www.freizeitkarte-osm.de/garmin/de/entwicklung.html)

Build OSM map for Garmin Fenix
---------------------------------

The build is described in the links aboved.
You can set up a environment with the following commands:
```
cd Freizeitkarte-Entwicklung/
./mt.pl bootstrap urls http://osm.thkukuk.de/data/bounds-latest.zip http://osm.thkukuk.de/data/sea-latest.zip
./mt.pl create
```
To build a map use:
```
./mt.pl --downloadbar fetch_osm Freizeitkarte_AUT
./mt.pl --downloadbar fetch_ele Freizeitkarte_AUT

./mt.pl --ram=22528 --cores=8 join Freizeitkarte_AUT
./mt.pl --ram=22528 --cores=8 --language=de split Freizeitkarte_AUT
./mt.pl --ram=22528 --cores=8 --typfile=fenix.TYP --style=fzk-fenix --language=de build Freizeitkarte_AUT
./mt.pl --ram=22528 --cores=8 --typfile=fenix.TYP --style=fzk-fenix --language=de gmapsupp Freizeitkarte_AUT
```
The generated map was stored in the folder `install/`.
To see all the available maps use the help `./mt.pl -?`.

_Note: For using 1 CPU core you need 2GB of RAM. I have 16GB of RAM in my machine and use also 8 cores._
