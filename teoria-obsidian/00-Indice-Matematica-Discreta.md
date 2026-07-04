---
tags: [matematica-discreta, indice, unsam, MOC]
aliases: ["Matemática Discreta", "MOC Matemática Discreta", "Índice"]
---

# Matemática Discreta — Índice General (MOC)

> [!info] Qué es esto
> Este es el **mapa de contenidos (MOC)** de los apuntes teóricos de Matemática Discreta (UNSAM), pensados para el **final de equivalencia** que evalúa 5 subtemas aislados. Cada nota de unidad es extensa, con definiciones formales, demostraciones completas, fórmulas y ejemplos. Esta nota es el punto de entrada: desde acá navegás a cada unidad y ves cómo se conectan entre sí.

## Las 5 unidades

| # | Unidad | Nota | Núcleo del tema |
|---|--------|------|-----------------|
| 1 | Razonamientos Categóricos | [[01-Razonamientos-Categoricos]] | Cuantificadores, reglas de inferencia, validez/invalidez |
| 2 | Relaciones de Equivalencia | [[02-Relaciones-de-Equivalencia]] | Reflexiva-simétrica-transitiva, clases, cociente, partición |
| 3 | Redes y Álgebras de Boole | [[03-Redes-y-Algebras-de-Boole]] | Orden parcial, retículos, distributividad, complemento, Boole |
| 4 | Congruencias / Euler-Fermat | [[04-Congruencias-Euler-Fermat]] | Congruencia módulo n, φ de Euler, Fermat, ecuaciones lineales |
| 5 | Relaciones de Recurrencia | [[05-Relaciones-de-Recurrencia]] | Ecuación característica, homogénea + particular, inducción |

Estas notas **expanden con rigor matemático** la teoría condensada que ya está en el repo (`01_razonamientos_categoricos/readme.md` … `05_relaciones_recurrencia/readme.md`), que sigue sirviendo como "hoja de examen" ultra-resumida. Acá el objetivo es **entender de cero**, no solo repasar.

## Por qué la materia no son 5 temas sueltos

Aunque el examen los evalúa por separado, matemáticamente estos 5 temas comparten una columna vertebral: **la relación binaria** y **el razonamiento deductivo formal**. Casi todo lo que se demuestra en la materia es, en el fondo, una de estas dos cosas:

1. Probar que una relación binaria cumple ciertas propiedades (reflexiva, simétrica/antisimétrica, transitiva) → aparece en Equivalencia y en Órdenes/Boole.
2. Construir una derivación deductiva rigurosa, paso a paso, cada paso justificado por una regla → aparece en Categóricos, en las demostraciones algebraicas de Boole, en Fermat/Euler-Fermat y en la inducción de Recurrencia.

## Mapa de conexiones

```mermaid
graph TD
    T1["Tema 1<br/>Razonamientos Categóricos<br/>(lógica de cuantificadores)"]
    T2["Tema 2<br/>Relaciones de Equivalencia<br/>(reflexiva-simétrica-transitiva)"]
    T3["Tema 3<br/>Redes y Álgebras de Boole<br/>(orden parcial, retículos)"]
    T4["Tema 4<br/>Congruencias / Euler-Fermat<br/>(teoría de números)"]
    T5["Tema 5<br/>Relaciones de Recurrencia<br/>(ecuaciones en diferencias)"]

    T1 -- "estructura de las demostraciones<br/>(∀x arbitrario = G.U.)" --> T2
    T1 -- "leyes de Boole formalizan<br/>los conectivos lógicos" --> T3
    T1 -- "Fermat/Euler-Fermat son<br/>proposiciones categóricas ∀" --> T4
    T1 -- "inducción = G.U. recursiva" --> T5

    T2 -- "orden parcial vs equivalencia:<br/>antisimétrica vs simétrica" --> T3
    T2 -- "congruencia mod n ES la relación;<br/>Z_n ES el cociente" --> T4
    T2 -.. "partición ~ homogénea+particular<br/>(analogía estructural)" .-> T5

    T3 -- "(D_n; |): mcd=ínfimo, mcm=supremo;<br/>factorización prima" --> T4
    T3 -.. "|P(A)| = 2^n satisface<br/>una recurrencia de orden 1" .-> T5

    T4 -- "Euclides es una recurrencia;<br/>soluciones x0+k·n/d es progresión" --> T5
```

(Líneas punteadas = conexión más débil/analógica; líneas sólidas = conexión matemática directa y fuerte.)

## Los 3 vínculos más importantes para el examen

1. **Congruencia = Equivalencia.** La relación "≡ (mod n)" del Tema 4 no es *parecida* a una relación de equivalencia: **es una**, y $\mathbb{Z}_n$ es literalmente $\mathbb{Z}/{\equiv_n}$. Si entendés bien clases y cociente en el Tema 2, la mitad del Tema 4 ya está entendida.
2. **$(D_n; \mid)$ conecta Boole con Congruencias.** El mismo `mcd` y `mcm` que usás para resolver `mcd(a,n)` con Euclides son el ínfimo y el supremo de la red de divisores. Y el criterio "$D_n$ es álgebra de Boole $\iff$ $n$ libre de cuadrados" depende de la misma factorización prima que usás para $\varphi(n)$.
3. **Toda demostración es un razonamiento categórico.** "Sea $x \in A$ arbitrario…" (Tema 2), encadenar leyes de Boole (Tema 3), la prueba de Fermat (Tema 4), o verificar por inducción (Tema 5) — todas son, estructuralmente, la misma maquinaria lógica del Tema 1: hipótesis, reglas, conclusión.

## Cómo estudiar con estas notas

1. Empezá cada unidad por la sección **"Introducción y motivación"** y las **Definiciones formales** — no te saltees a las fórmulas sin entender de dónde salen.
2. Leé las **demostraciones completas** de la sección 3 al menos una vez con lápiz y papel, reproduciéndolas vos.
3. Usá la tabla de **fórmulas clave** (sección 4) como repaso exprés los últimos días antes del examen.
4. Resolvé los **ejemplos** tapando la solución antes de mirarla.
5. Al terminar una unidad, leé su sección **"Conectores con otras unidades"** y anotá (en Obsidian, con backlinks) cómo se relaciona con lo que ya estudiaste.
6. Contestá las **preguntas de autoevaluación** sin mirar la nota.
7. Complementá con los ejercicios resueltos del repo (carpeta `ejercicios-resueltos/`) y con `../PLAN_ESTUDIO_SEPTIEMBRE_2026.md` para el cronograma día a día.

## Referencias generales del repo
- Plan de estudio (cronograma hacia septiembre): `../PLAN_ESTUDIO_SEPTIEMBRE_2026.md`
- Teoría condensada original ("hoja de examen"): `../01_razonamientos_categoricos/readme.md`, `../02_relaciones_equivalencia/readme.md`, `../03_redes_algebras_boole/readme.md`, `../04_congruencias_euler_fermat/readme.md`, `../05_relaciones_recurrencia/readme.md`
- Ejercicios resueltos: `../ejercicios-resueltos/`
- Finales anteriores mapeados por subtema: `../finales_resueltos/readme.md`
