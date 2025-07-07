..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

=============================
Guía 16: React - LocalStorage
=============================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar persistencia de datos en el navegador para la mejora de la experiencia de usuario sin necesidad de una base de datos externa.

Actividades previas
=====================

Ambiente de desarrollo
----------------------

1. Acceda a su proyecto *dashboard* en Codespaces o en su máquina local.
2. Cree y utilice la(s) rama(s) de desarrollo.
3. Instale los paquetes y levante el servidor, con:

   .. code-block:: bash

      npm install
      npm run dev

Actividades en clases
=====================

LocalStorage
------------

1. Revise la documentación API de:
    
   a) `localStorage` para almacenar datos en el navegador que se encuentra en `Window: localStorage property <https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage>`_. 
   b) Chrome DevTools para inspeccionar el almacenamiento local en `Chrome DevTools: Ver y editar el almacenamiento local <https://developer.chrome.com/docs/devtools/storage/localstorage>`_.

2. Sin utilizar IAG, diseñe e implemente una estrategia de almacenamiento temporal de la respuesta a un requerimiento asincrónico en la memoria del navegador, considerando: 

    - El `localStorage`, con una clave específica, como almacenamiento de su respuesta.
    - La eficiencia (menos llamadas a la API), la resiliencia (uso de datos en caso de falla) y la vigencia de la información (control temporal de *x* minutos) en su respuesta.

3. Verifique su respuesta en el navegador. 
4. Utilice su cliente de IAG para justificar la eficiencia, la resiliencia y la vigencia de la información de su estrategia.

Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Cómo te ayudó la inteligencia artificial generativa a entender el papel de localStorage en la persistencia de datos del lado del cliente, y qué limitaciones tiene en cuanto a seguridad y capacidad?

    * ¿Qué modificaciones realizaste a la estrategia generada por la IA para adaptarla al flujo de tu dashboard, asegurando una sincronización efectiva entre localStorage y el estado de la aplicación?

    * ¿Cómo garantizas que la estrategia aplicada refleje tanto tu comprensión técnica como tu compromiso con la calidad, confiabilidad y mantenimiento del dashboard a lo largo del tiempo?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">What is JavaScript local Storage and 🧵 how to use local Storage to store persistent data. <a href="https://t.co/A1k3546Eiq">pic.twitter.com/A1k3546Eiq</a></p>&mdash; Garen Crowngaurd (@0xGaren) <a href="https://twitter.com/0xGaren/status/1611689064243298312?ref_src=twsrc%5Etfw">January 7, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>