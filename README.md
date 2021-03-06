LeafLet Extension for Yii2
==========================

Extension library to display interactive maps with [LeafletJs](http://leafletjs.com/)

Installation
------------

The preferred way to install this extension is through
[composer](http://getcomposer.org/download/).  This requires the
[`composer-asset-plugin`](https://github.com/francoispluchino/composer-asset-plugin),
which is also a dependency for yii2 – so if you have yii2 installed, you are
most likely already set.

Either run

```
php composer.phar require "2amigos/yii2-leaflet-extension" "*"
```
or add

```json
"2amigos/yii2-leaflet-extension" : "*"
```

to the require section of your application's `composer.json` file.

Usage
-----

One of the things to take into account when working with [LeafletJs](http://leafletjs.com/) is that we need a Tile
Provider. Is very important, if we fail to provide a Tile Provider Url, the map will display plain, without any maps at
all.

The following example, is making use of [MapQuest](http://developer.mapquest.com/):

```
// first lets setup the center of our map
$center = new dosamigos\leaflet\types\LatLng(['lat' => 51.508, 'lng' => -0.11]);

// now lets create a marker that we are going to place on our map
$marker = new \dosamigos\leaflet\layers\Marker(['latLng' => $center, 'popupContent' => 'Hi!']);

// The Tile Layer (very important)
$tileLayer = new \dosamigos\leaflet\layers\tiles\MapQuest();

// now our component and we are going to configure it
$leaflet = new \dosamigos\leaflet\LeafLet([
    'center' => $center, // set the center
]);
// Different layers can be added to our map using the `addLayer` function.
$leaflet->addLayer($marker)      // add the marker
        ->addLayer($tileLayer);  // add the tile layer

// finally render the widget
echo \dosamigos\leaflet\widgets\Map::widget([
    'leafLet' => $leaflet,
    'height' => 300,     // map height in px, defaults to 200px
]);

// we could also do
// echo $leaflet->widget(['height' => 300]);
```

Further Information
-------------------

For further information regarding the multiple settings of LeafLetJS library please visit
[its API reference](http://leafletjs.com/reference.html)


> [![2amigOS!](http://www.gravatar.com/avatar/55363394d72945ff7ed312556ec041e0.png)](http://www.2amigos.us)

<i>Web development has never been so fun!</i>
[www.2amigos.us](http://www.2amigos.us)
