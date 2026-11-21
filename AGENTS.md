# AGENTS.md

## Reglas transversales

1. Demuestra que funciona antes de darlo por hecho: comando real, test o captura.
2. Arregla la causa raíz, no el síntoma.
3. Resta antes de sumar: borra código muerto antes de añadir.
4. Haz el cambio mínimo que resuelve, sin capas ni abstracciones especulativas.
5. Los tests prueban comportamiento observable, no la implementación.
6. Amplía un test existente antes de crear otro y borra los que dejen de aplicar.
7. Sin comentarios en el código: que el nombre y la estructura lo expliquen.
8. Validación y manejo de errores en los bordes del sistema, no repartidos por todo el código.
9. Operaciones idempotentes: se pueden repetir sin daño.
10. Una unidad verificable por commit o PR.
11. Antes de reportar un número, explícalo y mídelo bien.
12. Si una corrección se repite, conviértela en estructura (test, lint, tipo) y no en otra instrucción.
13. Nunca inventes comandos, stack ni datos: solo lo comprobado.
14. Sin ficheros `.md` largos de planes o decisiones; el porqué va en la PR o en el commit.
15. Prosa breve y sin relleno en PRs, commits y documentación.
16. No cambies alcance, diseño ni prioridades por tu cuenta; si algo te bloquea, dilo con exactitud.
17. La preparación del entorno vive en `scripts/setup`. Es idempotente. Los archivos de cada proveedor de agentes en la nube solo lo invocan. Si cambias dependencias, toolchain o pasos de arranque, actualiza el script y comprueba que esos envoltorios siguen funcionando. Si el proyecto usa un proveedor sin envoltorio, créalo.

## Mantenimiento de skills

Hay dos clases:

1. **Instaladas desde pstack** (inglés, instalador oficial): `blast-radius`, `correct`, `principle-prove-it-works`, `tdd` y `unslop`. Se añaden o actualizan con el CLI [`skills`](https://github.com/vercel-labs/skills), por ejemplo:

   ```bash
   npx skills add cursor/plugins --skill tdd -a cursor -a github-copilot -a codex -a gemini-cli -a claude-code -y
   ```

   Esas skills pueden nombrar otras de pstack que no vienen en la plantilla (por ejemplo, `blast-radius` menciona `why` y `arena`). Si las necesitas, instálalas con `npx skills add cursor/plugins --skill <nombre>` o con `/add-plugin pstack` en Cursor.

2. **Propias de la plantilla** (español): `setup-proyecto`, `entorno-agentes`, `pr-lista`, `technical-writing` y `how`. Viven solo en este repositorio; para que Claude Code las vea, mantén los enlaces en `.claude/skills/` apuntando a `.agents/skills/<nombre>`.

Para actualizar las skills bloqueadas en `skills-lock.json`:

```bash
npx skills update -y
```

Revisa el diff, valida con `npx skills check` y commitea `.agents/skills/`, `.claude/skills/` y `skills-lock.json`.

### Créditos de skills de pstack

Skills de [pstack](https://github.com/cursor/plugins/tree/main/pstack) por Lauren Tan (licencia MIT), instaladas con el instalador oficial. Las adaptaciones en español `how` y `technical-writing` derivan del mismo origen; ver `.agents/skills/LICENSE`.

## Este proyecto

Lo rellena la skill `setup-proyecto` en la primera tarea del repositorio.