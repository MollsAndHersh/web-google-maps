# Web Google Maps

Web Google Maps is a Web Component which lets you easily integrate Google Maps in your application.

[![GitHub](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/fluster/web-google-maps)
[![npm](https://img.shields.io/npm/dm/web-photo-filter.svg)]()

## Goals

The goal of this project is to provide an agnostic Web Component to easily integrate Google Maps into my project [Fluster](https://fluster.io).

### Features

Furthermore to offering a simple wrapper to use Google Maps, this Web Component will inject and load only once the Google Maps Javascript API. This allows you for example to include multiple Google Maps in a single page. 

## Installation

    $ npm install web-google-maps

## Getting Started

The Web Google Maps Component could be use like following:

    <web-google-maps [lat]="47.36667" [lng]="8.55"></web-google-maps>

Both `lat` and `lng` are mandatory.

### Google Maps API key

To use the Google Maps API you need to provide your own Google Maps API key. This Web Component will take care of injecting and loading the Google Map Javascript bundle only once using your key. 

    <web-google-maps [apiKey]="XXXXXXXXXXXXXXXXXXXXXXXXX" [lat]="47.36667" [lng]="8.55"></web-google-maps>

### Options

Map's options could be provided using the property `options`. This property inherit all options from `google.maps.MapOptions`.

     const myOptions = {
         zoom: 9
     };
     
     <web-google-maps [lat]="47.36667" [lng]="8.55" [options]="myOptions"></web-google-maps>

### Style

A map style could be provided using the property `mapStyle`. This property should contains then `name` of the style and a style array which inherit all options from `google.maps.MapTypeStyle[]`.

     const mapStyle = {
         style: [
           {
             "featureType": "road",
             "stylers": [
               {
                 "hue": "#5e00ff"
               },
               {
                 "saturation": -79
               }
             ]
           }
         ],
            name: "Purple Rain"
         }; 
      
      <web-google-maps [lat]="47.36667" [lng]="8.55" [mapStyle]="mapStyle"></web-google-maps>

### Circles

Circles could be provided using the property `circles`. This property is an array of values which inherit all options from `google.maps.CircleOptions`. If you don't wish to define a center value, you could provide `lat` and `lng` parameters instead.

     const circles = [
         {
           lat: 47.46667,
           lng: 8.55,
           radius: 10000,
           fillColor: '#ff8ea3',
           draggable: false,
           editable: false,
           clickable: false
         }
     ];
     
     <web-google-maps [lat]="47.36667" [lng]="8.55" [circles]="circles"></web-google-maps>

### Markers

Markers could be provided using the property `markers`. The property could contains an array of markers which inherit all options from `google.maps.MarkerOptions` and a boolean variable `fitBounds` which will trigger a resize of the maps around all markers. Furthermore, for each marker, you could provide information window inheriting properties from `google.maps.InfoWindowOptions` and if you wish, `lat` and `lng` instead of providing a center.

     const markers = [{
         lat: 43.073051,
         lng: -89.401230,
         infoWindowOptions: {
           content: "Cool"
         }
     }];
     
     const myMarkers = {
         markers: markers,
         fitBounds: true
     };
     
     <web-google-maps [lat]="47.36667" [lng]="8.55" [markers]="markers"></web-google-maps>


**Important note**: Safari 11 does not seems to handle correctly `markers` if the Google Maps is used in a shadow dom, which is the case of this Web Component. The workaround is to specify an `icon` for each markers which will make Safari happy (References: [Stackoverflow workaround](https://stackoverflow.com/a/50964637/5404186) and [Google Web Components issue](https://github.com/GoogleWebComponents/google-map/issues/419))

#### Vanilla JS

For an example of Vanilla JS use, you could have a look to the [index.html](src/index.html).

Note: In Vanilla JS, only `string` properties could be directly set to the component. In order to specify object or boolean properties, wait for the document to be loaded and set the properties with the help of a script.

## Showcase

A showcase is available at [https://webgoogl3maps.com](https://webgoogl3maps.com)  

The above showcase is simply the `www` folder of this project. If you clone the repository you could run it locally too using `npm start`, but you would need first to inject your `apiKey` in [index.html](src/index.html).

## License

MIT © [David Dal Busco](mailto:david.dalbusco@outlook.com) 
     
     