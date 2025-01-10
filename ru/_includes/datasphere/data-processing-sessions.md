В кластере {{ dataproc-name }} ваш код выполняется в [сессиях](https://livy.incubator.apache.org/docs/latest/rest-api.html#session). Сессия хранит промежуточное состояние до тех пор, пока вы не удалите ее или кластер. У каждого кластера есть сессия по умолчанию. Ее идентификатор равен идентификатору проекта.

Для управления сессиями используйте следующие команды:
* `%create_livy_session --cluster <имя_кластера> --id <идентификатор_сессии>` — создание сессии;
* `%delete_livy_session --cluster <имя_кластера> --id <идентификатор_сессии>` — удаление сессии.

Например, следующая команда создаст в кластере `my-new-cluster` сессию `ses1`, которая позволит каждому процессу использовать максимум 4 ядра CPU в кластере и 4 ГБ RAM (подробнее см. в [документации Spark](https://spark.apache.org/docs/latest/configuration.html)):

```python
%create_livy_session --cluster my-new-cluster --id ses1 --conf spark.cores.max=4 --conf spark.executor.memory=4g
```

По умолчанию в сессиях включено динамическое выделение ресурсов. Чтобы ограничить ресурсы сессии, используйте параметр `--conf spark.dynamicAllocation.enabled=false`.

### Параметры Livy-сессии {#parameters}

Полный список параметров для команды `%create_livy_session`:

| Параметр                     | Тип      | Описание                                   |
|------------------------------|----------|--------------------------------------------|
| `--cluster`                  | `string` | Идентификатор или имя кластера {{ dataproc-name }} |
| `--id`                       | `string` | Идентификатор сессии, произвольная строка. Если не указан, то формируется автоматически |
| `--conf`                     | `string` | Свойства конфигурации Spark                |
| `--proxyUser`                | `string` | Логин пользователя операционной системы кластера {{ dataproc-name }}, от имени которого будет выполняться задание. По умолчанию `spark` |
| `--jars`                     | `string` | Библиотеки Java для использования в сессии |
| `--files`                    | `string` | Файлы для использования в сессии           |
| `--pyFiles`                  | `string` | Python-файлы для использования в сессии    |
| `--driverMemory`             | `string` | Объем памяти драйвера                      |
| `--driverCores`              | `int`    | Количество ядер для драйвера               |
| `--executorMemory`           | `string` | Объем памяти процесса-исполнителя          |
| `--executorCores`            | `int`    | Количество ядер для процесса-процесса      |
| `--numExecutors`             | `int`    | Количество процессов-исполнителей          |
| `--archives`                 | `string` | Архивы для использования в сессии          |
| `--queue`                    | `string` | Название очереди YARN                      |
| `--variables`                | `string` | Переменные для использования в сессии      |
| `--return_variables`         | `string` | Переменные, которые передадутся из сессии  |
| `--heartbeatTimeoutInSecond` | `int`    | Время бездействия до завершения сеанса     |
| `--ttl`                      | `string` | Время ожидания неактивного сеанса          |

Подробнее о параметрах livy-сессии см. в [официальной документации](https://livy.incubator.apache.org/docs/latest/rest-api.html).