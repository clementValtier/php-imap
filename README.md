php-imap
========

An object-oriented PHP IMAP library.

PHP >= 8.4 is required for version 2.x. For PHP 7 or earlier, use version 1.x.

Installation
------------

```
composer require acucchieri/php-imap
```

Usage
-----

```php
<?php

use AC\Imap\Imap;

$imap = new Imap([
    'host' => 'imap-server.domain.tld', // Hostname. Required
    'port' => 143,                      // Host port. Default : 143
    'folder' => 'INBOX',                // Mailbox name. Default : 'INBOX'
    'user' => 'user-login',             // Login. Required
    'password' => 'user-password',      // Password. Required
    'flags' => [],                      // Connection flags. Optionnal
    'lazy' => false,                    // Lazy mode. Default : false
]);

/** @var \AC\Imap\Collection\MessageCollection $result */
$result = $imap->search('FROM "foo@bar.tld"');

foreach ($result as $message) {
    /** @var \AC\Imap\Message $message */
    var_dump($message->getSubject());
}
```

Tests
-----

Create phpunit.xml file based on phpunit.xml.dist and populate environment variables.

```
./vendor/bin/phpunit
```

