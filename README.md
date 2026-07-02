# OpenSpec: Design-Driven Development 🎨🚀

Este repositorio implementa un flujo de trabajo (**workflow**) modificado de **OpenSpec** enfocado en el **desarrollo guiado por el diseño** (Design-Driven Development) antes que por las especificaciones exhaustivas (*specs*).

En este enfoque, el diseño visual y la arquitectura de componentes son el punto de partida y la única fuente de verdad, reduciendo la fricción de mantenimiento de especificaciones pesadas.

---

## 💡 Concepto Principal

A diferencia del flujo de trabajo tradicional de OpenSpec, que a menudo requiere la creación de un `spec.md` detallado o la extracción formal de requerimientos antes de codificar, este workflow simplificado sitúa al **diseño** como el artefacto principal.

*   **El diseño es el punto de partida:** Nos enfocamos en cómo se ve y se comporta la interfaz a nivel de componentes.
*   **Sin sobrecarga de specs:** Evitamos la duplicidad de información eliminando documentos de especificación técnica separados (`spec.md`, `proposal.md`, delta specs, etc.).
*   **Checklist derivado del diseño:** El plan de ejecución (`tasks.md`) se genera única y exclusivamente a partir del documento de diseño.

---

## 🛠️ Flujo de Trabajo: `minimal-design-task`

El esquema utilizado en este repositorio es `minimal-design-task`. El flujo se divide en tres fases principales:

### 1. Diseño Técnico (`design.md`)
Es la **única fuente de verdad** (Single Source of Truth).
*   Se listan y analizan los componentes existentes en `packages/ui/src/` para maximizar la reutilización.
*   Se extraen tokens de diseño directamente de Figma o de la descripción visual (colores, espaciado, border-radius, tipografía).
*   Se definen:
    *   **Main Components:** Esqueleto JSX de alto nivel y firmas de TypeScript para las pantallas principales.
    *   **Components:** Esqueleto JSX y firmas de TypeScript para los subcomponentes reutilizables.
    *   **Storybook Variants:** Variaciones visuales y estados a verificar.
    *   **Component Tree:** Diagrama Mermaid de relaciones e indicación de componentes nuevos vs. existentes.

### 2. Plan de Implementación (`tasks.md`)
Un checklist ordenado de tareas pequeñas, acotadas y verificables.
*   Se deriva **exclusivamente** de lo definido en `design.md`.
*   Sirve como hoja de ruta durante la fase de codificación.

### 3. Implementación y Validación
*   Se implementa el código en pequeños bloques siguiendo el checklist.
*   Se validan visualmente los componentes mediante Storybook y pruebas manuales/automatizadas.
*   Se confirma que no se hayan introducido artefactos prohibidos en el commit final.

---

## 🚫 Artefactos Permitidos y Prohibidos

Para mantener el repositorio limpio y ágil, se definen estrictamente las reglas de qué documentos pueden existir en una tarea:

| Artefactos Permitidos ✅ | Artefactos Prohibidos ❌ |
| :--- | :--- |
| **`design.md`** (Diseño técnico único) | **`spec.md`** (Especificación técnica formal) |
| **`tasks.md`** (Tareas derivadas de `design.md`) | **`proposal.md`** (Propuestas preliminares) |
| Convenciones globales (`openspec/specs/components-conventions/design.md`) | Delta specs o Synced specs |
| | Flujos de sincronización automatizada de requerimientos |

---

## 📁 Estructura del Repositorio

*   `openspec/`
    *   `config.yaml`: Archivo de configuración global de OpenSpec que define el esquema activo y el contexto global.
    *   `specs/components-conventions/design.md`: Convenciones de diseño globales del proyecto (rutas de componentes, estilos comunes, límites de tamaño, etc.).
    *   `schemas/minimal-design-task/`: Definición del esquema de tareas simplificado.
        *   `schema.yaml`: Reglas de generación y flujo de artefactos.
        *   `templates/`: Plantillas predefinidas para `design.md` y `tasks.md`.
*   `README.md`: Este archivo explicativo.
