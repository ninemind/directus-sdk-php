<p align="center">
<img src="https://s3.amazonaws.com/f.cl.ly/items/3Q2830043H1Y1c1F1K2D/directus-logo-stacked.png" alt="Directus Logo"/>
</p>

# Directus SDK for PHP
For PHP driven applications, use this SDK to more easily communicate with your Directus managed database.

[![Build Status](https://img.shields.io/travis/directus/directus-sdk-php.svg?style=flat-square)](https://travis-ci.org/directus/directus-sdk-php)
[![Scrutinizer](https://img.shields.io/scrutinizer/g/directus/directus-sdk-php.svg?style=flat-square)](https://scrutinizer-ci.com/g/directus/directus-sdk-php)
[![Scrutinizer Coverage](https://img.shields.io/scrutinizer/coverage/g/directus/directus-sdk-php.svg?style=flat-square)](https://scrutinizer-ci.com/g/directus/directus-sdk-php/?branch=master)

## Work In Process.

## Install

### Via Composer

You can install the SDK using [Composer](http://getcomposer.org) by running the command below:

``` bash
$ composer require directus/sdk
```

Or add `directus/sdk` to composer `require` list.
```json
{
  "require": {
    "directus/sdk": "0.9.*"
  }
}
```

Then run `composer install`.

To use the SDK you have to include the [composer autoload](https://getcomposer.org/doc/01-basic-usage.md#autoloading)

```php
require_once 'vendor/autoload.php';
```

## Usage

### Database connection
``` php
require 'vendor/autoload.php';

$config = [
    'database' => [
        'hostname' => 'localhost',
        'username' => 'root',
        'password' => '123',
        'database' => 'directus_db',
    ]
];

$client = \Directus\SDK\ClientFactory::create($config);
$articles = $client->getEntries('articles');

foreach($articles as $article) {
    echo $article->title . '<br>';
}
```

### Directus Hosted

```php
require 'vendor/autoload.php';

$client = new \Directus\SDK\ClientFactory::create('user-token', [
    // the sub-domain in your instance url
    'instance_key' => 'user--instance',
    'version' => '1' // Optional - default 1
]);

$articles = $client->getEntries('articles');
foreach($articles as $article) {
    echo $article->title . '<br>';
}
```

### Your own server

```php
require 'vendor/autoload.php';

$client = new \Directus\SDK\ClientFactory::create('user-token', [
    // Directus API Path without its version
    'base_url' => 'http://directus.local/api/',
    'version' => '1' // Optional - default 1
]);

$articles = $client->getEntries('articles');
foreach($articles as $article) {
    echo $article->title . '<br>';
}
```
