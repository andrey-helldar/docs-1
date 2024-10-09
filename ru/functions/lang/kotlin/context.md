---
title: Контекст вызова функции на Kotlin в {{ sf-full-name }}
---

# Контекст вызова функции на Kotlin

_Контекст вызова_ — это объект, который опционально принимается [обработчиком запросов](handler.md), если используется [интерфейс YcFunction](model/yc-function.md) в качестве модели программирования. Контекст вызова представляет собой объект типа `yandex.cloud.sdk.functions.Context` и предоставляет методы для получения информации о свойствах версии функции:

* `getFunctionId()` — возвращает строковый идентификатор функции;
* `getFunctionVersionId()` — возвращает строковый идентификатор версии функции;
* `getMemoryLimitInMB()` — возвращает объем памяти, указанный при создании версии, МБ;
* `getRequestId()` — возвращает идентификатор обрабатываемого запроса;
* `getTokenJson()` — возвращает параметры для аутентификации в API сервисов {{ yandex-cloud }}.

Чтобы получить информацию из контекста вызова, используйте одну из функций выше в методе-обработчике.