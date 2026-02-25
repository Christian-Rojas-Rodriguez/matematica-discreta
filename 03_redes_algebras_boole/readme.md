# Redes y Algebras de Boole

## Que es y que NO es este subtema

**QUE ES:** Relaciones de orden parcial, diagramas de Hasse, elementos notables (maximal, minimal, maximo, minimo, supremo, infimo, cotas), redes (reticulados), redes distributivas, redes complementadas, algebras de Boole, propiedades y demostraciones.

**QUE NO ES:** Relaciones de equivalencia (tema 2), funciones, composicion de relaciones, matrices booleanas como tema aislado.

## Contexto del Examen
- Formato tipico: dado un conjunto ordenado (Dn; |) o (P(A); ⊆), analizar si es red, si es distributiva, si es complementada, si es algebra de Boole
- Pueden pedir: hallar elementos notables, dibujar diagrama de Hasse, hallar complementos
- Pueden pedir: demostrar propiedades en algebras de Boole genericas usando las leyes

---

## HOJA DE TEORIA (Teoria Condensada)

### 1. Relacion de Orden Parcial
Una relacion R en A es de **orden** si cumple:
- **Reflexiva:** ∀x ∈ A: xRx
- **Antisimetrica:** ∀x,y ∈ A: xRy ∧ yRx → x = y
- **Transitiva:** ∀x,y,z ∈ A: xRy ∧ yRz → xRz

Notacion: (A; ≤) o (A; ≼)

### 2. Diagrama de Hasse
- Se dibuja de abajo (menores) hacia arriba (mayores)
- Se omiten lazos (reflexiva) y flechas transitivas
- Se omiten puntas de flecha (se entiende que va hacia arriba)
- Solo se dibujan las relaciones "inmediatas" (cobertura)

### 3. Elementos Notables
| Elemento | Definicion | Puede no existir? |
|----------|------------|-------------------|
| **Minimo** (0_A) | ∀x ∈ A: 0_A ≼ x (menor que todos) | Si, puede no existir |
| **Maximo** (1_A) | ∀x ∈ A: x ≼ 1_A (mayor que todos) | Si, puede no existir |
| **Minimal** | No hay nadie menor que el (excepto el mismo) | Siempre existe al menos 1 |
| **Maximal** | No hay nadie mayor que el (excepto el mismo) | Siempre existe al menos 1 |
| **Cota superior** de S | c es cota sup de S si ∀x ∈ S: x ≼ c | Puede no existir |
| **Cota inferior** de S | c es cota inf de S si ∀x ∈ S: c ≼ x | Puede no existir |
| **Supremo** de S | La menor de las cotas superiores | Unico si existe |
| **Infimo** de S | La mayor de las cotas inferiores | Unico si existe |

**Relacion clave:**
- Si existe minimo → es unico y es el unico minimal
- Si existe maximo → es unico y es el unico maximal
- Supremo ∈ S → es el maximo de S
- Infimo ∈ S → es el minimo de S

### 4. Ejemplos importantes de conjuntos ordenados
| Conjunto | Relacion | Supremo de {a,b} | Infimo de {a,b} |
|----------|----------|-------------------|------------------|
| (D_n; \|) | a\|b (divisibilidad) | mcm(a,b) | mcd(a,b) |
| (P(A); ⊆) | inclusion | A ∪ B | A ∩ B |
| (ℕ; ≤) | orden usual | max(a,b) | min(a,b) |

### 5. Redes (Reticulos / Lattice)
```
(A; ≼) es RED  ⟺  ∀ a,b ∈ A: existen sup{a,b} e inf{a,b}
```

**Notacion:** sup{a,b} = a ∨ b,  inf{a,b} = a ∧ b

**Para verificar si es red:** Solo hay que chequear los pares INCOMPARABLES (los comparables siempre tienen sup e inf).

**Criterios rapidos:**
- Mas de 1 maximal o mas de 1 minimal → **NO es red** (los maximales no tienen supremo entre si)
- Unico maximal y unico minimal → condicion NECESARIA pero NO SUFICIENTE

**Propiedad clave:** Si a ≼ b → a ∨ b = b y a ∧ b = a

### 6. Propiedades de las operaciones ∨ e ∧ en una Red
| Propiedad | ∨ (supremo) | ∧ (infimo) |
|-----------|-------------|------------|
| Cerrada | ∀x,y: x ∨ y ∈ A | ∀x,y: x ∧ y ∈ A |
| Asociativa | x ∨ (y ∨ z) = (x ∨ y) ∨ z | x ∧ (y ∧ z) = (x ∧ y) ∧ z |
| Conmutativa | x ∨ y = y ∨ x | x ∧ y = y ∧ x |
| Idempotente | x ∨ x = x | x ∧ x = x |
| Absorcion | x ∨ (x ∧ y) = x | x ∧ (x ∨ y) = x |

**Equivalencia fundamental:** a ≼ b ⟺ a ∨ b = b ⟺ a ∧ b = a

