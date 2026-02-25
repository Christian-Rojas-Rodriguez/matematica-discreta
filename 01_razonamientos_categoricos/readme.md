# Razonamientos Categoricos

## Que es y que NO es este subtema

**QUE ES:** Razonamientos con cuantificadores (∀, ∃) y predicados, simbolizados con diccionario y conjunto universal, demostrados por reglas de inferencia o refutados con contraejemplo.

**QUE NO ES:** Tablas de verdad de proposiciones compuestas, clasificacion tautologia/contradiccion/contingencia, simplificacion por leyes logicas, logica proposicional pura sin cuantificadores.

## Contexto del Examen
- Final de equivalencia: te dan un razonamiento en lenguaje natural
- Debes: armar diccionario + conjunto universal, simbolizar, y demostrar validez (reglas) o invalidez (contraejemplo)
- Formato tipico: 1 ejercicio de demostrar validez + 1 de refutar con contraejemplo

---

## HOJA DE TEORIA (Teoria Condensada)

### 1. Conectivos Logicos (solo como herramienta para simbolizar)
| Simbolo | Nombre | Lectura |
|---------|--------|---------|
| ¬ | Negacion | "no" |
| ∧ | Conjuncion | "y" |
| ∨ | Disyuncion | "o" |
| → | Condicional | "si...entonces" |
| ↔ | Bicondicional | "si y solo si" |

### 2. Cuantificadores
| Simbolo | Nombre | Lectura | Negacion |
|---------|--------|---------|----------|
| ∀x | Universal | "para todo x" | ¬(∀x P(x)) ≡ ∃x ¬P(x) |
| ∃x | Existencial | "existe un x tal que" | ¬(∃x P(x)) ≡ ∀x ¬P(x) |

### 3. Reglas de Inferencia Basicas
| Regla | Esquema | Abreviatura |
|-------|---------|-------------|
| Modus Ponens | p→q, p ⊢ q | M.P. |
| Modus Tollens | p→q, ¬q ⊢ ¬p | M.T. |
| Silogismo Disyuntivo | p∨q, ¬p ⊢ q | S.D. |
| Silogismo Hipotetico | p→q, q→r ⊢ p→r | S.H. |
| Dilema Constructivo | p→q, r→s, p∨r ⊢ q∨s | Dilema |
| Absorcion | p→q ⊢ p→(p∧q) | Abs. |
| Simplificacion | p∧q ⊢ p | Simp. |
| Adicion | p ⊢ p∨q | Ad. |
| Conjuncion | p, q ⊢ p∧q | Conj. |

### 4. Reglas con Cuantificadores
| Regla | Descripcion | Restricciones |
|-------|-------------|---------------|
| **P.U.** (Particularizacion Universal) | ∀x P(x) ⊢ P(a) para cualquier a ∈ U | Sin restricciones |
| **G.U.** (Generalizacion Universal) | P(a) ⊢ ∀x P(x) | "a" debe ser ARBITRARIO (no aparecer en premisas ni supuestos) |
| **P.E.** (Particularizacion Existencial) | ∃x P(x) ⊢ P(c) | "c" debe ser un nombre NUEVO (no usado antes) |
| **G.E.** (Generalizacion Existencial) | P(a) ⊢ ∃x P(x) | Sin restricciones |

### 5. Como armar el Diccionario
1. Identificar el **Conjunto Universal** U (ej: "personas", "estudiantes", "numeros")
2. Asignar **letras predicado** a cada propiedad (ej: P(x): "x es programador")
3. Las **constantes** son individuos especificos (ej: a: "Juan")
4. Simbolizar cada premisa y la conclusion

### 6. Metodo para DEMOSTRAR VALIDEZ
```
1. Premisa 1                    (Premisa)
2. Premisa 2                    (Premisa)
3. P(a)                         (P.U. en 1)  ← particularizo
4. ...                          (regla en lineas anteriores)
...
n. Conclusion                   (regla final)
```
- Numerar cada paso
- Justificar con la regla usada y las lineas de referencia
- Usar P.U. para "bajar" cuantificadores universales
- Usar P.E. para instanciar existenciales (nombre nuevo!)
- Aplicar reglas basicas para avanzar
- Cerrar con G.U. o G.E. si la conclusion tiene cuantificadores

### 7. Metodo para REFUTAR (Contraejemplo)
1. Definir un **Conjunto Universal** U concreto y pequeno (ej: U = {1, 2, 3})
2. Asignar **interpretaciones** a los predicados (ej: P = {1, 2}, Q = {2, 3})
3. Verificar que **TODAS las premisas sean Verdaderas**
4. Verificar que la **conclusion sea Falsa**
5. Si se logra → el razonamiento es INVALIDO

### 8. Tabla rapida: Verdad de proposiciones cuantificadas
| Proposicion | V cuando... | F cuando... |
|-------------|-------------|-------------|
| ∀x P(x) | P se cumple para TODO elemento de U | Existe al menos un elemento donde P falla |
| ∃x P(x) | P se cumple para AL MENOS UN elemento | P no se cumple para NINGUN elemento |

---

## Metodo de Resolucion Paso a Paso

### Para DEMOSTRAR validez:
1. **Leer** el razonamiento completo
2. **Armar diccionario**: U, predicados, constantes
3. **Simbolizar** cada premisa y la conclusion con cuantificadores
4. **Desmontar** cuantificadores (P.U., P.E.) para trabajar con proposiciones
5. **Encadenar** reglas basicas hasta llegar a la conclusion
6. **Remontar** cuantificadores si la conclusion los tiene (G.U., G.E.)

### Para REFUTAR:
1. **Simbolizar** premisas y conclusion
2. **Elegir** U pequeno (2 o 3 elementos)
3. **Probar** interpretaciones hasta que premisas=V y conclusion=F
4. **Verificar** cada premisa explicitamente

---

## Referencias Cruzadas

### Ejercicios RELEVANTES
- `1_problema_categorica.pdf` → Seccion III: **Ej.10-18**
  - Ej.10-12: Razonamientos categoricos basicos
  - Ej.13-18: Categoricos puros (mas representativos del final)
  - **Ej.18**: Incluye diagramas de Venn para categoricos

### Ejercicios NO relevantes (ignorar)
- `1_problema_categorica.pdf` → Seccion I (Ej.1-6): logica simbolica proposicional
- `1_problema_categorica.pdf` → Seccion II (Ej.7-9): funciones proposicionales puras

### Teoria de referencia
- `1_teoria_categorico.pdf` → Slides 25-44 (razonamientos y reglas de inferencia)

---

## Prioridad de Practica
1. **ALTA**: Ej.13-18 (categoricos puros, formato tipico de final)
2. **MEDIA**: Ej.10-12 (categoricos con algo de proposicional)
3. **BAJA**: Ej.18 con Venn (menos probable en final pero posible)
