..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

==============================
Guía 19: Django - Introducción
==============================

.. topic:: Objetivo específico
    :class: objetivo

    Introducir al uso del framework Django para el desarrollo backend con el fin de establecer una base sólida que permita construir una aplicacion de backend estructurada y escalable. 

Actividades previas
=====================

Ambiente de desarrollo
----------------------

1. Cree un repositorio en GitHub con el nombre *backend*.

   a) Agregue un archivo README.md con el título de su backend y una breve descripción del objetivo de su proyecto.
   b) Agregue un archivo *.gitignore* con la plantilla de *Python*.
   
2. Acceda a su proyecto *backend* en Codespaces o en su máquina local.
3. Cree y utilice la(s) rama(s) de desarrollo.
4. Cree y habilite el :term:`ambiente virtual de desarrollo`, con:

   .. code-block:: bash

       python -m venv environment
       source environment/bin/activate

   .. note:: 
      
      Revise las instrucciones para `habilitar el ambiente de desarrollo <https://docs.python.org/3/tutorial/venv.html#tut-venv>`_ para su sistema operativo.

Actividades en clases
=====================

Paquete: Django
---------------

1. Instale :term:`Django` en su ambiente de desarrollo:

   .. code-block:: bash
    
       pip install django

2. Utilice su cliente de IAG generativa para explicar qué es Django y cuáles son sus principales características.

Proyecto: Backend
-----------------

1. Cree un :term:`proyecto Django` llamado *backend* en la ubicación actual:

   .. code-block:: bash

       django-admin startproject backend .

2. Levante el servidor de desarrollo de Django:

   .. code-block:: bash

       python manage.py runserver

3. Revise los cambios en el navegador en la URL `http://127.0.0.1:8000/`
4. Utilice su cliente de IAG generativa para explicar la estructura de archivos de un proyecto, en el contexto de Django.

Aplicación: Main
----------------

Creación de la aplicación
^^^^^^^^^^^^^^^^^^^^^^^^^

1. Cree una :term:`aplicación Django` llamada *main*:

   .. code-block:: bash

       python manage.py startapp main

Registro de la aplicación
^^^^^^^^^^^^^^^^^^^^^^^^^

2. Modifique el archivo ``backend/settings.py`` del proyecto:

   .. code-block:: python
      :emphasize-lines: 3

      INSTALLED_APPS = [
        ...
        "main",
      ]

3. En el archivo ``backend/urls.py``, importe el módulo **include** y asocie la ruta \"main/\" con las rutas de la aplicación **main**:

   .. code-block:: python
      :emphasize-lines: 2, 6

      from django.contrib import admin
      from django.urls import path, include

      urlpatterns = [
            path("admin/", admin.site.urls),
            path("main/", include("main.urls")),
      ]

Rutas y Vistas de la aplicación
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

4. Cree el archivo ``main/urls.py`` con las rutas de la aplicación:

   .. code-block:: python
      :emphasize-lines: 1-6

      from django.urls import path
      from . import views

      urlpatterns = [
            path("index/", views.index, name="index"),
      ]

5. Cree la vista en ``main/views.py`` que retorne un mensaje de bienvenida:

   .. code-block:: python
      :emphasize-lines: 4-7

      from django.shortcuts import render

      # Create your views here.
      from django.http import HttpResponse

      def index(request):
          return HttpResponse("¡Bienvenido a la aplicación Django!")

6. Levante el servidor de desarrollo de Django:

   .. code-block:: bash

       python manage.py runserver

7. Revise los cambios en el navegador en la URL `http://127.0.0.1:8000/main/index/`
8. Utilice su cliente de IAG generativa para explicar la estructura de archivos de una aplicación, en el contexto de Django.

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

    * ¿Cómo te ayudó la IA a diferenciar entre el propósito de un proyecto y el de una aplicación dentro de Django, y por qué es importante esa distinción en el desarrollo modular del backend?

    * ¿Qué decisiones técnicas tomaste al adaptar el código sugerido por la IA para crear correctamente un proyecto y una aplicación en Django que respondan a los requerimientos iniciales del proyecto?

    * ¿Cómo mantuviste tu rol activo y reflexivo durante el proceso de aprendizaje, evitando depender exclusivamente del código generado por la IA para configurar tu proyecto Django?


Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="es" dir="ltr">Si te gusta Python, en este artículo se comparan pros y contras de algunos de los frameworks de desarrollo web más potentes.<br><br>Reflex vs Django vs Flask vs Gradio vs Streamlit vs Dash vs FastAPI<br><br>→ <a href="https://t.co/PiQFOqWWEx">https://t.co/PiQFOqWWEx</a> <a href="https://t.co/3zXjrKsVa4">pic.twitter.com/3zXjrKsVa4</a></p>&mdash; Brais Moure (@MoureDev) <a href="https://twitter.com/MoureDev/status/1870839215161840071?ref_src=twsrc%5Etfw">December 22, 2024</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>