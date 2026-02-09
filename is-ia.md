# IS-IA: Ingeniería de Software en la Era de la IA

*Prácticas, metodologías y transformaciones para construir software de calidad
cuando la inteligencia artificial participa activamente en cada etapa del desarrollo.*

---

## Tabla de contenidos

1. [Introducción: el punto de inflexión](#1-introducción-el-punto-de-inflexión)
2. [Revisión sistemática de la literatura](#2-revisión-sistemática-de-la-literatura)
3. [Estudio de factibilidad](#3-estudio-de-factibilidad)
4. [Requerimientos: elicitación, análisis y especificación](#4-requerimientos-elicitación-análisis-y-especificación)
5. [Diseño](#5-diseño)
6. [Implementación](#6-implementación)
7. [Testing](#7-testing)
8. [Despliegue y operaciones](#8-despliegue-y-operaciones)
9. [Evolución y mantenimiento](#9-evolución-y-mantenimiento)
10. [El nuevo profesional del software](#10-el-nuevo-profesional-del-software)
11. [Conclusiones](#11-conclusiones)
12. [Referencias](#12-referencias)

---

## 1. Introducción: el punto de inflexión

> [!IMPORTANT]
> *La ingeniería de software no desaparece cuando la IA escribe código — se vuelve más necesaria que nunca. Lo que cambia es dónde se aplica.*

### 1.1. Del asistente al implementador

El desarrollo de software es una disciplina que involucra diversas etapas:
desde la obtención de requerimientos, la planificación y el diseño, hasta la
implementación, las pruebas y el mantenimiento del producto [1]. Durante
décadas, cada avance tecnológico optimizó alguna de estas fases — los IDEs
mejoraron la implementación, los frameworks aceleraron el diseño, las
herramientas de CI/CD automatizaron el despliegue. Pero ningún avance previo
había impactado **todas las etapas simultáneamente**.

La inteligencia artificial generativa — y en particular los modelos de
lenguaje de gran tamaño (LLMs) y los agentes autónomos — representa un punto
de inflexión sin precedentes. No se trata de una herramienta que mejora una
etapa específica del ciclo de vida. Se trata de una tecnología que puede
participar activamente en **cada fase del proceso**, desde la elicitación de
requerimientos hasta el monitoreo en producción.

```
2018          2021          2022          2024          2026
 │             │             │             │             │
 ▼             ▼             ▼             ▼             ▼

Tabnine      Copilot       ChatGPT     Agentes IA     IA en
"sugerí"    "completá"    "conversá"   "resolvé"     todo el
                                                      SDLC
 │             │             │             │             │
 └──────┬──────┘      ┌─────┘             │             │
        │             │                   │             │
 La IA predice   La IA genera      La IA planifica,  La IA participa
 la siguiente    funciones         ejecuta, testea   en CADA etapa
 palabra         completas         y corrige sola    del desarrollo
```

En 2024, un trabajo presentado en el XXX Congreso Argentino de Ciencias de la
Computación demostró la viabilidad de usar LLMs en las etapas de elicitación
y análisis de requerimientos, comparando siete modelos de lenguaje en la
generación de entrevistas y la especificación de historias de usuario [2]. Los
resultados fueron reveladores: la mayoría de los modelos produjeron resultados
aceptables a satisfactorios, evidenciando que la IA no solo puede escribir
código, sino también participar en las etapas más tempranas y conceptuales del
desarrollo de software.

Este documento extiende esa investigación a **todo el ciclo de vida del
software**. No como un ejercicio teórico, sino como una formalización de
prácticas reales — algunas ya consolidadas en la industria, otras emergentes,
y algunas que proponemos a partir de la experiencia profesional en desarrollo
de software y la evidencia empírica disponible.

### 1.2. Lo que este documento no es

No es un catálogo de herramientas. Las herramientas cambian cada semana — lo
que hoy es Copilot mañana será otra cosa. Lo que no cambia tan rápido son los
**principios** sobre los cuales se construye software de calidad:
especificación precisa, diseño coherente, validación rigurosa, despliegue
controlado y evolución sostenible.

Tampoco es una apología de la automatización total. La premisa central es que
la IA amplifica las capacidades del profesional de software, pero no elimina
la necesidad de juicio crítico, experiencia de dominio y responsabilidad
profesional.

### 1.3. Alcance y enfoque

Este documento recorre cada etapa del ciclo de vida del desarrollo de
software (SDLC) y para cada una analiza:

- **El estado actual**: qué puede hacer la IA hoy, con evidencia concreta.
- **Las prácticas recomendadas**: cómo integrar la IA de manera efectiva,
  manteniendo calidad y control.
- **Los riesgos y limitaciones**: qué puede salir mal y cómo mitigarlo.
- **El rol del profesional**: qué cambia en las responsabilidades humanas.

```
┌─────────────────────────────────────────────────────────────────┐
│                    CICLO DE VIDA DEL SOFTWARE                   │
│                      CON IA INTEGRADA                           │
│                                                                 │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐       │
│  │Factibili-│→ │Requeri-  │→ │          │→ │Implemen- │       │
│  │dad       │  │mientos   │  │  Diseño  │  │tación    │       │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘       │
│       │             │             │             │               │
│       ▼             ▼             ▼             ▼               │
│   IA analiza    IA elicita    IA propone    IA genera          │
│   viabilidad    y especifica  arquitectura  código             │
│                                                                 │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐       │
│  │          │→ │Despliegue│→ │Evolución │→ │Manteni-  │       │
│  │ Testing  │  │          │  │          │  │miento    │       │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘       │
│       │             │             │             │               │
│       ▼             ▼             ▼             ▼               │
│   IA testea     IA despliega  IA detecta    IA monitorea      │
│   y valida      y monitorea   deuda técnica y corrige         │
│                                                                 │
│  ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─   │
│   EL PROFESIONAL: supervisa, decide, valida, asume            │
│   responsabilidad en CADA etapa                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

La orientación es **profesional y práctica**. Cada sección se respalda con
evidencia académica y datos de la industria, pero el objetivo final es que un
equipo de desarrollo pueda tomar estas prácticas y aplicarlas en su trabajo
diario.

La sección 2 presenta una **revisión sistemática de la literatura** siguiendo
la metodología de Kitchenham [3], que constituye la base empírica sobre la
cual se construyen las recomendaciones prácticas de las secciones 3-10.

---

## 2. Revisión sistemática de la literatura

> [!IMPORTANT]
> *Esta revisión sigue la metodología de Kitchenham para revisiones sistemáticas en ingeniería de software [3], organizada en tres fases: planificación, conducción y documentación.*

### 2.1. Motivación y necesidad de la revisión

La aplicación de IA generativa al desarrollo de software es un campo que
evoluciona con velocidad sin precedentes. Entre 2022 y 2026, la investigación
ha crecido de manera explosiva — solo en testing con LLMs, la producción
académica pasó de 1 paper en 2021 a 73 en 2024 [4]. Esta velocidad genera
un problema: la evidencia está fragmentada, a veces contradictoria, y
frecuentemente mezclada con afirmaciones de marketing sin respaldo empírico.

Una revisión sistemática de la literatura (SLR) permite:
- Identificar, evaluar y sintetizar la evidencia disponible de manera
  rigurosa y reproducible.
- Distinguir hallazgos con respaldo empírico sólido de afirmaciones
  anecdóticas o promocionales.
- Detectar contradicciones y brechas en el conocimiento actual.
- Proveer una base fundamentada para las recomendaciones prácticas que
  constituyen el cuerpo principal de este documento.

### 2.2. Protocolo de revisión

#### 2.2.1. Preguntas de investigación

Se definieron cinco preguntas de investigación (RQs) que cubren las
dimensiones fundamentales del impacto de la IA en el desarrollo de software:

| RQ | Pregunta | Dimensión |
|----|----------|-----------|
| **RQ1** | ¿Cuál es el estado actual de la aplicación de IA generativa (LLMs y agentes) en cada etapa del SDLC (2022-2026)? ¿Qué capacidades han sido demostradas empíricamente y qué limitaciones persisten? | Estado del arte por fase |
| **RQ2** | ¿Cuál es el impacto medible de la IA en la calidad, seguridad y mantenibilidad del software producido? | Calidad y seguridad |
| **RQ3** | ¿Cuál es el efecto real de las herramientas de IA en la productividad de los desarrolladores, y en qué medida coincide la productividad percibida con la medida? | Productividad |
| **RQ4** | ¿Cómo se está transformando el rol del profesional de software y qué competencias emergentes son requeridas? | Rol profesional |
| **RQ5** | ¿Qué marcos metodológicos y prácticas han surgido para integrar la IA de manera sistemática en el SDLC, preservando calidad, seguridad y control? | Frameworks y metodologías |

#### 2.2.2. Estrategia de búsqueda

**Bases de datos académicas:** IEEE Xplore, ACM Digital Library, Springer
Link, ScienceDirect, Wiley, arXiv, MDPI, Frontiers, Google Scholar.

**Fuentes de industria (grey literature):** Gartner, Forrester, Stack
Overflow Survey, JetBrains Developer Ecosystem, GitHub Octoverse/Research,
Microsoft Research.

**Período:** enero 2022 — febrero 2026.

**Idiomas:** inglés y español.

**Strings de búsqueda:** combinaciones de ("LLM" OR "generative AI" OR "AI
agent" OR "AI coding assistant") AND ("software development" OR "SDLC" OR
"software engineering"), con refinamientos específicos por fase del SDLC.

**Snowballing:** forward y backward desde papers clave: Jimenez et al./
SWE-bench [5], Peng et al./Copilot [6], METR [7], Liu et al./agents survey
[8], Wang et al./testing survey [4].

#### 2.2.3. Criterios de inclusión y exclusión

**Criterios de inclusión:**
- IC1: Estudios que evalúan empíricamente o revisan sistemáticamente IA/LLMs
  en al menos una fase del SDLC.
- IC2: Publicados entre enero 2022 y febrero 2026.
- IC3: Publicados en venues peer-reviewed o arXiv con citas subsecuentes.
- IC4: Reportes de industria de organizaciones reconocidas con metodología
  documentada.
- IC5: Proveen datos cuantitativos o análisis cualitativo sistemático.
- IC6: Escritos en inglés o español.

**Criterios de exclusión:**
- EC1: IA/ML general sin aplicación específica a procesos de desarrollo.
- EC2: Piezas de opinión o blogs sin respaldo empírico (excepción: frameworks
  con adopción significativa, clasificados como grey literature).
- EC3: Enfocados exclusivamente en entrenamiento/arquitectura de modelos sin
  aplicación a ingeniería de software.
- EC4: Estudios duplicados o supersedidos por publicaciones posteriores de los
  mismos autores.
- EC5: Preprints arXiv >6 meses con <5 citas y sin validación empírica.

#### 2.2.4. Evaluación de calidad

**Para estudios académicos** (score 0/0.5/1 por criterio, máximo 7):

| # | Criterio |
|---|----------|
| QA1 | ¿Los objetivos de investigación están claramente definidos? |
| QA2 | ¿El diseño del estudio es apropiado para las preguntas de investigación? |
| QA3 | ¿El método de recolección de datos está adecuadamente descrito? |
| QA4 | ¿El tamaño de muestra/dataset es adecuado? |
| QA5 | ¿Se discuten amenazas a la validez? |
| QA6 | ¿Los hallazgos están soportados por los datos presentados? |
| QA7 | ¿El estudio es reproducible con la información provista? |

**Para reportes de industria** (score 0/0.5/1, máximo 4):

| # | Criterio |
|---|----------|
| QI1 | ¿La metodología está claramente descrita? |
| QI2 | ¿El tamaño de muestra/cobertura es adecuado? |
| QI3 | ¿La organización/publisher es reconocida en el campo? |
| QI4 | ¿Los hallazgos son consistentes con otras fuentes independientes? |

**Umbral:** estudios académicos con score <3/7 o reportes de industria <2/4
se excluyen o se reportan con caveats explícitos.

**Clasificación de fortaleza de evidencia:**
- **Fuerte:** múltiples experimentos controlados con resultados convergentes.
- **Moderada:** case studies + surveys con resultados consistentes.
- **Emergente:** estudio único o grey literature sin replicación.

#### 2.2.5. Extracción de datos

Para cada estudio incluido se extrajeron:

- **Datos bibliográficos:** autor(es), año, título, venue, tipo, DOI/URL.
- **Clasificación:** fase(s) del SDLC, metodología de investigación,
  herramientas/modelos IA evaluados.
- **Datos cuantitativos:** tamaño de muestra, métricas clave, tamaños de
  efecto, significancia estadística.
- **Datos cualitativos:** hallazgos clave, limitaciones reconocidas,
  dimensión de impacto (RQ abordada).
- **Score de calidad** según los criterios definidos en §2.2.4.

**Estrategia de síntesis:** síntesis narrativa con tabulación cuantitativa,
tablas resumen por fase del SDLC, análisis cruzado por RQ, y resolución de
contradicciones presentando ambos lados con assessment de calidad comparativo.

### 2.3. Resultados de la búsqueda

#### 2.3.1. Proceso de selección (diagrama PRISMA)

```
┌─────────────────────────────────────────────────────────┐
│                    IDENTIFICACIÓN                        │
│                                                          │
│  Fuentes existentes en          Búsqueda sistemática     │
│  investigacion/ + is-ia.md      en bases de datos         │
│        (n = 117)                    (n = 89)              │
│              │                        │                   │
│              └───────────┬────────────┘                   │
│                          ▼                                │
│               Total identificados                         │
│                    (n = 206)                               │
├──────────────────────────────────────────────────────────┤
│                     SCREENING                             │
│                                                          │
│  Duplicados removidos (n = 74)                            │
│                          ▼                                │
│              Screened por título/abstract                  │
│                    (n = 132)                               │
│                          │                                │
│  Excluidos por IC/EC (n = 41)                             │
│  • EC1 - IA general sin aplicación a SE (n = 14)          │
│  • EC3 - Solo arquitectura de modelos (n = 9)             │
│  • EC2 - Opinión sin evidencia (n = 8)                    │
│  • EC5 - Preprints sin impacto (n = 6)                    │
│  • EC4 - Supersedidos (n = 4)                             │
├──────────────────────────────────────────────────────────┤
│                    ELEGIBILIDAD                           │
│                                                          │
│              Texto completo evaluado                      │
│                    (n = 91)                                │
│                          │                                │
│  Excluidos tras lectura completa (n = 14)                 │
│  • Datos insuficientes para responder RQs (n = 6)         │
│  • Calidad bajo umbral (n = 5)                            │
│  • No verificable (URL/DOI inaccesible) (n = 3)           │
├──────────────────────────────────────────────────────────┤
│                     INCLUIDOS                             │
│                                                          │
│          Estudios incluidos en la síntesis                │
│                    (n = 77)                                │
│                                                          │
│  ┌────────────────────┬──────────────────────────┐       │
│  │ Académicos (n = 48)│ Industria/grey (n = 29)  │       │
│  └────────────────────┴──────────────────────────┘       │
└─────────────────────────────────────────────────────────┘
```

#### 2.3.2. Descripción de los estudios incluidos

De los 77 estudios incluidos:

| Tipo de fuente | Cantidad | Porcentaje |
|----------------|----------|------------|
| Papers en conferencia/journal peer-reviewed | 32 | 41.6% |
| Preprints arXiv con impacto demostrado | 16 | 20.8% |
| Surveys/reports de industria | 18 | 23.4% |
| Systematic reviews/surveys académicas | 8 | 10.4% |
| Grey literature con adopción significativa | 3 | 3.9% |

**Metodologías predominantes:**

| Metodología | Estudios |
|-------------|----------|
| Experimento controlado / RCT | 6 |
| Análisis cuantitativo (dataset/benchmark) | 18 |
| Systematic review / mapping study | 12 |
| Survey a gran escala | 11 |
| Case study / experiencia industrial | 9 |
| Propuesta metodológica con evaluación | 8 |
| Análisis de repositorios (mining) | 7 |
| Reporte de industria con metodología | 6 |

#### 2.3.3. Distribución temporal y por fase del SDLC

```
Publicaciones por año:

2022  ██ (3)
2023  ████ (6)
2024  ██████████████████████████████ (31)
2025  ████████████████████████████████████ (34)
2026  ██ (3)

Cobertura por fase del SDLC:

Implementación/Coding  ████████████████████ 26 estudios
Testing                ██████████████ 16 estudios
Calidad/Seguridad      ██████████ 12 estudios
Evolución/Manten.      ████████ 10 estudios
Requerimientos         ████████ 9 estudios
Diseño/Arquitectura    ███████ 8 estudios
Transversal/SDLC       ██████ 7 estudios
Factibilidad/Estim.    █████ 6 estudios
Despliegue/DevOps      ███ 4 estudios
Gestión de proyectos   ███ 4 estudios
```

**Observación:** la implementación y el testing concentran la mayor parte de
la investigación (54.5%), mientras que el despliegue/DevOps y la gestión de
proyectos están significativamente subrepresentados. Esta distribución refleja
tanto la madurez relativa de las herramientas como el sesgo de publicación
hacia las fases más visibles del SDLC.

### 2.4. Hallazgos por etapa del SDLC (RQ1)

> *RQ1: ¿Cuál es el estado actual de la aplicación de IA generativa en cada
> etapa del SDLC? ¿Qué capacidades han sido demostradas empíricamente y qué
> limitaciones persisten?*

#### 2.4.1. Estudio de factibilidad y estimación

**Evidencia: Emergente (6 estudios)**

La aplicación de LLMs a la estimación de esfuerzo y costo es un área
incipiente pero con resultados prometedores. Lopez-Martin et al. [9]
demostraron que GPT-3.5 fine-tuneado con el dataset ISBSG puede mejorar la
precisión de las estimaciones de costo y duración, aunque los resultados son
inconsistentes entre proyectos. Cabrera-Diego et al. [10] mapearon 30
estudios primarios sobre LLMs en estimación temprana, identificando un pico
de publicaciones en 2024 (11 estudios).

El framework SEEAgent de Bui [11] propone un sistema multi-agente para
estimación ágil, mientras que Hasnain et al. [12] abordan los desafíos de
estimar esfuerzo cuando se incluyen interfaces basadas en LLMs en el diseño.

Un hallazgo preocupante proviene del LLM Risk Assessment Framework [13]:
aproximadamente el 50% de los outputs de ChatGPT para análisis de riesgo
requieren corrección experta, evidenciando fallos sistemáticos en la
precisión de estimación de riesgos.

| Capacidad demostrada | Evidencia | Limitación |
|---------------------|-----------|------------|
| Estimación de costo con fine-tuning | Moderada [9] | Resultados inconsistentes entre dominios |
| Estimación ágil multi-agente | Emergente [11] | Sin validación a gran escala |
| Análisis de riesgo | Emergente [13] | 50% requiere corrección experta |
| Modelos híbridos (LLM + tradicional) | Emergente [10] | Superan a cada enfoque individual |

#### 2.4.2. Requerimientos

**Evidencia: Moderada (9 estudios)**

La investigación en requerimientos asistidos por IA es más madura. Panigo
et al. [2] evaluaron siete LLMs en generación de entrevistas e historias de
usuario, demostrando resultados aceptables a satisfactorios en la mayoría de
los modelos. Sami et al. [14] propusieron un sistema multi-agente para
elicitación y análisis de requerimientos con resultados empíricos positivos.

Gonzalez et al. [15] evaluaron 10 LLMs de última generación para generación
automática de historias de usuario, encontrando que los LLMs igualan la
cobertura y calidad estilística humana pero exhiben **menor diversidad y
creatividad**. El framework Elicitron de Zhao et al. [16] utiliza agentes
LLM para simular usuarios en procesos de elicitación de diseño.

Una revisión sistemática publicada en Frontiers [17] encontró que los modelos
basados en GPT dominan el 90% de la investigación en ingeniería de
requerimientos con LLMs, con zero-shot prompting utilizado en el 44% de los
estudios y few-shot en el 29%.

| Capacidad demostrada | Evidencia | Limitación |
|---------------------|-----------|------------|
| Generación de entrevistas | Moderada [2] | Calidad variable entre modelos |
| Historias de usuario | Moderada [2][15] | Menor diversidad/creatividad que humanos |
| Sistema multi-agente para RE | Emergente [14] | Validación limitada |
| Simulación de usuarios | Emergente [16] | Sin validación a escala |
| Evaluación de calidad de HU | Moderada [15] | Funciona con criterios claros |

#### 2.4.3. Diseño y arquitectura

**Evidencia: Emergente (8 estudios)**

El diseño arquitectónico con IA es un área relativamente subexplorada
comparada con la implementación. Galster et al. [18] realizaron una revisión
sistemática analizando 18 artículos, encontrando un crecimiento pronunciado
en 2024 (10 artículos) tras una producción mínima antes de 2023. El 73% de
los modelos utilizados son decoder-only (GPT, Llama, DeepSeek).

La investigación abarca desde la generación de decisiones arquitectónicas
(ADDs) usando RAG y fine-tuning [19], la transformación de requerimientos en
lenguaje natural a diseños arquitectónicos [20], hasta la detección de
antipatrones de elasticidad [21] y smells arquitectónicos [22] usando LLMs.

| Capacidad demostrada | Evidencia | Limitación |
|---------------------|-----------|------------|
| Generación de ADDs con RAG | Emergente [19] | Validación en pocos proyectos |
| Detección de antipatrones | Emergente [21][22] | Sin benchmarks estandarizados |
| NL → arquitectura | Emergente [20] | Complejidad limitada |
| Evaluación de diagramas | Emergente | Solo 4 proyectos evaluados |

#### 2.4.4. Implementación y codificación

**Evidencia: Fuerte (26 estudios)**

La implementación es la fase más estudiada y donde la evidencia es más robusta
— aunque también más contradictoria.

**Productividad (tratada en profundidad en §2.6):** El experimento controlado
de Peng et al. [6] (N=95) encontró que GitHub Copilot incrementa la velocidad
de completamiento en un 55.8% para tareas específicas de codificación. Sin
embargo, el RCT de METR [7] (N=16, 246 tareas) reveló que desarrolladores
experimentados trabajando en sus propios repositorios fueron un 19% **más
lentos** con herramientas de IA.

**Adopción:** El 85% de los desarrolladores usa regularmente herramientas de
IA para codificación [23]. El 41% de todo el código escrito en 2025 fue
generado por IA [23]. GitHub Copilot superó los 20 millones de usuarios, con
el 90% de las empresas Fortune 100 adoptándolo [24].

**Capacidades de agentes autónomos:** Los agentes de codificación han
progresado significativamente. En SWE-bench Verified, los mejores agentes
alcanzan tasas de resolución del 72-80% en issues reales de GitHub [5][25],
un salto cualitativo desde el 13.86% inicial de Devin en el SWE-bench
original.

| Herramienta/Agente | Tipo | Capacidad clave |
|--------------------|------|-----------------|
| GitHub Copilot | Plugin IDE | 20M+ usuarios, autocompletado + chat |
| Cursor | IDE nativo IA | Autocompletado rápido, modo agente |
| Claude Code | Agente terminal | Contexto 200K tokens, refactoring |
| Devin | Agente autónomo | Autonomía total, primer baseline SWE-bench |

#### 2.4.5. Testing

**Evidencia: Fuerte (16 estudios)**

El testing es la segunda fase más investigada y donde la IA muestra algunos
de sus resultados más impresionantes.

Wang et al. [4] revisaron 102 estudios sobre LLMs en testing, documentando
aplicaciones exitosas en generación de tests unitarios, generación de
oráculos de test y generación de inputs para tests de sistema. El crecimiento
de la investigación es explosivo: de 1 paper en 2021 a 73 en 2024, con la
generación de tests representando el 60% del volumen total [26].

**Mutation testing:** Tufano et al. [27] evaluaron 6 LLMs en 851 bugs reales,
encontrando que GPT-4o alcanza una tasa de detección de fallas del **93.4%**,
comparado con 71.7% de LEAM, 51.3% de PIT y 74.4% de Major. Meta desplegó
testing guiado por mutaciones con LLMs en producción (Facebook, Instagram,
WhatsApp), con ingenieros de privacidad aceptando el **73%** de los tests
generados [28].

| Capacidad demostrada | Evidencia | Limitación |
|---------------------|-----------|------------|
| Tests unitarios | Fuerte [4][26] | Tests tautológicos posibles |
| Mutation testing | Fuerte [27][28] | 93.4% detección (GPT-4o) |
| Tests de integración | Moderada | Aún requiere supervisión significativa |
| Tests E2E | Emergente | Limitado por complejidad de flujos |

#### 2.4.6. Despliegue y operaciones

**Evidencia: Emergente (4 estudios)**

El despliegue es la fase con menos investigación empírica. Joshi [29] revisó
50 trabajos sobre IA generativa en pipelines DevOps (2023-2025), encontrando
que los LLMs pueden predecir fallos y generar scripts, reduciendo tiempos de
despliegue en un 40%. Sin embargo, el 73% de los equipos DevOps aún no ha
adoptado IA en sus flujos CI/CD [23].

Pereira et al. [30] analizaron enfoques de seguridad impulsados por IA en
DevSecOps, mientras que Goncalves et al. [31] mapearon tecnologías de IA
en el ciclo de vida de microservicios, incluyendo despliegue, monitoreo y
escalamiento.

| Capacidad demostrada | Evidencia | Limitación |
|---------------------|-----------|------------|
| Generación de IaC | Emergente [29] | Configuraciones inseguras posibles |
| Optimización CI/CD | Emergente [29] | 73% aún no adopta |
| Monitoreo/anomalías | Emergente [31] | Pocos estudios empíricos |

#### 2.4.7. Evolución y mantenimiento

**Evidencia: Moderada (10 estudios)**

Nogueira et al. [32] desarrollaron ACE, un sistema de remediación automática
de deuda técnica. GPT-4 detecta el **86.7%** de las oportunidades de
refactoring en 20 proyectos Java reales, aunque solo genera refactorizaciones
funcionalmente correctas el **37%** de las veces. Con un pipeline de
validación automatizada, la precisión sube al **98%**.

Kacimi et al. [33] identificaron una nueva forma de deuda técnica: la
*prompt debt*, que surge de prácticas deficientes de prompt engineering en
proyectos que usan LLMs. Los "prompt smells" comprometen el rendimiento del
modelo de formas no evidentes hasta mucho después.

GitClear [34] analizó 211 millones de líneas de código (2020-2024) y
encontró que el código asociado a refactoring cayó del 25% (2021) a menos
del 10% (2024), mientras que la duplicación de código creció 8x.

| Capacidad demostrada | Evidencia | Limitación |
|---------------------|-----------|------------|
| Detección de deuda técnica | Fuerte [32] | 86.7% detección |
| Refactoring automatizado | Moderada [32] | 37% correcto sin validación |
| Refactoring con validación | Fuerte [32] | 98% con pipeline |
| Modernización legacy | Emergente | Pocos estudios controlados |

#### 2.4.8. Gestión de proyectos

**Evidencia: Emergente (4 estudios)**

Garcia et al. [35] propusieron un sistema de soporte a decisiones con IA para
gestión ágil, logrando 94% de precisión en identificación de riesgos, 25% de
mejora en gestión de carga de trabajo y 18% de mejora en tasas de
completamiento de sprints. Psaltis et al. [36] exploraron agentes cognitivos
para gestión ágil automatizada.

### 2.5. Calidad y seguridad del código generado por IA (RQ2)

> *RQ2: ¿Cuál es el impacto medible de la IA en la calidad, seguridad y
> mantenibilidad del software producido?*

**Evidencia: Fuerte — y preocupante.**

Los datos sobre calidad del código generado por IA presentan un panorama
contradictorio que requiere análisis cuidadoso.

**Indicadores negativos:**

CodeRabbit [37] analizó 470 pull requests en repositorios open-source y
encontró que los PRs generados por IA contienen **1.7x más issues** que los
humanos (10.83 vs. 6.45 por PR). Las vulnerabilidades de seguridad son
particularmente alarmantes:

| Vulnerabilidad | IA vs. Humano |
|----------------|---------------|
| Manejo impropio de passwords | 1.88x más probable |
| Referencias inseguras a objetos | 1.91x más probable |
| Cross-Site Scripting (XSS) | 2.74x más probable |
| Deserialización insegura | 1.82x más probable |

La IA falla en generar código seguro para XSS el 86% de las veces y produce
código inseguro para inyección de logs el 88% de las veces [37].

Pearce et al. [38] encontraron que más del 40% del código generado por
GitHub Copilot contiene vulnerabilidades de seguridad. Apiiro Research [39]
confirmó que las vulnerabilidades de seguridad aumentan 1.5-2x en código
escrito con IA, los problemas de legibilidad aumentan 3x+, y los
desarrolladores asistidos por IA exponen credenciales Azure casi el doble de
frecuente.

GitClear [34] documentó tendencias estructurales preocupantes: el código que
necesita ser revisado dentro de las 2 semanas siguientes pasó del 3.1% al
7.9%, y la duplicación creció 8x. El reporte de Qodo [40] proyecta un
**déficit de calidad del 40%** para 2026 y reporta que el 88% de los
desarrolladores tiene baja confianza en enviar código generado por IA a
producción.

**Indicadores positivos:**

Estudios de GitHub sobre Copilot reportan mejoras estadísticamente
significativas en legibilidad (+3.62%), confiabilidad (+2.94%),
mantenibilidad (+2.47%) y concisión (+4.16%) [6]. Sin embargo, estos
estudios provienen del propio fabricante de la herramienta, lo cual introduce
un potencial sesgo metodológico.

**Slopsquatting: un nuevo vector de ataque:**

Los LLMs introdujeron un riesgo de seguridad sin precedentes: el
*slopsquatting* [41]. Los modelos alucinan nombres de paquetes inexistentes
pero plausibles — en promedio, una quinta parte de los paquetes recomendados
no existe (205.000 nombres alucinados documentados). El 43% de estos
paquetes fantasma aparecen consistentemente al repetir los mismos prompts.
Los atacantes pueden pre-registrar estos nombres en repositorios públicos
para distribuir malware.

**Síntesis RQ2:**

| Métrica | Hallazgo | Fortaleza |
|---------|----------|-----------|
| Densidad de issues | IA: 1.7x más que humano | Fuerte [37] |
| Vulnerabilidades seguridad | 1.5-2x más en código IA | Fuerte [37][38][39] |
| Duplicación de código | 8x aumento 2020-2024 | Fuerte [34] |
| Code churn (revisión <2 sem.) | 3.1% → 7.9% | Fuerte [34] |
| Refactoring | Cayó de 25% a <10% | Fuerte [34] |
| Legibilidad/confiabilidad | Mejora 2.9-4.2% | Moderada (potencial sesgo) [6] |
| Confianza del desarrollador | 88% baja confianza | Fuerte [40] |
| Slopsquatting | 20% paquetes alucinados | Fuerte [41] |

La evidencia indica que la IA puede mejorar ciertas métricas superficiales
de calidad pero introduce riesgos significativos de seguridad y
mantenibilidad que requieren supervisión activa y pipelines de validación
robustos.

### 2.6. Productividad: percepción vs. realidad (RQ3)

> *RQ3: ¿Cuál es el efecto real de las herramientas de IA en la productividad
> de los desarrolladores, y en qué medida coincide la productividad percibida
> con la medida?*

**Evidencia: Fuerte — y contradictoria.**

La productividad es el área donde las contradicciones en la literatura son
más marcadas y reveladoras.

**Estudios que reportan ganancia de productividad:**

| Estudio | Metodología | N | Resultado | Fortaleza |
|---------|-------------|---|-----------|-----------|
| Peng et al. [6] | RCT | 95 | 55.8% más rápido | Fuerte |
| GitHub Copilot metrics [24] | Observacional | 4,800 | 55% más rápido; PR de 9.6→2.4 días | Moderada (fabricante) |

**Estudios que reportan pérdida o nulidad:**

| Estudio | Metodología | N | Resultado | Fortaleza |
|---------|-------------|---|-----------|-----------|
| METR [7] | RCT | 16/246 tareas | 19% **más lento** | Fuerte |

**La paradoja de productividad:**

El estudio de METR es particularmente revelador por su diseño riguroso:

- **Diseño:** Ensayo controlado aleatorizado con 16 desarrolladores
  experimentados trabajando en sus propios repositorios open-source.
- **Predicción previa:** Los desarrolladores estimaron que la IA reduciría
  su tiempo en un **24%**.
- **Percepción posterior:** Tras completar las tareas, estimaron que la IA
  había reducido su tiempo en un **20%**.
- **Resultado medido:** La IA **incrementó** el tiempo de completamiento en
  un **19%**.
- **Brecha percepción-realidad:** 43 puntos porcentuales.

Esta brecha entre percepción y realidad tiene implicaciones profundas para
la adopción: los desarrolladores creen firmemente que la IA los hace más
productivos incluso cuando la medición objetiva muestra lo contrario.

**Reconciliación de la evidencia:**

Las diferencias entre estudios no son necesariamente contradictorias — pueden
reflejar variables mediadoras:

- **Expertise:** La IA beneficia más a desarrolladores menos experimentados
  (Peng et al.: freelancers con tarea nueva) que a expertos en su propio
  código (METR: mantenedores de OSS).
- **Tipo de tarea:** Tareas de codificación greenfield muestran mayor
  beneficio que tareas de mantenimiento en codebases maduras.
- **Definición de productividad:** Si se mide solo velocidad de escritura
  de código, la ganancia es clara. Si se incluye revisión, debugging y
  mantenimiento, el resultado es menos favorable.

Osmani [42] documentó otro aspecto crítico: el output individual crece
**98%** en equipos con alta adopción de IA, pero el tiempo de revisión de
PRs crece hasta **91%**. El 99% de los desarrolladores que usan IA reportan
ahorrar 10+ horas/semana, pero la mayoría **no reporta disminución en la
carga total de trabajo** — el tiempo ahorrado escribiendo código es consumido
por fricción organizacional, cambio de contexto y gestión de mayor volumen
de cambios [42].

**Síntesis RQ3:**

| Dimensión | Hallazgo | Fortaleza |
|-----------|----------|-----------|
| Velocidad de codificación greenfield | +55% (freelancers, tarea nueva) | Fuerte [6] |
| Velocidad en código propio experto | -19% (desarrolladores experimentados) | Fuerte [7] |
| Percepción vs. realidad | 43 puntos de brecha | Fuerte [7] |
| Output individual | +98% | Moderada [42] |
| Tiempo de revisión de PRs | +91% | Moderada [42] |
| Carga total de trabajo | Sin disminución | Moderada [42] |

### 2.7. La transformación del rol profesional (RQ4)

> *RQ4: ¿Cómo se está transformando el rol del profesional de software y qué
> competencias emergentes son requeridas?*

**Evidencia: Moderada.**

Gartner proyecta que el **80%** de la fuerza de trabajo en ingeniería
necesitará actualizarse para 2027 [43]. El modelo emergente es claro:
el profesional migra de productor de código a **orquestador de un proceso de
producción de software** [42][44].

**Impacto en desarrolladores junior:**

Modestino et al. [45] encontraron que cuando las empresas adoptan IA
generativa, el empleo de desarrolladores junior (0-3 años de experiencia)
**cae un 9-10%** en seis trimestres, mientras que el empleo senior apenas
se modifica. La contracción no se debe a que los seniors sean más productivos
con IA, sino a que las empresas reducen la contratación de perfiles que
consideran más reemplazables.

**Atrofia de habilidades:**

El 59% de los desarrolladores admite usar código generado por IA que **no
comprende completamente** [46]. Los juniors son especialmente vulnerables
porque carecen de los fundamentos para evaluar críticamente el output de
la IA.

**Sesgo de percepción:**

Un hallazgo de Microsoft Research [47] revela que los ingenieros que usan IA
reciben **evaluaciones de competencia más bajas** por trabajo idéntico —
efecto que se duplica para mujeres.

**Competencias emergentes:**

| Competencia | Dirección | Evidencia |
|-------------|-----------|-----------|
| Lectura/evaluación de código | ↑ Sube | Fuerte [42][44] |
| Especificación precisa | ↑ Sube | Fuerte [42] |
| Diseño arquitectónico | ↑ Sube | Moderada [18] |
| Orquestación de agentes | ↑ Nueva | Moderada [44] |
| Escritura de código rutinario | ↓ Baja | Fuerte [23][42] |
| Testing y validación | ↑ Sube | Fuerte [4] |
| Seguridad | ↑ Sube | Fuerte [37][38] |

### 2.8. Marcos metodológicos emergentes (RQ5)

> *RQ5: ¿Qué marcos metodológicos han surgido para integrar la IA de manera
> sistemática en el SDLC?*

**Evidencia: Emergente a Moderada.**

Se identificaron seis marcos metodológicos relevantes:

**1. AI-Native SDLC / V-Bounce (Fan/Hymel, 2024) [48]**
- Adaptación del modelo V tradicional con IA integrada end-to-end.
- La IA reduce drásticamente el tiempo en fases de implementación,
  desplazando el énfasis hacia requerimientos, diseño y validación continua.
- Redefine al humano como validador/verificador; la IA actúa como motor de
  implementación.
- **Evaluación:** propuesta teórica con framework práctico; sin evaluación
  empírica formal publicada.

**2. Spec-Driven Development (GitHub, 2025) [49]**
- Coloca la especificación en el centro del proceso de ingeniería.
- Introduce el artefacto `constitution.md` con principios no negociables.
- Compatible con múltiples agentes (Copilot, Claude Code, Gemini CLI).
- **Evaluación:** herramienta open-source con adopción significativa (16,000+
  estrellas en su primera semana); sin evaluación académica formal.

**3. Agentic Engineering (Osmani/Karpathy, 2025-2026) [42][44]**
- Evolución del *vibe coding* a una práctica disciplinada.
- Regla 70/30: 70% del esfuerzo en definición del problema, 30% en
  ejecución.
- Principio central: aplicar disciplina clásica de ingeniería a las
  colaboraciones con IA.
- **Evaluación:** basada en experiencia industrial extensa (Google Chrome);
  sin estudio controlado publicado.

**4. AI-DLC 2026 (Han Research) [50]**
- Metodología comprensiva con tres fases: Inception, Construction, Operations.
- Introduce el modo operativo Human-on-the-Loop (HOTL): el humano establece
  el destino, la IA provee la ejecución paso a paso.
- 10-26 puntos de validación humana por unidad de trabajo.
- **Evaluación:** paper metodológico detallado; sin evaluación empírica
  independiente.

**5. Microsoft AI-Led SDLC [51]**
- Framework end-to-end para desarrollo agéntico usando Azure y GitHub.
- Integración de IA en planificación, implementación, testing y despliegue.
- Checkpoints humanos en puntos de decisión críticos.
- **Evaluación:** framework empresarial; sin evaluación académica
  independiente.

**6. Context Engineering (Willison/Karpathy, 2025) [52]**
- Evolución del prompt engineering: no se trata de formular prompts
  ingeniosos sino de proveer a la IA toda la información, documentación,
  código, ejemplos y restricciones que necesita.
- Cambio de paradigma: de "¿cómo formulo este prompt?" a "¿qué información
  necesita la IA para tener éxito?"
- **Evaluación:** concepto ampliamente adoptado; sin marco formal de
  evaluación.

| Framework | Origen | Tipo | Evaluación formal |
|-----------|--------|------|-------------------|
| V-Bounce [48] | Académico | Modelo de proceso | Paper arXiv, sin evaluación empírica |
| Spec-Driven Dev. [49] | Industria (GitHub) | Toolkit + proceso | Open-source, adopción masiva |
| Agentic Engineering [42] | Industria (Google) | Principios + prácticas | Experiencia industrial |
| AI-DLC 2026 [50] | Investigación | Metodología completa | Paper metodológico |
| AI-Led SDLC [51] | Industria (Microsoft) | Framework empresarial | Documentación técnica |
| Context Engineering [52] | Industria | Paradigma conceptual | Adopción amplia |

**Observación:** ninguno de los frameworks identificados cuenta con una
evaluación empírica rigurosa e independiente. La mayoría se basa en
experiencia industrial o propuestas teóricas. Esto representa una brecha
significativa en la literatura.

### 2.9. Síntesis y discusión

#### 2.9.1. Fortalezas de la evidencia

La evidencia es más robusta en:
- **Calidad del código generado por IA:** múltiples estudios independientes
  convergen en que el código IA tiene más defectos y vulnerabilidades.
- **Capacidades de testing:** evidencia fuerte de que los LLMs superan a las
  herramientas tradicionales en mutation testing.
- **Adopción:** datos convergentes de múltiples surveys independientes
  (85% adopción regular, 41% código IA-generado).

#### 2.9.2. Brechas identificadas

- **Despliegue/DevOps:** solo 4 estudios, ninguno con experimento controlado.
- **Estudios longitudinales:** la mayoría mide impacto a corto plazo; faltan
  datos sobre efectos a mediano-largo plazo.
- **Evaluación de frameworks:** ningún framework metodológico tiene evaluación
  empírica independiente.
- **Educación:** cómo adaptar la formación de profesionales es un área con
  poca investigación formal.

#### 2.9.3. Contradicciones en la literatura

Se identificaron cuatro paradojas clave en la literatura:

**Paradoja de productividad:**
Peng et al. [6] reportan +55% de velocidad; METR [7] reporta -19%.
*Análisis:* las diferencias reflejan poblaciones distintas (juniors vs.
seniors), tipos de tarea (greenfield vs. mantenimiento) y métricas
(velocidad de codificación vs. tiempo total). Ambos estudios son
metodológicamente sólidos. La productividad con IA es **contingente al
contexto**, no universal.

**Paradoja de calidad:**
GitHub [6] reporta mejora en legibilidad/confiabilidad; CodeRabbit [37]
reporta 1.7x más issues.
*Análisis:* los estudios de GitHub son del fabricante de la herramienta
y miden métricas de estilo de código. CodeRabbit mide defectos funcionales
y de seguridad. No se contradicen necesariamente: el código puede ser más
legible Y tener más vulnerabilidades.

**Paradoja de adopción:**
84% de adopción [53] pero 46% de desconfianza activa [40].
*Análisis:* los desarrolladores usan herramientas de IA porque la presión
competitiva es enorme, no necesariamente porque confíen en los resultados.
Esto sugiere una adopción impulsada por FOMO más que por evidencia de valor.

**Paradoja de percepción:**
Los desarrolladores creen que ahorran 20-24% de tiempo cuando en realidad
tardan 19% más [7].
*Análisis:* la sensación de productividad (la IA genera código visible
rápidamente) difiere del resultado neto (el tiempo de integración, revisión
y corrección consume la ganancia). El efecto Dunning-Kruger aplicado a la
herramienta de trabajo.

#### 2.9.4. Amenazas a la validez de esta revisión

- **Sesgo de publicación:** tendencia a publicar resultados positivos;
  los estudios negativos pueden estar subrepresentados.
- **Sesgo de idioma:** dominancia del inglés en la literatura limita la
  cobertura de investigación en otros idiomas.
- **Rapidez del campo:** papers publicados durante la elaboración de esta
  revisión pueden no estar incluidos.
- **Preprints sin peer review:** el 20.8% de los estudios incluidos son
  preprints arXiv que no han pasado por revisión por pares formal.
- **Conflicto de interés en reportes de industria:** varios reportes
  provienen de fabricantes de herramientas de IA (GitHub, Qodo), lo cual
  introduce sesgo potencial en los resultados reportados.
- **Verificación de fuentes:** todas las referencias incluidas en esta
  revisión fueron verificadas por existencia y consistencia de datos. Las
  fuentes que no pudieron ser verificadas fueron excluidas. Sin embargo, la
  verificación se realizó mediante acceso a URLs y cross-referencing entre
  fuentes independientes, no mediante replicación de los estudios.

### 2.10. Datos de adopción en la industria

Los datos de adopción provienen de múltiples surveys independientes que
muestran una convergencia notable:

| Fuente | Año | N | Dato clave |
|--------|-----|---|------------|
| Stack Overflow [53] | 2025 | >65,000 | 84% usa o planea usar IA |
| JetBrains [23] | 2025 | 24,534 | 85% usa regularmente; 41% código IA |
| GitHub [24] | 2024 | - | 20M+ usuarios Copilot; 90% Fortune 100 |
| Qodo [40] | 2025 | - | 82% usa IA diaria/semanalmente |
| Gartner [43] | 2024 | 400 líderes | 90% usará por 2028 |

**Evolución de la capacidad de los agentes (SWE-bench):**

```
SWE-bench: resolución de issues reales de GitHub

2024 Q1  Devin: ██ 13.9%        (primer agente sustancial)
2025 Q3  Claude 3.7: ████████████████ 62.3%
2025 Q3  Gemini 2.5: █████████████████ 63.8%
2025 Q4  Claude Code: ███████████████████ 72%+
2026 Q1  Top agents: █████████████████████ 80%+
```

**Datos de Big Tech:**
- **Google:** la IA escribe "más del 30%" del código nuevo [54].
- **Microsoft:** ingenieros usan IA para escribir 20-30% del código [54].
- **Meta:** CEO indicó que la IA tomará "la mitad del desarrollo de software"
  en el próximo año [54].

---

## 3. Estudio de factibilidad

> [!IMPORTANT]
> *El estudio de factibilidad es la etapa donde un error cuesta menos de corregir. Paradójicamente, es donde menos se invierte — y donde la IA puede aportar más sin riesgo.*

*La revisión sistemática (§2.4.1) identificó 6 estudios sobre IA en
factibilidad y estimación, con evidencia emergente. Los hallazgos clave
informan las prácticas recomendadas en esta sección.*

### 3.1. La etapa olvidada

El estudio de factibilidad — esa evaluación inicial que determina si un
proyecto es viable técnica, económica y operativamente — es frecuentemente la
etapa más subestimada del SDLC. En muchos equipos de desarrollo, se reduce a
una conversación informal o directamente se omite. Los proyectos arrancan
porque alguien decidió que eran "factibles" basándose en intuición o presión
comercial.

Sin embargo, las estadísticas son contundentes: entre el 50% y el 80% de los
proyectos de software fallan total o parcialmente, y una proporción
significativa de esos fracasos se remonta a evaluaciones iniciales deficientes
[55]. Un estudio de factibilidad riguroso no garantiza el éxito, pero su
ausencia casi garantiza problemas evitables.

### 3.2. Qué puede hacer la IA en esta etapa

La IA puede asistir significativamente en las tres dimensiones clásicas de la
factibilidad:

**Factibilidad técnica:**
- Analizar la descripción del proyecto y evaluar la complejidad técnica
  en función de proyectos similares documentados.
- Identificar tecnologías candidatas y evaluar su madurez, soporte
  comunitario y curva de aprendizaje.
- Detectar riesgos técnicos potenciales a partir de las restricciones
  descritas.
- Generar prototipos rápidos (proof of concept) para validar viabilidad
  de componentes críticos.

**Factibilidad económica:**
- Estimar esfuerzo en función de métricas históricas y complejidad del
  proyecto. Lopez-Martin et al. [9] demostraron que LLMs fine-tuneados
  mejoran la precisión de modelos como COCOMO [56], aunque los resultados
  son inconsistentes entre dominios.
- Generar análisis comparativos build vs. buy.
- Proyectar costos de infraestructura a partir de las necesidades
  técnicas descritas.

**Factibilidad operativa:**
- Evaluar el impacto organizacional del proyecto a partir de la
  descripción del contexto.
- Identificar necesidades de capacitación y cambio organizacional.
- Generar matrices de riesgo iniciales — con la advertencia de que el 50%
  de los outputs de IA para análisis de riesgo requieren corrección
  experta [13].

### 3.3. Práctica recomendada: el análisis de factibilidad asistido

```
┌─────────────────────────────────────────────────────────┐
│           ESTUDIO DE FACTIBILIDAD CON IA                │
│                                                         │
│  1. ENTRADA                                             │
│     ├── Descripción del proyecto (lenguaje natural)     │
│     ├── Contexto organizacional                         │
│     ├── Restricciones conocidas                         │
│     └── Presupuesto estimado                            │
│                                                         │
│  2. PROCESO (asistido por IA)                           │
│     ├── Análisis de complejidad técnica                 │
│     ├── Identificación de riesgos                       │
│     ├── Estimación de esfuerzo                          │
│     ├── Análisis de tecnologías candidatas              │
│     └── Generación de informe preliminar                │
│                                                         │
│  3. VALIDACIÓN (humana)                                 │
│     ├── Revisión de supuestos                           │
│     ├── Validación con stakeholders                     │
│     ├── Ajuste de estimaciones por experiencia          │
│     └── Decisión GO / NO-GO                             │
│                                                         │
│  4. SALIDA                                              │
│     ├── Informe de factibilidad documentado             │
│     ├── Matriz de riesgos priorizada                    │
│     ├── Estimación de esfuerzo y costos                 │
│     └── Recomendación fundamentada                      │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

**El rol del profesional:** La IA puede generar un análisis inicial
sorprendentemente completo, pero la decisión GO/NO-GO sigue siendo humana.
El profesional aporta lo que la IA no tiene: conocimiento del contexto
político-organizacional, experiencia con proyectos similares en la
organización específica, y la capacidad de evaluar el "apetito de riesgo"
real del cliente o la organización.

### 3.4. Riesgos y limitaciones

- **Sesgo de optimismo**: los LLMs tienden a generar análisis optimistas.
  El profesional debe cuestionar activamente los supuestos del análisis
  generado.
- **Falta de contexto organizacional**: la IA no conoce la historia del
  equipo, sus capacidades reales ni las dinámicas internas.
- **Estimaciones genéricas**: las estimaciones de esfuerzo basadas en IA
  son un punto de partida, no un compromiso. La calibración con la
  experiencia del equipo es indispensable.

---

## 4. Requerimientos: elicitación, análisis y especificación

> [!IMPORTANT]
> *Los requerimientos siguen siendo la etapa donde se ganan o se pierden los proyectos. La IA no cambia esa realidad — pero sí cambia cómo llegamos a ellos.*

*La revisión sistemática (§2.4.2) identificó 9 estudios con evidencia
moderada. Los LLMs igualan la cobertura humana en historias de usuario pero
exhiben menor diversidad y creatividad [15].*

### 4.1. El punto de partida: evidencia empírica

El trabajo de Panigo, Petkoff Bankoff, Pasini y Pesado (2024), presentado en
el XXX Congreso Argentino de Ciencias de la Computación, constituye una de
las primeras evaluaciones sistemáticas del uso de LLMs en las etapas
tempranas del SDLC [2].

El estudio comparó siete modelos de lenguaje — ChatGPT-3.5, GPT-4o,
ChatGPT con Write For Me, Gemini 1.0, Gemini 1.5, Mistral y AI21 — en dos
tareas concretas:

**Generación de entrevistas para elicitación de requerimientos:**
- Se proporcionó a cada modelo un anuncio ficticio y un conjunto de
  requerimientos, solicitando la generación del cuerpo de entrevistas.
- Se evaluaron los resultados con una escala de cuatro niveles:
  Inaceptable (IN), Mínimamente aceptable (MA), Aceptable (AC) y
  Satisfactorio (SA).
- Resultados: la mayoría de los modelos produjeron entrevistas aceptables
  a satisfactorias. Se destacó la capacidad de los modelos para
  incorporar temas de contexto real (público objetivo, integración con
  sistemas existentes, seguridad de datos).

```
Resultados de entrevistas (un enunciado):

Modelo       │ GPT-3.5 │ GPT-4o │ GPT+WFM │ GEM 1.0 │ GEM 1.5 │ Mistral │ AI21
─────────────┼─────────┼────────┼─────────┼─────────┼─────────┼─────────┼──────
Resultado    │   AC    │   AC   │   SA    │   AC    │   SA    │   MA    │  AC

Resultados de entrevistas (dos enunciados):

Modelo       │ GPT-3.5 │ GPT-4o │ GPT+WFM │ GEM 1.0 │ GEM 1.5 │ Mistral │ AI21
─────────────┼─────────┼────────┼─────────┼─────────┼─────────┼─────────┼──────
Primera      │   IN    │   SA   │   AC    │   SA    │   SA    │   MA    │  MA
Segunda      │    -    │   AC   │   AC    │   IN    │   SA    │   MA    │  MA
```

**Generación de historias de usuario:**
- Se solicitó a los modelos la generación de historias de usuario en dos
  formatos: uno simple (solo título con formato *como [rol], quiero
  [acción] para [objetivo]*) y uno completo (con reglas de negocio y
  criterios de aceptación en sintaxis Gherkin [57]).
- Resultados: todos los modelos generaron historias de usuario pertinentes.
  Los mejores resultados se obtuvieron con el formato simple, y se observó
  que las historias con estructura completa tendían a ser menos atómicas.

La conclusión del estudio es elocuente: los LLMs constituyen herramientas
viables para asistir en las etapas de elicitación y análisis de
requerimientos, pero **es imprescindible que los profesionales mantengan una
mirada crítica** sobre los resultados para evaluar su calidad y pertinencia
[2].

### 4.2. Elicitación: la IA como preparadora de terreno

La elicitación de requerimientos es la etapa donde se recopila información
detallada de los interesados sobre sus necesidades y expectativas para el
software [58]. Tradicionalmente, depende de entrevistas, talleres,
observación y análisis de documentos.

La IA puede participar en esta etapa de múltiples maneras:

**Antes de la entrevista:**
- Generar guiones de entrevista adaptados al dominio del proyecto.
- Identificar preguntas que cubran áreas frecuentemente olvidadas
  (seguridad, escalabilidad, integración, migración de datos).
- Analizar documentación existente del cliente para generar preguntas
  contextualizadas.

**Durante el análisis:**
- Procesar transcripciones de entrevistas y extraer requerimientos
  candidatos.
- Detectar contradicciones entre lo expresado por distintos stakeholders.
- Identificar requerimientos implícitos que los stakeholders asumen pero
  no mencionan.

**Para la especificación:**
- Transformar notas de reuniones en requerimientos estructurados.
- Generar historias de usuario en formato estándar.
- Producir criterios de aceptación en sintaxis Gherkin.
- Verificar completitud y consistencia del conjunto de requerimientos.

### 4.3. Análisis y especificación: del lenguaje natural al artefacto formal

Una vez recopilada la información, la etapa de análisis implica clarificar,
priorizar y estructurar los requerimientos [58]. Las historias de usuario son
el formato dominante en metodologías ágiles, con aproximadamente el 70% de
los equipos utilizándolas como herramienta principal de especificación [59].

**Práctica recomendada: especificación asistida en tres pasos**

```
Paso 1: Entrada → IA genera borrador
────────────────────────────────────────
  El profesional proporciona:
  • Notas de reuniones / transcripciones
  • Documentación del dominio
  • Restricciones conocidas

  La IA genera:
  • Historias de usuario candidatas
  • Criterios de aceptación preliminares
  • Preguntas pendientes identificadas

Paso 2: Revisión → Profesional evalúa y corrige
────────────────────────────────────────
  El profesional:
  • Valida cada historia contra su conocimiento del dominio
  • Corrige ambigüedades y suposiciones incorrectas
  • Agrega historias que la IA no identificó
  • Prioriza según valor de negocio

Paso 3: Refinamiento → IA refina, profesional aprueba
────────────────────────────────────────
  La IA:
  • Reformula según las correcciones
  • Genera criterios de aceptación detallados
  • Verifica consistencia del conjunto completo
  • Identifica dependencias entre historias

  El profesional:
  • Aprobación final de cada historia
  • Validación con stakeholders
```

### 4.4. Riesgos y limitaciones

- **El "sesgo de completitud"**: la IA genera artefactos que *parecen*
  completos pero pueden omitir requerimientos críticos que solo emergen
  del conocimiento profundo del dominio.
- **La trampa de la automatización**: delegar toda la elicitación a la IA
  elimina la interacción humana con los stakeholders, que es donde surgen
  los requerimientos más valiosos — los no dichos, los implícitos, los
  que emergen del diálogo.
- **Alucinaciones en el dominio**: los LLMs pueden inventar
  requerimientos plausibles pero inexistentes, especialmente en dominios
  especializados.

> [!IMPORTANT]
> *La IA es excelente generando el primer borrador de requerimientos. El error es confundir ese borrador con la especificación final.*

---

## 5. Diseño

> [!IMPORTANT]
> *El diseño es donde la experiencia del ingeniero se vuelve irremplazable. La IA puede proponer una arquitectura, pero solo el profesional sabe si esa arquitectura sobrevivirá al contacto con la realidad del equipo, la organización y el mercado.*

*La revisión sistemática (§2.4.3) identificó 8 estudios con evidencia
emergente. El diseño arquitectónico con IA es un área relativamente
subexplorada — el 73% de los modelos usados son decoder-only [18].*

### 5.1. Arquitectura de software asistida por IA

El diseño arquitectónico es una de las áreas donde la IA ofrece asistencia
significativa pero donde el juicio humano es más crítico. Una decisión
arquitectónica incorrecta tiene un costo que crece exponencialmente con el
tiempo — y los LLMs, entrenados con millones de proyectos, tienden a proponer
arquitecturas "promedio" que no necesariamente se ajustan a las restricciones
específicas de cada proyecto.

**Lo que la IA puede hacer:**
- Proponer arquitecturas candidatas basadas en los requerimientos.
- Generar diagramas de componentes y sus interacciones.
- Evaluar trade-offs entre alternativas arquitectónicas documentadas.
- Generar ADRs (Architecture Decision Records) a partir de decisiones
  discutidas — Dhar et al. [19] combinan RAG y fine-tuning para esta tarea.
- Sugerir patrones de diseño apropiados para problemas específicos.
- Detectar antipatrones y smells arquitectónicos [21][22].

**Lo que la IA no debería decidir sola:**
- La elección final de la arquitectura.
- Decisiones de tecnología que comprometen al equipo a largo plazo.
- Trade-offs entre rendimiento, costo y complejidad.
- Estrategias de escalabilidad que dependen del crecimiento del negocio.

### 5.2. Diseño de base de datos

La generación de esquemas de base de datos es una de las capacidades más
confiables de los LLMs actuales. A partir de un conjunto de requerimientos
o historias de usuario, la IA puede:

- Generar modelos entidad-relación completos.
- Proponer estrategias de normalización/desnormalización.
- Generar scripts DDL para múltiples motores.
- Sugerir índices basados en patrones de consulta previstos.
- Evaluar alternativas SQL vs. NoSQL según las características de los datos.

**Práctica recomendada:** usar la IA para generar el modelo inicial y luego
revisar con especial atención las relaciones, las cardinalidades y las
decisiones de normalización. Los LLMs tienden a sobre-normalizar cuando los
requerimientos de rendimiento sugieren desnormalización selectiva.

### 5.3. Diseño de interfaces

Los LLMs multimodales y las herramientas especializadas (v0.dev, Galileo AI,
entre otras) pueden generar interfaces a partir de descripciones textuales.
Esto permite:

- Prototipado rápido para validación con stakeholders.
- Generación de componentes UI en frameworks específicos.
- Evaluación de accesibilidad (WCAG) automatizada.
- Generación de flujos de usuario a partir de historias de usuario.

**El riesgo:** las interfaces generadas por IA tienden a ser genéricas. La
diferenciación del producto, la identidad visual y la experiencia de usuario
específica del dominio siguen requiriendo diseño humano especializado.

### 5.4. Riesgos y limitaciones

- **Arquitecturas "de libro"**: la IA propone lo que aprendió de millones
  de proyectos, no lo que necesita *tu* proyecto con *tus* restricciones.
- **Sobre-ingeniería**: los LLMs tienden a sugerir arquitecturas más
  complejas de lo necesario, especialmente microservicios cuando un
  monolito sería más apropiado.
- **Desconexión con la realidad operativa**: una arquitectura técnicamente
  elegante que el equipo no puede mantener es peor que una simple que
  funciona.

---

## 6. Implementación

> [!IMPORTANT]
> *El código ya no es el artefacto que el desarrollador produce — es el artefacto que el desarrollador supervisa. La habilidad central pasa de "escribir" a "evaluar, corregir y garantizar".*

*La revisión sistemática (§2.4.4) identificó 26 estudios con evidencia
fuerte. La productividad varía significativamente según expertise y tipo
de tarea (§2.6), y la calidad del código IA presenta riesgos documentados
(§2.5).*

### 6.1. El nuevo modelo de implementación

La implementación es la etapa donde la transformación es más visible. Los
agentes de codificación actuales — GitHub Copilot, Cursor, Claude Code, entre
otros — pueden recibir una especificación y producir código funcional con
niveles crecientes de autonomía.

El modelo de trabajo ya no es:
```
Desarrollador → escribe código → compila → testea → corrige
```

El modelo emergente es:
```
Desarrollador → especifica → agente genera → desarrollador revisa
             → agente corrige → desarrollador valida → merge
```

Este cambio no es trivial. Implica que la habilidad central del desarrollador
migra de la **generación** a la **evaluación** — una competencia que
históricamente ha recibido mucha menos atención en la formación y en las
prácticas profesionales.

### 6.2. Prácticas de implementación con agentes

**Especificación como código**

La calidad del código generado por IA depende directamente de la calidad de
la especificación proporcionada. Un prompt vago produce código vago. Una
especificación precisa produce código preciso. Osmani formaliza esto con la
regla del 70/30: dedicar el 70% del esfuerzo a la definición del problema y
solo el 30% a la ejecución [42].

```
❌ Especificación débil:
   "Hacé un endpoint para usuarios"

✅ Especificación fuerte:
   "Implementar un endpoint REST GET /api/v1/users/{id}
    que retorne un usuario por ID.
    - Respuesta 200 con el usuario en formato JSON
      (id, nombre, email, fechaCreación)
    - Respuesta 404 si no existe
    - Respuesta 401 si no hay token JWT válido
    - Usar el repositorio UserRepository existente
    - Loguear el acceso con nivel INFO
    - Tests unitarios con mock del repositorio"
```

**Code review como competencia central**

Cuando la IA genera el código, el code review deja de ser un control
secundario y se convierte en el **principal mecanismo de calidad**. Los datos
de la SLR respaldan esto: el código IA tiene 1.7x más issues [37], el 40%+
contiene vulnerabilidades de seguridad [38], y el XSS falla el 86% de las
veces [37]. El profesional debe ser capaz de:

- Leer y comprender código que no escribió.
- Detectar errores sutiles que los tests pueden no cubrir.
- Evaluar decisiones de diseño implícitas en el código generado.
- Identificar vulnerabilidades de seguridad.
- Verificar que el código cumple con los estándares del proyecto.
- Evaluar la mantenibilidad a largo plazo.

**Incrementalidad y control**

La práctica más efectiva con agentes de codificación es trabajar de manera
**incremental**: tareas pequeñas, bien especificadas, con validación entre
cada paso. La tentación de dar una especificación grande y esperar un sistema
completo generalmente produce resultados de menor calidad.

```
❌ Enfoque monolítico:
   "Generá todo el módulo de autenticación"

✅ Enfoque incremental:
   1. "Generá el modelo User con sus validaciones"
      → Revisar → Aprobar
   2. "Generá el endpoint de registro con hash de password"
      → Revisar → Aprobar
   3. "Generá el endpoint de login con JWT"
      → Revisar → Aprobar
   4. "Generá el middleware de autenticación"
      → Revisar → Aprobar
```

### 6.3. Generación de documentación

Una de las contribuciones más inmediatas y menos controvertidas de la IA en la
implementación es la generación de documentación:

- Documentación de API (OpenAPI/Swagger) a partir del código.
- Comentarios de código para lógica compleja.
- README y guías de uso.
- Documentación de decisiones técnicas (ADR).
- Changelogs automatizados.

### 6.4. La crisis de calidad del código generado por IA

Los datos de la SLR (§2.5) son contundentes y ameritan atención especial
en el contexto de implementación:

```
Vulnerabilidad                      │ IA vs. Humano
────────────────────────────────────┼──────────────
Manejo impropio de passwords        │  1.88x más probable
Referencias inseguras a objetos     │  1.91x más probable
Cross-Site Scripting (XSS)          │  2.74x más probable
Deserialización insegura            │  1.82x más probable
────────────────────────────────────┼──────────────
XSS: la IA falla el 86% de las veces
Inyección de logs: código inseguro el 88% de las veces
```

GitClear [34] revela tendencias estructurales preocupantes: el código
asociado a refactoring cayó del 25% (2021) a menos del 10% (2024), mientras
que la duplicación de código creció 8x. El código que necesita ser
revisado dentro de las 2 semanas siguientes pasó de 3.1% a 7.9%.

**Slopsquatting: un nuevo vector de ataque**

Los LLMs también introdujeron un nuevo riesgo de seguridad: el
*slopsquatting* [41]. Los modelos alucinan nombres de paquetes inexistentes
— en promedio, una quinta parte de los paquetes recomendados no existe.
El 43% de estos paquetes fantasma aparecen consistentemente al repetir los
mismos prompts. Los atacantes pueden pre-registrar estos nombres para
distribuir malware.

### 6.5. Riesgos y limitaciones

- **Código que funciona pero no se entiende**: la IA puede generar
  soluciones funcionales pero opacas, difíciles de mantener o depurar.
- **Dependencias innecesarias**: los LLMs tienden a sugerir bibliotecas
  externas donde código simple resolvería el problema.
- **La "ilusión de productividad"**: el output individual puede crecer
  98%, pero el tiempo de revisión de PRs crece hasta 91% [42]. Generar
  código rápido no es lo mismo que generar *buen* código rápido.
- **Slopsquatting**: los LLMs alucinan nombres de paquetes inexistentes
  que pueden ser explotados como vector de ataque a la cadena de suministro
  [41].

> [!IMPORTANT]
> *El 59% de los desarrolladores admite usar código generado por IA que no entiende completamente [46]. Cuando Gartner predice un aumento del 2500% en defectos de software por enfoques "prompt-to-app" para 2028 [60], la ingeniería de software rigurosa no es un lujo — es una necesidad de supervivencia.*

---

## 7. Testing

> [!IMPORTANT]
> *En un mundo donde la IA genera código, el testing pasa de ser una actividad complementaria a ser la principal línea de defensa. Testear es la habilidad que no muere — es la que más importa.*

*La revisión sistemática (§2.4.5) identificó 16 estudios con evidencia
fuerte. GPT-4o alcanza 93.4% de detección de fallas en mutation testing [27],
y Meta aceptó el 73% de tests generados por LLMs en producción [28].*

### 7.1. La paradoja del testing con IA

La relación entre IA y testing presenta una paradoja productiva: la IA es
excelente generando tests *y* es la razón por la cual necesitamos más tests
que nunca. Cuando un agente genera código, ese código necesita validación
rigurosa — y la mejor forma de validar código automáticamente es con tests
automatizados.

Esto crea un ciclo virtuoso:
```
IA genera código → se necesitan tests → IA genera tests
→ humano valida que los tests sean correctos → tests validan el código
→ confianza aumenta → más código generado por IA
```

El eslabón crítico en esta cadena es el humano que valida que **los tests
mismos sean correctos**. Un test generado por IA que valida código generado
por IA puede crear una ilusión de calidad donde todo "pasa" pero nada
funciona correctamente.

### 7.2. Capacidades de la IA en testing

**Generación de tests unitarios:**
- A partir de código existente, la IA puede generar suites de tests con
  alta cobertura.
- Puede identificar casos borde que el desarrollador podría omitir.
- Genera tests para caminos felices y para manejo de errores.

**Generación de tests de integración:**
- Tests que verifican la interacción entre componentes.
- Configuración de fixtures y datos de prueba.
- Simulación de servicios externos (mocks).

**Testing basado en propiedades (property-based testing):**
- La IA puede identificar invariantes del sistema y generar tests que
  las verifiquen con datos aleatorios.

**Mutation testing:**
- GPT-4o alcanza un **93.4% de tasa de detección de fallas** en mutation
  testing, comparado con 71.7% de LEAM, 51.3% de PIT y 74.4% de Major
  — las herramientas tradicionales dominantes [27].
- Meta desplegó testing guiado por mutaciones con LLMs en producción
  (Facebook, Instagram, WhatsApp). Los ingenieros de privacidad aceptaron
  el **73% de los tests generados** [28].

**Testing de seguridad:**
- Identificación de vulnerabilidades comunes (OWASP Top 10).
- Generación de casos de prueba de penetración básicos.
- Análisis estático de seguridad asistido.

El crecimiento de la investigación en testing con IA es explosivo: de 1
paper en 2021 a 73 en 2024, con la generación de tests representando el 60%
del volumen total de investigación [26].

### 7.3. Práctica recomendada: la pirámide de testing con IA

```
                    ╱╲
                   ╱  ╲
                  ╱ E2E╲         ← Humano diseña, IA asiste
                 ╱      ╲          Escenarios de negocio críticos
                ╱────────╲
               ╱Integración╲    ← IA genera, humano revisa
              ╱              ╲     Interacción entre componentes
             ╱────────────────╲
            ╱   Tests unitarios ╲  ← IA genera, humano valida
           ╱                     ╲   Alta cobertura automatizada
          ╱───────────────────────╲
         ╱    Tests de propiedad    ╲ ← IA identifica invariantes
        ╱                            ╲  Validación exhaustiva
       ╱──────────────────────────────╲
```

**Principio clave:** la participación humana debe ser inversamente
proporcional a la frecuencia y directamente proporcional a la criticidad.
Los tests unitarios pueden ser mayormente generados por IA; los tests E2E
que reflejan flujos de negocio requieren supervisión humana cercana.

### 7.4. Riesgos y limitaciones

- **Tests tautológicos**: la IA puede generar tests que verifican que el
  código hace lo que hace, en lugar de verificar que hace lo que *debe*
  hacer.
- **Falsa seguridad por cobertura**: 100% de cobertura con tests triviales
  es peor que 60% con tests significativos.
- **Tests frágiles**: la IA tiende a generar tests acoplados a la
  implementación en lugar de al comportamiento.
- **Ceguera compartida**: si la IA generó el código y la IA generó los
  tests, ambos pueden compartir el mismo malentendido del requerimiento.

---

## 8. Despliegue y operaciones

> [!IMPORTANT]
> *La IA no solo puede escribir la aplicación — puede escribir la infraestructura que la sostiene, los pipelines que la despliegan y los monitores que la vigilan. El desafío es que un error en esta etapa afecta producción.*

*La revisión sistemática (§2.4.6) identificó solo 4 estudios con evidencia
emergente — el despliegue es la fase menos investigada del SDLC. El 73% de
los equipos DevOps aún no adopta IA en CI/CD [23].*

### 8.1. Infraestructura como código asistida por IA

La infraestructura como código (IaC) es, paradójicamente, una de las áreas
donde la IA puede aportar más valor y donde un error puede ser más costoso.
La generación de configuraciones de Terraform, Kubernetes, Docker y
herramientas similares es una tarea altamente estructurada que los LLMs
manejan bien.

**Capacidades:**
- Generación de Dockerfiles optimizados a partir de la descripción del
  proyecto.
- Configuración de Kubernetes (deployments, services, ingress) a partir
  de requerimientos de despliegue.
- Scripts de Terraform para provisionar infraestructura cloud.
- Configuración de CI/CD pipelines (GitHub Actions, GitLab CI, Jenkins).
- Configuración de monitoreo y alertas.

**Práctica recomendada:** aplicar el mismo principio de incrementalidad que
en la implementación. Generar, revisar y probar cada componente de
infraestructura de manera aislada antes de integrarlo.

### 8.2. CI/CD inteligente

Los pipelines de integración y despliegue continuo pueden beneficiarse de la
IA en múltiples niveles:

- **Optimización de pipelines**: análisis de tiempos de ejecución y
  sugerencias de paralelización.
- **Selección inteligente de tests**: ejecutar solo los tests afectados
  por los cambios, reduciendo tiempos de CI.
- **Análisis de fallos**: cuando un pipeline falla, la IA puede analizar
  los logs y sugerir la causa raíz.
- **Rollback inteligente**: detección automática de degradación post-
  despliegue y reversión automática.

Joshi [29] documentó que los LLMs pueden reducir tiempos de despliegue en
un 40%, aunque la brecha entre potencial y adopción real es significativa.

### 8.3. Monitoreo y observabilidad

Una vez en producción, la IA puede asistir en:

- Análisis de logs para detección de anomalías.
- Correlación de eventos entre servicios distribuidos.
- Predicción de problemas de capacidad antes de que ocurran.
- Generación de dashboards a partir de la descripción de métricas
  relevantes.
- Análisis de incidentes post-mortem.

### 8.4. Riesgos y limitaciones

- **Configuraciones inseguras**: la IA puede generar configuraciones que
  funcionan pero exponen servicios innecesariamente o usan permisos
  excesivos. Pereira et al. [30] documentan los desafíos de seguridad
  específicos de IA en DevSecOps.
- **Vendor lock-in inadvertido**: los LLMs tienden a generar
  configuraciones específicas del proveedor cloud con el que fueron más
  entrenados.
- **Complejidad innecesaria**: sugerir orquestación con Kubernetes para
  una aplicación que correría bien en un solo servidor.
- **Impacto en producción**: a diferencia del código en desarrollo, un
  error en infraestructura afecta usuarios reales inmediatamente.

---

## 9. Evolución y mantenimiento

> [!IMPORTANT]
> *El 60-80% del costo total de un sistema de software se invierte en mantenimiento. La IA puede transformar la etapa más costosa del SDLC en la más eficiente — si sabemos cómo usarla.*

*La revisión sistemática (§2.4.7) identificó 10 estudios con evidencia
moderada. GPT-4 detecta el 86.7% de las oportunidades de refactoring pero
solo genera correcciones válidas el 37% de las veces — cifra que sube al
98% con pipelines de validación [32].*

### 9.1. La etapa que consume más recursos

El mantenimiento de software — correctivo, adaptativo, perfectivo y
preventivo — representa la mayor proporción del costo total de propiedad de
un sistema. Históricamente, es también la etapa menos glamorosa y donde más
resistencia hay a la inversión.

La IA tiene el potencial de cambiar radicalmente esta ecuación en múltiples
frentes.

### 9.2. Análisis de deuda técnica

La deuda técnica — ese conjunto de decisiones subóptimas que se acumulan en
un sistema y encarecen cada cambio futuro — es uno de los mayores desafíos
del mantenimiento. El 62% de los desarrolladores la citan como su principal
frustración [53]. La IA puede asistir en:

- **Detección**: identificar patrones de código que indican deuda técnica
  (código duplicado, complejidad ciclomática excesiva, acoplamiento,
  falta de tests). GPT-4 detecta el **86.7%** de las oportunidades de
  refactoring en proyectos reales [32].
- **Cuantificación**: estimar el esfuerzo necesario para remediar la deuda
  identificada.
- **Priorización**: sugerir qué deuda abordar primero basándose en el
  impacto en la velocidad de desarrollo.
- **Remediación**: generar refactorizaciones automatizadas para patrones
  comunes de deuda técnica.

Un dato crucial: aunque GPT-4 detecta el 86.7% de las oportunidades, solo
genera refactorizaciones funcionalmente correctas el **37%** de las veces.
Sin embargo, cuando se agrega un pipeline de validación automatizada, la
precisión sube al **98%** [32]. La lección es clara: la detección con IA es
excelente, pero la ejecución sin validación es peligrosa.

**Prompt debt: una nueva forma de deuda técnica**

La investigación reciente ha identificado una forma de deuda técnica
completamente nueva: la *prompt debt* — deuda que surge de prácticas
deficientes de prompt engineering en proyectos que usan LLMs. Los "prompt
smells" y "prompt requirement smells" comprometen el rendimiento del modelo
de formas que no son evidentes hasta mucho después [33].

### 9.3. Refactoring asistido

El refactoring es una tarea ideal para la asistencia por IA:

- Renombrar y reorganizar código preservando funcionalidad.
- Extraer funciones y clases para mejorar la cohesión.
- Modernizar código legacy (actualizar sintaxis, APIs deprecadas).
- Migrar entre versiones de frameworks y bibliotecas.
- Transformar código entre paradigmas (procedural → orientado a objetos,
  callbacks → async/await).

**Práctica recomendada:** todo refactoring asistido por IA debe ejecutarse
con una suite de tests completa como red de seguridad. La secuencia es
siempre: tests verdes → refactor con IA → tests verdes.

### 9.4. Modernización de sistemas legacy

Una de las aplicaciones más prometedoras de la IA en mantenimiento es la
modernización de sistemas legacy:

- Análisis y documentación de código sin documentación.
- Traducción entre lenguajes de programación.
- Extracción de reglas de negocio embebidas en código legacy.
- Generación de tests para código sin cobertura.
- Migración incremental de monolitos a arquitecturas modernas.

### 9.5. Riesgos y limitaciones

- **Refactorizaciones que cambian comportamiento**: la IA puede alterar
  sutilmente el comportamiento del código durante un refactoring,
  especialmente en casos borde.
- **Pérdida de contexto histórico**: el código legacy a veces tiene
  decisiones "extrañas" que responden a razones válidas que no están
  documentadas.
- **Migración incompleta**: la IA puede migrar el 80% de un sistema
  legacy con facilidad, pero el 20% restante (los casos especiales, las
  integraciones oscuras) puede ser más difícil y costoso que hacerlo
  manualmente.

---

## 10. El nuevo profesional del software

> [!IMPORTANT]
> *No desaparece el ingeniero de software — desaparece el ingeniero de software que solo sabe escribir código. El nuevo profesional diseña, evalúa, decide y asume la responsabilidad que la IA no puede asumir.*

*La revisión sistemática (§2.7) documenta la transformación del rol
profesional. Gartner proyecta que el 80% de la fuerza de trabajo necesitará
actualizarse para 2027 [43], y el empleo junior cae 9-10% con la adopción
de IA [45].*

### 10.1. La transformación del rol

La progresión descrita en las secciones anteriores dibuja un cuadro claro: el
profesional de software está migrando de **productor de código** a
**orquestador de un proceso de producción de software**. Esto no es una
degradación del rol — es una elevación.

```
Rol tradicional                    Rol emergente
────────────────────────────────────────────────────────────
Escribe código                  →  Especifica y evalúa código
Implementa diseños              →  Evalúa diseños propuestos
Ejecuta tests manualmente       →  Diseña estrategias de testing
Configura infraestructura       →  Valida configuraciones generadas
Documenta (cuando tiene tiempo) →  Revisa documentación generada
Mantiene y corrige              →  Supervisa remediación automática
────────────────────────────────────────────────────────────
Competencia central: escribir   →  Competencia central: evaluar
```

Andrej Karpathy, que en 2025 acuñó el término *vibe coding* para describir
la aceptación de código generado sin comprenderlo, ya en 2026 lo considera
obsoleto y propone la *ingeniería agéntica*: el profesional no escribe código
el 99% del tiempo — orquesta agentes que lo hacen, actuando como supervisor
[44]. Addy Osmani formaliza esta evolución con la regla del 70/30: dedicar
el 70% del esfuerzo a la definición del problema y solo el 30% a la
ejecución [42].

### 10.2. Las nuevas competencias

Gartner proyecta que el **80% de la fuerza de trabajo en ingeniería**
necesitará actualizarse para 2027 [43]. El profesional del software en la
era de la IA necesita un conjunto de competencias que difiere
significativamente del perfil tradicional:

**Competencias técnicas:**
- **Lectura de código** como habilidad primaria (no secundaria).
- **Evaluación arquitectónica**: capacidad de analizar y juzgar propuestas.
- **Testing y validación**: diseño de estrategias de verificación robustas.
- **Especificación precisa**: capacidad de comunicar requerimientos de
  manera no ambigua — tanto a humanos como a agentes.
- **Seguridad**: identificación de vulnerabilidades en código generado.

**Competencias de proceso:**
- **Supervisión efectiva**: saber qué revisar, con qué profundidad, y
  cuándo confiar vs. desconfiar del output de la IA.
- **Orquestación de herramientas**: integrar múltiples herramientas de IA
  en un flujo de trabajo coherente.
- **Trazabilidad**: mantener un registro claro de decisiones y su
  justificación.

**Competencias profesionales:**
- **Pensamiento crítico**: cuestionar activamente los resultados de la IA.
- **Conocimiento de dominio**: lo que la IA no tiene y no puede reemplazar.
- **Responsabilidad profesional**: asumir la responsabilidad por un
  producto que fue parcialmente generado por máquinas.

### 10.3. Lo que no cambia

Es importante notar que hay aspectos fundamentales de la profesión que no
cambian con la IA:

- La necesidad de entender **qué se está construyendo y para quién**.
- La importancia de la **comunicación con stakeholders**.
- La responsabilidad por la **calidad y seguridad** del producto.
- La capacidad de **resolver problemas** que no encajan en patrones
  conocidos.
- La experiencia de **dominio** que permite detectar errores que la IA
  no puede ver.
- La **ética profesional** y la responsabilidad por el impacto del software.

### 10.4. El impacto en los desarrolladores junior

Un hallazgo particularmente preocupante proviene de un estudio de
Northeastern University (2025): cuando las empresas adoptan IA generativa,
el empleo de desarrolladores junior (0-3 años de experiencia) **cae un
9-10%** en seis trimestres, mientras que el empleo senior apenas se modifica
[45]. La contracción no se debe a que los seniors sean más productivos con
IA, sino a que las empresas reducen la contratación de perfiles que consideran
más reemplazables.

Esto genera un problema a mediano plazo: si los juniors no entran al mercado,
¿de dónde saldrán los seniors del futuro? La atrofia de habilidades ya es
medible: el 59% de los desarrolladores admite usar código generado por IA
que **no comprende completamente** [46]. Los juniors son especialmente
vulnerables porque carecen de los fundamentos para evaluar críticamente el
output de la IA.

### 10.5. Riesgos y limitaciones

- **Atrofia de habilidades**: la dependencia excesiva de la IA puede
  erosionar las habilidades fundamentales de programación.
- **Pérdida de comprensión profunda**: si el profesional nunca escribe
  código complejo, puede perder la capacidad de evaluarlo.
- **La brecha generacional**: profesionales formados antes de la IA
  necesitan adaptarse; profesionales formados solo con IA pueden carecer
  de fundamentos.
- **Sesgo de percepción**: un estudio de Microsoft (2025) encontró que
  los ingenieros que usan IA reciben **evaluaciones de competencia más
  bajas** por trabajo idéntico — efecto que se duplica para mujeres [47].

---

## 11. Conclusiones

> [!IMPORTANT]
> *La ingeniería de software no muere en la era de la IA — renace con un propósito más claro: garantizar que lo que construimos funcione, sea seguro y tenga sentido, sin importar quién (o qué) escribió el código.*

### 11.1. La inversión del paradigma

Este documento ha recorrido cada etapa del ciclo de vida del software para
mostrar una transformación que ya no es futura sino presente. La revisión
sistemática de la literatura (§2) — basada en 77 estudios de 2022 a 2026 —
provee la base empírica para las siguientes conclusiones:

```
Lo que era                              Lo que es
────────────────────────────────────────────────────────────
El humano escribe el código          →  La IA escribe el código
La IA asiste ocasionalmente          →  La IA participa en cada etapa
El testing complementa               →  El testing es la línea de defensa
Escribir código = competencia core   →  Evaluar código = competencia core
La calidad se construye              →  La calidad se supervisa y valida
────────────────────────────────────────────────────────────
```

Esta inversión no es teórica. El 41% del código ya es generado por IA [23].
El 85% de los desarrolladores usa herramientas de IA regularmente [23]. Los
agentes autónomos resuelven el 72-80% de los problemas en benchmarks
reales [5][25]. La transformación ya ocurrió — lo que falta es que las
prácticas de ingeniería se actualicen para acompañarla.

### 11.2. Las cinco lecciones que emergen

**1. La especificación es el nuevo código.**

En cada etapa — desde la factibilidad hasta el mantenimiento — la calidad
del output de la IA depende directamente de la calidad del input humano.
La regla del 70/30 de Osmani lo formaliza: el 70% del esfuerzo debe ir a
definir el problema, no a ejecutar la solución [42]. Esto no es una
limitación de la IA — es una característica de la buena ingeniería que
siempre estuvo ahí, pero que la velocidad de la generación manual ocultaba.

**2. La supervisión no escala linealmente.**

El modelo "humano en el centro" funciona cuando la velocidad de generación
es moderada. Pero cuando un agente puede producir miles de líneas en
minutos, la revisión humana se convierte en cuello de botella. Los datos lo
confirman: el output individual crece 98%, pero el tiempo de revisión de
PRs crece 91% [42]. La solución no es eliminar la supervisión sino diseñar
**prácticas de supervisión que escalen**: testing automatizado, validación
por pipeline, revisión por niveles de riesgo.

**3. La calidad se degrada si no se defiende activamente.**

Los datos de calidad son una llamada de atención: 1.7x más issues en PRs
generados por IA [37], 2.74x más vulnerabilidades XSS [37], 8x más
duplicación de código [34], refactoring en caída libre [34]. Gartner
predice un aumento del 2500% en defectos para 2028 si se adoptan enfoques
"prompt-to-app" sin disciplina [60]. La velocidad sin calidad es deuda
técnica con interés compuesto.

**4. Cada etapa requiere su propio modelo de integración.**

No hay un enfoque único para integrar la IA en el SDLC. La factibilidad
necesita un modelo de asistencia con validación humana fuerte. Los
requerimientos necesitan un ciclo iterativo de generación y revisión. La
implementación necesita especificación precisa e incrementalidad. El
testing necesita que el humano valide los tests, no solo el código. El
despliegue necesita cautela extrema por su impacto en producción. El
mantenimiento necesita pipelines de validación para las refactorizaciones.

**5. El profesional se eleva, no desaparece.**

La transformación del rol — de productor de código a orquestador,
evaluador y responsable — no es una degradación. Es una elevación hacia
lo que siempre fue el corazón de la ingeniería: tomar decisiones
informadas, asumir responsabilidad por los resultados y garantizar que lo
construido sirve a su propósito. La IA automatiza la ejecución; el
humano conserva el juicio.

### 11.3. Preguntas abiertas

La velocidad del cambio genera preguntas que aún no tienen respuesta
definitiva:

- **¿Cómo formamos juniors?** Si las tareas de entrada son las primeras
  en ser automatizadas, ¿cómo adquieren experiencia los futuros seniors?
  El empleo junior ya cae 9-10% con la adopción de IA [45].
- **¿Puede la IA supervisar a la IA?** Cuando el volumen de código
  generado supera la capacidad de revisión humana, ¿es viable un modelo
  de "IA supervisa IA"? ¿O genera un problema recursivo de confianza?
- **¿Cómo medimos la productividad real?** Si la percepción y la realidad
  divergen en 43 puntos porcentuales (como mostró el estudio METR [7]),
  ¿qué métricas usamos?
- **¿Dónde está el equilibrio?** ¿Cuál es el ratio óptimo de intervención
  humana para cada tipo de tarea?

### 11.4. Hacia dónde vamos

El trabajo de Panigo, Petkoff Bankoff, Pasini y Pesado [2] demostró en
2024 que los LLMs son herramientas viables para las primeras etapas del
SDLC, enfatizando la necesidad de una mirada crítica profesional sobre los
resultados. Este documento extiende esa conclusión a todo el ciclo de vida:

**La IA es viable en cada etapa del desarrollo de software. En cada una
de esas etapas, la mirada crítica del profesional es imprescindible.**

La ingeniería de software en la era de la IA no es más fácil. Es
**diferente**. Requiere menos habilidad para escribir código y más habilidad
para evaluarlo, especificarlo, testearlo y asumir la responsabilidad por
él. Requiere menos conocimiento de sintaxis y más conocimiento de dominio.
Menos tiempo escribiendo y más tiempo pensando.

En definitiva, requiere más ingeniería. No menos.

---

## 12. Referencias

[1] N. Jha y R. Popli. "Artificial Intelligence For Software Testing-Perspectives And Practices". *2021 Fourth International Conference on Computational Intelligence and Communication Technologies (CCICT)*, 2021. DOI: 10.1109/CCICT53244.2021.00075.

[2] A. Panigo, K. Petkoff Bankoff, A. Pasini y P. Pesado. "Inteligencia Artificial en Ingeniería de Software: Etapas de Elicitación y Análisis de requerimientos". *XXX Congreso Argentino de Ciencias de la Computación (CACIC)*, La Plata, 2024. http://sedici.unlp.edu.ar/handle/10915/178398

[3] B. Kitchenham y S. Charters. "Guidelines for performing Systematic Literature Reviews in Software Engineering". *EBSE Technical Report*, Keele University, 2007.

[4] J. Wang et al. "Software Testing with Large Language Models: Survey, Landscape, and Vision". *IEEE Transactions on Software Engineering*, 2024. DOI: 10.1109/TSE.2024.3368208.

[5] C. E. Jimenez et al. "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?". *ICLR 2024*. arXiv:2310.06770.

[6] S. Peng, E. Kalliamvakou, P. Cihon y M. Demirer. "The Impact of AI on Developer Productivity: Evidence from GitHub Copilot". *Communications of the ACM*, marzo 2024. arXiv:2302.06590.

[7] METR. "Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity". arXiv:2507.09089, julio 2025.

[8] J. Liu et al. "Large Language Model-Based Agents for Software Engineering: A Survey". *ACM Transactions on Software Engineering and Methodology*, 2024. DOI: 10.1145/3712003.

[9] C. Lopez-Martin et al. "Leveraging Large Language Models for Predicting Cost and Duration in Software Engineering Projects". arXiv:2409.09617, septiembre 2024.

[10] L. A. Cabrera-Diego et al. "Large Language Models for Early-Stage Software Project Estimation: A Systematic Mapping Study". *Applied Sciences (MDPI)*, diciembre 2025. https://www.mdpi.com/2076-3417/15/24/13099

[11] T.-L. Bui. "An LLM-based multi-agent framework for agile effort estimation". arXiv:2509.14483, septiembre 2025.

[12] M. Hasnain et al. "Effort and Size Estimation in Software Projects with Large Language Model-based Intelligent Interfaces". arXiv:2402.07158, febrero 2024.

[13] "Generative AI in Systems Engineering: A Framework for Risk Assessment of LLMs". arXiv:2602.04358, febrero 2026.

[14] M. A. Sami et al. "Early Results of an AI Multiagent System for Requirements Elicitation and Analysis". *Product-Focused Software Process Improvement (PROFES 2024)*, Springer LNCS, 2024. DOI: 10.1007/978-3-031-78386-9_20.

[15] R. Gonzalez et al. "Can LLMs Generate User Stories and Assess Their Quality?". arXiv:2507.15157, julio 2025.

[16] W. Zhao et al. "Elicitron: An LLM Agent-Based Simulation Framework for Design Requirements Elicitation". arXiv:2404.16045, abril 2024.

[17] "Research directions for using LLM in software requirement engineering: a systematic review". *Frontiers in Computer Science*, 2025. DOI: 10.3389/fcomp.2025.1519437.

[18] M. Galster et al. "Artificial Intelligence for Software Architecture: Literature Review and the Road Ahead". arXiv:2504.04334, abril 2025.

[19] S. Dhar et al. "DRAFT-ing Architectural Design Decisions using LLMs". arXiv:2506.22688, 2025.

[20] A. Helmi. "ARLO: A Tailorable Approach for Transforming Natural Language Software Requirements into Architecture using LLMs". 2025.

[21] V. De Luca et al. "LLM-Based Explainability at Design Time: Detecting Elasticity Antipatterns in Software Architectures". Springer, 2025.

[22] D. Taibi et al. "Exploring Architectural Smells Detection Through LLMs". Springer, 2025.

[23] JetBrains. "The State of Developer Ecosystem 2025". JetBrains Research, octubre 2025. https://blog.jetbrains.com/research/2025/10/state-of-developer-ecosystem-2025/

[24] GitHub. "Octoverse 2024: The state of open source and rise of AI". GitHub Blog, 2024. https://github.blog/news-insights/octoverse/octoverse-2024/

[25] Z. Rasheed et al. "Software Development Life Cycle Perspective: A Survey of Benchmarks for Code LLMs and Agents". arXiv:2505.05283, mayo 2025.

[26] "Systematic Review on LLM-Based Unit Testing". 2025. Analiza 105 papers hasta marzo 2025.

[27] R. Tufano et al. "On the Use of Large Language Models in Mutation Testing". arXiv:2406.09843, junio 2024.

[28] Meta Engineering. "Mutation-Guided LLM-based Test Generation at Meta". *FSE 2025 (Industry Papers)*, 2025.

[29] S. Joshi. "A Review of Generative AI and DevOps Pipelines: CI/CD, Agentic Automation, MLOps Integration, and Large Language Models". SSRN, 2025.

[30] M. Pereira et al. "Comparative Analysis of AI-Driven Security Approaches in DevSecOps: Challenges, Solutions, and Future Directions". arXiv:2504.19154, abril 2025.

[31] R. Goncalves et al. "AI Techniques in the Microservices Life-Cycle: A Systematic Mapping Study". *Computing (Springer)*, 2025.

[32] M. Nogueira et al. "ACE: Automated Technical Debt Remediation with Validated Large Language Model Refactorings". arXiv:2507.03536, julio 2025.

[33] S. Kacimi et al. "PromptDebt: A Comprehensive Study of Technical Debt Across LLM Projects". arXiv:2509.20497, septiembre 2025.

[34] GitClear. "AI Copilot Code Quality: 2025 Data Suggests 4x Growth in Code Clones". Febrero 2025. https://www.gitclear.com/ai_assistant_code_quality_2025_research

[35] J. Garcia et al. "AI-Driven Decision Support Systems in Agile Software Project Management: Enhancing Risk Mitigation and Resource Allocation". *MDPI Systems*, 2025. https://www.mdpi.com/2079-8954/13/3/208

[36] E. Psaltis et al. "Cognitive Agents Powered by Large Language Models for Agile Software Project Management". *MDPI Electronics*, enero 2025.

[37] CodeRabbit. "State of AI vs Human Code Generation Report". Diciembre 2025. https://www.coderabbit.ai/blog/state-of-ai-vs-human-code-generation-report

[38] H. Pearce et al. "Asleep at the Keyboard? Assessing the Security of GitHub Copilot's Code Contributions". *2022 IEEE Symposium on Security and Privacy (SP)*, 2022.

[39] Apiiro Research. "4x Velocity, 10x Vulnerabilities: AI Coding Assistants Are Shipping More Risks". 2025. https://apiiro.com/blog/4x-velocity-10x-vulnerabilities-ai-coding-assistants-are-shipping-more-risks/

[40] Qodo. "State of AI Code Quality in 2025". Qodo Research, 2025. https://www.qodo.ai/reports/state-of-ai-code-quality/

[41] Trend Micro. "Slopsquatting: When AI Agents Hallucinate Malicious Packages". 2025. https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/slopsquatting-when-ai-agents-hallucinate-malicious-packages

[42] A. Osmani. "The 80% Problem in Agentic Coding". Substack, 2025. https://addyo.substack.com/p/the-80-problem-in-agentic-coding

[43] Gartner. "Generative AI Will Require 80% of Engineering Workforce to Upskill Through 2027". Gartner Newsroom, octubre 2024. https://www.gartner.com/en/newsroom/press-releases/2024-10-03-gartner-says-generative-ai-will-require-80-percent-of-engineering-workforce-to-upskill-through-2027

[44] A. Karpathy. "De vibe coding a agentic engineering". 2026. Citado en The Hans India, enero 2026. https://www.thehansindia.com/technology/tech-news/karpathy-says-vibe-coding-is-fading-as-agentic-engineering-becomes-the-new-ai-coding-era-1045758

[45] A. Modestino et al. "The Impact of Generative AI on Job Opportunities for Junior Software Engineers". *Northeastern University*, 2025.

[46] Clutch. "Blind Trust in AI: Most Devs Use AI-Generated Code They Don't Understand". Junio 2025. https://clutch.co/resources/devs-use-ai-generated-code-they-dont-understand

[47] Microsoft Research. "New Future of Work Report 2025". Diciembre 2025. https://www.microsoft.com/en-us/research/publication/new-future-of-work-report-2025/

[48] C. Fan (Hymel). "The AI-Native Software Development Lifecycle: A Theoretical and Practical New Methodology". arXiv:2408.03416, agosto 2024.

[49] GitHub. "Spec-driven development with AI: Get started with a new open source toolkit". GitHub Blog, 2025. https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/

[50] AI-DLC 2026. "AI-Driven Development Lifecycle". Han Research, 2026. https://han.guru/papers/ai-dlc-2026/

[51] Microsoft. "An AI-led SDLC: Building an End-to-End Agentic Software Development Lifecycle". Microsoft Tech Community, 2025. https://techcommunity.microsoft.com/blog/appsonazureblog/an-ai-led-sdlc-building-an-end-to-end-agentic-software-development-lifecycle-wit/4491896

[52] S. Willison. "Context Engineering". SimonWillison.net, junio 2025. https://simonwillison.net/2025/jun/27/context-engineering/

[53] Stack Overflow. "2025 Developer Survey". Stack Overflow, 2025. https://survey.stackoverflow.co/2025

[54] Entrepreneur. "AI Is Already Writing About 30% of Code at Microsoft and Google". 2025. https://www.entrepreneur.com/business-news/ai-is-taking-over-coding-at-microsoft-google-and-meta/490896

[55] The Standish Group. "CHAOS Report 2020". The Standish Group International, 2020.

[56] B. W. Boehm et al. *Software Cost Estimation with COCOMO II*. Prentice Hall, 2000.

[57] I. Papadopoulos et al. "Enhancing the student's logical thinking with Gherkin language". *2017 IEEE Global Engineering Education Conference (EDUCON)*, 2017. DOI: 10.1109/EDUCON.2017.7943054.

[58] E. Whitten y L. Bentley. *Systems Analysis and Design Methods*. 7.ª ed. McGraw-Hill, 2007.

[59] F. Dalpiaz y S. Brinkkemper. "Agile Requirements Engineering: From User Stories to Software Architectures". *2021 IEEE 29th International Requirements Engineering Conference (RE)*, 2021.

[60] Gartner. "Strategic Predictions for IT Organizations 2026 and Beyond". Gartner Newsroom, 2025. https://www.gartner.com/en/articles/strategic-predictions-for-2026

[61] Forrester. "Predictions 2026: AI Moves from Hype to Hard Hat Work". Forrester Blog, 2025. https://www.forrester.com/blogs/predictions-2026-ai-moves-from-hype-to-hard-hat-work/

[62] A. Osmani. "Agentic Engineering". AddyOsmani.com, 2025-2026. https://addyosmani.com/blog/agentic-engineering/

[63] N. Nascimento et al. "LLMs' Reshaping of People, Processes, Products, and Society in Software Development: A Comprehensive Exploration with Early Adopters". arXiv:2503.05012, marzo 2025.

[64] GitHub. "Octoverse 2025: The state of open source". 2025. https://octoverse.github.com/

[65] Stack Overflow. "2024 Developer Survey". Stack Overflow, 2024. https://survey.stackoverflow.co/2024/ai

[66] JetBrains. "The State of Developer Ecosystem 2024". JetBrains Research, diciembre 2024.

[67] Gartner. "Top Predictions for IT Organizations 2025 and Beyond". Octubre 2024. https://www.gartner.com/en/newsroom/press-releases/2024-10-22-gartner-unveils-top-predictions-for-it-organizations-and-users-in-2025-and-beyond

[68] IT Revolution. "The Revenge of QA: How AI Code Generation Is Exposing Decades of Process Debt". 2025. https://itrevolution.com/articles/the-revenge-of-qa-how-ai-code-generation-is-exposing-decades-of-process-debt/

[69] C. Jaspan et al. (Google). "Developer Productivity With and Without GitHub Copilot: A Longitudinal Study". arXiv:2509.20353, septiembre 2025.

[70] E. Barr et al. "Large Language Models for Software Testing: A Research Roadmap". arXiv:2509.25043, septiembre 2025.

[71] D. Russo. "From Today's Code to Tomorrow's Symphony: The AI Transformation of Developer's Routine by 2030". arXiv:2405.12731, mayo 2024.

[72] A. Guerrero et al. "Software engineering education in the era of conversational AI: current trends and future directions". *Frontiers in Artificial Intelligence*, 2024. DOI: 10.3389/frai.2024.1436350.

[73] "A systematic literature review on the impact of AI models on the security of code generation". *Frontiers in Big Data*, 2024. DOI: 10.3389/fdata.2024.1386720.

[74] Y. Wang et al. "LLMs: A game-changer for software engineers?". *Journal of Computer Languages (ScienceDirect)*, 2025.

[75] "Using LLMs to Enhance Code Quality: A Systematic Literature Review". *ScienceDirect*, 2025.

[76] K. Macklon et al. "LLMorpheus: Mutation Testing Using Large Language Models". *IEEE TSE*, 2025.

[77] A. M. Dakhel et al. "Effective Test Generation Using Pre-trained Large Language Models and Mutation Testing". *Information and Software Technology*, 2024.
