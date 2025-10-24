..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

====================================
Guía 09: Promesas, Servicios y JSON 
====================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar funciones en JavaScript que consuman servicios externos utilizando promesas para recuperar datos en formato JSON y mostrarlos dinámicamente en la landing page mejorando así la interactividad y la presentación de contenido relevante para el usuario.

Actividades previas
=====================

JSON
----

1. Visite el sitio web de `ReqBin <https://reqbin.com/>`_.
2. Realice las siguientes peticiones HTTP, p.e.:
   
   a) Petición GET a los Datos Generales de la API:

      - **URL:** `https://data-dawm.github.io/Datos/Products/GeneralData.json`
      - **Método:** `GET`
    
   b) Petición GET a los Datos Privados de la API:

      - **URL:** `https://data-dawm.github.io/Datos/Products/PrivateData.json`
      - **Método:** `GET`

3. Explore la :term:`petición HTTP` y la :term:`respuesta HTTP` en formato :term:`JSON` que se muestra en la sección de respuesta.
4. Utilice un cliente de IAG para explicar cómo se estructura la petición y la respuesta de la API; además del formato :term:`JSON`.

Ambiente de desarrollo
----------------------

1. Acceda a su proyecto *landing* en Codespaces o en su máquina local.
2. Cree y utilice la(s) rama(s) de desarrollo.
3. Instale los paquetes y levante el servidor, con:

   .. code-block:: bash

      npm install
      npm run dev

Actividades en clases
=====================

HTML
----

1. En el documento *index.html*, agregue una sección para mostrar los datos obtenidos de la API de Faker.

   .. dropdown:: Ver el código 
    :color: primary
    
    .. code-block:: html
        :emphasize-lines: 3-42
    
        <section class="bg-slate-50 dark:bg-gray-900"> ... </section>

        <!-- Nuestros Productos -->
        <section class="bg-slate-50 dark:bg-gray-900">
            <div id="container-05" class="px-4 py-5 mx-auto max-w-md md:max-w-xl">
                <div class="grid grid-cols-1 gap-4 md:grid-cols-1">
                    <h2 class="text-4xl font-extrabold tracking-tight text-gray-900 dark:text-white text-center">Nuestros de
                    productos</h2>
                </div>
            </div>
            <div id="container-06" class="max-w-4xl pt-5 pb-5 mx-auto">
                <div id="skeleton-container" class="grid grid-cols-1 md:grid-cols-3 gap-6 p-6">

                    <!-- Skeleton Card -->
                    <div class="animate-pulse space-y-4 bg-white dark:bg-gray-800 p-4 rounded-2xl shadow">
                    <div class="w-full h-40 bg-gray-300 dark:bg-gray-700 rounded-lg"></div>
                    <div class="h-6 bg-gray-300 dark:bg-gray-700 rounded w-3/4"></div>
                    <div class="h-5 bg-gray-300 dark:bg-gray-700 rounded w-1/2"></div>
                    <div class="space-y-2">
                        <div class="h-3 bg-gray-300 dark:bg-gray-700 rounded w-full"></div>
                        <div class="h-3 bg-gray-300 dark:bg-gray-700 rounded w-5/6"></div>
                    </div>
                    </div>

                    <!-- Skeleton Card -->
                    <div class="animate-pulse space-y-4 bg-white dark:bg-gray-800 p-4 rounded-2xl shadow">
                    <div class="w-full h-40 bg-gray-300 dark:bg-gray-700 rounded-lg"></div>
                    <div class="h-6 bg-gray-300 dark:bg-gray-700 rounded w-3/4"></div>
                    <div class="h-5 bg-gray-300 dark:bg-gray-700 rounded w-1/2"></div>
                    <div class="space-y-2">
                        <div class="h-3 bg-gray-300 dark:bg-gray-700 rounded w-full"></div>
                        <div class="h-3 bg-gray-300 dark:bg-gray-700 rounded w-5/6"></div>
                    </div>
                    </div>

                    <!-- Skeleton Card -->
                    <div class="animate-pulse space-y-4 bg-white dark:bg-gray-800 p-4 rounded-2xl shadow">
                    <div class="w-full h-40 bg-gray-300 dark:bg-gray-700 rounded-lg"></div>
                    <div class="h-6 bg-gray-300 dark:bg-gray-700 rounded w-3/4"></div>
                    <div class="h-5 bg-gray-300 dark:bg-gray-700 rounded w-1/2"></div>
                    <div class="space-y-2">
                        <div class="h-3 bg-gray-300 dark:bg-gray-700 rounded w-full"></div>
                        <div class="h-3 bg-gray-300 dark:bg-gray-700 rounded w-5/6"></div>
                    </div>
                    </div>

                </div>
            </div>
        </section>

        <div id="toast-interactive" ... > </div>

