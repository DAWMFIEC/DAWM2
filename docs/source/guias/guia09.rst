..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

====================================
Guía 09: Promesas, Servicios y JSON 
====================================

.. topic:: Objetivo específico
    :class: objetivo

    Implementar funciones en JavaScript que consuman servicios externos utilizando promesas para la recuperación y presentación de datos en formato JSON y XML en la landing page.

Actividades previas
=====================

HTTP: Requerimientos y respuestas
----------------------------------

1. Visite el sitio web de `ReqBin <https://reqbin.com/>`_.
2. Realice las siguientes peticiones HTTP, p.e.:
   
   a) Petición GET de los productos:

      - **URL:** `https://data-dawm.github.io/datum/reseller/products.json`
      - **Método:** `GET`
    
   b) Petición GET de las categorías:

      - **URL:** `https://data-dawm.github.io/datum/reseller/categories.xml`
      - **Método:** `GET`

3. Explore la :term:`petición HTTP` y la :term:`respuesta HTTP` en la interfaz.
4. Utilice un cliente de IAG para explicar cómo se estructura la petición y la respuesta de la API; además de los formatos :term:`JSON` y :term:`XML`.

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

1. En el documento *index.html*, agregue una sección para mostrar los datos obtenidos de los productos y sus categorías.

   .. dropdown:: Ver el código 
    :color: primary
    
    .. code-block:: html
        :emphasize-lines: 3-59
    
        <section class="bg-slate-50 dark:bg-gray-900"> ... </section>
        
        <section class="bg-slate-50 dark:bg-gray-900">

            <div id="container-05" class="px-4 pt-8 mx-auto max-w-md md:max-w-xl">
                <div class="grid grid-cols-1 gap-4 md:grid-cols-1">
                    <h2 class="text-4xl font-extrabold tracking-tight text-gray-900 dark:text-white text-center">Productos más
                    vendidos</h2>
                </div>
            </div>

            <div id="container-06" class="max-w-4xl pt-8 mx-auto">
                <form class="max-w-sm mx-auto">
                    <select id="categories"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                    <option selected>Seleccione una categoría</option>
                    <option value="1">Category01</option>
                    <option value="2">Category02</option>
                    <option value="3">Category03</option>
                    </select>
                </form>
            </div>

            <div id="container-07" class="max-w-4xl pt-5 pb-5 mx-auto">
                <div id="products-container" class="grid grid-cols-1 md:grid-cols-3 gap-3 p-6">

                    <!-- Products Card -->
                    <div class="animate-pulse space-y-4 bg-white dark:bg-gray-800 p-4 rounded-2xl shadow">
                        <div class="w-full h-40 bg-gray-300 dark:bg-gray-700 rounded-lg"></div>
                        <div class="h-6 bg-gray-300 dark:bg-gray-700 rounded w-3/4"></div>
                        <div class="h-5 bg-gray-300 dark:bg-gray-700 rounded w-1/2"></div>
                        <div class="space-y-2">
                            <div class="h-6 bg-gray-300 dark:bg-gray-700 rounded w-full"></div>
                        </div>
                    </div>

                    <!-- Products Card -->
                    <div class="animate-pulse space-y-4 bg-white dark:bg-gray-800 p-4 rounded-2xl shadow">
                        <div class="w-full h-40 bg-gray-300 dark:bg-gray-700 rounded-lg"></div>
                        <div class="h-6 bg-gray-300 dark:bg-gray-700 rounded w-3/4"></div>
                        <div class="h-5 bg-gray-300 dark:bg-gray-700 rounded w-1/2"></div>
                        <div class="space-y-2">
                            <div class="h-6 bg-gray-300 dark:bg-gray-700 rounded w-full"></div>
                        </div>
                    </div>

                    <!-- Products Card -->
                    <div class="animate-pulse space-y-4 bg-white dark:bg-gray-800 p-4 rounded-2xl shadow">
                        <div class="w-full h-40 bg-gray-300 dark:bg-gray-700 rounded-lg"></div>
                        <div class="h-6 bg-gray-300 dark:bg-gray-700 rounded w-3/4"></div>
                        <div class="h-5 bg-gray-300 dark:bg-gray-700 rounded w-1/2"></div>
                        <div class="space-y-2">
                            <div class="h-6 bg-gray-300 dark:bg-gray-700 rounded w-full"></div>
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

1. Dentro de la carpeta *js*, cree el documento javascript *functions.js*. Declare el modo estricto del documento. 
2. Escribe una función llamada `fetchProducts` que reciba un parámetro `url`, con las siguientes instrucciones:

   .. note::

      :material-round:`note_alt;1.5em;sd-text-success` Tome como referencia `How to fetch json in JavaScript <https://codetogo.io/how-to-fetch-json-in-javascript/>`_ crear el objeto fetch.

   a) Dentro de la función, utiliza la palabra clave **return** para devolver el resultado de `fetch(url)`.
   b) Agregue el primer bloque `.then(response => { /*  bloque then - 1 */ })`. Dentro del *bloque then - 1*, realice lo siguiente:
   
      i) Usa la estructura if con la condición **!response.ok** para lanzar un error con `throw new Error("Error HTTP: "+response.status)`.
      ii) Caso contrario, si la respuesta es correcta, retorne `response.json()` para procesar los datos.

   c) Agregue el segundo bloque `.then(data => { /* bloque then - 2 */ })`. Dentro del *bloque then - 2*, retorne un objeto con las claves **success** (valor true) y **body** (contenido de data).
   d) Agregue el bloque `catch(error => { /* bloque catch */ })`. Dentro del *bloque catch*, retorne un objeto con las claves **success** (valor false) y **body** (mensaje de error `\`"${error.message}"\``).

   .. dropdown:: Ver la solución
    :color: success

    .. code-block:: javascript
        
        'use strict';

        let fetchProducts =  (url) => {

            return fetch(url)
                .then(response => {

                    // Verificar si la respuesta no es exitosa
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

                    // Error en la solicitud
                    return {
                        success: false,
                        body: `"${error.message}"`
                    };

                });
        }

        export { fetchProducts }

3. Exporte la función `fetchProducts`.

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