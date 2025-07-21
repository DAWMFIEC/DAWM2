..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

=============================================
Guía 23: Django - Server Side Rendering (SSR)
=============================================

.. topic:: Objetivo específico
    :class: objetivo

    Explorar la integración del API REST con aplicaciones que utilizan renderizado del lado del servidor (SSR), evaluando su impacto en el rendimiento, la indexación SEO y la interacción inicial del usuario, con el fin de asegurar una experiencia web optimizada desde el servidor.

Actividades previas
=====================

Ambiente de desarrollo
----------------------

1. Cree un repositorio en GitHub con el nombre *django_ssr_visualizer*.

   a) Agregue un archivo README.md con el título de su backend y una breve descripción del objetivo de su proyecto.
   b) Agregue un archivo *.gitignore* con la plantilla de *Python*.
   
2. Acceda a su proyecto *django_ssr_visualizer* en Codespaces o en su máquina local.
3. Cree y utilice la(s) rama(s) de desarrollo.
4. Cree y habilite el :term:`ambiente virtual de desarrollo`, con:

   .. code-block:: bash

       python -m venv env
       source env/bin/activate

Actividades en clases
=====================

Proyecto: Server Side Rendering (SSR)
-------------------------------------

1. Instale `Django` en su ambiente de desarrollo.
2. Cree un proyecto Django llamado *backend_dashboard_server* en la ubicación actual.
3. Cree una la aplicación **dashboard** en su proyecto.

   a) Registre la aplicación en el archivo de configuración ``backend_data_server/settings.py`` del proyecto:
   b) Registre la ruta \"\" con las subrutas de la aplicación **dashboard**

4. Modifique el archivo ``dashboard/views.py`` con su cliente de IAG generativa, de acuerdo con:

   a) Importe los módulos **APIView**, **Response** y **status** de DRF,
   b) Cree la vista **index** vista basada en funciones.

5. Cree el archivo ``dashboard/urls.py`` con la ruta \"\" a la vista **index**.
6. Levante el servidor de desarrollo de Django.
7. Revise los cambios en el navegador con la URL raíz, seguida por la ruta `/dashboard/`

Gestión de dependencias
-----------------------

1. Genere el archivo `requirements.txt` con la lista de paquetes utilizados, con:

   .. code-block:: bash

       pip freeze > requirements.txt

2. Desactive el ambiente virtual de desarrollo, con:

   .. code-block:: bash

       deactivate

Versionamiento
--------------

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *django_ssr_visualizer*.
2. Genere la(s) solicitud(es) de cambios (pull request) para la rama principal y apruebe los cambios.

Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Cómo?

    * ¿Cómo?

    * ¿Cómo?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">⚛️ useEffect cheatsheet ↓<br><br>❌ Thinking of useEffect as a lifecycle method.<br><br>✅ Thinking of useEffect as a mechanism to sync data (state/props) with systems that aren’t controlled by React. <a href="https://t.co/v8BK5CLsSn">pic.twitter.com/v8BK5CLsSn</a></p>&mdash; George Moller (@_georgemoller) <a href="https://twitter.com/_georgemoller/status/1714250976947794418?ref_src=twsrc%5Etfw">October 17, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>