`sharding` — настройки для [шардирования](../../../../../managed-clickhouse/concepts/sharding.md) данных. Вы можете указать только один из вариантов шардирования:

* `columnValueHash.columnName` — имя колонки в таблицах, по которой следует шардировать данные. Равномерное распределение по шардам будет определяться хешем значения этой колонки.

* `customMapping` — шардирование по значению колонки:

    * `columnName` — имя колонки в таблицах, по которой следует шардировать данные.

    * `mapping` — сопоставление значений колонки и шардов:

        * `columnValue.stringValue` — значение колонки.
        * `shardName` — имя шарда.

* `transferId` — данные по шардам будут распределяться на основе значения идентификатора трансфера. Параметр не содержит значения.

* `roundRobin` — данные по шардам будут распределяться случайным образом (количество данных на каждом шарде будет примерно одинаковым). Параметр не содержит значения.

Если вариант шардирования не указан, то все данные переносятся в один шард.