---
name: pr-lista
description: Checklist antes de pedir revisión de un pull request. Verifica tests, evidencia en la plantilla de PR y alcance acotado.
---

# Lista antes de la PR

Repasa esto antes de marcar la PR como lista para revisión.

## Checklist

1. **Tests en verde.** Ejecuta build y tests del proyecto (ver `AGENTS.md`) y confirma que pasan.
2. **Plantilla de PR.** Rellena Qué, Por qué, Cómo se ha probado y Evidencias. Si hay cambios visuales, incluye captura o enlace.
3. **Alcance.** El diff solo contiene lo pedido. Sin refactors, formateos masivos ni dependencias no relacionadas.
4. **Descripción breve.** Prosa directa, sin relleno ni listas de archivos sin contexto.
5. **Unidad verificable.** Cada commit o la PR completa se puede validar de forma independiente.
6. **Demostración.** Si afirmas que algo funciona, adjunta comando, salida de test o evidencia reproducible.

## Si falta algo

Corrige antes de pedir revisión. Si algo te bloquea, dilo en la PR con exactitud en lugar de enviar trabajo incompleto.