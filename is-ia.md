# IS-IA: Ingeniería de Software en la Era de la IA

*Prácticas, metodologías y transformaciones para construir software de calidad
cuando la inteligencia artificial participa activamente en cada etapa del desarrollo.*

---

## Tabla de contenidos

1. [Introducción: el punto de inflexión](#1-introducción-el-punto-de-inflexión)
2. [La nueva realidad del desarrollo de software](#2-la-nueva-realidad-del-desarrollo-de-software)
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

---

## 2. La nueva realidad del desarrollo de software

> [!IMPORTANT]
> *En 2025, la pregunta dejó de ser "¿debería usar IA para programar?" y pasó a ser "¿cómo integro la IA en cada etapa sin perder el control?"*

### 2.1. Los números que cambiaron todo

La adopción de herramientas de IA en el desarrollo de software dejó de ser una
tendencia para convertirse en el estándar de la industria. Los datos más
recientes muestran una transformación que ya es irreversible:

- **El 84% de los desarrolladores** ya utiliza herramientas de IA en su
  trabajo diario (GitHub, 2024) [3].
- **El 41% del código** en GitHub es generado por IA (GitHub Copilot
  Report, 2025) [4].
- **El 76% de los problemas** de repositorios reales pueden ser resueltos
  por agentes autónomos como SWE-Agent (Princeton, 2024) [5].
- **El 97% de los desarrolladores** ha usado herramientas de IA al menos
  una vez (Stack Overflow Developer Survey, 2024) [6].
- **55% de aumento en productividad** reportado por desarrolladores que usan
  GitHub Copilot para tareas de codificación (GitHub, 2022) [7].

Pero los números también cuentan una historia más compleja. Un estudio
controlado y aleatorizado de METR (2025) reveló una paradoja inquietante:
cuando 16 desarrolladores experimentados trabajaron en sus propios
repositorios open-source, el uso de herramientas de IA **incrementó** el
tiempo de completamiento en un 19% — a pesar de que los desarrolladores
**percibían** un ahorro del 20-24% [14]. La productividad percibida y la
productividad real pueden divergir significativamente.

No son solo números de adopción — son números de **transformación
estructural**. Cuando casi la mitad del código es generado por máquinas y
prácticamente todos los desarrolladores usan herramientas de IA, las
prácticas de ingeniería de software diseñadas para un mundo donde los humanos
escriben todo el código necesitan ser repensadas. Pero repensadas con rigor,
no con entusiasmo ciego.

### 2.2. La evolución: de autocompletar a orquestar

La integración de la IA en el desarrollo de software no ocurrió de golpe.
Siguió una progresión que permite entender hacia dónde vamos:

**Generación 1 — Autocompletado inteligente (2018-2020)**

Herramientas como Tabnine y los primeros modelos de completado predecían la
siguiente línea de código. El desarrollador seguía escribiendo; la IA solo
sugería. El impacto en la productividad era modesto pero medible [7].

**Generación 2 — Generación de funciones (2021-2022)**

GitHub Copilot marcó un antes y un después. A partir de un comentario o una
firma de función, el modelo generaba implementaciones completas. El
desarrollador pasó de escribir a **revisar y aceptar**. La adopción fue
explosiva: un millón de usuarios en los primeros meses [3].

**Generación 3 — Conversación y contexto (2022-2023)**

ChatGPT y los chatbots especializados permitieron mantener conversaciones
sobre código — explicar errores, refactorizar, diseñar arquitecturas a través
del diálogo. El código dejó de ser el único artefacto; el **proceso de
razonamiento** se volvió visible y compartible.

**Generación 4 — Agentes autónomos (2024-2025)**

SWE-Agent, Devin, Claude Code, Cursor Agent Mode. La IA ya no espera
instrucciones línea por línea — recibe un objetivo, planifica una estrategia,
ejecuta múltiples acciones (leer código, modificar archivos, ejecutar tests,
corregir errores) y reporta resultados. El desarrollador pasó de escribir
código a **supervisar y validar** el trabajo de un agente [5].

**Generación 5 — IA en todo el SDLC (2025-2026)**

La frontera actual. La IA no solo genera código — participa en la
elicitación de requerimientos [2], propone arquitecturas, genera tests,
configura despliegues y monitorea producción. El profesional del software se
convierte en **orquestador, evaluador y responsable último** de un proceso
donde la IA interviene en cada paso.

```
Generación    Capacidad              Rol del humano         Impacto
─────────────────────────────────────────────────────────────────────
Gen 1         Predice la siguiente   Escribe                Bajo
(2018)        palabra                                       (~10% más rápido)

Gen 2         Genera funciones       Revisa y acepta        Medio
(2021)        completas                                     (~55% más rápido)

Gen 3         Conversa sobre         Dialoga y decide       Alto
(2022)        diseño y código                               (impacto cualitativo)

Gen 4         Resuelve problemas     Supervisa y valida     Muy alto
(2024)        de manera autónoma                            (76% resolución)

Gen 5         Participa en todo      Orquesta, evalúa,      Transformador
(2025)        el SDLC                asume responsabilidad  (cambia la profesión)
─────────────────────────────────────────────────────────────────────
```

### 2.3. Lo que la IA puede y lo que no puede (todavía)

La capacidad de la IA en el desarrollo de software no es uniforme. Es
fundamental entender el mapa de capacidades para diseñar prácticas adecuadas:

**Lo que la IA hace bien hoy:**
- Generar código boilerplate y funciones estándar
- Escribir tests unitarios a partir de código existente
- Traducir entre lenguajes de programación
- Explicar código complejo
- Generar documentación técnica
- Detectar patrones de errores comunes
- Refactorizar código siguiendo buenas prácticas
- Generar entrevistas y historias de usuario [2]

**Lo que la IA hace de manera aceptable:**
- Diseñar arquitecturas simples a medianas
- Resolver bugs en código conocido
- Generar configuraciones de infraestructura
- Escribir tests de integración
- Analizar requerimientos y detectar inconsistencias

**Lo que la IA aún no hace bien:**
- Entender requerimientos de negocio complejos y ambiguos
- Tomar decisiones arquitectónicas con implicaciones a largo plazo
- Evaluar trade-offs de seguridad en contextos específicos
- Comprender el contexto organizacional y político de un proyecto
- Asumir responsabilidad profesional por las decisiones

> [!IMPORTANT]
> *La IA es un implementador cada vez más capaz, pero no es un ingeniero. La ingeniería implica responsabilidad, juicio y contexto — tres cosas que siguen siendo irreductiblemente humanas.*

### 2.4. El principio del "humano en el centro"

La integración de la IA en el SDLC no es un proceso de reemplazo sino de
**reconfiguración de responsabilidades**. En cada etapa, el profesional pasa
de ser el ejecutor principal a ser el **director, evaluador y responsable
último**. Este principio se repite a lo largo de todo este documento:

1. **La IA propone, el humano dispone.** Cada artefacto generado por IA —
   sea un conjunto de requerimientos, una arquitectura, código o un plan de
   testing — debe ser evaluado por un profesional antes de ser aceptado.

2. **La supervisión escala con el riesgo.** No todo código necesita el mismo
   nivel de revisión. Una función utilitaria simple no requiere la misma
   atención que un módulo de autenticación o un cálculo financiero.

3. **La trazabilidad es innegociable.** En un mundo donde la IA genera
   artefactos, saber **quién decidió qué y por qué** se vuelve más
   importante que nunca.

4. **La calidad se valida, no se asume.** El hecho de que un agente haya
   "resuelto" un problema no significa que la solución sea correcta,
   completa, segura o mantenible.

---

## 3. Estudio de factibilidad

> [!IMPORTANT]
> *El estudio de factibilidad es la etapa donde un error cuesta menos de corregir. Paradójicamente, es donde menos se invierte — y donde la IA puede aportar más sin riesgo.*

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
[8]. Un estudio de factibilidad riguroso no garantiza el éxito, pero su
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
  proyecto (modelos como COCOMO pueden ser asistidos por IA) [9].
- Generar análisis comparativos build vs. buy.
- Proyectar costos de infraestructura a partir de las necesidades
  técnicas descritas.

**Factibilidad operativa:**
- Evaluar el impacto organizacional del proyecto a partir de la
  descripción del contexto.
- Identificar necesidades de capacitación y cambio organizacional.
- Generar matrices de riesgo iniciales.

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
  criterios de aceptación en sintaxis Gherkin [10]).
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
software [11]. Tradicionalmente, depende de entrevistas, talleres,
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
priorizar y estructurar los requerimientos [11]. Las historias de usuario son
el formato dominante en metodologías ágiles, con aproximadamente el 70% de
los equipos utilizándolas como herramienta principal de especificación [12].

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
  discutidas.
- Sugerir patrones de diseño apropiados para problemas específicos.

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
especificación precisa produce código preciso.

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
secundario y se convierte en el **principal mecanismo de calidad**. El
profesional debe ser capaz de:

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

La documentación es un área donde la IA tiene una ventaja natural: no se
cansa, no la pospone, y puede generar documentación consistente y completa
en segundos. La responsabilidad del profesional es **validar la precisión**
de lo documentado.

### 6.4. La crisis de calidad del código generado por IA

Los datos sobre calidad del código generado por IA son preocupantes y
ameritan una subsección propia. Un análisis de CodeRabbit (2025) sobre 470
pull requests en repositorios open-source encontró que los PRs generados por
IA contienen **1.7x más issues** que los humanos (10.83 vs. 6.45 por PR)
[15]. Las vulnerabilidades de seguridad son especialmente alarmantes:

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

El estudio de GitClear (2025), basado en 211 millones de líneas de código
(2020-2024), revela tendencias estructurales preocupantes: el código
asociado a refactoring cayó del 25% (2021) a menos del 10% (2024), mientras
que la duplicación de código creció 8x [16]. El código que necesita ser
revisado dentro de las 2 semanas siguientes pasó de 3.1% a 7.9%.

**Slopsquatting: un nuevo vector de ataque**

Los LLMs también introdujeron un nuevo riesgo de seguridad sin precedentes:
el *slopsquatting*. Los modelos alucinan nombres de paquetes que no existen
pero son plausibles — en promedio, una quinta parte de los paquetes
recomendados no existe (205.000 nombres alucinados documentados). El 43%
de estos paquetes fantasma aparecen consistentemente al repetir los mismos
prompts. Los atacantes pueden pre-registrar estos nombres en repositorios
públicos para distribuir malware [17].

### 6.5. Riesgos y limitaciones

- **Código que funciona pero no se entiende**: la IA puede generar
  soluciones funcionales pero opacas, difíciles de mantener o depurar.
- **Dependencias innecesarias**: los LLMs tienden a sugerir bibliotecas
  externas donde código simple resolvería el problema.
- **Vulnerabilidades de seguridad**: el 51.24% de los programas C generados
  por ChatGPT contienen al menos una vulnerabilidad de seguridad. Más del
  40% del código generado por IA tiene fallas de seguridad [13].
- **La "ilusión de productividad"**: generar código rápido no es lo mismo
  que generar *buen* código rápido. El output individual puede crecer 98%,
  pero el tiempo de revisión de PRs crece hasta 91% [18].
- **Slopsquatting**: los LLMs alucinan nombres de paquetes inexistentes
  que pueden ser explotados como vector de ataque a la cadena de suministro
  [17].

> [!IMPORTANT]
> *El 59% de los desarrolladores admite usar código generado por IA que no entiende completamente. Cuando Gartner predice un aumento del 2500% en defectos de software por enfoques "prompt-to-app" para 2028, la ingeniería de software rigurosa no es un lujo — es una necesidad de supervivencia.*

---

## 7. Testing

> [!IMPORTANT]
> *En un mundo donde la IA genera código, el testing pasa de ser una actividad complementaria a ser la principal línea de defensa. Testear es la habilidad que no muere — es la que más importa.*

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
- Introducir mutaciones controladas en el código para verificar que los
  tests las detectan.
- La IA puede generar mutantes más sofisticados que las herramientas
  tradicionales.
- GPT-4o alcanza un **93.4% de tasa de detección de fallas** en mutation
  testing, comparado con 71.7% de LEAM, 51.3% de PIT y 74.4% de Major
  — las herramientas tradicionales dominantes [19].
- Meta desplegó testing guiado por mutaciones con LLMs en producción
  (Facebook, Instagram, WhatsApp). Los ingenieros de privacidad aceptaron
  el **73% de los tests generados** [20].

**Testing de seguridad:**
- Identificación de vulnerabilidades comunes (OWASP Top 10).
- Generación de casos de prueba de penetración básicos.
- Análisis estático de seguridad asistido.

El crecimiento de la investigación en testing con IA es explosivo: de 1
paper en 2021 a 73 en 2024, con la generación de tests representando el 60%
del volumen total de investigación [21].

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
  excesivos.
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
frustración, y el 40% de los presupuestos de IT se destina a abordarla
(Gartner, 2025) [22]. La IA puede asistir en:

- **Detección**: identificar patrones de código que indican deuda técnica
  (código duplicado, complejidad ciclomática excesiva, acoplamiento,
  falta de tests). GPT-4 detecta el **86.7%** de las oportunidades de
  refactoring en proyectos reales [23].
- **Cuantificación**: estimar el esfuerzo necesario para remediar la deuda
  identificada.
- **Priorización**: sugerir qué deuda abordar primero basándose en el
  impacto en la velocidad de desarrollo.
- **Remediación**: generar refactorizaciones automatizadas para patrones
  comunes de deuda técnica.

Un dato crucial: aunque GPT-4 detecta el 86.7% de las oportunidades, solo
genera refactorizaciones funcionalmente correctas el **37%** de las veces.
Sin embargo, cuando se agrega un pipeline de validación automatizada, la
precisión sube al **98%** [23]. La lección es clara: la detección con IA es
excelente, pero la ejecución sin validación es peligrosa.

**Prompt debt: una nueva forma de deuda técnica**

La investigación reciente ha identificado una forma de deuda técnica
completamente nueva: la *prompt debt* — deuda que surge de prácticas
deficientes de prompt engineering en proyectos que usan LLMs. Los "prompt
smells" y "prompt requirement smells" comprometen el rendimiento del modelo
de formas que no son evidentes hasta mucho después [24].

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

La industria está convergiendo hacia un nombre para este nuevo rol. Andrej
Karpathy, que en 2025 acuñó el término *vibe coding* para describir la
aceptación de código generado sin comprenderlo, ya en 2026 lo considera
obsoleto y propone la *ingeniería agéntica*: el profesional no escribe código
el 99% del tiempo — orquesta agentes que lo hacen, actuando como supervisor
[25]. Addy Osmani, líder de ingeniería en Google Chrome, formaliza esta
evolución con la regla del 70/30: dedicar el 70% del esfuerzo a la
definición del problema (especificaciones, criterios de éxito, tests) y solo
el 30% a la ejecución [18].

### 10.2. Las nuevas competencias

Gartner proyecta que el **80% de la fuerza de trabajo en ingeniería**
necesitará actualizarse para 2027 [26]. El profesional del software en la
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

Un hallazgo particularmente preocupante proviene de un estudio de Harvard
(2025): cuando las empresas adoptan IA generativa, el empleo de
desarrolladores junior (0-3 años de experiencia) **cae un 9-10%** en seis
trimestres, mientras que el empleo senior apenas se modifica [27]. La
contracción no se debe a que los seniors sean más productivos con IA, sino a
que las empresas reducen la contratación de perfiles que consideran más
reemplazables.

Esto genera un problema a mediano plazo: si los juniors no entran al mercado,
¿de dónde saldrán los seniors del futuro? La atrofia de habilidades ya es
medible: el 59% de los desarrolladores admite usar código generado por IA
que **no comprende completamente** [28]. Los juniors son especialmente
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
  bajas** por trabajo idéntico — efecto que se duplica para mujeres [29].

---

## 11. Conclusiones

> [!IMPORTANT]
> *La ingeniería de software no muere en la era de la IA — renace con un propósito más claro: garantizar que lo que construimos funcione, sea seguro y tenga sentido, sin importar quién (o qué) escribió el código.*

### 11.1. La inversión del paradigma

Este documento ha recorrido cada etapa del ciclo de vida del software para
mostrar una transformación que ya no es futura sino presente. Los datos son
inequívocos:

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

Esta inversión no es teórica. El 41% del código ya es generado por IA.
El 85% de los desarrolladores usa herramientas de IA regularmente. Los
agentes autónomos resuelven el 72-80% de los problemas en benchmarks
reales. La transformación ya ocurrió — lo que falta es que las prácticas
de ingeniería se actualicen para acompañarla.

### 11.2. Las cinco lecciones que emergen

**1. La especificación es el nuevo código.**

En cada etapa — desde la factibilidad hasta el mantenimiento — la calidad
del output de la IA depende directamente de la calidad del input humano.
La regla del 70/30 de Osmani lo formaliza: el 70% del esfuerzo debe ir a
definir el problema, no a ejecutar la solución. Esto no es una limitación
de la IA — es una característica de la buena ingeniería que siempre estuvo
ahí, pero que la velocidad de la generación manual ocultaba.

**2. La supervisión no escala linealmente.**

El modelo "humano en el centro" funciona cuando la velocidad de generación
es moderada. Pero cuando un agente puede producir miles de líneas en
minutos, la revisión humana se convierte en cuello de botella. Los datos lo
confirman: el output individual crece 98%, pero el tiempo de revisión de
PRs crece 91%. La solución no es eliminar la supervisión sino diseñar
**prácticas de supervisión que escalen**: testing automatizado, validación
por pipeline, revisión por niveles de riesgo.

**3. La calidad se degrada si no se defiende activamente.**

Los datos de calidad son una llamada de atención: 1.7x más issues en PRs
generados por IA, 2.74x más vulnerabilidades XSS, 8x más duplicación de
código, refactoring en caída libre. Gartner predice un aumento del 2500%
en defectos para 2028 si se adoptan enfoques "prompt-to-app" sin
disciplina. La velocidad sin calidad es deuda técnica con interés
compuesto.

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
- **¿Puede la IA supervisar a la IA?** Cuando el volumen de código
  generado supera la capacidad de revisión humana, ¿es viable un modelo
  de "IA supervisa IA"? ¿O genera un problema recursivo de confianza?
- **¿Cómo medimos la productividad real?** Si la percepción y la realidad
  divergen (como mostró el estudio METR), ¿qué métricas usamos?
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

[2] A. Panigo, K. Petkoff Bankoff, A. Pasini y P. Pesado. "Inteligencia Artificial en Ingeniería de Software: Etapas de Elicitación y Análisis de requerimientos". *XXX Congreso Argentino de Ciencias de la Computación (CACIC)*, La Plata, 2024.

[3] GitHub. "Octoverse 2024: The state of open source and rise of AI". GitHub Blog, 2024.

[4] JetBrains. "The State of Developer Ecosystem 2025". JetBrains Research, octubre 2025.

[5] C. E. Jimenez et al. "SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering". *Princeton University*, 2024. arXiv:2405.15793.

[6] Stack Overflow. "2024 Developer Survey". Stack Overflow, 2024.

[7] S. Peng, E. Kalliamvakou, P. Cihon y M. Demirer. "The Impact of AI on Developer Productivity: Evidence from GitHub Copilot". *Communications of the ACM*, marzo 2024. arXiv:2302.06590.

[8] The Standish Group. "CHAOS Report 2020". The Standish Group International, 2020.

[9] B. W. Boehm et al. *Software Cost Estimation with COCOMO II*. Prentice Hall, 2000.

[10] I. Papadopoulos et al. "Enhancing the student's logical thinking with Gherkin language". *2017 IEEE Global Engineering Education Conference (EDUCON)*, 2017. DOI: 10.1109/EDUCON.2017.7943054.

[11] E. Whitten y L. Bentley. *Systems Analysis and Design Methods*. 7.ª ed. McGraw-Hill, 2007.

[12] F. Dalpiaz y S. Brinkkemper. "Agile Requirements Engineering: From User Stories to Software Architectures". *2021 IEEE 29th International Requirements Engineering Conference (RE)*, 2021.

[13] H. Pearce et al. "Asleep at the Keyboard? Assessing the Security of GitHub Copilot's Code Contributions". *2022 IEEE Symposium on Security and Privacy (SP)*, 2022.

[14] METR. "Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity". arXiv:2507.09089, julio 2025.

[15] CodeRabbit. "State of AI vs Human Code Generation Report". Diciembre 2025.

[16] GitClear. "AI Copilot Code Quality: 2025 Data Suggests 4x Growth in Code Clones". Febrero 2025.

[17] Trend Micro. "Slopsquatting: When AI Agents Hallucinate Malicious Packages". 2025.

[18] A. Osmani. "The 80% Problem in Agentic Coding". Substack, 2025.

[19] R. Tufano et al. "On the Use of Large Language Models in Mutation Testing". arXiv:2406.09843, junio 2024.

[20] Meta Engineering. "Mutation-Guided LLM-based Test Generation at Meta". *FSE 2025 (Industry Papers)*, 2025.

[21] J. Wang et al. "Software Testing with Large Language Models: Survey, Landscape, and Vision". *IEEE Transactions on Software Engineering*, 2024. DOI: 10.1109/TSE.2024.3368208.

[22] Stack Overflow. "2025 Developer Survey". Stack Overflow, 2025.

[23] M. Nogueira et al. "ACE: Automated Technical Debt Remediation with Validated Large Language Model Refactorings". arXiv:2507.03536, julio 2025.

[24] S. Kacimi et al. "PromptDebt: A Comprehensive Study of Technical Debt Across LLM Projects". arXiv:2509.20497, septiembre 2025.

[25] A. Karpathy. "De vibe coding a agentic engineering". 2026. Citado en The Hans India, enero 2026.

[26] Gartner. "Generative AI Will Require 80% of Engineering Workforce to Upskill Through 2027". Gartner Newsroom, octubre 2024.

[27] A. Modestino et al. "The Impact of Generative AI on Job Opportunities for Junior Software Engineers". *Northeastern University*, 2025.

[28] Clutch. "Blind Trust in AI: Most Devs Use AI-Generated Code They Don't Understand". Junio 2025.

[29] Microsoft Research. "New Future of Work Report 2025". Diciembre 2025.

[30] C. Fan (Hymel). "The AI-Native Software Development Lifecycle: A Theoretical and Practical New Methodology". arXiv:2408.03416, agosto 2024.

[31] J. Liu et al. "Large Language Model-Based Agents for Software Engineering: A Survey". *ACM Transactions on Software Engineering and Methodology*, 2024.

[32] M. Galster et al. "Artificial Intelligence for Software Architecture: Literature Review and the Road Ahead". arXiv:2504.04334, abril 2025.

[33] C. Lopez-Martin et al. "Leveraging Large Language Models for Predicting Cost and Duration in Software Engineering Projects". arXiv:2409.09617, septiembre 2024.

[34] M. A. Sami et al. "Early Results of an AI Multiagent System for Requirements Elicitation and Analysis". *Product-Focused Software Process Improvement (PROFES 2024)*, Springer LNCS, 2024.

[35] J. Garcia et al. "AI-Driven Decision Support Systems in Agile Software Project Management: Enhancing Risk Mitigation and Resource Allocation". *MDPI Systems*, 2025.

[36] S. Joshi. "A Review of Generative AI and DevOps Pipelines: CI/CD, Agentic Automation, MLOps Integration, and Large Language Models". SSRN, 2025.

[37] Qodo. "State of AI Code Quality in 2025". Qodo Research, 2025.

[38] Apiiro Research. "4x Velocity, 10x Vulnerabilities: AI Coding Assistants Are Shipping More Risks". 2025.

[39] Gartner. "Strategic Predictions for IT Organizations 2026 and Beyond". Gartner Newsroom, 2025.

[40] GitHub. "Spec-driven development with AI: Get started with a new open source toolkit". GitHub Blog, 2025.

[41] Forrester. "Predictions 2026: AI Moves from Hype to Hard Hat Work". Forrester Blog, 2025.

[42] A. Osmani. "Agentic Engineering". AddyOsmani.com, 2025-2026.
