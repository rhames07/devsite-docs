---
sites_supported:
  - mla
  - mlb
  - mlm
---

## ¿Qué es la API de Integraciones?

Es una interfaz que permite conectar tus **puntos de venta** (PDV) al ecosistema Point para recibir pagos en las terminales que tengas configuradas y garantizar una experiencia de cobro unificada.

![Diagrama 1](/images/mobile/pdv-flow.png)

----[mla]----
> INFO
>
> Dispositivos soportados con esta integración:
>
> - [Point Smart (POS)](https://www.mercadopago.com.ar/point-smart?ref=devsite)
> - [Point Plus (POS)](https://www.mercadopago.com.ar/point-plus?ref=devsite)
------------

----[mlb]----
> INFO
>
> Dispositivos soportados con esta integración:
>
> - [Point Pro2 (POS)](https://www.mercadopago.com.br/point-pro-2?ref=devsite)
> - [Point Mini Chip (POS)](https://www.mercadopago.com.br/point-mini-chip?ref=devsite)
------------

**Características:**

- **Es segura.** Todas las peticiones se hacen a través de HTTPS.
- **Fácil de usar.** Únicamente necesitas tus credenciales de acceso para utilizarla.
- Administra tus ordenes de pago desde tu PDV.
- Disminuye la posibilidad de errores al momento de cobrar.

## Guía de integración paso a paso
Puedes dar click sobre cada paso para facilitar tu navegación

<center>
<img src="/mobile/integration-steps.png" usemap="#image-map"/>
</center>
<map name="image-map">
    <area target="_blank" alt="requisitos_previos" title="requisitos_previos" href="requirements" coords="22,71,799,130" shape="">
    <area target="_blank" alt="obten_tus_credenciales" title="obten_tus_credenciales" href="requirements#bookmark_1._obtén_las_credenciales_de_identificación_para_tu_integración" coords="52,153,210,200" shape="">
    <area target="_blank" alt="registra_tu_aplicación" title="registra_tu_aplicación" href="requirements#bookmark_2._registra_tu_aplicación" coords="236,153,393,198" shape="0">
    <area target="_blank" alt="configura_tu_webhook" title="configura_tu_webhook" href="requirements#bookmark_3._prepara_y_configura_tu_webhook_(opcional)" coords="424,154,580,199" shape="0">
    <area target="_blank" alt="asocia_tu_device" title="asocia_tu_device" href="requirements#bookmark_4._asocia_tu_dispositivo_point_a_tu_cuenta_de_mercado_pago" coords="611,155,767,199" shape="0">
    <area target="_blank" alt="procesa_tus_pagos" title="procesa_tus_pagos" href="create-payment-intent" coords="21,221,800,281" shape="0">
    <area target="_blank" alt="crea_intencion_de_pago" title="crea_intencion_de_pago" href="create-payment-intent#bookmark_1._crea_una_intención_de_pago" coords="72,304,260,348" shape="0">
    <area target="_blank" alt="procesa_tu_pago" title="procesa_tu_pago" href="create-payment-intent#bookmark_2._procesa_tu_intención_de_pago" coords="316,302,505,350" shape="0">
    <area target="_blank" alt="recibe_tu_notificación" title="recibe_tu_notificación" href="create-payment-intent#bookmark_3._recibe_tu_notificación" coords="562,305,748,350" shape="0">
</map>

----[mla]----
> NOTE
>
> API Reference
>
> Está a tu disposición la documentación de la API de Integraciones, puedes descargarla y ejecutarla en Postman.
> Recuerda tener tu **ACCESS_TOKEN** a la mano. [API Reference](https://documenter.getpostman.com/view/16045907/TzzEou9q)
------
------------
----[mlb]----
> NOTE
>
> API Reference
>
> Está a tu disposición la documentación de la API de Integraciones, puedes descargarla y ejecutarla en Postman.
> Recuerda tener tu **ACCESS_TOKEN** a la mano. [API Reference](https://documenter.getpostman.com/view/16045907/TzzEoaMm)
------
------------

### Próximos pasos

> LEFT_BUTTON_REQUIRED_ES
> 
> Glosario
>
> Términos y definiciones que son importantes que conozcas. 
>
> [Glosario](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/es/guides/in-person-payments/mp-point/integration-api/glossary)

> RIGHT_BUTTON_RECOMMENDED_ES
>
> Inicia tu integración
>
> Revisa qué consideraciones debes tener en cuenta antes de empezar a usar la API.
>
> [Requisitos previos](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/es/guides/in-person-payments/mp-point/integration-api/requirements)
