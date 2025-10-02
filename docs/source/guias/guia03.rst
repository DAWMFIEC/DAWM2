..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

=======================================================================
Guía 03: HTML - Etiquetas multimedia, formularios y semánticas de texto
=======================================================================

.. topic:: Objetivo específico
    :class: objetivo

    Usar etiquetas HTML en contenido interactivo y multimedia mediante el desarrollo de un currículum vitae digital para la presentación de información profesional de manera organizada y accesible en línea.

Actividades previas
=====================

Diseño
------

1. Decida el contenido de su CV para que incorpore un formulario, una imagen, un video y un mapa, considerando la recomendación para el :download:`diseño del contenido de un CV <./pdfs/guia03-disenocontenido.pdf>`.

2. Escoja las secciones en su documento *index.html* en las que colocará el formulario, la imagen, el video y el mapa.

Ambiente de desarrollo
----------------------

1. Acceda a su proyecto *curriculum* en Codespaces o en su máquina local.
2. :material-round:`note_alt;1.5em;sd-text-success` Revise la documentación para `crear o cambiar de rama <https://docs.github.com/es/codespaces/developing-in-a-codespace/using-source-control-in-your-codespace#crear-o-cambiar-de-rama>`_ en Codespaces.
3. Haga clic en el ícono de `Live Preview` en la barra de estado de VSCode para iniciar el servidor local.

Actividades en clases
=====================

Etiquetas multimedia
--------------------

1. Utilice un cliente de IAG para generar una recomendación del uso de etiquetas :term:`multimedia` en el documento *index.html*:

   a) Agregue un mapa de Google Maps.

   .. hint::

      Genera una etiqueta HTML para insertar un mapa de Google Maps en mi CV. 
      El mapa debe mostrar la ubicación de la Escuela Superior Politécnica del Litoral, Guayaquil - Ecuador, en la sección **contacto**.

   b) Añada una imagen con el placeholder de `Picsum <https://picsum.photos>`_ o `Placehold <https://placehold.co>`_.
   c) Incorpore un video de YouTube (incluya la URL).
         
2. Compruebe la vista previa del resultado en el navegador.
3. :material-round:`note_alt;1.5em;sd-text-success` Revise la documentación de `¿Cómo insertar vídeos de YouTube en nuestra web (HTML)? <https://www.desarrollolibre.net/blog/html/como-insertar-videos-de-youtube-en-nuestra-web-html>`_ y `Cómo crear un mapa con Leaflet <https://mappinggis.com/2013/06/como-crear-un-mapa-con-leaflet/>`_ mediante etiquetas HTML.
    
Etiquetas de formularios
------------------------

1. Utilice un cliente de IAG para generar una recomendación de el uso de etiquetas de :term:`formularios` en el documento *index.html*:

   .. info::
      
      El formulario debe incluir, al menos, un elemento para ingresar un texto en una línea, un elemento con una lista desplegable, un conjunto de opciones relacionadas, un vector de valores, un elemento para un área de texto y un botón para enviar el formulario. Todos los elementos son obligatorios. No utilice la etiqueta `<br>`.

2. Compruebe la vista previa del resultado en el navegador.
3. :material-round:`note_alt;1.5em;sd-text-success` Revise la documentación con los :term:`atributos` de los elementos HTML en `HTML Attributes <https://www.w3docs.com/learn-html/html-attributes.html>`_.

Etiquetas de semántica de texto
-------------------------------

1. Utilice un cliente de IAG para generar una recomendación de el uso de etiquetas de :term:`semántica de texto` en el documento *index.html*. El documento debe incluir:

   a) Un párrafo con un enlace a un sitio web. 
   b) Una lista ordenada de elementos.
   c) Una lista no ordenada de elementos.
   d) Una tabla sin bordes, con al menos tres filas y tres columnas. La primera fila y la primera columna debe contener los encabezados de la tabla.

2. Utilice un cliente de IAG para generar una recomendación del uso de etiquetas contenedoras en el documento *index.html*. El documento, en la sección referencias, debe contener, al menos, tres testimonios de personas para la que usted ha trabajado. Cada testimonio debe contener una frase, un párrafo con el nombre de la persona, su cargo y una breve descripción de su experiencia laboral con usted. Incluya la referencia en el menu de navegación.

3. Consulta a tu cliente de IAG la justificación de cada etiqueta contenedora.

   .. admonition:: Prompt sugerido

      Desarrolla la justificación para el uso de las etiquetas HTML [coloque aquí las etiquetas HTML] en un documento HTML relacionado con un curriculum vitae digital.

4. Compruebe la vista previa del resultado en el navegador.

Versionamiento
--------------

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *curriculum*.
2. :material-round:`note_alt;1.5em;sd-text-success` Revise la documentación para `levantar una solicitud de cambios <https://docs.github.com/es/codespaces/developing-in-a-codespace/using-source-control-in-your-codespace#levantar-una-solicitud-de-cambios>`_ en Codespaces.
3. Compruebe el resultado en el navegador.

Conclusiones
============

.. topic:: Preguntas de cierre

   * ¿Qué ventajas y riesgos observas al utilizar inteligencia artificial generativa para incorporar etiquetas de formularios, multimedia y texto semántico en la estructura de tu currículum HTML, en comparación con hacerlo de forma manual?
  
   * Si tuvieras que explicar tu proceso de integración de esas etiquetas a otro estudiante, ¿cómo justificarías cada decisión técnica tomada con base en las sugerencias de la IA y tus propios criterios?

   * ¿Cómo puedes asegurar que el resultado final del currículum vitae refleje tu diseño como desarrollador web, a pesar de haber utilizado inteligencia artificial en parte del proceso de codificación?


Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">HTTP 1.0 -&gt; HTTP 1.1 -&gt; HTTP 2.0 -&gt; HTTP 3.0 (QUIC).<br><br>What problem does each generation of HTTP solve?<br><br>The diagram below illustrates the key features.<br><br>🔹HTTP 1.0 was finalized and fully documented in 1996. Every request to the same server requires a separate TCP connection.… <a href="https://t.co/V9uSXv0tvn">pic.twitter.com/V9uSXv0tvn</a></p>&mdash; Alex Xu (@alexxubyte) <a href="https://twitter.com/alexxubyte/status/1692560840853962987?ref_src=twsrc%5Etfw">August 18, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>