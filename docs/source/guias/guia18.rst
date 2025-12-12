..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

==================================================
Guía 18: React y Ionic - Introducción y Despliegue
==================================================

.. topic:: Objetivo específico
    :class: objetivo

    Explorar el framework Ionic junto con React para el desarrollo y despliegue de una aplicación móvil híbrida.

Actividades previas
=====================

Ambiente de desarrollo
----------------------

1. Cree un repositorio en GitHub con el nombre *mobile*.

   a) Agregue un archivo README.md con el título de su aplicación híbrida y una breve descripción del objetivo de su proyecto.
   b) Use el archivo *.gitignore* con la plantilla de *Node*.
   
2. Acceda a su proyecto *mobile* en Codespaces o en su máquina local.
3. Cree y utilice la(s) rama(s) de desarrollo.

Ambiente de despliegue
----------------------

1. Obtenga una cuenta en `Ionic Appflow <https://ionic.io/appflow>`_.

    a) Verifique su cuenta a través del correo electrónico.
    b) Inicie sesión en `Ionic Appflow <https://ionic.io/appflow>`_.
    
2. Cree una nueva aplicación en Ionic Appflow con el nombre de su proyecto móvil híbrido.

Actividades en clases
=====================

Ionic CLI 
---------

1. Instale Ionic CLI globalmente en su ambiente de desarrollo.

   .. code-block:: bash
       
       npm install -g @ionic/cli

2. Verifique la instalación de Ionic CLI.

   .. code-block:: bash

       ionic --version

3. Utilice un cliente de IAG para explicar la utilidad de Ionic Framework y Ionic CLI en el desarrollo de aplicaciones móviles híbridas.

Creación de una aplicación híbrida con Ionic y React
----------------------------------------------------

1. Cree una nueva aplicación híbrida con Ionic y React utilizando Ionic CLI, a partir de la plantilla *tabs* y con Capacitor como herramienta de empaquetado.

   .. code-block:: bash

       ionic start temp tabs --type=react --capacitor
       cp -r temp/* .
       rm -rf temp

   **Nota:** No es necesario crear una cuenta en Ionic al solicitarlo durante el proceso de creación de la aplicación.

2. Inicie la aplicación en modo de desarrollo.

   .. code-block:: bash

       ionic serve

3. Revise el funcionamiento de la aplicación en el navegador web e inspecione la vista responsiva para dispositivos móviles.
4. Utilice un cliente de IAG para explicar las características principales de la estructura del proyecto generado por Ionic CLI para una aplicación híbrida con React y de Capacitor como herramienta de empaquetado.

Versionamiento
--------------

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *mobile*.
2. Cree una solicitud de extracción (pull request) para fusionar la(s) rama(s) de desarrollo en la rama principal (main).

Despliegue en Ionic Appflow
---------------------------

1. Conecte la aplicación híbrida en el repositorio *mobile* con la aplicación creada en Ionic Appflow.

   a) Siga las instrucciones en `Ionic Appflow <https://ionic.io/appflow/docs/getting-started/connecting-your-repo>`_ para conectar su repositorio GitHub con Ionic Appflow.
   b) Seleccione el repositorio *mobile* y la rama principal (main) para conectar con Ionic Appflow.

2. Realice un despliegue manual de la aplicación híbrida en Ionic Appflow.
    a) Siga las instrucciones en `Ionic Appflow <https://ionic.io/appflow/docs/getting-started/manual-deploys>`_ para realizar un despliegue manual.
    b) Espere a que el proceso de construcción (build) finalice exitosamente.

3. Revise el historial de despliegues en Ionic Appflow para verificar que el despliegue manual se haya realizado correctamente.
4. Luego de completar exitosamente el despliegue manual, descargue o utilice el QR code proporcionado por Ionic Appflow para instalar la aplicación híbrida en un dispositivo móvil compatible.

Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Cómo te ayudó la inteligencia artificial generativa a comprender Ionic y React en el desarrollo de una aplicación híbrida?

    * ¿Cómo aseguraste que la interacción entre los componentes de Ionic y la navegación entre vistas fuera fluida y coherente?

    * ¿Qué actitudes consideras fundamentales para asegurar que el resultado final de la aplicación híbrida sea auténtica y producto de tu criterio profesional, incluso si partiste de una base generada por IA?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">Ionic Framework v8.7.6 has been released! 🚀<br><br>Check out the changes here: <a href="https://t.co/Moah8hq94t">https://t.co/Moah8hq94t</a></p>&mdash; ionic (@Ionicframework) <a href="https://twitter.com/Ionicframework/status/1976146354041672091?ref_src=twsrc%5Etfw">October 9, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>