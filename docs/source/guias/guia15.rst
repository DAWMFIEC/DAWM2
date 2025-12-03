..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

==================================
Guía 15: React - Hooks (useEffect)
==================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar la gestión efectos secundarios y la actualización dinámica de la interfaz según los cambios de ubicación o preferencias del usuario en el dashboard. 

Actividades previas
=====================

Open-Meteo
----------

1. Acceda a la página web de `Open-Meteo API <https://open-meteo.com/en/docs>`_.
2. Configure el API de Open-Meteo:
   
   a) En la sección **Location and Time**, seleccione la zona de _America/Chicago (GMT-5)_.
   b) Marque los indicadores: temperatura (`Temperature (2 m)`), humedad relativa (`Relative Humidity (2 m)`), temperatura aparente (`Apparent Temperature`) y  velocidad del viento (`Wind Speed (10 m)`), en la sección **Current Weather** .
   c) En **Settings**, escoja la configuración de las unidades de medida de la API, en este caso: temperatura (`Celsius °C`), velocidad del viento (`km/h`) y unidades de precipitación (`Millimeter`).  

3. Compruebe la estructura del JSON en su navegador.

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

Tipos de datos e Interfaces
---------------------------

1. Acceda al sitio `Transform Tools / JSON to TypeScript <https://transform.tools/json-to-typescript>`_. 
2. Utilice el JSON de salida de la API de Open-Meteo para generar las interfaces de TypeScript. 
3. Dentro de su proyecto *dashboard*, cree el archivo `src/types/DashboardTypes.tsx`, con:

   a) Utilice las interfaces generadas en el paso anterior y modifique el nombre de la interfaz `Root` por `OpenMeteoResponse`.
   b) Agregue la interfaz `DataFetcherOutput`, con:

   .. code-block:: tsx
       :emphasize-lines: 1-7

        export interface DataFetcherOutput {
            data: OpenMeteoResponse | null;
            loading: boolean;
            error: string | null;
        }

4. Utilice su cliente de IAG para justificar el uso de las interfaces y el tipo de datos que representan.

IndicatorUI
-----------

1. Revise la documentación del componente `Card <https://mui.com/material-ui/react-card/>`_.
2. Cree el componente funcional `IndicatorUI` en el archivo `src/components/IndicatorUI.tsx`, con el siguiente código:
  
   .. code-block:: tsx
       :emphasize-lines: 1-23

        import Card from '@mui/material/Card';
        import CardContent from '@mui/material/CardContent';
        import Typography from '@mui/material/Typography';

        interface IndicatorUIProps {
            title?: string;
            description?: string;
        }

        export default function IndicatorUI(props: IndicatorUIProps) {
            return (
                <Card>
                    <CardContent sx={{ height: '100%' }}>
                    <Typography variant="h5" component="div">
                        {props.description}
                    </Typography>
                    <Typography variant="body2" component="p" color="text.secondary">
                        {props.title}
                    </Typography>
                    </CardContent>
                </Card>
            )
        }

3. Modifique el archivo `src/App.tsx`, con:

   a) Importe el componente `IndicatorUI` desde el archivo `./components/IndicatorUI`.
   b) En la sección en la seccion **Indicadores**:

      (i) Convierta el componente Grid un _contenedor_.
      (ii) Agregue cuatro componentes Grid con indicadores `IndicatorUI`, con los props:

      (i) Título: "Temperatura (2m)", Descripción: "XX°C"
      (ii) Título: "Temperatura aparente", Descripción: "YY°C"
      (iii) Título: "Velocidad del viento", Descripción: "ZZkm/h"
      (iv) Título: "Humedad relativa", Descripción: "NN%"

   .. code-block:: tsx
       :emphasize-lines: 2, 12-30

       ...
       import IndicatorUI from './components/IndicatorUI';
       ...

       function App() {

            ...
            return (
                <Grid ... >

                    {/* Indicadores */}
                    <Grid container size={{ xs: 12, md: 9 }} >

                        <Grid size={{ xs: 12, md: 3 }}>
                            <IndicatorUI title='Temperatura (2m)' description='XX°C' />
                        </Grid>

                        <Grid size={{ xs: 12, md: 3 }}>
                            <IndicatorUI title='Temperatura aparente' description='YY°C' />
                        </Grid>

                        <Grid size={{ xs: 12, md: 3 }}>
                            <IndicatorUI title='Velocidad del viento' description='ZZkm/h' />
                        </Grid>
                        
                        <Grid size={{ xs: 12, md: 3 }}>
                            <IndicatorUI title='Humedad relativa' description='NN%' />
                        </Grid>

                    </Grid>

                </Grid>
            )
       }