### 7. Red Algebraica
(A; ∗; ∗') es red algebraica si ∗ y ∗' son: cerradas, asociativas, conmutativas, idempotentes y cumplen absorcion.

**Toda red ordenada es algebraica y viceversa.**
- De ordenada a algebraica: ∨ = sup, ∧ = inf
- De algebraica a ordenada: a ≼ b ⟺ a ∧ b = a (o a ∨ b = b)

### 8. Complemento de un elemento
Sea (A; ≼) una red con primer elemento 0_A y ultimo elemento 1_A.

**Complemento de a** (notacion: ā):
```
a ∧ ā = 0_A   y   a ∨ ā = 1_A
```

En una red, un elemento puede tener 0, 1 o mas complementos.

### 9. Red Complementada
```
Red complementada ⟺ TODOS los elementos tienen al menos un complemento
```
(Requiere que existan 0_A y 1_A)

### 10. Red Distributiva
```
∀a,b,c ∈ A:  a ∨ (b ∧ c) = (a ∨ b) ∧ (a ∨ c)
             a ∧ (b ∨ c) = (a ∧ b) ∨ (a ∧ c)
```

**Propiedad clave:** En toda red distributiva, si un complemento existe, es UNICO.
- Si algun elemento tiene 2+ complementos → la red NO es distributiva.

**Criterio visual:** Una red finita es distributiva sii NO contiene una subred isomorfa a ninguno de estos dos diagramas (pentagonal o diamante con 3 atomos en el medio).

### 11. ALGEBRA DE BOOLE
```
Algebra de Boole = Red DISTRIBUTIVA + COMPLEMENTADA (+ tiene 0 y 1)
```

**Definicion equivalente:** (B; ∨; ∧) es Algebra de Boole si:
- ∨ e ∧ son cerradas y conmutativas
- ∨ e ∧ son distributivas entre si
- ∨ e ∧ tienen neutros 0_B y 1_B respectivamente
- Todo elemento tiene complemento

### 12. Criterios rapidos para Algebra de Boole
| Conjunto | Es Algebra de Boole? | Criterio |
|----------|---------------------|----------|
| (D_n; \|) | **SI** sii n es libre de cuadrados (producto de primos DISTINTOS) | 30=2·3·5 SI, 12=2²·3 NO |
| (P(A); ⊆) | **SIEMPRE** | Complemento: Ā = A - X |
| ({0,1}; +; ·) logica | **SI** | Es la algebra de Boole canonica (la menor) |

**Propiedad:** El cardinal de toda Algebra de Boole finita es potencia de 2 (2, 4, 8, 16...).

### 13. Propiedades en Algebra de Boole
- 0_B y 1_B son unicos
- Todo complemento es unico
- Involucion: ā̄ = a (doble complemento)
- Neutros se complementan: 1̄_B = 0_B, 0̄_B = 1_B
- **Leyes de De Morgan:** (a ∨ b)̄ = ā ∧ b̄,  (a ∧ b)̄ = ā ∨ b̄
- Principio de Dualidad: si una propiedad vale, su dual tambien (intercambiando ∨↔∧ y 0↔1)

### 14. Isomorfismo
Toda Algebra de Boole finita con 2^n elementos es isomorfa a (P({a₁,...,aₙ}); ⊆).

---

## Metodo de Resolucion Paso a Paso

### Para analizar (D_n; |):
1. **Hallar divisores** de n
2. **Dibujar Hasse:** a → b si a|b y no hay c intermedio
3. **Elementos notables:** min=1, max=n, minimales, maximales
4. **¿Es red?** Verificar sup e inf para pares incomparables (en D_n siempre es red: sup=mcm, inf=mcd)
5. **¿Es distributiva?** En D_n siempre es distributiva (mcm y mcd distribuyen)
6. **¿Es complementada?** Buscar complemento de cada divisor d: mcd(d,d̄)=1 y mcm(d,d̄)=n
7. **¿Es Algebra de Boole?** Criterio rapido: n es libre de cuadrados?

### Para demostrar propiedades en Algebra de Boole:
1. Partir de la hipotesis
2. Usar las propiedades: distributiva, complementacion, absorcion, De Morgan, neutros
3. Para VERDADERO: demostrar algebraicamente
4. Para FALSO: dar contraejemplo en un algebra concreta (ej: D_30)

---

## Referencias Cruzadas

### Ejercicios RELEVANTES
- `8_ejercicio_boole.pdf` → **Ej.1-30** (todo el tema aplica)
- **Respuestas:** `8_respuesta_boole.pdf`

### Teoria de referencia
- `8_teoria_boole.pdf` (completo, ~55 slides)

---

## Prioridad de Practica
1. **ALTA**: Determinar si (D_n; |) es Algebra de Boole y hallar complementos
2. **ALTA**: Demostrar/refutar propiedades en algebras de Boole genericas
3. **MEDIA**: Analizar si un conjunto ordenado dado es red
4. **MEDIA**: Hallar elementos notables en diagramas de Hasse
5. **BAJA**: Construir tablas de ∨ e ∧ (laborioso, poco probable en final)
