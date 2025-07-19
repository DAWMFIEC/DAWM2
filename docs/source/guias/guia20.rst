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

Paquete: Django REST framework (DRF)
------------------------------------

1. Instale :term:`Django REST framework` en su ambiente de desarrollo:

   .. code-block:: bash
    
       pip install djangorestframework

2. Registre el Django REST framework en el archivo ``backend_data_server/settings.py`` del proyecto:

   .. code-block:: python
      :emphasize-lines: 3

      INSTALLED_APPS = [
        ...
        "rest_framework",
      ]

3. Utilice su cliente de IAG generativa para explicar qué es `Django REST framework <https://www.django-rest-framework.org/>`_ y cuáles son sus principales características.

Aplicación: DEMO API
--------------------

1. Cree una la aplicación **demo_api** en su proyecto.
2. Registre la ruta \"demo/api/\" con las subrutas de la aplicación **demo_api**
3. Cree el archivo ``demo_api/urls.py`` con la ruta raíz a la vista **DemoRestApi**:

   .. code-block:: python
      :emphasize-lines: 1-6

      from django.urls import path
      from . import views

      urlpatterns = [
            path("index/", views.DemoRestApi.as_view(), name="demo_rest_api_resources" ),
      ]

4. Cree la :term:`vista basada en clases` en ``demo_api/views.py`` que retorne un mensaje de bienvenida:

   .. code-block:: python
      :emphasize-lines: 4-19

      from django.shortcuts import render

      # Create your views here.
      from rest_framework.views import APIView
      from rest_framework.response import Response
      from rest_framework import status

      import uuid

      # Simulación de base de datos local en memoria
      data_list = []

      # Añadiendo algunos datos de ejemplo para probar el GET
      data_list.append({'id': str(uuid.uuid4()), 'name': 'User01', 'email': 'user01@example.com', 'is_active': True})
      data_list.append({'id': str(uuid.uuid4()), 'name': 'User02', 'email': 'user01@example.com', 'is_active': True})
      data_list.append({'id': str(uuid.uuid4()), 'name': 'User03', 'email': 'user01@example.com', 'is_active': False}) # Ejemplo de item inactivo
      
      class DemoRestApi(APIView):
          name = "Demo REST API"

5. Levante el servidor de desarrollo de Django:

   .. code-block:: bash

       python manage.py runserver

6. Revise los cambios en el navegador con la URL raíz, seguido por la ruta `/demo/api/index/`
7. Utilice su cliente de IAG generativa para explicar el estilo arquitectónico :term:`REST` y su implementación en DRF. 

GET
^^^

1. Utilice su cliente de IAG para manejar el método GET en la vista de la API, considerando:

   a) Retorne el arreglo **data_list** como respuesta JSON, con el :term:`código de estado HTTP` 200 OK.

   .. dropdown:: Ver el código 
      :color: primary  
    
      .. code-block:: python
         :emphasize-lines: 4-5

         class DemoRestApi(APIView):
            ...

            def get(self, request):
                return Response(data_list, status=status.HTTP_200_OK)

2. Revise los cambios en el navegador con la URL raíz, seguido por las rutas `/demo/api/` y `/demo/api/?format=json`

POST
^^^^

1. Utilice su cliente de IAG para manejar el método POST en la vista de la API, considerando:

   a) Extraiga los datos enviados en el cuerpo de la solicitud en la variable **data**.
   b) Validar que los campos **name** y **email** estén presentes. Si falta alguno, debe retornar una respuesta con código HTTP 400 y un mensaje de error.
   c) Si los campos son válidos:
      
      (i) Generar un identificador único utilizando uuid.uuid4() y agregue el campo `'id'` a la variable **data**, 
      (ii) Agregue el campo `'is_active'` con el valor **True** a la variable **data**, 
      (iii) Agregue la variable **data** a la lista **data_list**. 
      (iv) Finalmente, debe retornar una respuesta con código HTTP 201 (Created), un mensaje de éxito y los datos guardados.

   .. dropdown:: Ver el código 
      :color: primary  
    
      .. code-block:: python
         :emphasize-lines: 4-15

         class DemoRestApi(APIView):
            ...

            def post(self, request):
                data = request.data

                # Validación mínima
                if 'name' not in data or 'email' not in data:
                    return Response({'error': 'Faltan campos requeridos.'}, status=status.HTTP_400_BAD_REQUEST)
                
                data['id'] = str(uuid.uuid4())
                data['is_active'] = True
                data_list.append(data)

                return Response({'message': 'Dato guardado exitosamente.', 'data': data}, status=status.HTTP_201_CREATED)

2. Revise los cambios en el navegador con la URL raíz, seguido por la ruta `/demo/api/` y envíe una solicitud POST con el cuerpo, p.e.:

   .. code-block:: json
      :emphasize-lines: 1-4

      {
          "name": "John Jay",
          "email": "john.jay@example.com"
      }


PUT, PATCH y DELETE
^^^^^^^^^^^^^^^^^^^

1. Utilice su cliente de IAG para modificar:

   a) El archivo ``demo_api/views.py`` con la clase ``DemoRestApiItem``, que responda a los métodos:
   
      (i) **PUT** debe reemplazar completamente los datos de un elemento del arreglo, excepto el identificador que se envía como campo obligatorio en el cuerpo de la solicitud.
      (ii) **PATCH** debe actualizar parcialmente los campos del elemento identificado por su identificador, manteniendo los valores no modificados.
      (iii) **DELETE** debe eliminar lógicamente un elemento del arreglo según el identificador proporcionado.

      .. note:: 
         
         Cada método debe responder, en caso de éxito o error, con el código de estado HTTP correspondiente.

   b) El archivo ``demo_api/urls.py`` con la ruta `"<str:id>/"` con la vista ``DemoRestApiItem``.

2. Revise los cambios en el navegador con la URL raíz, seguido por la ruta `/demo/api/<str:id>/` y compruebe el funcionamiento de las solicituds PUT, PATCH y DELETE.


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