4. Compruebe la vista previa del resultado en el navegador.

React - Hook: useEffect
-----------------------

.. note::

    Considere la explicación del uso del hook `useEffect <https://es.react.dev/reference/react/useEffect>`_.

DataFetcher
^^^^^^^^^^^

1. Cree el componente funcional `DataFetcher` en el archivo `src/functions/DataFetcher.tsx`.
2. Cree el componente `DataFetcher`, con:

   a) Importe los hooks `useState` y `useEffect` de React.
   b) Importe las interfaces como tipos de datos (`type`)  `OpenMeteoResponse` y `DataFetcherOutput` en el archivo `../types/DashboardTypes.tsx`. 
   c) Declare que el componente `DataFetcher` retorna un objeto del tipo `DataFetcherOutput`.
   
   .. dropdown:: Ver la solución 
        :color: success
        
        .. code-block:: tsx

            import { useEffect, useState } from 'react';
            import { type OpenMeteoResponse, type DataFetcherOutput } from '../types/DashboardTypes';

            export default function DataFetcher() : DataFetcherOutput { }

3. Dentro de `DataFetcher`:
      
   a) Declare el hook `useState` para almacenar los datos obtenidos de la API (`data`, valor predeterminado **null**)
   b) Agregue el hook `useEffect` para que reaccione **únicamente** después del primer renderizado del DOM.
   
    d) Dentro del hook **useEffect**:
   
      (i) Defina la constante `url` con la URL de la API de Open-Meteo que obtuvo en las actividades previas.
      (ii) Defina la función asíncrona `fetchData` que realizará la petición asíncrona a la API de Open-Meteo. 
      (iii) Valide si la respuesta no es exitosa, lance un error. Caso contrario, si la respuesta es exitosa (código de estado HTTP 200), convierta la respuesta a JSON y almacene el resultado en el estado `data` con `setData`. 
      (iv) En caso de error, almacene el mensaje de error en el estado `error` con `setError`
      (v) Ya sea por éxito o por error, cambie el estado `loading` a `false` una vez que se haya completado la petición.
      (vi) Llame a la función `fetchData` dentro del hook `useEffect`.

   e) El componente `DataFetcher` retorna un objeto con los objetos `data`, `loading` y `error` como propiedades.

   .. dropdown:: Ver la solución 
        :color: success
        
        .. code-block:: tsx
            :emphasize-lines: 1-53

            export default function DataFetcher() : DataFetcherOutput {

                const [data, setData] = useState<OpenMeteoResponse | null>(null);
                const [loading, setLoading] = useState(true);
                const [error, setError] = useState<string | null>(null);

                useEffect(() => {

                    // Reemplace con su URL de la API de Open-Meteo obtenida en actividades previas
                    const url = ``

                    const fetchData = async () => {

                        try {
                            
                            const response = await fetch(url);

                            if (!response.ok) {
                                throw new Error(`Error HTTP: ${response.status} - ${response.statusText}`);
                            }

                            const result: OpenMeteoResponse = await response.json();
                            setData(result);

                        } catch (err: any) {

                            if (err instanceof Error) {
                                setError(err.message);
                            } else {
                                setError("Ocurrió un error desconocido al obtener los datos.");
                            }

                        } finally {
                            setLoading(false);
                        }
                    };

                    fetchData();

                }, []); // El array vacío asegura que el efecto se ejecute solo una vez después del primer renderizado

                return { data, loading, error };

            }
            
