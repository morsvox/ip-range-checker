# IP Range Checker

This is a simple helper package that I use when I need to check if an IP is in a given IP range.

All ideas, contributions and criticism are welcome.

# Installation

```bash
composer require morsvox/ip-range-checker
```

# Usage

Import the class in your script:

```php
use IlkerMutlu\IPRangeChecker\Checker;

$ip = '192.168.0.22';
$checker = Checker::forIp($ip);
```

Pass the start IP and end IP in an array to the ```setRange()``` method.

```php
$checker->setRange([
    '192.168.0.1',
    '192.168.0.28'
]);

// $checker->check() will return true for IPs between
// 192.168.0.1 and 192.168.0.28
// 192.168.0.19 will return TRUE
// 192.168.1.41 will return FALSE
```

You can also use a wildcard.

```php
$checker->setRange('192.168.0.*');

// $checker->check() will return TRUE for IPs between
// 192.168.0.1 and 192.168.0.255
// 192.168.0.41 will return TRUE
// 192.168.1.41 will return FALSE
```

OR, you can pass in two IPs separated with a dash.

```php
$checker->setRange('192.168.0.4-192.168.0.54');

// $checker->check() will return TRUE for IPs between
// 192.168.0.4 and 192.168.0.54
// 192.168.0.41 will return TRUE
// 192.168.0.61 will return FALSE
```

After setting the range, just call the ```check()``` method on the checker instance, which will return a boolean value.

```php
$checker->check();
```

## TODO

1. Tests
2. ~~Support dashed IP range strings~~
3. Support CIDR
