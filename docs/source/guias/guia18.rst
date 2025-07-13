..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

=========================================
Guía 18: React - Cliente de IA generativa
=========================================

.. topic:: Objetivo específico
    :class: objetivo

    Integrar el servicio de procesamiento de lenguaje natural en el dashboard para generar descripciones automatizadas, recomendaciones o resúmenes interpretativos de los datos climáticos en tiempo real

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

1. Obtenga una cuenta `Cohere <https://cohere.com/>`_ y cree un proyecto.
2. Obtenga el token de acceso a la `API Keys <https://dashboard.cohere.com/api-keys>`_ de Cohere.
3. Instale el paquete de `Cohere-AI <https://www.npmjs.com/package/cohere-ai>`_ en su proyecto React:

   .. code-block:: bash

      npm install cohere-ai

4. Cree el componente ``CohereAssistant`` en `src/functions/CohereAssistant.tsx`, considerando la documentación `Working with Cohere's API and SDK <https://docs.cohere.com/reference/about>`_.
5. Utilice el componente ``CohereAssistant`` en su dashboard para enviar consultas al modelo de lenguaje y recibir respuestas relacionadas con el clima. Asegúrese de manejar adecuadamente las respuestas, especialmente si son ambiguas o extensas.

Conclusiones
============

.. topic:: Preguntas de cierre

    * ¿Qué conceptos sobre procesamiento de lenguaje natural y consumo de APIs de modelos de lenguaje identificaste como esenciales para la correcta integración del asistente climático, y cómo los complementaste con la información proporcionada por la IA generativa?

    * ¿Cómo garantizaste que el flujo de datos entre el usuario, el asistente del clima (Cohere) y la interfaz del dashboard fuera eficiente y coherente, especialmente considerando posibles respuestas ambiguas o extensas?

    * ¿Qué reflexiones éticas surgen al integrar una IA generativa como Cohere en un dashboard que proporciona recomendaciones sobre el clima, y cómo aseguras la responsabilidad sobre la información que se muestra al usuario?

Actividades autónomas
=====================

Recursos extras
------------------------------

En redes:

.. raw:: html

    <blockquote class="twitter-tweet"><p lang="en" dir="ltr">Benchmarks are a vital part of successful AI adoption for enterprises. But how do you choose the right benchmarks? And how do you build a real-world evaluation suite?<br><br>Read our latest article from Cohere experts Neeral Beladia and Alex Wang to learn more about AI benchmarks for… <a href="https://t.co/6QUeqdGXpM">pic.twitter.com/6QUeqdGXpM</a></p>&mdash; cohere (@cohere) <a href="https://twitter.com/cohere/status/1942612997945381352?ref_src=twsrc%5Etfw">July 8, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>