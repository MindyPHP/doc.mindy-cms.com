---
title: Fixtures
slug: data_fixture_bundle
---
 
Установка:

```
composer require mindy/data-fixture-bundle
```

Настройка:

В файл `config/bundles.php` добавьте: 

```php
    // ...
    Mindy\Bundle\DataFixtureBundle\DataFixtureBundle::class => ['dev' => true],
    // ...
```

### Использование

В вашем `bundle` добавьте директорию `DataFixture` с классом

```php
<?php

declare(strict_types=1);

namespace App\Bundle\MyBundle\DataFixture;

use App\Bundle\MyBundle\Model\User;
use Mindy\Bundle\DataFixtureBundle\DataFixtureManager\AbstractFixtureProvider;

class ConsultFixtureProvider extends AbstractFixtureProvider
{
    public function load()
    {
        $consult = new User([
            'id' => 1,
            'name' => 'test',
            'phone' => 'test'
        ]);
        $consult->save();
    }
}
```

Далее вы можете загрузить ваши фикстуры с помощью команды `orm:fixture:load`

```bash
./bin/console orm:fixture:load -b MyBundle # Загрузка фикстур только из 1 бандла
./bin/console orm:fixture:load # Загрузка фикстур только из всех бандлов
```
