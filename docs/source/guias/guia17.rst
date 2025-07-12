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

Producción en local
-------------------

1. Asegúrese de que su proyecto esté funcionando correctamente en el entorno de desarrollo.
2. Compile su proyecto para producción, con: 

   .. code-block:: bash

      npm run build

3. Verifique que la compilación se haya realizado correctamente, revisando la carpeta ``dist`` que se genera en el directorio raíz del proyecto.
4. Levante un servidor local para servir los archivos de producción, con:

   .. code-block:: bash

      npm run preview

5. Abra su navegador y acceda a la URL de su aplicación

PWA Vite Plugin
---------------

1. Instale el plugin de `PWA Vite Plugin <https://vite-pwa-org.netlify.app/>`_, con:

   .. code-block:: bash

      npm install -D vite-plugin-pwa

2. Configure el plugin en el archivo ``vite.config.ts``, con:

   a) Asegúrese que la base de la URL sea **base: "/dashboard/"**.
   b) Importe y configure el plugin.

   .. code-block:: javascript
      :emphasize-lines: 2, 4, 7-12

      ...
      import { VitePWA } from 'vite-plugin-pwa'

      export default defineConfig({
         base: "/dashboard/",
         plugins: [
            react(),
            VitePWA({
               registerType: 'autoUpdate',
               devOptions: {
                  enabled: true
               }
            })
         ]
      }

3. Compile para producción y levante el servidor local, con:

   .. code-block:: bash

      npm run build
      npm run preview

4. Verifique que la carpeta  ``dist`` contenga los archivos necesarios para la PWA, como ``manifest.webmanifest`` y ``sw.js``.
5. Use el inspector de su navegador para verificar que el service worker se ha registrado correctamente y que el manifest está disponible.
6. Utilice su cliente de IAG para explicar el concepto y los archivos necesarios para desarrollar una :term:`PWA`; además, explique el beneficio en utilizar el `PWA Vite Plugin`.


Manifesto de la PWA
-------------------

1. Utilice el servicio `Image Generator <https://www.pwabuilder.com/imageGenerator>`_ para generar los íconos de la PWA.
2. Descargue los íconos generados y guárdelos en la carpeta ``public`` de su proyecto. Asegúrese de que los íconos tengan los siguientes tamaños: 192x192 y 512x512 píxeles.
3. Modifique la definición del :term:`manifest` de la PWA en el archivo ``vite.config.ts``, con:

   .. code-block:: javascript
      :emphasize-lines: 8-27

      ...

      VitePWA({
         registerType: 'autoUpdate',
         devOptions: {
            enabled: true
         },
         includeAssets: ['favicon.ico', 'apple-touch-icon.png'],
         manifest: {
            id: '/dashboard/',
            name: 'Dashboard del Clima - Proyecto 04',
            short_name: 'Dashboard del Clima',
            description: 'Proyecto 04 - dashboard del clima desarrollado con React y MUI',
            theme_color: '#ffffff',
            icons: [
               {
                  src: 'pwa-192x192.png',
                  sizes: '192x192',
                  type: 'image/png'
               },
               {
                  src: 'pwa-512x512.png',
                  sizes: '512x512',
                  type: 'image/png'
               }
            ]
         }
      })

4. Compile para producción y levante el servidor local, con:

   .. code-block:: bash

      npm run build
      npm run preview

5. Inspeccione el sitio web en el navegador para verificar que se ha registrado el service worker y que el manifest está correctamente configurado.

Service workers
---------------


Almacenamiento en caché
-----------------------


Versionamiento
--------------

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *dashboard*.
2. Genere la(s) solicitud(es) de cambios (pull request) para la rama principal y apruebe los cambios.

Despliegue
----------

1. Desde la línea de comandos, ejecute el comando de transpilación y despliegue del sitio web, con:

   .. code-block:: bash

      npm run deploy

   a) De ser necesario, elimine, corrija o comente las secciones de código identificadas por el transpilador.
   b) Vuelva a ejecutar el comando de transpilación y despliegue del sitio web.

2. Compruebe el resultado en el navegador, con la URL: `https://<username>.github.io/dashboard`

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