# Ejemplo — Arrancar un Proyecto Derivado

## Escenario

Imagina que eres un desarrollador que llega a este repositorio por primera vez.

Quieres usarlo como base para un proyecto real llamado `Acme Customer Portal`.

Para este ejemplo:

* el producto será un portal de clientes
* el framework activo será `Laravel`
* la interfaz será `Blade`
* el enfoque de persistencia será `Eloquent in Infrastructure adapters`
* la primera feature será `user registration`

El mismo flujo sirve para Symfony.

Solo cambian las decisiones del stack activo.

---

## Objetivo

Al final de este ejemplo, el proyecto derivado debería tener:

* un stack activo declarado
* un primer incremento de producto claro
* una base arquitectónica definida
* suficiente estructura de entrega para empezar a implementar con seguridad

---

## Paso 1 — Crear el Proyecto Derivado

Copia este repositorio dentro de la carpeta del nuevo proyecto y renómbralo.

Ejemplo:

```bash
cp -R spec-driven-development acme-customer-portal
```

En este punto, no empieces todavía a escribir código de aplicación.

---

## Paso 2 — Leer los Documentos Mínimos Necesarios

No intentes leerlo todo al principio.

Empieza solo por estos archivos:

1. `README.es.md`
2. `AGENTS.md`
3. `docs/adr/0001-architecture-style.md`
4. `docs/adr/0002-project-structure-and-bounded-contexts.md`
5. `docs/project/active-stack.md`
6. `docs/standards/definition-of-ready.md`
7. `docs/standards/definition-of-done.md`
8. `docs/workflows/derived-project-setup.md`
9. `docs/workflows/feature-development.md`

Con eso tienes suficiente contexto para empezar de forma segura.

---

## Paso 3 — Definir el Primer Incremento de Producto

Crea el primer PRD a partir de `docs/prd/TEMPLATE.md`.

Archivo de ejemplo:

* `docs/prd/0001-user-registration.md`

Para este ejemplo, el PRD debería definir:

* usuario: visitante no autenticado
* problema: el visitante todavía no puede crear una cuenta
* alcance incluido: registro con nombre, email y contraseña
* alcance excluido: social login, recuperación de contraseña, aprobación manual por admin
* criterios de aceptación: registro exitoso, prevención de emails duplicados, feedback de validación

En esta fase, mantén el alcance intencionadamente pequeño.

Solo registro es un buen primer slice.

---

## Paso 4 — Declarar el Stack Activo

Edita `docs/project/active-stack.md` y sustituye los placeholders por decisiones reales.

Ejemplo:

```md
* language: `PHP`
* primary framework: `Laravel`
* interface delivery: `Blade`
* persistence adapter: `Eloquent`
* validation boundary: `Laravel Form Request`
* testing stack: `PHPUnit + Pest`
* async processing: `Laravel Jobs/Queues`
* UI styling system: `project choice`
* UI component approach: `shared components`
```

En `Active Skills`, lista solo las skills que aplican.

Ejemplo:

```md
* `laravel-frameworks`
* `server-rendered-ui`
```

En `Explicit Non-Goals`, deja visibles las opciones inactivas.

Ejemplo:

```md
* `Symfony`
* `Twig`
* `Doctrine`
```

Esto elimina ambigüedad para la implementación futura.

---

## Paso 5 — Registrar el Stack como un ADR

Las decisiones de framework y entrega son decisiones de arquitectura.

Crea un ADR a partir de `docs/adr/TEMPLATE.md`.

Archivo de ejemplo:

* `docs/adr/0003-active-project-stack.md`

Para este ejemplo, el ADR debería explicar:

* por qué Laravel es el framework activo
* por qué Blade es la elección de interfaz
* por qué Eloquent permanece dentro de Infrastructure adapters
* por qué Pest y PHPUnit son ambos aceptables
* qué queda explícitamente fuera del proyecto

Si el stack cambia más adelante, este ADR debe actualizarse o reemplazarse.

---

## Paso 6 — Decidir si Hacen Falta Convenciones de Proyecto

No crees `project conventions` por defecto.

Créalo solo cuando el proyecto ya tenga patrones repetidos reales.

Si hacen falta:

1. Copia `.codex/templates/skills/project-conventions/SKILL.md`
2. Renómbralo a `.codex/skills/laravel-project-conventions/SKILL.md`
3. Usa `.codex/examples/skills/laravel-project-conventions/SKILL.md` como referencia

Buenas razones para crearlo ahora:

