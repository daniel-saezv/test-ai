---
name: entorno-agentes
description: Deja el entorno de agentes en la nube listo y alineado. Un script de preparación y envoltorios por proveedor, sin duplicar lógica.
---

# Entorno de agentes

Usa esta skill cuando el proyecto arranque sin entorno preparado, cuando cambien dependencias, toolchain o pasos de arranque, o cuando entre un proveedor de agentes en la nube sin envoltorio.

Los detalles de cada proveedor (rutas, campos, triggers) están en [referencias/proveedores.md](referencias/proveedores.md). No los copies a `AGENTS.md`.

## Qué hacer

1. **Localiza la fuente de verdad.** Debe existir `scripts/setup` en la raíz. Si no existe, créalo con el mismo contrato que en la plantilla: `bash`, `set -euo pipefail`, `cd` a la raíz del repo, función `install_stack` entre los marcadores `stack (setup-proyecto)` y `fin stack`, y una llamada a esa función. El script sale 0. Es idempotente.
2. **Rellena el stack si ya lo conoces.** Si hay lockfile o versiones fijadas y un comando de instalación comprobado, ponlo dentro de `install_stack`. No instales a ciegas. Si aún no hay stack, deja el mensaje de que no hay nada que instalar.
3. **Detecta proveedores.** Recorre el repo y anota los que aplica:
   - Directorio `.cursor/` o archivo `.cursor/environment.json`.
   - `.github/copilot-instructions.md` o `.github/workflows/copilot-setup-steps.yml`.
   - Cualquier otro archivo de entorno de un proveedor documentado en la referencia.
   Si el repo nació de esta plantilla y aún no hay marcas, crea los envoltorios de la plantilla (los dos de la referencia). No inventes proveedores que el proyecto no usa.
4. **Crea o actualiza envoltorios.** Cada envoltorio solo invoca `bash scripts/setup`. Cero lógica de instalación propia. Sigue la referencia del proveedor: ruta, nombre de job, campos y triggers. Si el proyecto usa un proveedor de la referencia sin envoltorio, créalo.
5. **Comprueba.** Ejecuta `bash scripts/setup` dos veces seguidas y confirma salida 0 las dos. Abre cada envoltorio y verifica que llama al script y cumple la referencia. No des por bueno un campo de memoria: contrasta con [referencias/proveedores.md](referencias/proveedores.md).

## Qué no hacer

- No pongas comandos de instalación en el envoltorio.
- No nombres un proveedor como obligatorio en `AGENTS.md`.
- No añadas un devcontainer salvo que el proyecto ya lo use como entorno de desarrollo. Una plantilla sin stack no gana una imagen genérica que hay que mantener.
