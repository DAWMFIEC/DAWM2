..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

=====================
Guía 22: Django - JWT
=====================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar un sistema de autenticación basado en JSON Web Tokens (JWT) para proteger los endpoints del API REST, asegurando que solo los usuarios autenticados puedan acceder a los recursos gestionados desde la base de datos en Firebase, promoviendo así un control seguro, escalable y sin estado sobre las solicitudes recibidas.

Actividades previas
=====================

Ambiente de desarrollo
----------------------

1. Acceda a su proyecto *django_api_suite* en Codespaces o en su máquina local.
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

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *django_api_suite*.
2. Genere la(s) solicitud(es) de cambios (pull request) para la rama principal y apruebe los cambios.

Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Cómo te ayudó la IA a distinguir entre la autenticación basada en sesiones y la autenticación basada en tokens como JWT, y qué ventajas o desventajas identificaste en el uso de JWT en proyectos backend?

    * ¿Qué decisiones técnicas tomaste al integrar JWT en tu backend, y cómo contrastaste el flujo sugerido por la IA con los requerimientos reales del proyecto y las buenas prácticas de seguridad?

    * ¿Cómo puedes demostrar que el uso de JWT en tu proyecto no solo fue implementado correctamente, sino que también fue comprendido a nivel conceptual y aplicado con responsabilidad profesional?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="nl" dir="ltr">JWT — JSON Web Tokens <a href="https://t.co/4pGXLEENQF">pic.twitter.com/4pGXLEENQF</a></p>&mdash; Kamran Ahmed (@kamrify) <a href="https://twitter.com/kamrify/status/1683128191550930946?ref_src=twsrc%5Etfw">July 23, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>