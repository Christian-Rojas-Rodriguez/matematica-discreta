# Plan de Estudio — Final de Equivalencia (Matemática Discreta, UNSAM)

**Objetivo:** Rendir el final de equivalencia en **septiembre de 2026**, con las 5 hojas de teoría dominadas y los ejercicios de cada subtema resueltos con soltura.
**Inicio del plan:** 4 de julio de 2026 (~9 semanas de margen antes de la ventana de examen)
**Ventana de examen estimada:** primeras dos semanas de septiembre — **ajustá las fechas exactas de las Semanas 8-9 apenas tengas la fecha real de la mesa**.

> Material de estudio: los resúmenes teóricos extensos están en [`teoria-obsidian/`](teoria-obsidian/00-Indice-Matematica-Discreta.md) (para leer/entender), la teoría condensada "hoja de examen" está en `0N_tema/readme.md` (para repasar rápido), y los ejercicios resueltos están en `ejercicios-resueltos/` (para practicar).

---

## Estructura del examen

5 subtemas evaluados de forma aislada, con 1 hoja de teoría permitida por tema:

| # | Tema | Teoría extensa (Obsidian) | Teoría condensada | Ejercicios |
|---|------|---------------------------|--------------------|------------|
| 1 | Razonamientos Categóricos | [teoria-obsidian/01-Razonamientos-Categoricos.md](teoria-obsidian/01-Razonamientos-Categoricos.md) | [readme](01_razonamientos_categoricos/readme.md) | [tema1_categoricos.md](ejercicios-resueltos/tema1_categoricos.md) |
| 2 | Relaciones de Equivalencia | [teoria-obsidian/02-Relaciones-de-Equivalencia.md](teoria-obsidian/02-Relaciones-de-Equivalencia.md) | [readme](02_relaciones_equivalencia/readme.md) | [tema2_equivalencia.md](ejercicios-resueltos/tema2_equivalencia.md) |
| 3 | Redes y Álgebras de Boole | [teoria-obsidian/03-Redes-y-Algebras-de-Boole.md](teoria-obsidian/03-Redes-y-Algebras-de-Boole.md) | [readme](03_redes_algebras_boole/readme.md) | [tema3_boole.md](ejercicios-resueltos/tema3_boole.md) |
| 4 | Congruencias / Euler-Fermat | [teoria-obsidian/04-Congruencias-Euler-Fermat.md](teoria-obsidian/04-Congruencias-Euler-Fermat.md) | [readme](04_congruencias_euler_fermat/readme.md) | [tema4_congruencias.md](ejercicios-resueltos/tema4_congruencias.md) |
| 5 | Relaciones de Recurrencia | [teoria-obsidian/05-Relaciones-de-Recurrencia.md](teoria-obsidian/05-Relaciones-de-Recurrencia.md) | [readme](05_relaciones_recurrencia/readme.md) | [tema5_recurrencia.md](ejercicios-resueltos/tema5_recurrencia.md) |

Prioridad si el tiempo aprieta (según frecuencia histórica en finales, ver [finales_resueltos/readme.md](finales_resueltos/readme.md)): **Equivalencia, Boole y Congruencias aparecen en el 100% de los finales revisados; Recurrencia en el 100% también; Categóricos en ~4 de 6.** No hay tema "descartable", pero si hay que elegir dónde reforzar primero, priorizar 2, 3, 4 y 5 por sobre 1.

---

## Cronograma — 9 semanas (04/07 → ~06/09)

### Semana 1 (6–12 jul) — Tema 1: Razonamientos Categóricos
- Leer completa [[01-Razonamientos-Categoricos]] (teoría extensa): definiciones, demostraciones de M.P./M.T./De Morgan generalizada, restricciones de P.U./G.U./P.E./G.E.
- Practicar: 4-5 razonamientos de `tema1_categoricos.md` (mezcla de validez y contraejemplo).
- Cierre de semana: resolver las preguntas de autoevaluación de la nota sin mirar la teoría.

### Semana 2 (13–19 jul) — Tema 2: Relaciones de Equivalencia (parte 1)
- Leer [[02-Relaciones-de-Equivalencia]]: definiciones, demostración de que congruencia mod n es de equivalencia, teorema fundamental (relación ⟺ partición).
- Practicar: demostrar que una relación dada por fórmula es de equivalencia (5-6 ejercicios de `tema2_equivalencia.md`).

