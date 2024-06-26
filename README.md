## API сервис для Укорачивания Ссылок

Это простой REST API сервис для укорачивания URL-адресов. Он предоставляет конечные точки для укорачивания, доступа и удаления укороченных URL-адресов. Для доступа к сервису необходима базовая аутентификация, с тестовым логином `alex` и паролем `1234`. Авторизация не требуется для доступа к укороченным URL-адресам.

### Использование

1. **Укоротить URL**: Чтобы укоротить URL, отправьте POST запрос на `/url`. Включите параметр `url` в теле запроса (обязательно) и опционально включите `alias`. Вы получите укороченный URL в ответе.

2. **Доступ к Укороченному URL**: Чтобы получить доступ к укороченному URL, отправьте GET запрос на `/{ваш_alias}`. Сервис автоматически перенаправит вас на исходный ресурс.

3. **Удалить Укороченный URL**: Чтобы удалить укороченный URL, отправьте DELETE запрос на `/url/{ваш_alias}`.

### Пример

#### Укоротить URL
```bash
curl -X POST -u alex:1234 -H "Content-Type: application/json" -d '{"url":"https://example.com", "alias":"example"}' http://31.129.57.182:8082/url
```

Ответ:
```json
{
    "status": "OK",
    "alias": "http://31.129.57.182:8082/{alias}"
}
```

#### Доступ к Укороченному URL
```bash
curl -X GET http://31.129.57.182:8082/{alias}
```

Это автоматически перенаправит вас на `https://example.com`.

#### Удалить Укороченный URL
```bash
curl -X DELETE -u alex:1234 http://31.129.57.182:8082/url/{alias}
```

### Примечание
Для доступа к укороченным URL-адресам авторизация не требуется.
