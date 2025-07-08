..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

==============================================
Guía 16: React - Gestión y visualización datos
==============================================

.. topic:: Objetivo específico
    :class: objetivo

    Incorporar componentes avanzados de gestión y visualización de datos para la representación de datos climáticas en tiempo en el dashboard.

Actividades previas
=====================

Open-Meteo
----------

1. Configure API de Open-Meteo en `Open-Meteo API <https://open-meteo.com/en/docs>`_, con:
   
   a) Seleccione la zona horaria, para Ecuador elija la opción **America/Chicago** (GMT-5).
   b) Marque los indicadores que desea mostrar el dashboard en la sección de `Current Weather <https://open-meteo.com/en/docs#current_weather>`_ de la documentación, en este caso: temperatura (`Temperature (2 m)`), humedad relativa (`Relative Humidity (2 m)`), temperatura aparente (`Apparent Temperature`) y  velocidad del viento (`Wind Speed (10 m)`).
   c) **Seleccione dos variables meteorológicas por hora, por ejemplo: Temperatura (`Temperature (2 m)`) y Velocidad del viento (`Wind Speed (10 m)`), etc.**
   d) Seleccione la configuración de las unidades de medida de la API, en este caso: temperatura (`Celsius °C`), velocidad del viento (`km/h`) y unidades de precipitación (`Millimeter`), etc.  
2. Con la URL de la API con los parámetros seleccionados, compruebe la estructura del JSON de salida en su navegador.

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

TableUI y ChartUI
-----------------

1. Instale los paquetes necesarios para la gestión y visualización de datos, con:

   .. code-block:: bash

      npm install npm install @mui/x-data-grid @mui/x-charts

2. Cree los componentes funcionales.

   a) `TableUI` en el archivo `src/components/TableUI.tsx`, con el siguiente código:

   .. code-block:: tsx
       :emphasize-lines: 1-23

   b) `ChartUI` en el archivo `src/components/ChartUI.tsx`, con el siguiente código:

   .. code-block:: tsx
       :emphasize-lines: 1-23

       import { LineChart } from '@mui/x-charts/LineChart';
       import Typography from '@mui/material/Typography';

       const arrValues1 = [4000, 3000, 2000, 2780, 1890, 2390, 3490];
       const arrValues2 = [2400, 1398, 9800, 3908, 4800, 3800, 4300];
       const arrLabels = ['A','B','C','D','E','F','G'];


       export default function ChartUI() {
         return (
            <>
                  <Typography variant="h5" component="div">
                     Chart arrLabels vs arrValues1 & arrValues2
                  </Typography>
                  <LineChart
                     height={300}
                     series={[
                        { data: arrValues1, label: 'value1'},
                        { data: arrValues2, label: 'value2'},
                     ]}
                     xAxis={[{ scaleType: 'point', data: arrLabels }]}
                     
                  />
            </>
         );
       }

3. Importe los componentes `TableUI` y `ChartUI` en el archivo `src/App.tsx`, con:

   .. code-block:: tsx
       :emphasize-lines: 2-3, 15, 20

       ...
       import TableUI from './components/TableUI';
       import ChartUI from './components/ChartUI';

       function App() {

            ...
            return (
                <Grid ... >

                  ...

                  {/* Gráfico */}
                  <Grid size={{ xs: 6, md: 6 }} sx={{ display: { xs: "none", md: "block" } }}>
                     <ChartUI />
                  </Grid>

                  {/* Tabla */}
                  <Grid size={{ xs: 6, md: 6 }} sx={{ display: { xs: "none", md: "block" } }}>
                     <TableUI />
                  </Grid>

                  ...
                
                </Grid>
            )
       }

4. Compruebe la vista previa del resultado en el navegador.

Renderizado
-----------

1. Modifique los componentes `TableUI` y `ChartUI` para que obtengan los datos de la API de Open-Meteo.
2. Asegúrese de que los datos se muestren correctamente en la tabla y el gráfico, considerando el tiempo de carga y el manejo de errores.
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

    * ¿Cómo?

    * ¿Qué?

    * ¿Cómo?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    