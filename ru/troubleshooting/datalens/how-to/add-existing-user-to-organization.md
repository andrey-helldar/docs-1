# Добавление существующего пользователя в {{ datalens-short-name }}


## Описание сценария {#case-description}

Необходимо добавить существующего пользователя Яндекс ID (с адресом электронной почты в домене `@yandex.ru`) в {{ datalens-short-name }}.

## Решение {#case-resolution}

Если ваш экземпляр {{ datalens-short-name }} привязан к организации, то нужно зайти на [её страницу]({{ link-org-users }}) и добавить пользователя, а если {{ datalens-short-name }} привязан к облаку, нужно добавить пользователя внутри облака.

Не забудьте выдать пользователю необходимые роли, например, `{{ roles-datalens-instances-user }}` или `{{ roles-datalens-instances-admin }}`.

Подробнее о доступе к {{ datalens-short-name }} пишем [здесь](../../../datalens/security/index.md).

## Если ничего не получилось {#if-issue-still-persists}

Если вышеописанные действия не помогли решить задачу, [создайте запрос в техническую поддержку]({{ link-console-support }})).
При создании запроса укажите следующую информацию:

1. Идентификатор пользователя Яндекс ID, которого вы пытаетесь добавить в {{ datalens-short-name }}.
2. Что происходит при попытке добавить пользователя в {{ datalens-short-name }}.