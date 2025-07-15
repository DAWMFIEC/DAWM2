..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

==============================================
Guía 20: Django -  Django Rest Framework (DRF)
==============================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar Django Rest Framework (DRF) para la construcción y estructuración de los endpoints de una API REST. 

Actividades previas
=====================

Ambiente de desarrollo
----------------------

1. Acceda a su proyecto *backend* en Codespaces o en su máquina local.
2. Cree y utilice la(s) rama(s) de desarrollo.
3. Cree y habilite el ambiente virtual de desarrollo, con:

   .. code-block:: bash

       python -m venv environment
       source environment/bin/activate

4. Instale las librerías de requirements.txt, con:

   .. code-block:: bash

       pip install -r requirements.txt

Actividades en clases
=====================

Paquete: Django REST framework
------------------------------

1. Instale :term:`Django REST framework` en su ambiente de desarrollo:

   .. code-block:: bash
    
       pip install djangorestframework

2. Registre el Django REST framework en el archivo ``backend/settings.py`` del proyecto:

   .. code-block:: python
      :emphasize-lines: 3

      INSTALLED_APPS = [
        ...
        "rest_framework",
      ]

3. Utilice su cliente de IAG generativa para explicar qué es `Django REST framework <https://www.django-rest-framework.org/>`_ y cuáles son sus principales características.

Aplicación: Landing API
-----------------------

1. Cree la aplicación **landingapi** en su proyecto.
2. Registre la aplicación con  la ruta \"api/landing/\" con las rutas de la aplicación **landingapi**
3. Cree el archivo ``landingapi/urls.py`` con las rutas de la aplicación:

   .. code-block:: python
      :emphasize-lines: 1-6

      from django.urls import path
      from . import views

      urlpatterns = [
            path("", views.LandingAPI.as_view(), name="landing_resources" ),
      ]

4. Cree la vista en ``landingapi/views.py`` que retorne un mensaje de bienvenida:

   .. code-block:: python
      :emphasize-lines: 4-7

      from django.shortcuts import render

      # Create your views here.
      from rest_framework.views import APIView

      # Simulación de base de datos local en memoria
      landing_data = []
      
      class LandingAPI(APIView):
          name = "Landing API"

5. Levante el servidor de desarrollo de Django:

   .. code-block:: bash

       python manage.py runserver

6. Revise los cambios en el navegador en la URL `http://127.0.0.1:8000/api/landing/`
7. Utilice su cliente de IAG generativa para explicar y comparar las vistas que ofrece Django REST framework. 

GET
^^^

1. Utilice su cliente de IAG para manejar el método GET en la vista de la API:

   a) Retorne el arreglo **landing_data** como respuesta JSON, con el estado 200 OK.

   .. dropdown:: Ver el código 
      :color: primary  
    
      .. code-block:: python
         :emphasize-lines: 4-5

         class LandingAPI(APIView):
            ...

            def get(self, request):
                return Response(landing_data, status=status.HTTP_200_OK)

2. Compruebe el resultado en su navegador en la URL `http://127.0.0.1:8000/api/landing/?format=json`

POST
^^^^

1. Utilice su cliente de IAG para manejar el método POST en la vista de la API:

   a) Procese el requerimiento con los campos **name** y **email**. 
   b) En caso que no cuente con los campos requeridos retorne un mensaje y un estado de error.
   c) Caso contrario, agregue el dato al arreglo **landing_data**. Retorne un mensaje de éxito, con el dato agregado y el estado 201 Created.

   .. dropdown:: Ver el código 
      :color: primary  
    
      .. code-block:: python
         :emphasize-lines: 4-5

         class LandingAPI(APIView):
            ...

            def post(self, request):
                data = request.data

                # Validación mínima
                if 'name' not in data or 'email' not in data:
                    return Response({'error': 'Faltan campos requeridos.'}, status=status.HTTP_400_BAD_REQUEST)
                
                landing_data.append(data)
                return Response({'message': 'Dato guardado exitosamente.', 'data': data}, status=status.HTTP_201_CREATED)

2. Compruebe el resultado en su navegador en la URL `http://127.0.0.1:8000/api/landing/?format=api` 

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

    * ¿Qué conceptos clave del desarrollo de APIs con Django Rest Framework lograste comprender con mayor claridad gracias al uso de inteligencia artificial generativa, y qué conceptos consideras que deben ser reforzados mediante práctica directa?

    * ¿Cómo integraste correctamente los endpoints de DRF en tu proyecto, gestionando rutas, serializadores y permisos, y cómo evaluaste si el código sugerido por la IA era eficiente y seguro?

    * ¿Cómo aseguras que el uso de inteligencia artificial generativa no sustituya tu comprensión del ciclo completo de construcción de una API REST, y que tu participación sea consciente y formativa?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr"><a href="https://twitter.com/hashtag/REST?src=hash&amp;ref_src=twsrc%5Etfw">#REST</a> <a href="https://twitter.com/hashtag/API?src=hash&amp;ref_src=twsrc%5Etfw">#API</a> what is it?<br>Representational State Transfer<br>This means that when a <a href="https://twitter.com/hashtag/client?src=hash&amp;ref_src=twsrc%5Etfw">#client</a> requests a resource using a REST API, the <a href="https://twitter.com/hashtag/server?src=hash&amp;ref_src=twsrc%5Etfw">#server</a> transfers back the current state of the resource in a standardized representation <a href="https://t.co/xCFXw9cQFZ">pic.twitter.com/xCFXw9cQFZ</a></p>&mdash; Terrasoft (@Terrasoft_ltd) <a href="https://twitter.com/Terrasoft_ltd/status/1732354546528067738?ref_src=twsrc%5Etfw">December 6, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>