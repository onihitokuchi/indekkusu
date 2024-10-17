```sh
composer install
composer update

composer require livewire/livewire
php artisan livewire:publish --config

composer require livewire/volt
php artisan volt:install

composer require laravel/fortify
php artisan fortify:install

composer require intervention/image

composer require propaganistas/laravel-phone

composer require --dev barryvdh/laravel-debugbar

composer require --dev barryvdh/laravel-ide-helper

pnpm install
pnpm update

pnpm install -D sass
pnpm install -D @tabler/core
pnpm install -D tom-select
pnpm install -D @alpinejs/mask

touch ./database/database.sqlite
php artisan migrate

mkdir -p ./resources/views/pages
```

/.gitignore

```sh
/_ide_helper_models.php
/_ide_helper.php
/composer.lock
/pnpm-lock.yaml
```

/composer.json

```json
{
  "post-update-cmd": [
    "@php artisan ide-helper:generate",
    "@php artisan ide-helper:models -N"
  ]
}
```

/vite.config.js

```js
import { defineConfig } from "vite";
import laravel from "laravel-vite-plugin";

export default defineConfig({
  plugins: [
    laravel({
      input: ["resources/scss/index.scss", "resources/js/index.js"],
      refresh: true,
    }),
  ],
});
```

/config/livewire.php

```php
<?php

return [
    'inject_assets' => false,
    'pagination_theme' => 'bootstrap'
]
```

/resources/js/index.js

```js
import mask from "@alpinejs/mask";
import "@tabler/core/dist/js/demo-theme";
import "@tabler/core/dist/js/tabler";
import TomSelect from "tom-select";
import "./bootstrap";
window.TomSelect = TomSelect;

import {
  Alpine,
  Livewire,
} from "./../../vendor/livewire/livewire/dist/livewire.esm";

Alpine.plugin(mask);

Livewire.start();
```

/resources/scss/index.scss

```scss
@use "@tabler/core/dist/css/tabler.min.css";
@use "@tabler/core/dist/css/tabler-flags.min.css";
@use "@tabler/core/dist/css/tabler-payments.min.css";
@use "@tabler/core/dist/css/tabler-vendors.min.css";
@use "tom-select/dist/css/tom-select.min.css";

* {
  overscroll-behavior: contain;
}

:root {
  --tblr-font-sans-serif: "Inter", system-ui;
}

html {
  -moz-text-size-adjust: none;
  -webkit-text-size-adjust: none;
  text-size-adjust: none;
}

body {
  font-feature-settings: "cv03", "cv04", "cv11";
}

[data-bs-theme="light"] {
  color-scheme: dark;
}

[data-bs-theme="dark"] {
  color-scheme: dark;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  text-wrap: balance;
}

p,
figcaption {
  text-wrap: pretty;
}
```

/resources/views/components/layout.blade.php

```php
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>{{ config('app.name') }}</title>

  <link rel="icon" href="{{ asset('favicon.ico') }}" type="image/x-icon">

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">

  @livewireStyles
  @vite(['resources/scss/index.scss', 'resources/js/index.js'])
</head>

<body>
  {{ $slot }}

  @livewireScriptConfig
</body>

</html>
```

/app/Providers/AppServiceProvider.php

```php
<?php

namespace App\Providers;

use Carbon\CarbonImmutable;
use Illuminate\Support\Facades\DB;
use Illuminate\Pagination\Paginator;
use Illuminate\Support\Facades\Date;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Support\ServiceProvider;
use Illuminate\Validation\Rules\Password;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     */
    public function register(): void
    {
        //
    }

    /**
     * Bootstrap any application services.
     */
    public function boot(): void
    {
        DB::prohibitDestructiveCommands($this->app->isProduction());

        Model::shouldBeStrict(!$this->app->isProduction());
        Model::unguard();

        Password::defaults(fn() => $this->app->isProduction() ? Password::min(8)->max(20)->uncompromised() : null);

        Date::use(CarbonImmutable::class);

        Paginator::useBootstrapFive();
    }
}
```
