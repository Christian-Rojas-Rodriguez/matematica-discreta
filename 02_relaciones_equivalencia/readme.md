# Relaciones de Equivalencia

## Que es y que NO es este subtema

**QUE ES:** Relaciones que son reflexivas, simetricas y transitivas; clases de equivalencia; conjunto cociente; particiones. Demostrar que una relacion es de equivalencia. Hallar clases y cociente.

**QUE NO ES:** Relaciones de orden (tema 3), funciones, composicion de relaciones, clausura transitiva, matrices booleanas como tema general.

## Contexto del Examen
- Formato tipico: dada una relacion en un conjunto, demostrar que es de equivalencia, hallar las clases de equivalencia y el conjunto cociente
- Pueden dar la relacion por: formula, condicion, matriz, o conjunto de pares
- Pueden pedir que verifiques si es de equivalencia con matriz o digrafo

---

## HOJA DE TEORIA (Teoria Condensada)

### 1. Definicion: Relacion de Equivalencia
R en A es de **equivalencia** si cumple las 3 propiedades:

| Propiedad | Definicion formal | Significado |
|-----------|-------------------|-------------|
| **Reflexiva** | ∀x ∈ A: xRx | Todo elemento se relaciona consigo mismo |
| **Simetrica** | ∀x,y ∈ A: xRy → yRx | Si x se relaciona con y, entonces y se relaciona con x |
| **Transitiva** | ∀x,y,z ∈ A: xRy ∧ yRz → xRz | Si x~y e y~z, entonces x~z |

### 2. Criterios con MATRIZ (M es la matriz de R)

| Propiedad | Criterio en la Matriz |
|-----------|----------------------|
| **Reflexiva** | Diagonal principal = todos 1 |
| **Simetrica** | M = M^t (matriz simetrica respecto a la diagonal) |
| **Transitiva** | M² ≤ M (donde M² es el producto booleano, y ≤ significa: si M²[i,j]=1 entonces M[i,j]=1) |

### 3. Criterios con DIGRAFO

| Propiedad | Criterio en el Digrafo |
|-----------|----------------------|
| **Reflexiva** | Todo vertice tiene lazo (flecha a si mismo) |
| **Simetrica** | Toda flecha tiene su "vuelta" (si hay flecha a→b, hay flecha b→a) |
| **Transitiva** | Si hay camino de a a b (de cualquier longitud), hay flecha directa a→b |

### 4. Plantilla de Demostracion Formal

#### Reflexiva:
```
Sea x ∈ A arbitrario.
[Demostrar que xRx usando la definicion de R]
∴ xRx → R es reflexiva.
```

#### Simetrica:
```
Sean x, y ∈ A tales que xRy.  (Hipotesis)
[A partir de xRy, demostrar que yRx usando la definicion de R]
∴ xRy → yRx → R es simetrica.
```

#### Transitiva:
```
Sean x, y, z ∈ A tales que xRy ∧ yRz.  (Hipotesis)
[A partir de xRy e yRz, demostrar que xRz usando la definicion de R]
∴ xRy ∧ yRz → xRz → R es transitiva.
```

### 5. Ejemplo de demostracion: Congruencia modulo n
R en ℤ: xRy ⟺ n | (x-y)

**Reflexiva:** ∀x ∈ ℤ: x - x = 0 = n·0 → n | (x-x) → xRx ✓

**Simetrica:** Si xRy → n | (x-y) → x-y = n·k → y-x = n·(-k) → n | (y-x) → yRx ✓

**Transitiva:** Si xRy ∧ yRz → x-y = n·k ∧ y-z = n·t → (x-y)+(y-z) = n·k+n·t → x-z = n·(k+t) → n | (x-z) → xRz ✓

### 6. Clase de Equivalencia
```
x̄ = [x] = {y ∈ A / xRy}
```
Es el conjunto de TODOS los elementos de A que se relacionan con x.

**Propiedades:**
- x ∈ x̄ (por reflexividad)
- Si xRy → x̄ = ȳ (las clases de elementos relacionados son iguales)
- Si ¬(xRy) → x̄ ∩ ȳ = ∅ (las clases de no-relacionados son disjuntas)
- Cualquier elemento de una clase sirve como representante

### 7. Conjunto Cociente
```
A/R = {x̄ / x ∈ A} = {todas las clases de equivalencia distintas}
```

