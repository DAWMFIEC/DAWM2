..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

=============================================
Guía 24: Django - Server Side Rendering (SSR)
=============================================

.. topic:: Objetivo específico
    :class: objetivo

    Explorar la integración del API REST con aplicaciones que utilizan renderizado del lado del servidor (SSR), evaluando su impacto en el rendimiento, la indexación SEO y la interacción inicial del usuario, con el fin de asegurar una experiencia web optimizada desde el servidor. 

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

Plantillas
----------

1. En la raíz del repositorio, cree la jerarquía de carpetas ``templates/main`` 
2. Descargue el archivo :download:`base.html <./files/base.html>` con la plantilla base de la aplicación y colóquelo en la carpeta ``templates/main``.
   
   .. note:: 

      La plantilla original se encuentra en el repositorio de GitHub `Windmill Dashboard <https://github.com/estevanmaito/windmill-dashboard>`_, con la vista previa en `Windmill Dashboard <https://windmill-dashboard.vercel.app/>`_.

3. Modifique el archivo ``backend/settings.py`` 

   a) Importe el módulo **os**
   b) Agregue la ruta a las plantillas en el arreglo **TEMPLATES**, en la entrada **DIRS**.

   .. code-block:: python
      :emphasize-lines: 2, 9

      from pathlib import Path
      import os

      ... 

      TEMPLATES = [
          {
              ...
              "DIRS": [os.path.join(BASE_DIR, 'templates')],
              ...
          },
      ]

4. Edite el archivo ``main/views.py``:

   a) Agregue la renderización de la plantilla ``main/base.html`` en la vista `index`:

   .. code-block:: python
      :emphasize-lines: 4-5

      from django.shortcuts import render

      def index(request):
          # return HttpResponse("¡Bienvenido a la aplicación Django!")
          return render(request, 'main/base.html')

5. Revise los cambios en el navegador en la URL `http://127.0.0.1:8000/`

Archivos estáticos
------------------

1. En la raíz del repositorio, cree la carpeta ``static`` 
2. Descargue y descomprima el contenido del archivo :download:`static.zip <./files/static.zip>` en la carpeta ``static``.
3. Edite el archivo ``backend/settings.py``, 

   a) Agregue el arreglo **STATICFILES_DIRS** con la ruta a la carpeta de archivos estáticos:

   .. code-block:: python
      :emphasize-lines: 3-5

      STATIC_URL = "static/"

      STATICFILES_DIRS = [
          os.path.join(BASE_DIR, STATIC_URL),
      ]

4. Edite el archivo ``templates/main/base.html``:

   a) Agregue la etiqueta **{% load static %}** al inicio del archivo.
   b) Reemplace las rutas de los archivos estáticos por las etiquetas **{% static '...' %}**.

   .. code-block:: html
      :emphasize-lines: 1, 10, 15, 20-21

      {% load static %}

      <!DOCTYPE html>
      <html lang="en">
      <head>

         ...
         
         <!-- Local stylesheets -->
         <link rel="stylesheet" href="{% static 'css/tailwind.output.css' %}">
         
         ...
         
         <!-- Local script files -->
         <script src="{% static 'js/init-alpine.js' %}"></script>

         ...
         
         <!-- Local script files -->
         <script src="{% static 'js/charts-lines.js' %}" defer></script>
         <script src="{% static 'js/charts-pie.js' %}" defer></script>

      </head>
      <body>
          ...
      </body>
      </html>

5. Revise los cambios en el navegador en la URL `http://127.0.0.1:8000/`
6. Utilice su cliente de IAG generativa para explicar la estructura de archivos estáticos en un proyecto Django y la utilidad de la etiqueta **{% load static %}** .

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