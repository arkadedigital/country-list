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
- Format (csv, html, json, mysql.sql, php, postgresql.sql, sqlite.sql, txt, xliff, xml, yaml)

Get all countries in English as JSON

```php
Route::get('/', function() {
    return Countries::getList('en', 'json');
});
```

Get the name of Russia in English

```php
Route::get('/', function() {
    return Countries::getOne('RU', 'en');
});
```

### Dependency Injection

You can choose to use dependency injection if you are using Lumen or if you prefer them to Laravel's facades.

```php
use Arkadedigital\CountryList\CountryList;

class Controller extends BaseController
{
    protected $countryList;

    public function __construct(CountryList $countryList)
    {
        $this->countryList = $countryList;
    }

    public function index()
    {
        return $this->countryList->getList('en', 'csv');
    }
}
```

## Support

Feel free to [create a GitHub issue](https://github.com/arkadedigital/country-list/issues/new) or [send us an email](mailto:support@arkade.com.au) for support regarding this Laravel package.

## Credit

This project is a fork of Monarobase's [Country List](https://github.com/Monarobase/country-list) project.
