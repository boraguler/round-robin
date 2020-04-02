# RoundRobin for Laravel 5.8+
[![Latest Stable Version](https://poser.pugx.org/boraguler/round-robin/v/stable)](https://packagist.org/packages/boraguler/round-robin) [![Total Downloads](https://poser.pugx.org/boraguler/round-robin/downloads)](https://packagist.org/packages/boraguler/round-robin)
[![Monthly Downloads](https://poser.pugx.org/boraguler/round-robin/d/monthly)](https://packagist.org/packages/boraguler/round-robin) [![Latest Unstable Version](https://poser.pugx.org/boraguler/round-robin/v/unstable)](https://packagist.org/packages/boraguler/round-robin)
[![License](https://poser.pugx.org/boraguler/round-robin/license)](https://packagist.org/packages/boraguler/round-robin)

BoraGuler\Round-Robin is an easy way to create schedule with round-robin(rr) technique.

## Installation
1) In order to install BoraGuler\Round-Robin, just add the following to your composer.json. Then run `composer update`:
```json
"boraguler/round-robin": "1.0.*"
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
$teams = ['Galatasaray', 'Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = new RoundRobin($teams)->make();
// or with 'from' static method
$schedule = RoundRobin::from($teams)->make();
```

With a facade:
```php
$teams = ['Galatasaray', 'Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->make();
```


Generate a schedule without randomly shuffling the teams using the $shuffle boolean parameter:
```php
$teams = ['Galatasaray', 'Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->doNotShuffle()->make();
```

Use your own seed with the $seed integer parameter for predetermined shuffling:
```php
$teams = ['Galatasaray', 'Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->shuffle(15)->make();
```

If you want to pre-define round number (default = 1):
```php
$teams = ['Galatasaray', 'Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->rounds(3)->make();
```

If you want a double Round-robin:
```php
$teams = ['Galatasaray', 'Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->doubleRoundRobin()->make();
```

If you want a get a *Schedule* Object:
```php
$teams = ['Galatasaray', 'Arsenal', 'Atlético de Madrid', 'Borussia', 'Barcelona','Liverpool', 'Bayer 04', 'Real Madrid'];
$schedule = RoundRobin::from($teams)->makeSchedule();
```

## License
BoraGuler Round-Robin is free software distributed under the terms of the MIT license.
