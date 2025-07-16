..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

==============================================
Guía 22: Django - Autenticación y autorización
==============================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar la gestión efectos secundarios y la actualización dinámica de la interfaz según los cambios de ubicación o preferencias del usuario en el dashboard. 

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

Aplicación: Main
----------------

1. Cree una :term:`aplicación Django` llamada *main*:

   .. code-block:: bash

       python manage.py startapp main

2. Registre la aplicación *main* en el proyecto *backend*:

   a) Modifique el archivo ``backend/settings.py`` del proyecto:

   .. code-block:: python
      :emphasize-lines: 3

      INSTALLED_APPS = [
        ...
        'main',
      ]

   b) En el archivo ``backend/urls.py``, importe el módulo **include** y asocie la ruta raíz (\'\') con las rutas de la aplicación **main**:

   .. code-block:: python
      :emphasize-lines: 2, 6

      from django.contrib import admin
      from django.urls import path, include

      urlpatterns = [
            path('admin/', admin.site.urls),
            path('', include('main.urls')),
      ]

3. Cree un archivo ``main/urls.py`` con las rutas de la aplicación:

   .. code-block:: python
      :emphasize-lines: 1-6

      from django.urls import path
      from . import views

      urlpatterns = [
            path('', views.index, name='index'),
      ]

4. Cree una vista en ``main/views.py`` que retorne un mensaje de bienvenida:

   .. code-block:: python
      :emphasize-lines: 4-7

      from django.shortcuts import render

      # Create your views here.
      from django.http import HttpResponse

      def index(request):
          return HttpResponse("¡Bienvenido a la aplicación Django!")

5. Levante el servidor de desarrollo de Django:

   .. code-block:: bash

       python manage.py runserver

6. Revise los cambios en el navegador en la URL `http://127.0.0.1:8000/`
7. Utilice su cliente de IAG generativa para explicar la estructura de archivos de una aplicación (main) en Django.




Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Cómo te ayudó la inteligencia artificial generativa a comprender la estructura jerárquica de un proyecto Django y el rol que cumplen las aplicaciones, vistas y plantillas en la separación de responsabilidades?

    * ¿Cómo estructuraste los archivos estáticos y plantillas en tu proyecto para lograr una arquitectura clara, eficiente y reutilizable, y qué papel jugó la IA en ese proceso de diseño?

    * ¿Cómo aseguras que el uso de IA generativa no reemplace tu comprensión del marco de trabajo Django, sino que complemente tu aprendizaje como desarrollador backend responsable?


Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">⚛️ useEffect cheatsheet ↓<br><br>❌ Thinking of useEffect as a lifecycle method.<br><br>✅ Thinking of useEffect as a mechanism to sync data (state/props) with systems that aren’t controlled by React. <a href="https://t.co/v8BK5CLsSn">pic.twitter.com/v8BK5CLsSn</a></p>&mdash; George Moller (@_georgemoller) <a href="https://twitter.com/_georgemoller/status/1714250976947794418?ref_src=twsrc%5Etfw">October 17, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>