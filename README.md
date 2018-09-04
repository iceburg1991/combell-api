# Combell public API

[![Build Status](https://travis-ci.org/combell-nl/combell-api.svg?branch=master)](https://travis-ci.org/combell-nl/combell-api)
[![Coverage Status](https://coveralls.io/repos/github/combell-nl/combell-api/badge.svg?branch=master)](https://coveralls.io/github/combell-nl/combell-api?branch=master)

The *Combell public API project* wraps around [Guzzle](http://docs.guzzlephp.org/en/latest/) and offers *HMAC authentication*. You can use the client to easily connect to the Combell public API endpoint.

To learn more about the **Combell public API**, go to [https://api.combell.nl/](https://api.combell.nl/).

## Install

```
composer require combell-nl/combell-api
```


## Example

The code example below registers a new domain name on your account.

```php
<?php

require dirname(__DIR__) . '/vendor/autoload.php';

$client = new \Combell\Client(
    [
        'debug' => true,
        'base_uri' => 'https://api.combell.nl',
        'combell_api_key' => 'XXXX',
        'combell_api_secret' => 'YYYY'
    ]
);

$body = new \stdClass();
$body->domain_name = 'domain-name-to-register.eu';

// Register domain name
$response = $client->post('/v2/domains/registrations', ['json' => $body]);

// Dump location header with link to provisioning job
var_dump(
    $response->getHeader('Location')
);
```

Go to the [examples](examples) folder to see more examples.