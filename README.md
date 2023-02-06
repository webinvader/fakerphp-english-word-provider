# Extended Provider for PHP Faker Library to use english words

#### Purpose.

The default Lorem provider that comes with the PHP Faker Library generates words in Latin,
and it can be tricky to distinguish between the generated data.
This provider extends Lorem provider with the set of English words.

#### Install
```shell
$ composer require --dev webinvader/faker-english-word-provider
```

#### Usage in service provider

```php
<?php

namespace App\Providers;

use Webinvader\Faker\Provider\EnglishWord;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        $this->app->bind('Faker\Generator:en_US', function ($app) {
            $faker = \Faker\Factory::create();
            $faker->addProvider(EnglishWord::class);
            return $faker;
        });
    }
}
```

#### Or you can use it in individual test in factory definition
```php
    use Webinvader\Faker\Provider\EnglishWord;

    public function definition(): array
    {
        $this->faker->addProvider(EnglishWord::class);
    ...
```