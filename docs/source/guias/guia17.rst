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

   .. code-block:: javascript
      :emphasize-lines: 2, 7-12

      ...
      import { VitePWA } from 'vite-plugin-pwa'

      export default defineConfig({
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

4. Verifique en la carpeta  ``dist`` que se han generado los archivos necesarios para la PWA, como ``manifest.webmanifest`` y ``sw.js``.
5. Utilice su cliente de IAG para explicar el concepto y el uso de :term:`PWA`; además, cómo el plugin `PWA Vite Plugin` ayuda a implementarlo.

Manifesto de la PWA
-------------------

1. Modifique la definición del :term:`manifest` de la PWA en el archivo ``vite.config.ts``, con:

   .. code-block:: javascript
      :emphasize-lines: 8-28

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