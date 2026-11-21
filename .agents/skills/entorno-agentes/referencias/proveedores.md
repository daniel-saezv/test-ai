# Proveedores de entorno de agentes

Hechos para consultar. Verificado el 2026-11-21 contra la documentación oficial. Si un campo no está aquí, no lo inventes: abre el enlace.

Los envoltorios solo ejecutan `bash scripts/setup`.

## Cursor Cloud Agents

- Documentación: [Cloud Environment Setup](https://cursor.com/docs/cloud-agent/setup)
- Builds (cuándo corre `install`): [Cloud Agent Builds](https://cursor.com/docs/cloud-agent/builds)
- Esquema: [environment.schema.json](https://cursor.com/schemas/environment.schema.json)
- Ruta: `.cursor/environment.json`
- Campo: `install` (string). Cursor lo ejecuta al crear un Build, desde la raíz del proyecto, después del clone. Debe ser idempotente.
- Envoltorio mínimo:

```json
{
  "install": "bash scripts/setup"
}
```

- No añadas `$schema`: el esquema vigente rechaza propiedades no declaradas.
- No pongas Dockerfile, `start` ni `terminals` salvo que el stack lo necesite. `install` prepara disco; los procesos vivos van en `start` o `terminals`.
- Un entorno guardado en el panel solo lee este archivo si su ubicación de environment.json apunta a él. En un arranque de un solo repo sin entorno previo, un `.cursor/environment.json` válido en el repo queda registrado.

## GitHub Copilot cloud agent

- Documentación: [Configure the development environment for agents on GitHub Actions](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment)
- Ruta: `.github/workflows/copilot-setup-steps.yml` (en la rama por defecto para que Copilot lo use).
- Un solo job. El nombre del job es exactamente `copilot-setup-steps`. Si no, Copilot lo ignora.
- Copilot, en una sesión sobre GitHub Actions, ejecuta los `steps` de ese job antes de trabajar. Campos del job que honra: `steps`, `permissions`, `runs-on`, `services`, `snapshot`, `timeout-minutes` (máximo 59). El resto se ignora.
- El archivo también corre como workflow normal de Actions. La doc de ejemplo dispara `workflow_dispatch`, y `push`/`pull_request` cuando cambia el propio YAML, para validarlo en la pestaña Actions y en la PR. Esta plantilla añade `scripts/setup` a `paths` porque la lógica vive ahí, no en el YAML.
- Hace falta `actions/checkout` si vas a ejecutar el script del repo. Permiso mínimo: `contents: read`.
- Envoltorio mínimo: checkout (misma acción y SHA que `.github/workflows/skills.yml`) y `run: bash scripts/setup`.
- No aplica a sesiones en cloud sandbox de Copilot. Solo a sesiones en GitHub Actions.
