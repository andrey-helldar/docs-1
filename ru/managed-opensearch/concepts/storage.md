---
title: Типы дисков в {{ mos-full-name }}
description: Из статьи вы узнаете, какие типы дисков есть в {{ mos-name }} и познакомитесь с особенностями выбора типа хранилища при создании кластера.
---

# Типы дисков в {{ mos-name }}




{{ mos-name }} позволяет использовать сетевые и локальные диски для организации хранилища кластеров баз данных. Сетевые диски реализованы на базе сетевых блоков — виртуальных дисков в инфраструктуре {{ yandex-cloud }}. Локальные диски физически размещаются в серверах кластера.



{% include [storage-type](../../_includes/mdb/mos/storage-type.md) %}



## Выбор типа хранилища при создании кластера {#storage-type-selection}

Количество хостов с ролью `DATA`, которые можно создать вместе с кластером {{ OS }}, зависит от выбранного типа хранилища:

* При использовании хранилища на локальных SSD-дисках (`local-ssd`) или на нереплицируемых SSD-дисках (`network-ssd-nonreplicated`) вы можете создать кластер из трех или более хостов. Такой кластер будет отказоустойчивым.

   Хранилище на локальных SSD-дисках влияет на тарификацию кластера: он тарифицируется, даже если остановлен. Подробнее в [правилах тарификации](../pricing.md).

* При использовании хранилища на сетевых HDD-дисках (`network-hdd`) или сетевых SSD-дисках (`network-ssd`) вы можете добавить любое количество хостов в пределах текущей квоты.

Подробнее об ограничениях на количество хостов в кластере см. в разделе [Квоты и лимиты](./limits.md).

Для повышения отказоустойчивости вы можете настроить [репликацию индексов](scalability-and-resilience.md#replication) (только для многохостовых конфигураций кластера).


