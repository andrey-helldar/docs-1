# Обновить сертификат

{{ certificate-manager-name }} не управляет пользовательскими сертификатами. Чтобы обеспечить бесперебойную работу ресурсов с сертификатом, своевременно обновляйте его.

Чтобы получить новую версию пользовательского сертификата:

{% list tabs %}

- Консоль управления

    1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором был создан сертификат.
    1. В списке сервисов выберите **{{ certificate-manager-name }}**.
    1. Выберите в списке сертификат, который необходимо обновить.
    1. В открывшемся окне нажмите кнопку **Обновить сертификат**.
    1. В открывшемся окне в поле **Сертификат** нажмите кнопку **Добавить сертификат**.
        1. Выберите способ добавления: **Файл** или **Текст**.
        1. Нажмите кнопку **Добавить**.
    1. В поле **Цепочка промежуточных сертификатов** нажмите кнопку **Добавить цепочку**.
        1. Выберите способ добавления: **Файл** или **Текст**.
        1. Нажмите кнопку **Добавить**.
    1. В поле **Приватный ключ** нажмите кнопку **Добавить приватный ключ**.
        1. Выберите способ добавления: **Файл** или **Текст**.
        1. Нажмите кнопку **Добавить**.
    1. Нажмите кнопку **Создать**.

- CLI

    {% include [cli-install](../../../_includes/cli-install.md) %}

    {% include [default-catalogue](../../../_includes/default-catalogue.md) %}

    1. Посмотрите описание команды:

        ```bash
        yc certificate-manager certificate update --help
        ```

    1. Посмотрите список сертификатов:

        ```bash
        yc certificate-manager certificate list
        +----------------------+--------+-------------+---------------------+----------+--------+
        |          ID          |  NAME  |   DOMAINS   |      NOT AFTER      |   TYPE   | STATUS |
        +----------------------+--------+-------------+---------------------+----------+--------+
        | fpqmg47avvimp7rvmp30 | mycert | example.com | 2021-09-15 06:48:26 | IMPORTED | ISSUED |
        +----------------------+--------+-------------+---------------------+----------+--------+
        ```

    1. Выполните команду:

        ```bash
        yc certificate-manager certificate update \
          --id fpqmg47avvimp7rvmp30 \
          --chain myupdatedcert.pem \
          --key myupdatedkey.pem
        ```

        Параметры команды:

          - `--id` — идентификатор сертификата, который необходимо обновить.
          - `--chain` — путь к файлу новой цепочки сертификатов.
          - `--key` — путь к файлу нового закрытого ключа сертификата.

        Результат команды:

        ```bash
        id: fpqmg47avvimp7rvmp30
        folder_id: b1g7gvsi89m34qmcm3ke
        created_at: "2020-09-15T06:54:44.916Z"
        name: mycert
        type: IMPORTED
        domains:
        - example.com
        status: ISSUED
        issuer: CN=example.com
        subject: CN=example.com
        serial: 3df79e43df7c3868397b78bfc15a431fa942a135
        updated_at: "2020-09-15T08:23:50.147668Z"
        issued_at: "2020-09-15T08:23:50.147668Z"
        not_after: "2021-09-15T08:12:57Z"
        not_before: "2020-09-15T08:12:57Z"
        ```

- API
  
    Чтобы обновить сертификат, воспользуйтесь методом [update](../../api-ref/Certificate/update.md) для ресурса [Certificate](../../api-ref/Certificate/).

{% endlist %}