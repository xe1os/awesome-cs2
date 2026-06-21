<div align="center">

# Awesome CS2 Web Panel

Modern website and administration panel for Counter-Strike 2 community projects.

[![PHP 8.1+](https://img.shields.io/badge/PHP-8.1%2B-777BB4?logo=php\&logoColor=white)](https://www.php.net/)
[![CS2](https://img.shields.io/badge/Counter--Strike_2-Web_Panel-F2A900)](https://www.counter-strike.net/cs2)
[![Support](https://img.shields.io/badge/Support-Discord-5865F2?logo=discord\&logoColor=white)](https://discord.gg/futJpU9par)

[Discord Support](https://discord.gg/futJpU9par) · [YouTube Preview](https://youtu.be/Zqa4a8m-gS4)

[English](#english) · [Русский](#русский)

</div>

---

## English

### About

**Awesome CS2 Web Panel** is a modern PHP 8 web panel for Counter-Strike 2 projects.

It includes a public website, Steam authentication, player profiles, server integrations, skins/loadout pages, shop features and a full administration panel in one responsive interface.

The project was created with the assistance of AI tools.

### Features

* Steam OpenID authentication;
* administrator access by SteamID64;
* public CS2 skins/loadout module;
* weapons, knives, gloves, agents, stickers, keychains and music kits support;
* home page, player profiles, navigation and footer editor;
* server list with Source Query integration;
* leaderboard and optional LevelRanks integration;
* payments, balance, promo codes and payment history;
* product shop with periods, server selection, delivery settings and backups;
* support tickets, reports and punishment pages;
* multilingual interface;
* administration panel for website, users, databases, logs and modules;
* graceful handling of missing optional modules.

### Free and paid modules

The public repository contains the website core and public modules.

Some advanced integrations, private modules or third-party CS2 modules may be commercial, require a separate license, or be distributed separately.

Paid modules are not included in this repository.

A purchased module license grants only the right to use the module. Redistribution, resale, leaking, publishing or sharing paid modules with third parties is strictly prohibited.

For module availability, licensing and installation help, use the Discord support server.

### Compatibility

Most modules are primarily designed and tested with **Pisex** modules:

* Pisex LevelRank;
* Pisex AdminSystem;
* Pisex VIP.

Some features may work with other similar CS2 modules or custom databases, but full compatibility is not guaranteed.

If you use non-Pisex modules, additional configuration or code changes may be required. The project owner does not guarantee that every feature will work correctly with unsupported third-party modules.

### Requirements

| Component       | Requirement                                        |
| --------------- | -------------------------------------------------- |
| PHP             | PHP 8.1 or newer                                   |
| Recommended PHP | PHP 8.2+                                           |
| Database        | MySQL 5.7+ or MariaDB 10.3+                        |
| Web server      | Apache 2.4+ with mod_rewrite or Nginx with PHP-FPM |
| Steam           | Steam Web API key and administrator SteamID64      |

Required PHP extensions:

```text
pdo
pdo_mysql
curl
mbstring
openssl
json
session
fileinfo
```

Depending on enabled integrations, you may also need databases created by CS2 plugins such as WeaponPaints, LevelRanks, VIP, AdminSystem or other server-side modules.

### Installation

1. Download or clone the repository:

```bash
git clone YOUR_REPOSITORY_URL awesome
cd awesome
```

2. Point your website document root to the project directory.

3. Enable URL rewriting.

For Apache, enable `mod_rewrite` and allow `.htaccess` overrides:

```apache
<Directory /var/www/awesome>
    AllowOverride All
    Require all granted
</Directory>
```

For Nginx, use the security rules from `nginx.conf.example`.

Minimal routing example:

```nginx
root /var/www/awesome;
index index.php;

location / {
    try_files $uri $uri/ /index.php?$query_string;
}

location = /index.php {
    include fastcgi_params;
    fastcgi_param SCRIPT_FILENAME $document_root/index.php;
    fastcgi_pass unix:/run/php/php8.2-fpm.sock;
}

location ~ \.php$ {
    return 404;
}
```

4. Give the web-server user write access:

```bash
sudo chown -R www-data:www-data /var/www/awesome
sudo find /var/www/awesome -type d -exec chmod 750 {} \;
sudo find /var/www/awesome -type f -exec chmod 640 {} \;
```

5. Open the website in your browser.

If `config.json` does not exist, the installation wizard will start automatically.

6. Complete the setup wizard:

* select website language;
* enter your public website URL;
* enter administrator SteamID64;
* create and enter Steam Web API key;
* configure website database;
* connect databases for installed CS2 modules;
* enable only integrations that are actually installed on your server.

7. Use HTTPS in production.

### Configuration and security

The installer creates `config.json`.

This file contains API keys and database credentials. Do not upload it to public repositories.

Keep these files outside Git:

```text
config.json
data/admin/
data/runtime/
runtime-error.log
modules/shop/cache/shop-config.php
modules/shop/cache/backups/
database dumps
local backups
```

When updating an existing installation, do not overwrite server-side runtime files. Otherwise, you may lose current settings, users, logs or shop backups.

### Optional integrations

Enable integrations only when the required database, CS2 plugin and PHP configuration are available.

Supported or optional integration types may include:

* WeaponPaints / skins database;
* LevelRanks;
* VIP;
* AdminSystem;
* punishment systems;
* report systems;
* payment providers;
* Discord webhooks.

### License

This project is distributed under a proprietary license.

All rights are reserved unless otherwise stated by the copyright holder.

Paid modules, private modules, source code, assets and proprietary materials may not be copied, redistributed, resold, leaked, published or shared with third parties without permission.

See the `LICENSE` file for details.

### Support

For installation help, bug reports, paid modules and licensing questions, join the Discord support server:

https://discord.gg/futJpU9par

Video preview:

https://youtu.be/Zqa4a8m-gS4

---

## Русский

### О проекте

**Awesome CS2 Web Panel** — современная веб-панель на PHP 8 для проектов Counter-Strike 2.

Проект объединяет публичный сайт, авторизацию через Steam, профили игроков, серверные интеграции, страницы скинов, магазин и полноценную админ-панель в одном адаптивном интерфейсе.

При создании проекта использовались инструменты искусственного интеллекта.

### Возможности

* авторизация через Steam OpenID;
* доступ администратора по SteamID64;
* публичный модуль CS2 Skins / Loadout;
* поддержка оружия, ножей, перчаток, агентов, наклеек, брелоков и музыкальных наборов;
* главная страница, профили игроков, редактор навигации и футера;
* список серверов с интеграцией Source Query;
* таблица лидеров и опциональная интеграция LevelRanks;
* платежи, баланс, промокоды и история операций;
* магазин товаров со сроками, выбором сервера, настройками выдачи и резервными копиями;
* тикеты поддержки, жалобы и страницы наказаний;
* мультиязычный интерфейс;
* админ-панель для сайта, пользователей, баз данных, логов и модулей;
* безопасная работа без необязательных модулей.

### Бесплатные и платные модули

Публичный репозиторий содержит ядро сайта и публичные модули.

Некоторые расширенные интеграции, приватные модули или сторонние CS2-модули могут быть платными, требовать отдельную лицензию или распространяться отдельно.

Платные модули не входят в этот репозиторий.

Покупка модуля даёт только право пользоваться модулем. Перепродажа, слив, публикация, передача третьим лицам или распространение платных модулей запрещены.

По вопросам доступности модулей, лицензий и установки обращайтесь в Discord-сервер поддержки.

### Совместимость

Большинство модулей в первую очередь рассчитаны и протестированы с модулями **Pisex**:

* Pisex LevelRank;
* Pisex AdminSystem;
* Pisex VIP.

Некоторые функции могут работать с другими похожими CS2-модулями или кастомными базами данных, но полная совместимость не гарантируется.

Если вы используете не Pisex-модули, могут потребоваться дополнительные настройки или изменения в коде. Владелец проекта не гарантирует корректную работу всех функций с неподдерживаемыми сторонними модулями.

### Требования

| Компонент         | Требование                                    |
| ----------------- | --------------------------------------------- |
| PHP               | PHP 8.1 или новее                             |
| Рекомендуемый PHP | PHP 8.2+                                      |
| База данных       | MySQL 5.7+ или MariaDB 10.3+                  |
| Веб-сервер        | Apache 2.4+ с mod_rewrite или Nginx с PHP-FPM |
| Steam             | Steam Web API key и SteamID64 администратора  |

Необходимые расширения PHP:

```text
pdo
pdo_mysql
curl
mbstring
openssl
json
session
fileinfo
```

В зависимости от включённых интеграций также могут понадобиться базы данных от CS2-плагинов, например WeaponPaints, LevelRanks, VIP, AdminSystem или других серверных модулей.

### Установка

1. Скачайте или клонируйте репозиторий:

```bash
git clone YOUR_REPOSITORY_URL awesome
cd awesome
```

2. Укажите папку проекта как корень сайта.

3. Включите перенаправление URL.

Для Apache включите `mod_rewrite` и разрешите `.htaccess`:

```apache
<Directory /var/www/awesome>
    AllowOverride All
    Require all granted
</Directory>
```

Для Nginx используйте правила безопасности из файла `nginx.conf.example`.

Минимальный пример маршрутизации:

```nginx
root /var/www/awesome;
index index.php;

location / {
    try_files $uri $uri/ /index.php?$query_string;
}

location = /index.php {
    include fastcgi_params;
    fastcgi_param SCRIPT_FILENAME $document_root/index.php;
    fastcgi_pass unix:/run/php/php8.2-fpm.sock;
}

location ~ \.php$ {
    return 404;
}
```

4. Выдайте пользователю веб-сервера права на файлы:

```bash
sudo chown -R www-data:www-data /var/www/awesome
sudo find /var/www/awesome -type d -exec chmod 750 {} \;
sudo find /var/www/awesome -type f -exec chmod 640 {} \;
```

5. Откройте сайт в браузере.

Если `config.json` отсутствует, мастер установки запустится автоматически.

6. Пройдите мастер установки:

* выберите язык сайта;
* укажите публичный URL сайта;
* введите SteamID64 администратора;
* создайте и укажите Steam Web API key;
* настройте базу данных сайта;
* подключите базы данных установленных CS2-модулей;
* включайте только те интеграции, которые действительно установлены на сервере.

7. На рабочем сайте используйте HTTPS.

### Конфигурация и безопасность

Мастер установки создаёт файл `config.json`.

В нём находятся API-ключи и данные для подключения к базам данных. Не загружайте этот файл в публичные репозитории.

Не добавляйте в Git:

```text
config.json
data/admin/
data/runtime/
runtime-error.log
modules/shop/cache/shop-config.php
modules/shop/cache/backups/
дампы баз данных
локальные резервные копии
```

При обновлении уже установленного сайта не перезаписывайте runtime-файлы сервера. Иначе можно потерять текущие настройки, пользователей, логи или резервные копии магазина.

### Необязательные интеграции

Включайте интеграции только тогда, когда на сервере есть нужная база данных, CS2-плагин и PHP-настройки.

Поддерживаемые или необязательные типы интеграций:

* WeaponPaints / база скинов;
* LevelRanks;
* VIP;
* AdminSystem;
* системы наказаний;
* системы жалоб;
* платёжные провайдеры;
* Discord webhooks.

### Лицензия

Проект распространяется под закрытой проприетарной лицензией.

Все права защищены, если иное не указано правообладателем.

Платные модули, приватные модули, исходный код, ассеты и другие материалы проекта нельзя копировать, перепродавать, сливать, публиковать или передавать третьим лицам без разрешения.

Подробности смотрите в файле `LICENSE`.

### Поддержка

Помощь с установкой, сообщения об ошибках, платные модули и вопросы по лицензии доступны в Discord-сервере поддержки:

https://discord.gg/futJpU9par

Видео с демонстрацией проекта:

https://youtu.be/Zqa4a8m-gS4
