# Base de Spec-Driven Development

Base opinada para construir software mediante requisitos de producto explícitos, decisiones de arquitectura, estándares de desarrollo y skills reutilizables para agentes.

Este repositorio es intencionadamente ligero.

No es un esqueleto de aplicación.

Es una base estructurada para entregar software guiado por especificaciones.

## Versiones Disponibles

* English: `README.md`
* Español: `README.es.md`
* Example in English: `EXAMPLE.md`
* Ejemplo en español: `EXAMPLE.es.md`

## Propósito

El objetivo es ayudar a los equipos a empezar desde el entendimiento antes de implementar.

El repositorio está pensado para hacer explícitas estas preguntas:

* por qué existe el trabajo
* qué usuario se beneficia
* qué restricciones de arquitectura aplican
* cómo debe entregarse el trabajo de forma segura
* qué estándares definen una calidad aceptable

## Qué Contiene Este Repositorio

* `docs/prd/` para requisitos de producto y plantillas
* `docs/adr/` para decisiones de arquitectura y plantillas
* `docs/project/` para declarar el stack activo
* `docs/standards/` para estándares de desarrollo, incluyendo Definition of Ready y Definition of Done
* `docs/workflows/` para workflows de feature, bugfix y review
* `.codex/skills/` para skills reutilizables
* `.codex/examples/` para ejemplos concretos de proyectos derivados
* `.codex/templates/` para plantillas de skills específicas del proyecto
* `.opencode/agent/` para roles y responsabilidades de agentes
* `AGENTS.md` como guía de orquestación del proyecto

## Enfoque Actual

El sistema de entrega es genérico, pero las skills de implementación incluidas están actualmente optimizadas para proyectos PHP usando:

* Symfony
* Laravel
* UI server-rendered con Twig o Blade

Cada proyecto derivado debe declarar un único framework primario activo en `docs/project/active-stack.md`.

Los documentos de proceso siguen siendo útiles aunque el stack evolucione.

## Principios Base

* DDD y Hexagonal Architecture
* bounded contexts explícitos
* claridad de producto antes que código
* decisiones de arquitectura documentadas mediante ADRs
* entrega incremental y revisable
* alta testabilidad y mantenibilidad

## Workflow Recomendado

1. Empieza desde `docs/prd/TEMPLATE.md` para definir la intención de la feature.
2. Revisa los ADRs existentes y crea uno nuevo desde `docs/adr/TEMPLATE.md` cuando cambie la arquitectura.
3. Declara el stack activo en `docs/project/active-stack.md`.
4. Valida `docs/standards/definition-of-ready.md` antes de implementar.
5. Implementa de forma incremental siguiendo los estándares y workflows.
6. Valida `docs/standards/definition-of-done.md` antes de dar el trabajo por completado.

## Puntos de Entrada Sugeridos

* `EXAMPLE.es.md`
* `AGENTS.md`
* `docs/prd/0000-product-development-principles.md`
* `docs/adr/0001-architecture-style.md`
* `docs/adr/0002-project-structure-and-bounded-contexts.md`
* `docs/project/active-stack.md`
* `docs/standards/definition-of-ready.md`
* `docs/standards/definition-of-done.md`
* `docs/workflows/feature-development.md`
* `docs/workflows/derived-project-setup.md`

## Arranque de Proyecto Derivado

Al crear un proyecto a partir de esta base:

1. Rellena `docs/project/active-stack.md` con el stack real.
2. Mantén activo un solo framework PHP primario.
3. Revisa `docs/workflows/derived-project-setup.md`.
4. Copia `.codex/templates/skills/project-conventions/SKILL.md` dentro del proyecto derivado si aparecen convenciones repetidas reales.
5. Usa `.codex/examples/skills/laravel-project-conventions/SKILL.md` o `.codex/examples/skills/symfony-project-conventions/SKILL.md` como referencia de adaptación.
6. Renombra esa skill de forma explícita, por ejemplo `laravel-project-conventions` o `symfony-project-conventions`.
7. Usa las convenciones específicas del proyecto para acotar defaults, no para sobreescribir reglas de arquitectura.

## Guía de Personalización

Usa este repositorio como base y adáptalo de forma intencionada.

Ejemplos:

* reemplazar las skills específicas de PHP si tu stack cambia
* declarar un único framework activo por proyecto derivado
* añadir skills específicas de UI o framework solo cuando reflejen convenciones repetidas reales
* mantener las plantillas genéricas y los ejemplos de proyecto explícitos

Evita mezclar guía de proceso genérica con ejemplos específicos de dominio salvo que el repositorio esté pensado para un único producto.

## Nota

`README.es.md` y `EXAMPLE.es.md` están en español para facilitar el onboarding.

La mayoría de la documentación estructural del repositorio sigue en inglés por ahora.
