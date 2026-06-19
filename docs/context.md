# XELSTIA - Contexto Estratégico y de Producto

Este documento funciona como la memoria organizacional y el contexto para cualquier modelo de IA o desarrollador que trabaje en la plataforma de XELSTIA.

---

## 1. La Visión del Producto
> "XELSTIA captura la realidad física del planeta. Nosotros construimos la capa de inteligencia que transforma esa realidad en decisiones automáticas."

No vendemos imágenes, sensores ni mapas de colorcitos. Vendemos **reducción de pérdidas** y **mitigación de riesgos**. El valor se percibe cuando el cliente recibe una alerta directa en su flujo de trabajo (ej. WhatsApp) y puede tomar una acción correctora antes de perder capital.

---

## 2. El Foso Defensivo (The Moat): El Dataset Propietario
El verdadero valor a largo plazo de XELSTIA no está en el código (FastAPI, LLM o Twilio son commodities). El activo estratégico insustituible es el **feedback de campo (Ground Truth)**.

### El Ciclo de Retroalimentación:
1. **Alerta:** Enviamos una alerta de anomalía foliar/hídrica al celular del cliente.
2. **Acción/Feedback:** El cliente responde en WhatsApp confirmando o rechazando la alerta:
   * `"Sí, era Arañuela Roja."`
   * `"No, fue un reflejo de luz por riego."`
3. **Activo:** Guardamos esta respuesta etiquetada junto a los metadatos satelitales en nuestro almacén de conocimiento.
4. **Resultado:** Con miles de hectáreas monitoreadas, construimos el **primer dataset geoespacial de validación real en LATAM**, haciendo nuestros modelos predictivos imposibles de replicar por competidores que solo tienen "fotos espaciales".

---

## 3. Arquitectura del Proyecto (Clean Architecture)

Aislamos la lógica pura de negocio de las tecnologías de infraestructura y el conocimiento específico de cada vertical:

```text
xelstia/
├── docs/                      # Memoria del proyecto
│   ├── context.md             # Visión, glosario y negocio (Este archivo)
│   ├── presentation.md        # Pitch comercial y modelos de negocio
│   └── architecture.md        # Diagramas de secuencia y flujo de datos
├── knowledge/                 # El cerebro y reglas de las verticales (El Moat)
│   ├── agriculture/           # Umbrales NDVI/NDWI, patrones de plagas
│   ├── insurance/             # Reglas de siniestralidad, inundaciones
│   └── energy/                # Riesgos de vegetación y activos
├── src/                       # Código de producción
│   ├── core/                  # Entidades de dominio y reglas de negocio puras
│   ├── application/           # Workflows de caso de uso (Detección, Alerta, Feedback)
│   └── infrastructure/        # LLM (infraestructura), GIS, WhatsApp, DB, Clima
├── mocks/                     # Datos satelitales falsos para testeo local
├── README.md                  # Guía de onboarding y ejecución
└── requirements.txt           # Dependencias
```

* **LLM como Infraestructura:** La IA que redacta las alertas vive en `infrastructure/llm/`. Si cambiamos de proveedor (OpenAI a Claude o local), el core de la aplicación no se entera.
* **Knowledge como Entrada:** El conocimiento de agronomía o seguros vive en `knowledge/`. Alimenta los prompts y las reglas de negocio del orquestador de manera desacoplada.