2. Compruebe la vista previa del resultado en el navegador.


JS: Fetch con cadena de promesas
--------------------------------

.. sidebar:: 

   .. image:: https://cdn.hashnode.com/res/hashnode/image/upload/v1677409815862/3588ce49-a480-46fe-a229-9dafafa4c61d.png
      
   Mastering JavaScript Promises: The Ultimate Guide de `Loknath Reddy <https://loknath.hashnode.dev/mastering-javascript-promises-the-ultimate-guide>`_.

1. Con un cliente de IAG, explique cómo se manejan operaciones asincrónicas (como las peticiones HTTP) con cadena de promesas.

2. Cree el documento javascript *functions.js* dentro de la carpeta *js* de tu proyecto. Declare el modo estricto del documento. Cree la función flecha `fetchFakerData`. Exporte la función del módulo. 
   
3. Utilice un cliente de IAG para generar el código en *js/functions.js*, de acuerdo con las siguientes especificaciones:

   a) Modifique la función flecha `fetchFakerData` con una petición HTTP mediante el objeto fetch, sin opciones extras.
   b) Procese la respuesta en una cadena de :term:`promesas` (then y catch).
   c) La función siempre devuelve un objeto con las claves **success** y **body** o **error**.
      
      (i) La clave **success** tendrá un valor booleano que indica si la petición fue exitosa (true) o si ocurrió un error (false) en el servidor HTTP o durante el procesamiento del cliente. 
      
      (ii) En caso de éxito, el objeto debe incluir **body** con el contenido de la respuesta convertida a JSON. 
      
      (iii) En caso de error, el objeto debe incluir **error** con un mensaje descriptivo del error ocurrido.

   .. dropdown:: Ver la solución
    :color: success

    .. code-block:: javascript
        
        'use strict';

        let fetchFakerData =  (url) => {

            return fetch(url)
                .then(response => {

                    // Verificar si la respuesta es exitosa (status 200-299)
                    if (!response.ok) {
                        throw new Error(`Error HTTP: ${response.status}`);
                    }

                    return response.json();

                })
                .then(data => {

                    // Respuesta exitosa
                    return {
                        success: true,
                        body: data
                    };

                })
                .catch(error => {

                    return {
                        success: false,
                        error: `Error en la petición: ${error.message}`
                    };

                });
        }

        export { fetchFakerData }

JS: Fetch con async/await
-------------------------

.. sidebar:: 

   .. image:: https://i0.wp.com/blog.codeanalogies.com/wp-content/uploads/2019/12/AsyncDiag3Fail.jpg
      
   Async/Await Explained By Doing Your Morning Routine de `blog.codeanalogies.com <https://blog.codeanalogies.com/2019/12/22/async-await-explained-by-doing-your-morning-routine/>`_.

1. Con un cliente de IAG, explique cómo se manejan operaciones asincrónicas (como las peticiones HTTP) con async/await.

2. En el documento *js/file01.js*, importe la función `fetchFakerData` del documento *functions.js*.