**Ejemplo:** ℤ/≡₃ = {0̄, 1̄, 2̄} donde:
- 0̄ = {..., -6, -3, 0, 3, 6, ...} (multiplos de 3)
- 1̄ = {..., -5, -2, 1, 4, 7, ...} (resto 1 al dividir por 3)
- 2̄ = {..., -4, -1, 2, 5, 8, ...} (resto 2 al dividir por 3)

### 8. Particion
Una **particion** de A es una familia de subconjuntos {A₁, A₂, ..., Aₖ} tal que:
1. A_i ≠ ∅ para todo i
2. A_i ∩ A_j = ∅ si i ≠ j (son disjuntos entre si)
3. A₁ ∪ A₂ ∪ ... ∪ Aₖ = A (cubren todo A)

### 9. Teorema Fundamental
```
R es relacion de equivalencia en A  ⟺  A/R es una particion de A
```

- Toda relacion de equivalencia genera una particion (las clases)
- Toda particion define una relacion de equivalencia (xRy sii estan en el mismo bloque)

### 10. Como hallar las clases (metodo practico)
1. Tomar un elemento x₁ ∈ A
2. Hallar x̄₁ = {todos los y tal que x₁Ry}
3. Tomar un elemento x₂ ∈ A que NO este en x̄₁
4. Hallar x̄₂
5. Repetir hasta agotar A
6. A/R = {x̄₁, x̄₂, ..., x̄ₖ}

**Verificacion:** Las clases deben ser disjuntas y su union debe dar A.

---

## Metodo de Resolucion Paso a Paso

### Para DEMOSTRAR que R es de equivalencia:
1. **Reflexiva:** Tomar x ∈ A arbitrario, demostrar xRx
2. **Simetrica:** Suponer xRy, demostrar yRx
3. **Transitiva:** Suponer xRy ∧ yRz, demostrar xRz
4. Conclusion: R es de equivalencia por ser reflexiva, simetrica y transitiva

### Para HALLAR clases de equivalencia:
1. Elegir un elemento, hallar todo lo que se relaciona con el → esa es su clase
2. Elegir un elemento no cubierto, repetir
3. Escribir A/R = {clase1, clase2, ...}
4. Verificar: ¿son disjuntas? ¿cubren todo A?

### Para verificar con MATRIZ:
1. Diagonal toda de 1s → reflexiva ✓
2. M = M^t → simetrica ✓
3. Calcular M² (producto booleano), verificar M² ≤ M → transitiva ✓

### Ejemplo completo:
A = {1, 2, 3, 4, 5, 6}, R definida por: xRy ⟺ 3 | (x-y)

1. **Reflexiva:** x - x = 0, y 3|0 ✓
2. **Simetrica:** Si 3|(x-y) → x-y=3k → y-x=3(-k) → 3|(y-x) ✓
3. **Transitiva:** Si 3|(x-y) y 3|(y-z) → 3|((x-y)+(y-z)) → 3|(x-z) ✓
4. **Clases:**
   - 1̄ = {1, 4} (pues 3|(1-4)=-3)
   - 2̄ = {2, 5} (pues 3|(2-5)=-3)
   - 3̄ = {3, 6} (pues 3|(3-6)=-3)
5. **A/R = {{1,4}, {2,5}, {3,6}}** → Es particion de A ✓

---

## Referencias Cruzadas

### Ejercicios RELEVANTES
- `7_ejecicio_relaciones.pdf` → Seccion IV: **Ej.20-36**
- **Respuestas:** `7_respuesta_relaciones.pdf` Ej.20-25

### Ejercicios NO relevantes
- `7_ejecicio_relaciones.pdf` → Secciones I-III (Ej.1-19: relaciones generales, funciones, matrices booleanas)

### Teoria de referencia
- `7_teoria_relaciones.pdf` → Seccion de relaciones de equivalencia

---

## Prioridad de Practica
1. **ALTA**: Demostrar que una relacion dada por formula es de equivalencia (Ej.20-25)
2. **ALTA**: Hallar clases de equivalencia y conjunto cociente
3. **MEDIA**: Verificar equivalencia usando matriz (diagonal, simetria, M²≤M)
4. **MEDIA**: Relacionar particion con relacion de equivalencia
5. **BAJA**: Verificar con digrafo (menos comun en finales)
