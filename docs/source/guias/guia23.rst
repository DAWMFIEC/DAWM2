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

1. Cree un repositorio en GitHub con el nombre *django_data_monitor*.

   a) Agregue un archivo README.md con el título de su backend y una breve descripción del objetivo de su proyecto.
   b) Agregue un archivo *.gitignore* con la plantilla de *Python*.
   
2. Acceda a su proyecto *django_data_monitor* en Codespaces o en su máquina local.
3. Cree y utilice la(s) rama(s) de desarrollo.
4. Cree y habilite el ambiente virtual de desarrollo, con:

   .. code-block:: bash

       python -m venv env
       source env/bin/activate

Actividades en clases
=====================

Backend Analytics Server y Dashboard
------------------------------------

1. Instale `Django` en su ambiente de desarrollo.
2. Cree un proyecto Django llamado *backend_analytics_server* en la ubicación actual.
3. Cree una la aplicación *dashboard* en su proyecto y regístrela a la ruta raíz (\"\").
4. Descargue y renderice la plantilla :download:`base.html <./files/dashboard/base.html>`, con los archivos estáticos :download:`assets.zip <./files/dashboard/assets.zip>`, en la vista principal de la aplicación. 

   .. note:: 

      Reemplace las rutas de los archivos estáticos en la plantilla por las rutas relativas a la carpeta ``static`` del proyecto.

5. Inicie el servidor de desarrollo y revise los cambios en el navegador en la URL en la ruta raíz la aplicación.

Herencia de plantillas
----------------------

1. En el archivo ``templates/base.html``, encierre la sección ``Block content`` entre las etiquetas **{% block content %}**.

   .. code-block:: html      
       :emphasize-lines: 3, 15
      
       ...

       {% block content %}

         <!-- START - Block content -->

            <div class="flex items-center justify-center h-screen bg-gray-100 w-full">
                  <div class="p-6 bg-white shadow-md rounded">
                     Block content
                  </div>
            </div>
         
         <!-- END - Block content -->

       {% endblock %}

       ...


2. Cree la plantilla `index.html` en la carpeta `templates/dashboard/` y extienda la plantilla `base.html`.

   .. code-block:: html
       :emphasize-lines: 1-15

       {% extends "dashboard/base.html" %}

       {% block content %}

         <!-- START - Block content -->
       
            <div class="flex flex-col flex-1 w-full">

               <h1>Bienvenido al Dashboard</h1>

            </div>

         <!-- END - Block content -->
       
       {% endblock %}

3. Renderice la plantilla ``index.html`` en la vista principal de la aplicación *dashboard*.

   .. code-block:: python
       :emphasize-lines: 4

       from django.shortcuts import render

       def index(request):
           return render(request, 'dashboard/index.html')

4. Revise los cambios en el navegador con la URL raíz.
5. Utilice su cliente de IAG generativa para explicar la herencia de plantillas en Django.

Fragmentos de plantilla
-----------------------

1. Descargue los archivos :download:`header.html <./files/partials/header.html>` y :download:`data.html <./files/partials/data.html>` en la carpeta `templates/dashboard/partials/`.
2. En la plantilla `templates/dashboard/index.html`, reemplace el contenido de la sección `Block content` por los fragmentos de plantilla `header.html` y `data.html`.

   .. code-block:: html
       :emphasize-lines: 7-8

       {% extends "dashboard/base.html" %}

       {% block content %}
       
         <div class="flex flex-col flex-1 w-full">

            {% include "./partials/header.html" %}
            {% include "./partials/data.html" %}

         </div>
       
       {% endblock %}

3. Revise los cambios en el navegador con la URL raíz.
4. Utilice su cliente de IAG generativa para explicar los fragmentos de plantilla en Django.


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

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *django_data_monitor*.
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

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">Rendering on the Web – The SEO Version: Pros and Cons from Server Side to Full Client Side Rendering by <a href="https://twitter.com/jbobbink?ref_src=twsrc%5Etfw">@jbobbink</a> <a href="https://t.co/IioPUtth8Y">https://t.co/IioPUtth8Y</a> <a href="https://t.co/VzZrRGVOOo">pic.twitter.com/VzZrRGVOOo</a></p>&mdash; Aleyda Solis 🕊️ (@aleyda) <a href="https://twitter.com/aleyda/status/1094593901493714945?ref_src=twsrc%5Etfw">February 10, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>