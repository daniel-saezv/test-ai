---
name: technical-writing
description: Estándar de escritura técnica en capas (Diátaxis, estilo desarrollador, instrucciones claras). Usar al redactar o revisar docs, RFCs, README, descripciones de PR o mensajes de commit.
---

# Escritura técnica

Escribe para que alguien cansado entienda a la primera.

- Quita cada palabra que no trabaja.
- Usa la palabra corta y cotidiana: «usa», no «utiliza».
- Si una regla empeora una frase, arréglala de otro modo o déjala.
- Escribe el símbolo, archivo, flag o comando real, no un sinónimo.
- No inventes jerga. Usa lo que un desarrollador diría en voz alta. Explica un patrón con nombre la primera vez.

## Ritmo

- Alterna longitudes de frase. Parte la que lleva dos ideas. Conserva la larga que lleva una sola.
- En explicación puede haber opinión; en referencia, secado.
- Sé concreto. No «los cambios de esquema pueden dar problemas», sino «un renombre de columna rompe el build».

## Elige el modo primero (Diátaxis)

Un documento, un modo. No mezcles; divide y enlaza.

- **Tutorial: aprender haciendo.** Di qué construirá quien aprende. Cada paso produce un resultado visible y dices qué debe ver. La explicación, una cláusula y un enlace.
- **Guía práctica: pasos hacia un objetivo.** Resuelve el problema del lector. Asume competencia. Solo acción. Permite bifurcaciones. Nombra la guía por la tarea.
- **Referencia: hechos para consultar.** Solo describe. Seco, completo y seguro. Refleja la estructura de lo descrito.
- **Explicación: entender el porqué.** Un tema acotado. Contexto: decisiones de diseño, historia, restricciones, alternativas. La opinión solo aquí.

## Frases al lector (estilo desarrollador)

- Habla al lector como «tú», en presente.
- Di quién hace qué. La pasiva solo si el actor es irrelevante o desconocido.
- Instrucciones como órdenes. Condición antes del paso; caso habitual primero.
- Sin buzzwords, sin metáforas, sin «por favor», y nunca «simplemente», «fácil» o «rápido» en un procedimiento.
- No anuncies lo que vas a decir; no empieces frases seguidas igual.
- Enlaces con palabras que digan el destino.
- Títulos con el punto, en estilo frase. Un h1 por página, sin saltar niveles.
- Listas numeradas para secuencias; viñetas para el resto. Introduce la lista con frase completa. Ítems paralelos.
- Código en fuente monoespaciada. Elementos de interfaz en negrita. Comas seriadas. Sin «etc.».

## Una idea por frase

- Una instrucción por frase. Un pensamiento por frase en el resto.
- Parte instrucciones de más de unas veinte palabras y otras frases de más de unas veinticinco.
- Advertencia o condición antes del paso que protege.
- Conserva artículos definidos e indefinidos.
- Una palabra por acción; un significado por palabra.
- Procedimientos en imperativo directo, no narración ni pasiva.
- Evita gerundios donde puedas.

## Sin doble lectura

- «Solo» y «no» junto a la palabra que modifican.
- Rompe cadenas largas de sustantivos.
- Cada «esto», «ello» o «lo» apunta a algo obvio. No uses «lo cual» para una cláusula entera.
- No omitas verbos ni palabras de enlace como «que».
- Repite el artículo en series si evita ambigüedad. Di qué une «y» u «o».
- Puntos, no punto y coma ni rayas largas. Sin barras ni «(s)». El texto entre paréntesis debe ser gramaticalmente completo.
- Un nombre por cosa, en todo el documento.
- Sin modismos, latinismos abreviados ni metáforas.

## Relleno típico de IA

Evita vocabulario hueco («robusto», «meticuloso», «crucial», «es importante destacar»), muletillas de transición vacías, hedging innecesario y tablas o listas que no aportan dato nuevo.

## PRs y commits

Las descripciones de PR y los mensajes de commit también son escritura. Todas las capas salvo Diátaxis aplican. El cuerpo de la PR es un briefing de menos de un minuto. No pegues logs largos ni tablas de métricas; enlázalas.

Las cadenas de interfaz de producto no son documentación: sigue las guías de copy del producto.

Indenta fragmentos de código con tabuladores. Rutas reales. Cada conteo o árbol debe ser cierto en el commit que lo afirma, con el comando para regenerarlo.