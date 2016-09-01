# Country List

Country List is a package for Laravel and Lumen which lists all countries with names and ISO 3166-1 codes in all languages and data formats.


## Installation

Add `arkadedigital/country-list` to your Laravel or Lumen project using [Composer](https://getcomposer.org).

```sh
composer require arkadedigital/country-list
```

### Laravel

Open up `app/config/app.php` and add the service provider to your `providers` array.

```php
'providers' => [
    Arkadedigital\CountryList\CountryListServiceProvider::class,
]
```

Finally, add the alias.

```php
'aliases' => [
    'Countries' => Arkadedigital\CountryList\CountryListFacade::class,
]
```

### Lumen

Open up `bootstrap/app.php` and add the service provider to the file.

```php
$app->register(Arkadedigital\CountryList\CountryListServiceProvider::class);
```

## Usage

- Locale (en, en_US, fr, fr_CA...)
- Format (csv, flags.html, html, json, mysql.sql, php, postgresql.sql, sqlite.sql, sqlserver.sql, txt, xml, yaml)
- Data source (icu, cldr)

Get all countries

```php
Route::get('/', function() {
    return Countries::getList('en', 'json', 'cldr');
});
```


Get one country

```php
Route::get('/', function() {
    return Countries::getOne('RU', 'en', 'cldr');
});
```

## Credit

This project is a fork of Monarobase's [Country List](https://github.com/Monarobase/country-list) project.
