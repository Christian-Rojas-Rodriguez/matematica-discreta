# Ecuaciones Lineales de Congruencia / Teorema Euler-Fermat

## Que es y que NO es este subtema

**QUE ES:** Resolver ecuaciones ax≡b(mod n), aplicar funcion phi de Euler y teoremas de Fermat/Euler-Fermat para calcular restos de potencias grandes.

**QUE NO ES:** Divisibilidad general como tema aislado, MCD/MCM por si solos, numeros perfectos, algoritmo de Euclides sin aplicacion a congruencias.

## Contexto del Examen
- Formato tipico: 1 ecuacion lineal de congruencia para resolver + 1 calculo de resto de potencia grande usando Fermat o Euler-Fermat
- Pueden pedir: determinar si tiene solucion, cuantas soluciones tiene, hallar las soluciones principales
- Pueden pedir: hallar el resto de a^k dividido n, o el ultimo digito de un numero grande

---

## HOJA DE TEORIA (Teoria Condensada)

### 1. Congruencia Modulo n - Definicion
```
a ≡ b (mod n)  ⟺  n | (a - b)  ⟺  a y b tienen el mismo resto al dividir por n
```

### 2. Propiedades Operativas
Si a ≡ b (n) y c ≡ d (n), entonces:
- **Suma:** a + c ≡ b + d (n)
- **Producto:** a · c ≡ b · d (n)
- **Potencia:** a^k ≡ b^k (n)
- **Cancelacion:** Si a·c ≡ b·c (n) y mcd(c,n) = 1 → a ≡ b (n)

### 3. Clases Residuales y Conjunto Cociente
- Clase de equivalencia: x̄ = {y ∈ ℤ / y ≡ x (n)} = {y ∈ ℤ / y = nk + x, k ∈ ℤ}
- Conjunto cociente: ℤ_n = {0̄, 1̄, 2̄, ..., n̄-̄1̄}
- Operaciones: ā + b̄ = (a+b) mod n, ā · b̄ = (a·b) mod n

### 4. Ecuacion Lineal de Congruencia: a·x ≡ b (n)

#### Condicion necesaria y suficiente para tener solucion:
```
a·x ≡ b (n) tiene solucion  ⟺  mcd(a,n) | b
```
- **Cantidad de soluciones principales:** mcd(a,n)

#### Caso especial - mcd(a,n) = 1 (solucion unica):
```
x = a^(φ(n)-1) · b  (mod n)
```

#### Metodo completo de resolucion:
1. Calcular d = mcd(a,n)
2. Verificar si d | b
   - Si NO divide → **NO tiene solucion**
   - Si divide → tiene **d soluciones principales**
3. Simplificar: dividir a, b y n por d → ecuacion simplificada: (a/d)·x ≡ (b/d) (mod n/d)
4. La ecuacion simplificada tiene mcd(a/d, n/d) = 1 → solucion unica x₀
5. Hallar x₀ con la formula: x₀ = (a/d)^(φ(n/d)-1) · (b/d) mod (n/d)
6. Las d soluciones principales de la original son: x₀, x₀ + n/d, x₀ + 2n/d, ..., x₀ + (d-1)·n/d

### 5. Funcion φ de Euler
```
φ(n) = |{x ∈ ℕ / x ≤ n ∧ mcd(x,n) = 1}|
```
(Cantidad de numeros entre 1 y n coprimos con n)

#### Formulas de calculo:
| Caso | Formula | Ejemplo |
|------|---------|---------|
| p primo | φ(p) = p - 1 | φ(7) = 6 |
| p^k (p primo) | φ(p^k) = p^(k-1)·(p-1) | φ(9) = φ(3²) = 3¹·2 = 6 |
| mcd(n,m) = 1 | φ(n·m) = φ(n)·φ(m) | φ(15) = φ(3)·φ(5) = 2·4 = 8 |
| **Formula general** | **φ(n) = n·∏(1 - 1/p_i)** | φ(12) = 12·(1-1/2)·(1-1/3) = 4 |

donde p_i son los primos que dividen a n.

#### Metodo rapido para φ(n):
1. Factorizar n = p₁^k₁ · p₂^k₂ · ... · pᵣ^kᵣ
2. φ(n) = n · (1 - 1/p₁) · (1 - 1/p₂) · ... · (1 - 1/pᵣ)

