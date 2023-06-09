Yii 2 GeoIP extension
=====================
[![Latest Stable Version](https://poser.pugx.org/perfectpanel/yii2-geoip/version)](https://packagist.org/packages/perfectpanel/yii2-geoip) [![Total Downloads](https://poser.pugx.org/perfectpanel/yii2-geoip/downloads)](https://packagist.org/packages/perfectpanel/yii2-geoip) [![Build Status](https://travis-ci.org/perfectpanel/yii2-geoip.svg?branch=1.0.1)](https://travis-ci.org/perfectpanel/yii2-geoip) [![HHVM Status](https://img.shields.io/hhvm/perfectpanel/yii2-geoip.svg)](http://hhvm.h4cc.de/package/perfectpanel/yii2-geoip) [![CodeClimate](https://codeclimate.com/github/perfectpanel/yii2-geoip.png)](https://codeclimate.com/github/perfectpanel/yii2-geoip) 

Provides information about geographical location of user by IP address.

Currently available:
* Country
* City
* Latitude, Longitude
* Country ISO Code

## Install

Run

```bash
$ php composer.phar require perfectpanel/yii2-geoip "~1.0"
```

#### OR 

add to your `composer.json`

```json
{
    "require": {
        "perfectpanel/yii2-geoip": "~1.0"
    }
}
```

and run

```bash
$ php composer update
```


## Usage

### Like component

```php
<?php

$config = [
    ...
    'components' => [
        'geoip' => ['class' => 'perfectpanel\GeoIP\GeoIP'],
    ]
    ...
];
```

somewhere in code

```php
$ip = Yii::$app->geoip->ip(); // current user ip

$ip = Yii::$app->geoip->ip("208.113.83.165");

$ip->city; // "San Francisco"
$ip->country; // "United States"
$ip->location->lng; // 37.7898
$ip->location->lat; // -122.3942
$ip->isoCode; // "US"

```

### Like object directly somewhere in your application

```php
$geoip = new \perfectpanel\GeoIP\GeoIP();
$ip = $geoip->ip("208.113.83.165");

$ip->city; // "San Francisco"
$ip->country; // "United States"
$ip->location->lng; // 37.7898
$ip->location->lat; // -122.3942
$ip->isoCode;  // "US"
```

### Provide a custom database (for example, if you own a licence)

```php
<?php

$config = [
    ...
    'components' => [
        'geoip' => [
            'class' => 'perfectpanel\GeoIP\GeoIP',
            'dbPath' => Yii::getAlias('@example/maxmind/database/city.mmdb')
        ],
    ]
    ...
];
```

This product includes GeoLite2 data created by MaxMind, available from http://www.maxmind.com
