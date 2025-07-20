..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

======================================================
Guía 21: Django - DRF + Firebase Admin Python SDK
======================================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar Django Rest Framework (DRF) para la administración de los endpoints de una API REST que permitan realizar operaciones CRUD sobre datos en Firebase Realtime Database. 

Actividades previas
=====================

Ambiente de desarrollo
----------------------

1. Acceda a su proyecto *django-api-suite* en Codespaces o en su máquina local.
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

2. Registre el Firebase Admin Python SDK en el archivo ``backend_data_server/settings.py`` del proyecto:

   .. code-block:: python
      :emphasize-lines: 3

      INSTALLED_APPS = [
        ...
        "firebase_admin",
        "rest_framework",
        ...
      ]

3. Utilice su cliente de IAG generativa para explicar qué es `Firebase Admin Python SDK <https://firebase.google.com/docs/admin/setup>`_ y cuáles son sus principales características.

Firebase Admin Python SDK
---------------------------

.. note:: 
   
   Considere la documentación `Agrega el SDK de Firebase Admin a tu servidor <https://firebase.google.com/docs/admin/setup?hl=es-419>`_.

Credenciales
^^^^^^^^^^^^

1. En `Firebase Console <https://console.firebase.google.com/>`_, acceda a su proyecto **landing**.
2. Acceda a `Configuración de proyecto` > `Cuentas de servicio` > `SDK de Firebase Admin` para generar la clave privada. 
3. Acceda al servicio **Realtime Database** y copie la URL de referencia a la base de datos no relacional.

   .. note:: 
      
      La URL de referencia luce como `https://<PROJECT-ID>-default-rtdb.firebaseio.com/`

Secrets
^^^^^^^

4. En la raíz del repositorio, cree la carpeta ``secrets``
5. Agregue el archivo con la clave privada a la carpeta ``secrets`` y renombre el archivo como ``landing-key.json``.
6. Añada al archivo **.gitignore** la carpeta ``secrets``.

   .. code-block:: text
      :emphasize-lines: 4

      ...
      __marimo__/

      secrets/


Configuración en el proyecto
^^^^^^^^^^^^^^^^^^^^^^^^^^

7. Edite el archivo ``backend_data_server/settings.py``, con:

   .. code-block:: python
      :emphasize-lines: 4-5, 11-12, 14-17

      ...
      import os

      import firebase_admin
      from firebase_admin import credentials

      ...

      DEFAULT_AUTO_FIELD = ... 

      # Coloque la ruta relativa al archivo con la clave privada
      FIREBASE_CREDENTIALS_PATH = credentials.Certificate("secrets/landing-key.json")
      
      # Inicialice la conexión con el Realtime Database con la clave privada y la URL de referencia
      firebase_admin.initialize_app(FIREBASE_CREDENTIALS_PATH, {
         'databaseURL': 'https://<PROJECT-ID>-default-rtdb.firebaseio.com/'
      })

8. Utilice su cliente de IAG generativa para explicar cómo se configura el Firebase Admin SDK en un proyecto Django y cuáles son los pasos necesarios para establecer una conexión con Firebase Realtime Database.

Aplicación: Landing API
-----------------------

1. Cree una la aplicación **landing_api** en su proyecto.
2. Registre la aplicación en el archivo de configuración ``backend_data_server/settings.py`` del proyecto:
3. Registre la ruta \"landing/api/\" con las subrutas de la aplicación **landing_api**
4. En ``landing_api/views.py``, cree la vista basada en clases de DRF . 

   .. code-block:: python
      :emphasize-lines: 4-6

      from rest_framework.views import APIView
      from rest_framework.response import Response
      from rest_framework import status

      class LandingAPI(APIView):
         name = "Landing API"

5. Cree el archivo ``landing_api/urls.py`` con la ruta \"index/\" a la vista **LandingAPI**.


   .. code-block:: python
      :emphasize-lines: 1-6

      from django.urls import path
      from .views import LandingAPI

      urlpatterns = [
         path('index/', views.LandingAPI.as_view(), name='landing_api_index'),
      ]

6. Levante el servidor de desarrollo de Django.
7. Revise los cambios en el navegador con la URL raíz, seguida por la ruta `/landing/api/index/`

GET
---

1. Edite el archivo ``landing_api/views.py``, con:
2. Levante el servidor de desarrollo de Django.
3. Revise los cambios en el navegador en la URL en la ruta `/landing/api/`

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

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *django-api-suite*.
2. Genere la(s) solicitud(es) de cambios (pull request) para la rama principal y apruebe los cambios.

Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Cómo te ayudó la inteligencia artificial generativa a comprender la función del Firebase Admin SDK en la administración de servicios como la autenticación, la base de datos y el almacenamiento desde el backend en Python?

    * ¿Cómo garantizaste que las operaciones realizadas desde Firebase Admin SDK, como la lectura o escritura de datos, se ejecutaran de forma segura y eficiente en tu proyecto backend?

    * ¿Cómo equilibraste el uso del código generado por la IA con tu responsabilidad como desarrollador para asegurar que comprendes y controlas el flujo de datos y la configuración del backend?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">When you&#39;re building an app, you&#39;ll often need a way to send and get back data between your app &amp; a server.<br><br>And using a REST API is a great way to do this.<br><br>In this tutorial, <a href="https://twitter.com/_udemezue?ref_src=twsrc%5Etfw">@_udemezue</a> teaches you how to build a REST API in Django using the Django Rest Framework.… <a href="https://t.co/aPeAxcpTAM">pic.twitter.com/aPeAxcpTAM</a></p>&mdash; freeCodeCamp.org (@freeCodeCamp) <a href="https://twitter.com/freeCodeCamp/status/1945454273652785446?ref_src=twsrc%5Etfw">July 16, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>