---
title: Как создать трансляцию в {{ video-full-name }}
description: Следуя данной инструкции, вы сможете создать трансляцию {{ video-full-name }}.
---

# Создать трансляцию

{% list tabs group=instructions %}

- Интерфейс {{ video-name }} {#console}

  1. Откройте [главную страницу]({{ link-video-main }}) {{ video-name }}.
  1. Выберите канал.
  1. На вкладке ![image](../../../_assets/console-icons/antenna-signal.svg) **{{ ui-key.yacloud_video.streams.title_streams }}** нажмите кнопку **{{ ui-key.yacloud_video.streams.action_create-stream }}**.
  1. Введите имя и описание трансляции.
  1. Выберите или [создайте](../lines/create.md) новую линию.
  1. В поле **{{ ui-key.yacloud_video.thumbnails.label_thumbnail }}** нажмите кнопку ![image](../../../_assets/console-icons/cloud-arrow-up-in.svg) **Выберите файл** и выберите изображение для обложки.

      {% include [image-characteristic](../../../_includes/video/image-characteristic.md) %}

  1. Выберите нужный тип потока [трансляции](../../concepts/streams.md#streams):
  
      * `{{ ui-key.yacloud_video.streams.label_type-on-demand }}` — чтобы начать и завершить трансляцию вручную из интерфейса {{ video-name }}.
      * `{{ ui-key.yacloud_video.streams.label_type-schedule }}` — чтобы начать и завершить трансляцию автоматически в указанное время.

  1. Если вы выбрали тип потока `{{ ui-key.yacloud_video.streams.label_type-schedule }}`, укажите дату и время начала и окончания трансляции.
  1. (опционально) Чтобы поместить на сайт часть трансляции, выделите ее в отдельный эпизод:

      1. Нажмите кнопку ![image](../../../_assets/console-icons/plus.svg) **{{ ui-key.yacloud_video.streams.action_add-stream-episode }}**.
      1. Введите имя и описание эпизода.
      1. Укажите дату и время начала и окончания эпизода.
      1. В поле **{{ ui-key.yacloud_video.thumbnails.label_thumbnail }}** нажмите кнопку ![image](../../../_assets/console-icons/cloud-arrow-up-in.svg) **Выберите файл** и выберите изображение для обложки.

          {% include [image-characteristic](../../../_includes/video/image-characteristic.md) %}

      Вы можете добавить любое количество эпизодов. Чтобы удалить лишний эпизод, нажмите значок ![image](../../../_assets/console-icons/trash-bin.svg).

  1. Нажмите кнопку **{{ ui-key.yacloud_video.common.action_create }}**.

- API {#api}

  Воспользуйтесь методом REST API [create](../../api-ref/Stream/create.md) для ресурса [Stream](../../api-ref/Stream/index.md) или вызовом gRPC API [StreamService/Create](../../api-ref/grpc/stream_service.md#Create).

{% endlist %}