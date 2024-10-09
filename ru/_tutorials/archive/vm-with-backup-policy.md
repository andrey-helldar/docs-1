# Автоматическая привязка политики резервного копирования {{ backup-full-name }} к ВМ


Вы может создать [виртуальную машину](../../compute/concepts/vm.md) {{ compute-full-name }} на базе [поддерживаемого {{ backup-name }} образа](../../backup/concepts/vm-connection.md#os), к которой будет автоматически привязана [политика резервного копирования](../../backup/concepts/policy.md). 

Для этого в [метаданных](../../compute/concepts/vm-metadata.md) ВМ передается скрипт для установки агента резервного копирования и идентификатор нужной политики. Указанная политика автоматически привяжется к ВМ после того, как ВМ и агент создадутся, инициализируются и запустятся.

Создать инфраструктуру для автоматической привязки политики резервного копирования к ВМ можно с помощью следующих инструментов: