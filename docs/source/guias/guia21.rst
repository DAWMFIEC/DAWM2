..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

======================================================
Guía 21: Django - REST API + Firebase Admin Python SDK
======================================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar Django Rest Framework (DRF) para construir y estructurar los endpoints de una API REST que permitan realizar operaciones CRUD sobre datos en Firebase Realtime Database. 

Actividades previas
=====================

Ambiente de desarrollo
----------------------

1. Acceda a su proyecto *backend* en Codespaces o en su máquina local.
2. Cree y utilice la(s) rama(s) de desarrollo.
3. Cree y habilite el ambiente virtual de desarrollo, con:

   .. code-block:: bash

       python -m venv env
       source env/bin/activate

4. Instale las librerías de requirements.txt, con:

   .. code-block:: bash

       pip install -r requirements.txt

Actividades en clases
=====================

Paquete: Firebase Admin Python SDK
----------------------------------

1. Instale la librería :term:`Firebase Admin Python SDK` en su ambiente de desarrollo:

   .. code-block:: bash
    
       pip install firebase-admin

2. Registre el Firebase Admin Python SDK en el archivo ``backend/settings.py`` del proyecto:

   .. code-block:: python
      :emphasize-lines: 3

      INSTALLED_APPS = [
        ...
        "firebase_admin",
      ]

3. Utilice su cliente de IAG generativa para explicar qué es `Firebase Admin Python SDK <https://firebase.google.com/docs/admin/setup>`_ y cuáles son sus principales características.

Aplicación: Landing API
-----------------------

1. Cree una la aplicación **landing_api** en su proyecto.
2. Registre la ruta \"landing/api/\" con las subrutas de la aplicación **landing_api**
3. Cree la vista basada en clases **LandingAPI** en ``landing_api/views.py``
4. Cree el archivo ``landing_api/urls.py`` con la ruta raíz a la vista **RestAPI**.
5. Levante el servidor de desarrollo de Django.
6. Revise los cambios en el navegador en la URL en la ruta `/landing/api/`

Firebase Private key
--------------------

1. En `Firebase Console <https://console.firebase.google.com/>`_

   a) Acceda el proyecto **landing**
   b) Acceda a la `Configuración de proyecto` > `Cuentas de servicio` > `SDK de Firebase Admin`.
   c) Genere una clave privada. 

SDK Firebase Admin
------------------


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

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *backend*.
2. Genere la(s) solicitud(es) de cambios (pull request) para la rama principal y apruebe los cambios.

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

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">When you&#39;re building an app, you&#39;ll often need a way to send and get back data between your app &amp; a server.<br><br>And using a REST API is a great way to do this.<br><br>In this tutorial, <a href="https://twitter.com/_udemezue?ref_src=twsrc%5Etfw">@_udemezue</a> teaches you how to build a REST API in Django using the Django Rest Framework.… <a href="https://t.co/aPeAxcpTAM">pic.twitter.com/aPeAxcpTAM</a></p>&mdash; freeCodeCamp.org (@freeCodeCamp) <a href="https://twitter.com/freeCodeCamp/status/1945454273652785446?ref_src=twsrc%5Etfw">July 16, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>