3. Utilice un cliente de IAG para generar el código en *js/file01.js*, de acuerdo con las siguientes especificaciones:

   a) Agregue la función flecha `loadData` asíncrona (async), que:

      (i) Declare una constante `url` con el valor de la URL de la API de Faker `https://fakerapi.it/api/v2/texts?_quantity=10&_characters=120`.
      
      (ii) Llame a la función `fetchFakerData` pasando la constante `url` como argumento.  Espere (await) la respuesta de la función `fetchFakerData`.
      
      (iii) En caso de éxito, muestre los datos en la consola. En caso de error, muestre el mensaje de error en la consola. Utilice las claves **success** y **body** o **error** del objeto devuelto por la función `fetchFakerData`.

   b) Llame a la función `loadData` en la función de autojecución.

   .. dropdown:: Ver la solución
    :color: success

    .. code-block:: javascript
        :emphasize-lines: 3, 7-26, 33

        'use strict';

        import { fetchFakerData } from './functions.js';

        ...	

        const loadData = async () => {

            const url = 'https://fakerapi.it/api/v2/texts?_quantity=10&_characters=120';

            try {
                const result = await fetchFakerData(url);

                if (result.success) {
                    console.log('Datos obtenidos con éxito:', result.body);
                } else {
                    console.error('Error al obtener los datos:', result.error);
                }

            } catch (error) {

                console.error('Ocurrió un error inesperado:', error);
            
            }

        };

        // Función de autoejecución
        (() => {

            ...
            
            loadData();
        })();

4. Compruebe la vista previa del resultado y la consola del navegador para verificar la ejecución del código.

JS: Carga de datos
------------------

1. Utilice un cliente de IAG en el documento *js/file01.js*, para:

   a) Crear una función flecha `renderCards` que recibe un arreglo de objetos. Los objetos tienen las claves **title**, **author**, **genre** y **content**.
   b) Esta función debe iterar sobre tres primeros elementos del arreglo de objetos, vaciar los valores de las claves en una plantilla card de TailwindCSS version 4 y :term:`renderizar` en el elemento HTML con el identificador **skeleton-container**. 
   c) Dentro de la función `loadData`, en caso de éxito llame a la función `renderCards` y envíe el `result.body.data`.  

2. Compruebe la vista previa del resultado y la consola del navegador para verificar la ejecución del código.

JSDoc
-----

1. Utilice un cliente de IAG en el documento javascript para generar la documentación JSDoc de las funciones creadas. Asegúrese de que los comentarios JSDoc incluyan descripciones, parámetros y tipos de retorno.
2. Valide su respuesta con `JSDoc: La Guía Definitiva para Documentar tu Código JavaScript <https://dev.to/goaqidev/jsdoc-la-guia-definitiva-para-documentar-tu-codigo-javascript-ik5>`_.

Versionamiento
--------------

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *landing*.
2. Genere la(s) solicitud(es) de cambios (pull request) para la rama principal y apruebe los cambios.

Vercel
------

1. Verifique el despliegue continuo (CD) del proyecto en Vercel.

Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Cómo te ayudó la inteligencia artificial generativa a entender el flujo de ejecución de una promesa en JavaScript?
    
    * ¿Cómo verificaste que el manejo de errores y la estructura de los then, catch y finally respondieran adecuadamente a diferentes escenarios de respuesta del servicio externo?
    
    * ¿Cómo puedes asegurar que el uso de inteligencia artificial para manejar peticiones asincrónicas no sustituya tu razonamiento lógico y tu comprensión del manejo de datos en tiempo real?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    Promesas en JavaScript

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">JavaScript&#39;s Fetch API: A Beginner’s Guide 🧵 <a href="https://t.co/K3EUdD72F5">pic.twitter.com/K3EUdD72F5</a></p>&mdash; Csaba Kissi (@csaba_kissi) <a href="https://twitter.com/csaba_kissi/status/1904169335121465653?ref_src=twsrc%5Etfw">March 24, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

    APIs públicas para probar	

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">Try Public APIs for free<a href="https://t.co/YKUy0OdgTA">https://t.co/YKUy0OdgTA</a></p>&mdash; SwiftUIX (@SwiftUIHome) <a href="https://twitter.com/SwiftUIHome/status/1917132347260211689?ref_src=twsrc%5Etfw">April 29, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
    
    Dataset original 

    Chinmay Shanbhag. (2022). BigBasket Products [Data set]. Kaggle. https://doi.org/10.34740/KAGGLE/DSV/4100336