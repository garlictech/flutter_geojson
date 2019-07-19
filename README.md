# Geojson

Utilities to work with geojson data in Dart.

## Example

   ```dart
   import 'dart:io';
   import 'package:geojson/geojson.dart';

   void main() async {
     polygons();
     lines();
   }

   void polygons() async {
     final file = File("lakes_of_europe.geojson");
     final geoSeries = await geoSerieFromGeoJsonFile(file, nameProperty: "label");
     for (final geoSerie in geoSeries) {
       print("${geoSerie.name}: ${geoSerie.geoPoints.length} geopoints");
     }
   }

   void lines() async {
     final file = File("railroads_of_north_america.geojson");
     final geoSeries = await geoSerieFromGeoJsonFile(file, nameProperty: "continent");
     for (final geoSerie in geoSeries) {
       print("${geoSerie.name}: ${geoSerie.geoPoints.length} geopoints");
     }
   }
   ```

## Api

`geoSerieFromGeoJson`: create geoseries from geojson string data. Parameters:

- `data`: a string with the geojson data
- `nameProperty`: the property used for the geoserie name, default "name"
- `type`: the geoserie type, infered from the file if not provided
- `verbose`: print data if true

`geoSerieFromGeoJsonFile`: create geoseries from a geojson file. Parameters:

- `file`: the file to load, required
- `nameProperty`: the property used for the geoserie name, default "name"
- `type`: the geoserie type, infered from the file if not provided
- `verbose`: print data if true
