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
2. Haga clic en el ícono de `Live Preview` en la barra de estado de VSCode para iniciar el servidor local.

Actividades en clases
=====================

Etiquetas multimedia
--------------------

1. Utilice un cliente de IAG para generar una recomendación del uso de etiquetas :term:`multimedia` en el documento *index.html*:

   a) Agregue un mapa de Google Maps.

   .. admonition:: Prompt sugerido

      Genera una etiqueta HTML para insertar un mapa de Google Maps en mi CV. 
      El mapa debe mostrar la ubicación de la Escuela Superior Politécnica del Litoral, Guayaquil - Ecuador, en la sección **contacto**.

   b) Añada una imagen con el placeholder de `Picsum <https://picsum.photos>`_ o `Placehold <https://placehold.co>`_.
   c) Incorpore un video de YouTube (incluya la URL).
         
2. Compruebe la vista previa del resultado en el navegador.
    
Etiquetas de formularios
------------------------

1. Utilice un cliente de IAG para generar una recomendación de el uso de etiquetas de :term:`formularios` en el documento *index.html*:

   a) Añada un formulario que al menos incluya un elemento para ingresar un texto en una línea, un elemento con una lista desplegable, un conjunto de opciones relacionadas, un vector de valores, un elemento para un área de texto y un botón para enviar el formulario. Todos los elementos son obligatorios. No utilice la etiqueta <br>.

2. Compruebe la vista previa del resultado en el navegador.

Etiquetas de semántica de texto
-------------------------------

1. Utilice un cliente de IAG para generar una recomendación de el uso de etiquetas de :term:`semántica de texto` en el documento *index.html*, con:
   
   a) Agregue un párrafo con un enlace a un sitio web. 
   b) Añada una lista ordenada de elementos.
   c) Incorpore una lista no ordenada de elementos.
   d) Agregue una tabla sin bordes, con al menos tres filas y tres columnas. La primera fila y la primera columna debe contener los encabezados de la tabla.

2. Utilice un cliente de IAG para generar una recomendación del uso de etiquetas contenedoras en el documento *index.html*, con:

   a) Agregue la sección referencias, que contenga al menos tres testimonios de personas para la que usted ha trabajado. Cada testimonio debe contener una frase, un párrafo con el nombre de la persona, su cargo y una breve descripción de su experiencia laboral con usted. Incluya la referencia en el menu de navegación.

3. Consulta a tu cliente de IAG la justificación de cada etiqueta contenedora.

   .. admonition:: Prompt sugerido

      Desarrolla la justificación para el uso de las etiquetas HTML [coloque aquí las etiquetas HTML].

4. Compruebe la vista previa del resultado en el navegador.

Versionamiento
--------------

1. Versione local y remotamente la(s) rama(s) de desarrollo en el repositorio *curriculum*.
2. Genere la(s) solicitud(es) de cambios (pull request) para la rama principal y apruebe los cambios.
3. Compruebe el resultado en el navegador.

Conclusiones
============

.. topic:: Preguntas de cierre

   * ¿Qué ventajas y riesgos observas al utilizar inteligencia artificial generativa para incorporar etiquetas de formularios, multimedia y texto semántico en la estructura de tu currículum HTML, en comparación con hacerlo de forma manual?
  
   * Si tuvieras que explicar tu proceso de integración de esas etiquetas a otro estudiante, ¿cómo justificarías cada decisión técnica tomada con base en las sugerencias de la IA y tus propios criterios?

   * ¿Cómo puedes asegurar que el resultado final del currículum vitae refleje tu diseño como desarrollador web, a pesar de haber utilizado inteligencia artificial en parte del proceso de codificación?


Actividades autónomas
=====================

Atributos HTML	
------------------------------

* Revisa los :term:`atributos` del `HTML Attributes <https://www.w3docs.com/learn-html/html-attributes.html>`_.

Embeber contenido multimedia
------------------------------

* En `¿Cómo insertar vídeos de YouTube en nuestra web (HTML)? <https://www.desarrollolibre.net/blog/html/como-insertar-videos-de-youtube-en-nuestra-web-html>`_ se encuentran las instrucciones sobre cómo embeber videos de YouTube.
* Revisa las instrucciones de `Cómo crear un mapa con Leaflet <https://mappinggis.com/2013/06/como-crear-un-mapa-con-leaflet/>`_ para aprender a embeber mapas.
* Para agregar una canción o un playlist de SoundCloud, revisa `Embedding a track or playlist <https://help.soundcloud.com/hc/en-us/articles/115003568008-Embedding-a-track-or-playlist>`_.

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">HTTP 1.0 -&gt; HTTP 1.1 -&gt; HTTP 2.0 -&gt; HTTP 3.0 (QUIC).<br><br>What problem does each generation of HTTP solve?<br><br>The diagram below illustrates the key features.<br><br>🔹HTTP 1.0 was finalized and fully documented in 1996. Every request to the same server requires a separate TCP connection.… <a href="https://t.co/V9uSXv0tvn">pic.twitter.com/V9uSXv0tvn</a></p>&mdash; Alex Xu (@alexxubyte) <a href="https://twitter.com/alexxubyte/status/1692560840853962987?ref_src=twsrc%5Etfw">August 18, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>