**Ejemplos rapidos:**
- φ(48) = 48 · (1-1/2) · (1-1/3) = 48 · 1/2 · 2/3 = 16
- φ(75) = 75 · (1-1/3) · (1-1/5) = 75 · 2/3 · 4/5 = 40
- φ(100) = 100 · (1-1/2) · (1-1/5) = 100 · 1/2 · 4/5 = 40

### 6. Pequeno Teorema de Fermat
```
Si p es primo y mcd(a,p) = 1  →  a^(p-1) ≡ 1 (mod p)
```
Version alternativa: a^p ≡ a (mod p)

**Uso:** Calcular resto de a^k ÷ p (p primo)

**Metodo:**
1. Dividir el exponente k por (p-1): k = (p-1)·q + r
2. Entonces: a^k = (a^(p-1))^q · a^r ≡ 1^q · a^r ≡ a^r (mod p)
3. Calcular a^r mod p (exponente pequeno)

**Ejemplo:** Resto de 7^122 ÷ 11
- 122 = 10·12 + 2 (pues p-1 = 10)
- 7^122 ≡ 7^2 ≡ 49 ≡ 5 (mod 11)

### 7. Teorema de Euler-Fermat (generalizacion)
```
Si mcd(a,n) = 1  →  a^φ(n) ≡ 1 (mod n)
```
**Uso:** Calcular resto de a^k ÷ n (n NO necesariamente primo)

**Metodo:**
1. Verificar mcd(a,n) = 1
2. Calcular φ(n)
3. Dividir k por φ(n): k = φ(n)·q + r
4. a^k ≡ a^r (mod n)
5. Calcular a^r mod n

**Ejemplo:** Resto de 8^1791485 ÷ 21
- mcd(8,21) = 1 ✓
- φ(21) = φ(3·7) = φ(3)·φ(7) = 2·6 = 12
- 1791485 = 12·149290 + 5
- 8^1791485 ≡ 8^5 (mod 21)
- 8^5 = 8²·8²·8 = 64·64·8, y 64 ≡ 1 (21) → 8^5 ≡ 1·1·8 = 8 (mod 21)

### 8. Algoritmo de Euclides (herramienta para MCD)
Para mcd(a,b) con a > b:
```
a = b·q₁ + r₁
b = r₁·q₂ + r₂
r₁ = r₂·q₃ + r₃
...hasta resto 0
```
El ultimo resto no nulo es el mcd.

---

## Metodo de Resolucion Paso a Paso

### Para ECUACION a·x ≡ b (n):
1. Calcular d = mcd(a,n) con Euclides
2. ¿d | b? → Si no, NO hay solucion. Si si, hay d soluciones.
3. Simplificar: (a/d)·x ≡ (b/d) (mod n/d)
4. Calcular φ(n/d)
5. x₀ = (a/d)^(φ(n/d)-1) · (b/d) mod (n/d)
6. Soluciones: x₀, x₀ + n/d, x₀ + 2·n/d, ...

### Para RESTO de a^k mod n:
1. Verificar mcd(a,n) = 1
2. ¿n es primo? → Usar Fermat (exponente p-1). ¿No? → Usar Euler-Fermat (exponente φ(n))
3. Calcular φ(n) si corresponde
4. k = φ(n)·q + r (division entera)
5. a^k ≡ a^r (mod n)
6. Reducir a^r con productos parciales

---

## Referencias Cruzadas

### Ejercicios RELEVANTES
- `6_ejercicio_teoria_de_numeros.pdf` → Seccion III y IV (congruencias y ecuaciones)
- **Respuestas:** `6_respuesta_teoria_de_numeros.pdf` Ej.13-22

### Ejercicios NO relevantes
- `6_ejercicio_teoria_de_numeros.pdf` → Secciones I-II (divisibilidad basica, MCD, MCM)

### Teoria de referencia
- `6_teoria_teoria_de_numeros.pdf` → Seccion de Congruencias (desde slide ~21 en adelante)

---

## Prioridad de Practica
1. **ALTA**: Ejercicios de resolver ecuaciones a·x ≡ b (n) completas (con multiples soluciones)
2. **ALTA**: Ejercicios de calcular restos de potencias grandes con Euler-Fermat
3. **MEDIA**: Calcular φ(n) para numeros con muchos factores
4. **BAJA**: Pequeno Fermat aislado (es un caso particular de Euler-Fermat)
