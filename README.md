# Plantilla para proyectos con agentes

Punto de partida para repositorios nuevos que trabajen con Cursor, GitHub Copilot, Codex, Gemini CLI o Claude Code. Crea el tuyo con **Use this template** en GitHub.

## Primer paso

Pide al agente que ejecute la skill **setup-proyecto**. Esa skill explora el repositorio, rellena la sección «Este proyecto» en `AGENTS.md`, sustituye este README y propone CI y Dependabot según el stack real.

## Qué incluye

- `scripts/setup`: preparación idempotente del entorno. Los envoltorios de cada proveedor de agentes en la nube solo invocan este script.
- `AGENTS.md`: reglas transversales, mantenimiento de skills y, tras el setup, datos del proyecto (stack, estructura, comandos comprobados).
- `.agents/skills/`: skills del agente; su mantenimiento está en `AGENTS.md` (sección «Mantenimiento de skills»).
- `skills-lock.json`: versiones fijadas de las skills instaladas desde pstack.
- `.claude/skills/`: enlaces simbólicos para Claude Code hacia `.agents/skills/`.
- `.github/copilot-instructions.md`: enlace simbólico a `AGENTS.md` para que Copilot lea las mismas reglas.
- Plantilla de pull request y Dependabot para GitHub Actions.

`AGENTS.md` y `.agents/skills/` son la fuente de instrucciones para agentes en Cursor, Copilot, Codex y Gemini CLI. Claude Code lee las mismas skills vía `.claude/skills/`.

## Windows y enlaces simbólicos

Sin `core.symlinks=true`, Git en Windows guarda `.github/copilot-instructions.md` y `.claude/skills/*` como archivos de texto en lugar de enlaces. Actívalo:

```bash
git config --global core.symlinks true
```

Vuelve a clonar el repositorio después de cambiar la opción.
webhook wake test 2026-11-23