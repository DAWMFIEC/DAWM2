..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

=====================================
Guía 17: React - Hooks Personalizados
=====================================

.. topic:: Objetivo específico
    :class: objetivo

    Incorporar hooks personalizados de React para la gestión de estados y efectos secundarios en la obtención y visualización de datos climáticos en el dashboard. 

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

React - Hook: useFetchData
--------------------------

Una forma avanzada de implementar un requerimiento asincrónico es mediante el uso de variables de estado para vigilar el estado del proceso, como se muestra en la siguiente descripción:

1. `useFetchData` es un custom hook diseñado para realizar solicitudes asíncronas a una URL y gestionar el ciclo completo de estados asociados a la carga de datos. El hook encapsula tres variables de estado:

   a) `data`: para almacenar la información obtenida.
   b) `loading`: para indicar si la solicitud está en proceso. 
   c) `error`: para registrar cualquier falla ocurrida durante la carga.

   El hook ejecuta la solicitud y devuelve un objeto con estos tres estados para que cualquier componente pueda utilizarlos. Gracias a su implementación genérica, permite tipar los datos esperados al usarlo en TypeScript.

2. En el componente `App.tsx`, el hook `useFetchData` se invoca al cargar el componente. A partir de allí, el componente accede directamente a las variables de estado devueltas por el hook:

   a) Si loading es falso y no hay error, App muestra los datos.
   b) Si loading es verdadero, App muestra un indicador de carga. 
   c) Si existe un error, se presenta un mensaje informativo al usuario.

   Con este patrón, `App.tsx` se mantiene limpio y enfocado en la presentación, mientras que la lógica de obtención de datos se delega completamente al hook personalizado.

Versionamiento
--------------

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *dashboard*.
2. Genere la(s) solicitud(es) de cambios (pull request) para la rama principal y apruebe los cambios.

Despliegue
----------

1. Desde la línea de comandos, ejecute el comando de transpilación y despliegue del sitio web, con:

   .. code-block:: bash

      npm run deploy

   a) De ser necesario, elimine, corrija o comente las secciones de código identificadas por el transpilador.
   b) Vuelva a ejecutar el comando de transpilación y despliegue del sitio web.

2. Compruebe el resultado en el navegador, con la URL: `https://<username>.github.io/dashboard`

Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Cómo te ayudó la inteligencia artificial generativa a entender el propósito de los hooks con la relación con el ciclo de vida de los componentes en React?

    * ¿Qué decisiones tomaste al integrar un hook personalizados en tu dashboard para ejecutar tareas como peticiones asincrónicas o sincronización de datos?

    * ¿Cómo aseguras que el uso de hooks en tu proyecto refleja tu comprensión y no una dependencia automática de herramientas generativas, especialmente al enfrentar errores o comportamientos inesperados?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">⚛️ React tip: typing custom hooks return values using TypeScript ↓ <a href="https://t.co/gUCnG3P5m3">pic.twitter.com/gUCnG3P5m3</a></p>&mdash; George Moller (@_georgemoller) <a href="https://twitter.com/_georgemoller/status/1749603458527744106?ref_src=twsrc%5Etfw">January 23, 2024</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>