* el equipo ya sabe que usará Form Requests de forma consistente
* el equipo ya quiere una separación fija entre Pest y PHPUnit
* el equipo ya tiene convenciones claras de Blade components

Mala razón:

* "igual nos hace falta más adelante"

---

## Paso 7 — Alinear las Guías del Proyecto

Antes de programar, adapta el lenguaje genérico del repositorio donde haga falta.

Como mínimo, revisa:

* `README.md`
* `AGENTS.md`

Cambios típicos en el proyecto derivado:

* nombre del proyecto
* descripción real del producto
* stack activo real
* skill de convenciones del proyecto, si existe

El objetivo es que un desarrollador nuevo lea las guías del proyecto y vea la realidad, no placeholders.

---

## Paso 8 — Validar Definition of Ready

Antes de abrir la primera rama de implementación, confirma que todo esto es cierto:

* el problema de usuario está claro
* existe el primer PRD
* el stack activo está declarado
* existe el ADR del stack
* se conoce el bounded context afectado
* los criterios de aceptación son visibles
* las expectativas de testing son visibles
* la primera feature es lo bastante pequeña como para revisarse con seguridad

Para este ejemplo, el primer bounded context probable sería:

* `IdentityAccess`

Si alguno de estos puntos no está claro, para y corrige la documentación antes.

---

## Paso 9 — Empezar la Primera Rama de Feature

Solo ahora empieza la implementación.

Rama de ejemplo:

* `feature/user-registration`

Objetivo de implementación:

* un único vertical slice
* un único workflow user-facing claro
* un único bounded context

Para este ejemplo, eso significa:

* formulario de registro
* caso de uso de registro
* protección contra email duplicado
* creación exitosa de la cuenta
* tests de dominio, aplicación y flujo user-facing cuando aplique

Evita meter login, recuperación de contraseña, gestión de perfil y features de admin en esta primera rama.

---

## Paso 10 — Usar los Templates de Entrega

Al colaborar sobre el trabajo:

* usa `.github/ISSUE_TEMPLATE/feature.yml` para definir la feature
* usa `.github/PULL_REQUEST_TEMPLATE.md` para la pull request

La PR debería apuntar a:

* el PRD
* el ADR
* el stack activo
* los tests ejecutados

Así la implementación queda trazable.

---

## Conjunto Mínimo de Archivos Antes de la Primera Implementación Real

Para este ejemplo, deberías esperar al menos estos archivos antes de empezar a programar en serio:

* `docs/prd/0001-user-registration.md`
* `docs/adr/0003-active-project-stack.md`
* `docs/project/active-stack.md`
* opcional: `.codex/skills/laravel-project-conventions/SKILL.md`

El proyecto puede seguir siendo pequeño, pero ya no será ambiguo.

---

## Errores Habituales

No hagas esto:

* empezar a programar antes de declarar el stack activo
* mezclar convenciones de Symfony y Laravel en el mismo proyecto derivado
* abrir una primera rama de feature enorme
* crear `project conventions` sin patrones repetidos reales
* dejar que Eloquent o clases del framework definan la verdad del dominio
* tratar las plantillas como documentos finales sin adaptarlas

El mayor riesgo al principio no es la falta de código.

Es la ambigüedad oculta.

---

## Checklist Rápida

Si quieres la versión más corta y segura, haz esto en orden:

1. Lee `README.es.md`, `AGENTS.md` y los dos ADRs.
2. Crea `docs/prd/0001-user-registration.md`.
3. Rellena `docs/project/active-stack.md`.
4. Crea `docs/adr/0003-active-project-stack.md`.
5. Decide si `laravel-project-conventions` hace falta de verdad.
6. Confirma Definition of Ready.
7. Crea `feature/user-registration`.
8. Implementa la feature en un slice pequeño.
9. Abre la PR usando el template proporcionado.
10. Valida Definition of Done antes de mergear.

---

## Variante Symfony

Si el proyecto usa Symfony en lugar de Laravel, el flujo es el mismo.

Solo cambia las decisiones activas:

* `Laravel` -> `Symfony`
* `Blade` -> `Twig`
* `Eloquent` -> `Doctrine`
* `Laravel Jobs/Queues` -> `Messenger`
* `laravel-frameworks` -> `symfony-frameworks`
* `laravel-project-conventions` -> `symfony-project-conventions`

Todo lo demás permanece igual.

---

## Regla Final

Este repositorio no intenta frenarte.

Intenta asegurar que tus primeras decisiones de implementación sean lo bastante explícitas como para que el proyecto pueda crecer sin contradicciones ocultas.
