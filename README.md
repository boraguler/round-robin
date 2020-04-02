# RoundRobin for Laravel 5.8+


Round-Robin is an easy way to create schedule with round-robin(rr) technique.

## Installation
1) In order to install Laravel Round-Robin, just add the following to your composer.json. Then run `composer update`:
```json
"boraguler/round-robin": "0.1.*"
```
or run `composer require boraguler/round-robin`

2) Open your `config/app.php` and add the following to the `providers` array:
```php
BoraGuler\RoundRobin\RoundRobinServiceProvider::class,
```

3) Open your `config/app.php` and add the following to the `facades` array:
```php
'RoundRobin' => boraguler\RoundRobin\RoundRobinFacade::class,
```


## Controllers and etc
```php
use BoraGuler\RoundRobin\RoundRobin;
```


## Using (Examples)
Setuping (without Facade):
```php
$teams = ['Galatasaray','Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = new RoundRobin($teams)->make();
// or with 'from' static method
$schedule = RoundRobin::from($teams)->make();
```

With a facade:
```php
$teams = ['Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->make();
```


Generate a schedule without randomly shuffling the teams using the $shuffle boolean parameter:
```php
$teams = ['Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->doNotShuffle()->make();
```

Use your own seed with the $seed integer parameter for predetermined shuffling:
```php
$teams = ['Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->shuffle(15)->make();
```

If you want a double Round-robin:
```php
$teams = ['Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->doubleRoundRobin()->make();
```

If you want a get a *Schedule* Object:
```php
$teams = ['Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->makeSchedule();
```

## License
BoraGuler Round-Robin is free software distributed under the terms of the MIT license.
