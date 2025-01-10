Роль `dataproc.agent` позволяет [сервисному аккаунту](../../iam/concepts/users/service-accounts.md), привязанному к кластеру Yandex Data Processing, сообщать сервису о состоянии хостов кластера. Роль назначается сервисному аккаунту, привязанному к кластеру Yandex Data Processing.

Сервисные аккаунты с этой ролью могут:
* сообщать сервису Yandex Data Processing о состоянии хостов [кластера](../../data-proc/concepts/index.md#resources);
* получать информацию о [заданиях](../../data-proc/concepts/jobs.md) и статусах их выполнения;
* получать информацию о [лог-группах](../../logging/concepts/log-group.md) и добавлять в них записи.

Сейчас эту роль можно назначить только на каталог или облако.