..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

==========================================
Guía 17: React - Progressive Web App (PWA)
==========================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar funcionalidades propias de una Progressive Web App (PWA) con el fin de mejorar la accesibilidad, rendimiento y disponibilidad de la aplicación, incluso sin conexión a internet, fomentando así el desarrollo de interfaces modernas y resilientes. 

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

PWA Vite Plugin
---------------

1. Instale el plugin de `PWA Vite Plugin <https://vite-pwa-org.netlify.app/>`_, con:

   .. code-block:: bash

      npm install -D vite-plugin-pwa

2. Configure el plugin en el archivo ``vite.config.js``, agregando:

   .. code-block:: javascript
      :emphasize-lines: 2, 7

      ...
      import { VitePWA } from 'vite-plugin-pwa'

      let config = {}

      export default {
         plugins: [
            react(),
            VitePWA( config )
         ]
      }

3. Utilice su cliente de IAG para explicar el concepto y el uso de :term:`PWA`; además, cómo el plugin `PWA Vite Plugin` ayuda a implementarlo.

Manifiesto de la app web
------------------------

1. Use su cliente de IAG para explicar el concepto y uso del :term:`manifiesto de la app web`en relación con PWA. 
2. Revise la documentación `Manifiesto de la app web <https://web.dev/learn/pwa/web-app-manifest>`_.


Service workers
---------------

Almacenamiento en caché
-----------------------

Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Qué?

    * ¿Qué?

    * ¿Cómo?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">Many people don’t even know that a lot of the popular everyday use apps are actually Progressive Web Apps.<a href="https://twitter.com/hashtag/ProgressiveWebApp?src=hash&amp;ref_src=twsrc%5Etfw">#ProgressiveWebApp</a> <a href="https://twitter.com/hashtag/PWA?src=hash&amp;ref_src=twsrc%5Etfw">#PWA</a> <a href="https://twitter.com/hashtag/AppDevelopment?src=hash&amp;ref_src=twsrc%5Etfw">#AppDevelopment</a> <a href="https://twitter.com/hashtag/WebDevelopment?src=hash&amp;ref_src=twsrc%5Etfw">#WebDevelopment</a> <a href="https://twitter.com/hashtag/WebAppDevelopment?src=hash&amp;ref_src=twsrc%5Etfw">#WebAppDevelopment</a> <a href="https://twitter.com/hashtag/FutureAhead?src=hash&amp;ref_src=twsrc%5Etfw">#FutureAhead</a> <a href="https://t.co/xvFUv59EqW">https://t.co/xvFUv59EqW</a></p>&mdash; Valentin Podkamennyi (@vpodk) <a href="https://twitter.com/vpodk/status/1941847225291915594?ref_src=twsrc%5Etfw">July 6, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>