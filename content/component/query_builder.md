---
title: Query Builder
---

Построитель запросов был спроектирован под похожий синтаксис работы Django ORM из-за удобства и лаконичности кода.

---

## Недостатки

Билдер не учитывает тип колонки в базе данных, поэтому если у вас
колонка описана как `DATE`, то при запросе вида:

```php
$db->filter(['date__gte' => new DateTime])
```

вы получите следующий SQL

```sql
date >= '2018-02-04 08:26:06'
```
