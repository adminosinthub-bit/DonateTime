# DonateTime

Плейсхолдер для PlaceholderAPI, который показывает префикс игрока из LuckPerms вместе с оставшимся временем его донат-группы — например:

```
[Донат]  (10 дн.)
```

Если у группы нет срока действия (постоянная), время просто не показывается — выводится только префикс.

## Требования

- [LuckPerms](https://luckperms.net/)
- [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/)
- Java 21, Spigot/Paper 1.21+

## Плейсхолдеры

| Плейсхолдер | Описание |
|---|---|
| `%donatetime_prefix_with_time%` | Префикс игрока + оставшееся время самой долгой временной группы |
| `%donatetime_prefix%` | Просто префикс игрока (из LuckPerms) |
| `%donatetime_time%` | Только оставшееся время, без префикса |

Плейсхолдер смотрит на **временные** (`addtemp`) group-ноды игрока в LuckPerms — если их несколько, берётся та, что истекает позже всех. Работает только для игроков **онлайн** (чтобы не делать блокирующих запросов к базе LuckPerms).

## Пример настройки LuckPerms

```
/lp group create donate
/lp group donate meta setprefix "&6[Донат] "
/lp user <ник> parent addtemp donate 10d
```

После этого `%donatetime_prefix_with_time%` для этого игрока выведет `&6[Донат]  &7(10 дн.)`.

## Конфигурация

`plugins/DonateTime/config.yml`:

```yaml
# Цвет, которым всегда отображается остаток времени,
# независимо от цвета самого префикса.
time-color: GRAY
```

Доступные цвета: `BLACK`, `DARK_BLUE`, `DARK_GREEN`, `DARK_AQUA`, `DARK_RED`, `DARK_PURPLE`, `GOLD`, `GRAY`, `DARK_GRAY`, `BLUE`, `GREEN`, `AQUA`, `RED`, `LIGHT_PURPLE`, `YELLOW`, `WHITE`.

## Установка

Скачать `DonateTime.jar` со страницы [Releases](https://github.com/adminosinthub-bit/DonateTime/releases), положить в `plugins/`, перезапустить сервер.

## Автор

Voidix — [поддержать автора](https://www.donationalerts.com/r/dev_voidix)
