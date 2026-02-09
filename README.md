```
  ╭──────────────────────────────────────────────────────────╮
  │                                                          │
  │   ✦  IS-IA                                               │
  │                                                          │
  │   Ingeniería de Software en la Era de la IA              │
  │                                                          │
  │   Cómo construir software de calidad cuando la IA        │
  │   deja de ser asistente y se convierte en el             │
  │   implementador principal.                               │
  │                                                          │
  ╰──────────────────────────────────────────────────────────╯
```

---

### El cambio en un gráfico

```
¿En qué invierte su tiempo          vs.       ¿En qué invierte su tiempo
el desarrollador?                              el desarrollador?
(modelo tradicional)                           (realidad 2026)

┌─────────────────────────┐    ┌─────────────────────────┐
│                         │    │                         │
│  ████████████████ 80%   │    │  █ 5%                   │  Escribir código
│                         │    │                         │
│  █ 5%                   │    │  ██████ 30%             │  Supervisar y evaluar
│                         │    │                         │
│  █ 5%                   │    │  █████ 25%              │  Especificar y diseñar
│                         │    │                         │
│  █ 5%                   │    │  ████ 20%               │  Testear y validar
│                         │    │                         │
│                    0%   │    │  ███ 15%                │  Orquestar agentes
│                         │    │                         │
│  █ 5%                   │    │  █ 5%                   │  Reuniones y otros
│                         │    │                         │
└─────────────────────────┘    └─────────────────────────┘
```

### La premisa

> Si la IA ya puede **elicitar requerimientos**, **generar código**,
> **escribir tests**, **desplegar infraestructura** y **monitorear producción**...
>
> **...¿cómo tiene que cambiar la ingeniería de software para aprovecharla
> sin perder calidad, seguridad ni control?**

---

### Sobre este proyecto

Este documento formaliza prácticas reales de desarrollo de software con IA,
combinando experiencia profesional en una empresa de desarrollo (Bluegin) con
rigor académico y evidencia empírica.

No es un catálogo de herramientas. Es una propuesta metodológica para cada
etapa del ciclo de vida del software — desde el estudio de factibilidad hasta
la evolución y el mantenimiento — cuando la inteligencia artificial participa
activamente en el proceso.

**Punto de partida:** el trabajo de investigación *"Inteligencia Artificial en
Ingeniería de Software: Etapas de Elicitación y Análisis de requerimientos"*
(Panigo, Petkoff Bankoff, Pasini, Pesado — XXX CACIC, La Plata, 2024) que
demostró la viabilidad de usar LLMs en las primeras etapas del SDLC. Este
proyecto extiende esa investigación a **todas las etapas**.

### Lo que vas a encontrar

```
📄 is-ia.md
│
├── 1. Introducción ─────────────── El punto de inflexión
├── 2. Revisión sistemática ─────── SLR formal (Kitchenham) con 77 fuentes
│   ├── Protocolo: 5 RQs, PRISMA, quality assessment
│   ├── Hallazgos por etapa del SDLC (RQ1)
│   ├── Calidad y seguridad (RQ2)
│   ├── Productividad: percepción vs. realidad (RQ3)
│   ├── Transformación del rol profesional (RQ4)
│   ├── Marcos metodológicos emergentes (RQ5)
│   └── Datos de adopción en la industria
├── 3. Estudio de factibilidad ──── Viabilidad, estimación y riesgos con IA
├── 4. Requerimientos ───────────── Elicitación, análisis y especificación
│   └── Basado en el paper del XXX CACIC (2024)
├── 5. Diseño ───────────────────── Arquitectura, BD, interfaces, decisiones
├── 6. Implementación ───────────── Coding con agentes, review, documentación
├── 7. Testing ──────────────────── Generación de pruebas, calidad, validación
├── 8. Despliegue y operaciones ─── CI/CD, infraestructura, monitoreo
├── 9. Evolución y mantenimiento ── Deuda técnica, refactoring, modernización
├── 10. El nuevo profesional ────── Roles, habilidades, formación
├── 11. Conclusiones ────────────── Hacia dónde vamos
└── 12. Referencias ─────────────── 77 fuentes verificadas (formato IEEE)
```

### Estado

```
[████████████░░░░░░░░] 60% — SLR completa, secciones en desarrollo
```

| Sección | Estado |
|---|---|
| 1. Introducción | Completa |
| 2. Revisión sistemática de la literatura | Completa |
| 3. Estudio de factibilidad | En progreso |
| 4. Requerimientos | En progreso |
| 5. Diseño | En progreso |
| 6. Implementación | En progreso |
| 7. Testing | En progreso |
| 8. Despliegue y operaciones | En progreso |
| 9. Evolución y mantenimiento | En progreso |
| 10. El nuevo profesional | En progreso |
| 11. Conclusiones | En progreso |
| 12. Referencias | Completa (77 fuentes) |

---

### Este proyecto es parte de algo más grande

```
  ┌─────────────────────────────┐
  │                             │
  │    Y@ enseño {con IA}       │
  │    ¿Qué debe saber          │
  │    un profesional?          │
  │                             │
  └──────────────┬──────────────┘
                 │
        ┌────────┴────────┐
        │                 │
        ▼                 ▼
  ┌───────────┐    ┌────────────┐
  │           │    │            │
  │   AURA    │    │   IS-IA    │ ◄── Estás acá
  │           │    │            │
  │ ¿Con qué  │    │ ¿Cómo se   │
  │ lenguaje  │    │ construye  │
  │ programa  │    │ software   │
  │ un agente?│    │ con IA?    │
  │           │    │            │
  └───────────┘    └────────────┘
```

| Proyecto | Pregunta | Foco |
|---|---|---|
| [**Y@ enseño {con IA}**](https://github.com/bluegin-ush/yo-ense-o-con-IA-) | ¿Qué debe saber un profesional? | La **educación** |
| [**AURA**](https://github.com/bluegin-ush/aura) | Si la IA escribe código, ¿con qué lenguaje? | Las **herramientas** |
| **IS-IA** | ¿Cómo se construye software con IA? | La **profesión** |

**Y@ enseño** argumenta que el foco de la enseñanza debe pasar de escribir
código a evaluar, especificar y pensar críticamente.

**AURA** lleva esa premisa al extremo: si los agentes son los que programan,
necesitan un lenguaje diseñado *para ellos*.

**IS-IA** formaliza las prácticas de ingeniería de software para un mundo donde
la IA participa activamente en cada etapa del desarrollo — no como herramienta
auxiliar, sino como colaborador principal.

---

<div align="center">

*"La IA no va a reemplazar a los ingenieros de software.*
*Va a reemplazar a los ingenieros de software que no sepan trabajar con IA."*

*La pregunta ya no es si la IA cambia el desarrollo de software.*
*La pregunta es si las prácticas de ingeniería van a evolucionar a tiempo.*

</div>