### Semana 3 (20–26 jul) — Tema 2: Relaciones de Equivalencia (parte 2)
- Practicar: hallar clases de equivalencia y conjunto cociente, verificar con matriz (M², M=Mᵗ).
- Mini-examen: 2 ejercicios de Tema 2 en 30 min, sin apuntes.
- Repasar la sección "Conectores" de [[02-Relaciones-de-Equivalencia]] con [[04-Congruencias-Euler-Fermat]] (todavía no vista) para tener el gancho listo.

### Semana 4 (27 jul–2 ago) — Tema 5: Relaciones de Recurrencia (parte 1)
- Leer [[05-Relaciones-de-Recurrencia]]: ecuación característica, por qué funciona el ansatz $a_n = r^n$, caso de raíces distintas y raíz doble.
- Practicar: 4-5 recurrencias homogéneas de orden 2 de `tema5_recurrencia.md`.

### Semana 5 (3–9 ago) — Tema 5: Relaciones de Recurrencia (parte 2)
- Practicar: no homogéneas (constante, exponencial, con y sin resonancia), verificación por inducción, problema inverso.
- Mini-examen: 2 ejercicios de Tema 5 en 35 min, sin apuntes.

### Semana 6 (10–16 ago) — Tema 4: Congruencias / Euler-Fermat
- Leer [[04-Congruencias-Euler-Fermat]]: demostración de Fermat (permutación de residuos), Euler-Fermat, fórmula de $\varphi(n)$, condición de solución de $ax \equiv b \pmod n$.
- Practicar: cálculo de restos grandes (Fermat y Euler-Fermat) + ecuaciones de congruencia completas con $\gcd(a,n) > 1$.

### Semana 7 (17–23 ago) — Tema 3: Redes y Álgebras de Boole
- Leer [[03-Redes-y-Algebras-de-Boole]]: elementos notables, redes, unicidad del complemento en redes distributivas, criterio de álgebra de Boole para $(D_n; \mid)$.
- Practicar: analizar $(D_n; \mid)$ completo (Hasse, notables, red, distributiva, complementada, Boole) para 3-4 valores de $n$ distintos + demostraciones algebraicas genéricas en Boole.

### Semana 8 (24–30 ago) — Repaso cruzado + finales anteriores
- Repasar todos los conectores entre unidades (sección 6 de cada nota) — este es el momento de que la materia deje de sentirse como "5 temas sueltos".
- Resolver 2 finales completos de [finales_resueltos/readme.md](finales_resueltos/readme.md), cronometrados.
- Identificar los 2-3 puntos más débiles y reforzarlos puntualmente.

### Semana 9 (31 ago–6 sep) — Simulacro final + hojas de examen
- Preparar las 5 hojas de teoría condensada (una por tema, usando los `readme.md` de cada carpeta como base).
- Examen simulado completo (los 5 subtemas, tiempo real de examen).
- Repaso liviano día por medio de fórmulas clave (sección 4 de cada nota), sin ejercicios nuevos pesados.
- **Últimos 2-3 días antes de la fecha real:** solo repaso de fórmulas y errores comunes (sección 7 de cada nota), nada de contenido nuevo.

---

## Rutina semanal sugerida (2-3 hs/día, 5-6 días/semana)
1. **30 min** — leer/repasar teoría de la nota Obsidian del tema de la semana.
2. **60-90 min** — resolver ejercicios del tema (con el archivo de soluciones tapado hasta intentarlo).
3. **20-30 min** — repasar demostraciones clave a mano (sin mirar), y anotar dudas.
4. **Fin de semana** — mini-examen sin apuntes de lo visto esa semana + repaso de conectores con temas anteriores.

## Checklist de cierre (completar en la Semana 9)
- [ ] Las 5 notas de `teoria-obsidian/` leídas y entendidas de punta a punta.
- [ ] Las 5 hojas de teoría condensada impresas/preparadas.
- [ ] Al menos 2 finales anteriores completos resueltos cronometrados.
- [ ] Examen simulado hecho con ≥70% de aciertos.
- [ ] Fecha y lugar de la mesa de examen confirmados.
