# XELSTIA - Earth Intelligence Platform

Este es el repositorio central del núcleo de inteligencia de XELSTIA. Este sistema procesa la telemetría satelital y la transforma en alertas de decisión accionables para múltiples industrias.

## Estructura del Repositorio

El proyecto sigue los principios de **Clean Architecture** (Arquitectura Limpia) y desacopla la lógica del negocio de los proveedores tecnológicos (LLMs, APIs de Clima, WhatsApp):

* `docs/`: Memoria técnica, contexto de negocio y pitch comercial del proyecto.
* `knowledge/`: Foso defensivo (moat) con umbrales, reglas de negocio e hipótesis de cada vertical.
* `src/core/`: Entidades de dominio y modelos de datos puros.
* `src/application/`: Casos de uso (workflows como detección, alertas y procesamiento de feedback).
* `src/infrastructure/`: Adaptadores externos (servicios GIS, LLM, proveedores de Clima y WhatsApp).
* `mocks/`: Set de datos satelitales simulados en formato GeoJSON para pruebas locales.

## Inicialización del Proyecto

1. Asegúrate de configurar tus variables de entorno en un archivo `.env` basándote en `.env.example`.
2. Para que las IAs y copilotos lean el contexto del proyecto al instante, consulta siempre `docs/context.md`.
