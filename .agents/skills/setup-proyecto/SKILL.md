---
name: setup-proyecto
description: Primera tarea en un repositorio nuevo creado desde la plantilla. Rellena «Este proyecto» en AGENTS.md, sustituye el README y configura CI y Dependabot según lo que exista en el repo.
---

# Setup de proyecto

Ejecuta esta skill en la primera tarea de un repositorio recién creado desde la plantilla.

## Qué hacer

1. **Explorar el repositorio.** Recorre el árbol, los manifiestos de paquetes y la configuración existente. No asumas un stack: dedúcelo de lo que hay.
2. **Ejecutar comandos reales.** Instalación, build, tests y arranque. Anota solo comandos que hayas ejecutado y cuyo resultado hayas visto.
3. **Rellenar «Este proyecto» en AGENTS.md.** Qué es el proyecto, stack, estructura del código y comandos comprobados (instalación, build, tests, arranque). Incluye buenas prácticas propias del stack y una sección CI/CD: workflows existentes, checks obligatorios en PR y despliegue si aplica.
4. **Sustituir README.md.** Escribe el README del **proyecto** (no de la plantilla ni de agentes): qué es, requisitos, cómo instalarlo, ejecutarlo, probarlo y desplegarlo si aplica. Elimina por completo el texto de la plantilla. El README del proyecto no describe skills ni agentes; como mucho, una línea que remita a `AGENTS.md` para quien busque reglas o instrucciones del agente.
5. **Dependabot.** Si hay manifiesto de paquetes, amplía `.github/dependabot.yml` al ecosistema correspondiente. Mantén la entrada de `github-actions` si sigue aplicando.
6. **CI.** Si el stack lo permite, propone un workflow de GitHub Actions que ejecute build y tests en cada pull request. No añadas un workflow genérico que falle sin stack. Si el repositorio conserva `.github/workflows/skills.yml` de la plantilla, no lo quites: verifica las skills instaladas (`principle-prove-it-works`, `tdd`, `blast-radius`, `correct`, `unslop`) contra `skills-lock.json`.

## Reglas

- No inventes comandos, versiones ni rutas que no hayas comprobado.
- No copies instrucciones de otros proyectos.
- Si no hay código aplicable aún, documenta el estado real y deja CI para cuando existan comandos verificables.