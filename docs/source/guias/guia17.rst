..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

===============================================
Guía 17: React - Comunicación entre componentes
===============================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar una estrategia de comunicación entre componentes en React utilizando hooks personalizados para la gestión de estados y efectos secundarios. 

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

Comunicación entre componentes con hooks personalizados
-------------------------------------------------------

1. Analice el siguiente escenario de interacción en el dashboard: 

   a) El usuario selecciona una ciudad de la lista de opciones.
   b) El sistema realiza una petición asincrónica a una API de datos climáticos para obtener la información correspondiente a la ciudad seleccionada.
   c) De acuerdo con la respuesta de la API, el sistema actualiza los componentes visuales del dashboard, incluyendo indicadores, tablas y gráficos, para reflejar los datos climáticos de la ciudad seleccionada.

2. Genere el código necesario para implementar este escenario en su proyecto *dashboard*.

   a) En el componente `App.tsx`, utilice una hook para almacenar la opción seleccionada por el usuario y comunique la opción seleccionada al hook useFetchData
 
   .. code-block:: typescript
       :emphasize-lines: 1, 6, 7

       import { useState } from 'react';
       ...

       function App() {
        
         const [selectedOption, setSelectedOption] = useState<string | null>(null);
         const dataFetcherOutput = useFetchData(selectedOption);
        
       }

   b) En el hook `useFetchData.tsx`, defina el tipo de dato del prop, modifique el efecto secundario para que dependa de la opción seleccionada y parametrice la opción seleccionada en la URL del requerimiento asíncrono.

   .. code-block:: typescript
       :emphasize-lines: 3, 9-12,17

       ...

       export default function useFetchData(selectedOption: string | null) : OpenMeteoResponse {
        
         ...
        
         useEffect(() => {
           
           if (selectedOption !== null) {
              const cityConfig = CITY_COORDS[selectedOption];
              const URL = `https://api.open-meteo.com/v1/forecast?latitude=...&longitude=...`
           }

           fetch( URL )
             .then( ... )
           
         }, [selectedOption]); 
        
         ...
       }

3. Compruebe la vista previa del resultado en el navegador.

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

    * ¿Cómo te ayudó la inteligencia artificial generativa a entender la comunicación entre componentes en React?

    * ¿Qué decisiones tomaste al integrar un hook para personalizar la interacción en tu dashboard?

    * ¿Cómo aseguras que el uso de hooks en tu proyecto refleja tu comprensión y no una dependencia automática de herramientas generativas, especialmente al enfrentar errores o comportamientos inesperados?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">⚛️ React tip: typing custom hooks return values using TypeScript ↓ <a href="https://t.co/gUCnG3P5m3">pic.twitter.com/gUCnG3P5m3</a></p>&mdash; George Moller (@_georgemoller) <a href="https://twitter.com/_georgemoller/status/1749603458527744106?ref_src=twsrc%5Etfw">January 23, 2024</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>