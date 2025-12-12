..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

============================================================
Guía 19: React y Ionic - Acceso al dispositivo con Capacitor
============================================================

.. topic:: Objetivo específico
    :class: objetivo

    Init. 

Actividades previas
=====================


Ambiente de despliegue
----------------------

1. Obtenga una cuenta en `Ionic Appflow <https://ionic.io/appflow>`_.

    a) Verifique su cuenta a través del correo electrónico.

2. Inicie sesión en `Ionic Appflow <https://ionic.io/appflow>`_.


Actividades en clases
=====================

Plataforma Android
------------------

1. En el proyecto, genere los archivos nativos del proyecto Android dentro de una carpeta Android en el directorio raíz de tu proyecto.

   .. code-block:: bash

       ionic cap add android

2. Después de la primera adición, o cada vez que actualices tu código web, debes copiar los recursos web más recientes al proyecto nativo de Android. El comando sync se encarga de esto y también instala cualquier complemento nativo nuevo que hayas añadido.

   .. code-block:: bash

       ionic cap sync android

3. Utilice un cliente de IAG para explicar las características principales de Capacitor como herramienta de empaquetado para aplicaciones híbridas, enfocándose en la plataforma Android.


Despliegue en Ionic Appflow
---------------------------

1. Conecte la aplicación híbrida en el repositorio *mobile* con la aplicación creada en Ionic Appflow.

   a) Siga las instrucciones en `Connect Using GitHub <https://ionic.io/docs/appflow/quickstart/github>`_ para conectar su repositorio GitHub con Ionic Appflow.
   b) Seleccione el repositorio *mobile* y la rama principal (main) para conectar con Ionic Appflow.

2. Realice un compilación nativa de la aplicación híbrida en Ionic Appflow, de acuerdo con las instrucciones en `Start a Native Build <https://ionic.io/docs/appflow/quickstart/package#start-a-native-build>`_ para realizar la compilación nativa.
3. Luego de completar exitosamente el despliegue manual, descargue o utilice el QR code proporcionado por Ionic Appflow para instalar la aplicación híbrida en un dispositivo móvil compatible.


Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Qué?

    * ¿Qué?

    * ¿Cómo?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <iframe width="560" height="315" src="https://www.youtube.com/embed/VIDEO_ID" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>