2. Reemplace la URL de la API de Open-Meteo en el código del componente `DataFetcher` con la URL que obtuvo en las actividades previas.
3. Importe y almacene su salida en una constante `dataFetcherOutput` en el archivo `src/App.tsx`.

   .. code-block:: tsx
       :emphasize-lines: 2,8

       ...
       import DataFetcher from './functions/DataFetcher';
       ...

       function App() {

            ...
            const dataFetcherOutput = DataFetcher();
            ...
       
            return ( ... )
       }

4. Compruebe con el inspector resultado de la petición asíncrona del navegador.
5. Con un cliente de IAG, explique el uso del hook `useEffect` y la configuración del arreglo de dependencias.

Renderizado condicional
^^^^^^^^^^^^^^^^^^^^^^^

1. Modifique el archivo `src/App.tsx`, para mostrar el contenido de `dataFetcherOutput`:

   a) Si `dataFetcherOutput.loading` es **true**, muestre un mensaje de carga.
   b) Si `dataFetcherOutput.error` no es **null**, muestre el mensaje de error.
   c) Si `dataFetcherOutput.data` no es **null**, muestre los datos obtenidos de la API, como la temperatura actual, temperatura aparente, velocidad del viento y humedad relativa, utilizando el componente `IndicatorUI` para cada indicador.

   .. code-block:: tsx
       :emphasize-lines: 12-46

       ...

       function App() {

            ...
            return (
                <Grid ... >

                    {/* Indicadores */}
                    <Grid ... >

                        {/* Renderizado condicional de los datos obtenidos */}

                        {dataFetcherOutput.loading && <p>Cargando datos...</p>}
                        {dataFetcherOutput.error && <p>Error: {dataFetcherOutput.error}</p>}
                        {dataFetcherOutput.data && (
                        <>

                            {/* Indicadores con datos obtenidos */}

                            <Grid size={{ xs: 12, md: 3 }} >
                                <IndicatorUI
                                    title='Temperatura (2m)'
                                    description={dataFetcherOutput.data.current.temperature_2m + " " + dataFetcherOutput.data.current_units.temperature_2m} />
                            </Grid>

                            <Grid size={{ xs: 12, md: 3 }}>
                                <IndicatorUI 
                                    title='Temperatura aparente'
                                    description={dataFetcherOutput.data.current.apparent_temperature + " " + dataFetcherOutput.data.current_units.apparent_temperature} />
                            </Grid>

                            <Grid size={{ xs: 12, md: 3 }}>
                                <IndicatorUI 
                                    title='Velocidad del viento'
                                    description={dataFetcherOutput.data.current.wind_speed_10m + " " + dataFetcherOutput.data.current_units.wind_speed_10m} />
                            </Grid>

                            <Grid size={{ xs: 12, md: 3 }}>
                                <IndicatorUI 
                                    title='Humedad relativa'
                                    description={dataFetcherOutput.data.current.relative_humidity_2m + " " + dataFetcherOutput.data.current_units.relative_humidity_2m} />
                            </Grid>

                        </>
                        )}  

                    </Grid>

                </Grid>
            )
       }

2. Compruebe la vista previa del resultado en el navegador.
3. Con un cliente de IAG, explique el renderizado condicional en React, mediante el uso de variables de estado.

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

    * ¿Cómo te ayudó la inteligencia artificial generativa a entender el propósito de useEffect y su relación con el ciclo de vida de los componentes en React?

    * ¿Qué decisiones tomaste al integrar useEffect en tu dashboard para ejecutar tareas como peticiones asincrónicas o sincronización de datos?

    * ¿Cómo aseguras que el uso de useEffect en tu proyecto refleja tu comprensión y no una dependencia automática de herramientas generativas, especialmente al enfrentar errores o comportamientos inesperados?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">⚛️ useEffect cheatsheet ↓<br><br>❌ Thinking of useEffect as a lifecycle method.<br><br>✅ Thinking of useEffect as a mechanism to sync data (state/props) with systems that aren’t controlled by React. <a href="https://t.co/v8BK5CLsSn">pic.twitter.com/v8BK5CLsSn</a></p>&mdash; George Moller (@_georgemoller) <a href="https://twitter.com/_georgemoller/status/1714250976947794418?ref_src=twsrc%5Etfw">October 17, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>