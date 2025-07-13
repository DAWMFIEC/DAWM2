..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

==============================================
Guía 15: Django -  Django Rest Framework (DRF)
==============================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar Django Rest Framework (DRF) para la construcción y estructuración de los endpoints de una API REST, utilizando vistas, serializadores y rutas adecuadas que permitan realizar operaciones CRUD sobre datos en Firebase Realtime Database. 

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