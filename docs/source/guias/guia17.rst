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

   a) `loading`: para indicar si la solicitud está en proceso. El valor predeterminado es _true_.
   b) `data`: para almacenar la información obtenida o _null_ si no hay datos. El valor predeterminado es _null_.
   c) `error`: para registrar cualquier falla ocurrida durante la carga o _null_ si no hay errores. El valor predeterminado es _null_.

   Durante la petición asincrónica, el hook actualiza estas variables de estado según si la solicitud está en proceso, información obtenida y cualquier falla que ocurra.

   El hook devuelve un objeto que contiene estas tres variables de estado, permitiendo a los componentes que lo utilizan manejar fácilmente la lógica de presentación basada en el estado de la solicitud.

2. En el componente `App.tsx`, el hook `useFetchData` se invoca al cargar el componente. A partir de allí, el componente accede directamente a las variables de estado devueltas por el hook para el renderizado condicional:

   a) Si `dataFetcherOutput.loading` es **true**, muestre un mensaje de carga.
   b) Si `dataFetcherOutput.error` no es **null**, muestre el mensaje de error.
   c) Si `dataFetcherOutput.data` no es **null**, muestre los datos obtenidos de la API, como la temperatura actual, temperatura aparente, velocidad del viento y humedad relativa, utilizando el componente `IndicatorUI` para cada indicador.

3. Compruebe la vista previa del resultado en el navegador.
4. Con un cliente de IAG, explique el renderizado condicional en React, mediante el uso de variables de estado.


React - Hook: useUpdateData
---------------------------


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