# Tema 2 -- Relaciones de Equivalencia: Ejercicios Resueltos

> Guia de estudio para el final de Matematica Discreta (UNSAM)
> Ejercicios de la practica 7 (Relaciones) -- Seccion IV: Equivalencia

---

## Indice

- **TIER 1 -- ALTA PRIORIDAD**
  - Ejercicio 20 (a, b, c) -- Equivalencia en conjuntos finitos
  - Ejercicio 21 -- Reconstruir relacion desde restricciones
  - Ejercicio 22 -- Composicion y union de relaciones
  - Ejercicio 23 -- Hallar k en matriz para equivalencia
  - Ejercicio 24 -- Equivalencia en P(A) con interseccion
  - Ejercicio 25 -- Equivalencia con valor absoluto en R
- **TIER 2 -- MEDIA PRIORIDAD**
  - Ejercicio 26 -- Congruencia modulo 5 en Z
  - Ejercicio 27 -- Diferencia entera en R
  - Ejercicio 28 -- Equivalencia inducida por funcion
  - Ejercicio 29 -- Equivalencia con logaritmo en R+
  - Ejercicio 30 -- Producto de equivalencias
  - Ejercicio 31 -- Equivalencia en R^2
  - Ejercicio 32 -- Equivalencia en ZxZ
  - Ejercicio 33 -- Equivalencia que construye Q
  - Ejercicio 34 -- Verdadero o falso
  - Ejercicio 35 -- Equivalencia de parabolas
  - Ejercicio 36 -- Particiones de un conjunto

---

# TIER 1 -- ALTA PRIORIDAD

---

## Batch 01

---

### Ejercicio 20a -- Equivalencia por paridad de la suma

**Enunciado:** En A = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}, demostrar que la relacion aRb <=> a + b es par, es de equivalencia. Hallar las clases de equivalencia y el conjunto cociente.

**Identificacion del tipo:** Relacion de equivalencia definida por una condicion aritmetica (paridad). Se debe demostrar reflexiva, simetrica y transitiva, y luego hallar clases y cociente.

**Resolucion paso a paso:**

**Paso 1: Entender la condicion.** a + b es par significa que a y b tienen la misma paridad (ambos pares o ambos impares), ya que:
- par + par = par
- impar + impar = par
- par + impar = impar

**Paso 2: Demostrar reflexiva.**
Para todo a en A: a + a = 2a, que siempre es par.
Por lo tanto aRa para todo a en A. R es reflexiva.

**Paso 3: Demostrar simetrica.**
Sean a, b en A tales que aRb. Entonces a + b es par.
Como la suma es conmutativa: b + a = a + b, que tambien es par.
Por lo tanto bRa. R es simetrica.

**Paso 4: Demostrar transitiva.**
Sean a, b, c en A tales que aRb y bRc.
- aRb => a + b es par => a y b tienen la misma paridad
- bRc => b + c es par => b y c tienen la misma paridad
- Como a tiene la misma paridad que b, y b tiene la misma paridad que c, entonces a tiene la misma paridad que c.
- Por lo tanto a + c es par => aRc.
R es transitiva.

**Paso 5: Hallar las clases de equivalencia.**
La relacion agrupa elementos de la misma paridad:
- Cl(1) = {1, 3, 5, 7, 9} (todos los impares)
- Cl(2) = {2, 4, 6, 8, 10} (todos los pares)

Notar que Cl(1) = Cl(3) = Cl(5) = Cl(7) = Cl(9) y Cl(2) = Cl(4) = Cl(6) = Cl(8) = Cl(10).

**Paso 6: Conjunto cociente.**

A/R = { {1, 3, 5, 7, 9}, {2, 4, 6, 8, 10} }

**Respuesta:** R es de equivalencia. A/R = { {1, 3, 5, 7, 9}, {2, 4, 6, 8, 10} }

**Tips para el examen:**
- "a + b es par" equivale a decir "a y b tienen la misma paridad". Reconocer esta equivalencia simplifica la demostracion.
- Para transitividad con paridad, usar la propiedad transitiva de "tener la misma paridad".

**Errores comunes a evitar:**
- No confundir "a + b es par" con "a y b son pares". Dos impares sumados tambien dan par.
- En la transitividad, no olvidar usar el elemento intermedio b como puente.

---

### Ejercicio 20b -- Equivalencia por divisibilidad: 3|(a-b)

**Enunciado:** En A = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}, demostrar que aRb <=> 3|(a-b) es de equivalencia. Hallar clases y cociente.

**Identificacion del tipo:** Relacion de congruencia modulo 3 en un conjunto finito. Este es el modelo clasico de equivalencia por divisibilidad.

**Resolucion paso a paso:**

**Paso 1: Entender la condicion.**
3|(a-b) significa que a - b es multiplo de 3, es decir, a - b = 3k para algun k entero.
Esto es lo mismo que decir a es congruente con b modulo 3: a = b (mod 3).

**Paso 2: Demostrar reflexiva.**
Para todo a en A: a - a = 0 = 3 * 0.
Como 3|0, se tiene aRa. R es reflexiva.

**Paso 3: Demostrar simetrica.**
Sea aRb, entonces a - b = 3k para algun k entero.
Entonces b - a = -(a - b) = -3k = 3(-k).
Como -k es entero, 3|(b-a), por lo tanto bRa. R es simetrica.

**Paso 4: Demostrar transitiva.**
Sean aRb y bRc.
- a - b = 3k para algun k entero
- b - c = 3t para algun t entero
- Sumando: (a - b) + (b - c) = 3k + 3t => a - c = 3(k + t)
- Como k + t es entero, 3|(a-c) => aRc.
R es transitiva.

**Paso 5: Hallar clases de equivalencia.**
Clasificamos segun el resto de dividir por 3:
- Resto 0: Cl(3) = {3, 6, 9} (multiplos de 3 en A)
- Resto 1: Cl(1) = {1, 4, 7, 10} (dejan resto 1 al dividir por 3)
- Resto 2: Cl(2) = {2, 5, 8} (dejan resto 2 al dividir por 3)

Verificacion: {3, 6, 9} U {1, 4, 7, 10} U {2, 5, 8} = A. Correcto.

**Paso 6: Conjunto cociente.**

A/R = { {1, 4, 7, 10}, {2, 5, 8}, {3, 6, 9} }

**Respuesta:** R es de equivalencia. A/R = { {1, 4, 7, 10}, {2, 5, 8}, {3, 6, 9} }

**Tips para el examen:**
- La demostracion de transitividad en congruencias siempre usa la misma tecnica: sumar las dos igualdades para cancelar el termino del medio.
- Los restos posibles al dividir por n son {0, 1, ..., n-1}, asi que siempre habra n clases (o menos si el conjunto es finito y no tiene representantes de todos los restos).

**Errores comunes a evitar:**
- No confundir 3|(a-b) con 3|a y 3|b. La condicion es sobre la diferencia, no sobre cada elemento individual.
- En la simetria, recordar que si k es entero, -k tambien lo es.

---

### Ejercicio 20c -- Equivalencia por cantidad de letras del nombre

**Enunciado:** En A = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}, aRb <=> los nombres de "a" y "b" tienen la misma cantidad de letras (ejemplo: 3R6 ya que "tres" y "seis" tienen 4 letras). Demostrar equivalencia, hallar clases y cociente.

**Identificacion del tipo:** Equivalencia definida por una funcion (contar letras del nombre). Es un caso particular del nucleo de una funcion.

**Resolucion paso a paso:**

**Paso 1: Determinar la cantidad de letras de cada numero.**
| Numero | Nombre | Letras |
|--------|--------|--------|
| 1 | uno | 3 |
| 2 | dos | 3 |
| 3 | tres | 4 |
| 4 | cuatro | 6 |
| 5 | cinco | 5 |
| 6 | seis | 4 |
| 7 | siete | 5 |
| 8 | ocho | 4 |
| 9 | nueve | 5 |
| 10 | diez | 4 |

**Paso 2: Demostrar reflexiva.**
Para todo a en A, el nombre de a tiene la misma cantidad de letras que si mismo.
Por lo tanto aRa. R es reflexiva.

**Paso 3: Demostrar simetrica.**
Si aRb, los nombres de a y b tienen la misma cantidad de letras.
Entonces los nombres de b y a tambien tienen la misma cantidad de letras.
Por lo tanto bRa. R es simetrica.

**Paso 4: Demostrar transitiva.**
Si aRb y bRc:
- El nombre de a y el de b tienen la misma cantidad de letras (digamos n).
- El nombre de b y el de c tienen la misma cantidad de letras (tambien n, pues es el mismo b).
- Entonces el nombre de a y el de c tienen ambos n letras => aRc.
R es transitiva.

**Paso 5: Hallar clases de equivalencia.**
Agrupamos por cantidad de letras:
- 3 letras: Cl(1) = {1, 2}
- 4 letras: Cl(3) = {3, 6, 8, 10}
- 5 letras: Cl(5) = {5, 7, 9}
- 6 letras: Cl(4) = {4}

**Paso 6: Conjunto cociente.**

A/R = { {1, 2}, {3, 6, 8, 10}, {4}, {5, 7, 9} }

**Respuesta:** R es de equivalencia. A/R = { {1, 2}, {3, 6, 8, 10}, {4}, {5, 7, 9} }

**Tips para el examen:**
- Esta relacion es un ejemplo del nucleo de la funcion f: A -> N donde f(a) = cantidad de letras del nombre de a. Toda relacion de la forma "f(a) = f(b)" es automaticamente de equivalencia.
- Puede haber clases con un solo elemento (como {4}), eso es perfectamente valido.

**Errores comunes a evitar:**
- Contar mal las letras. Verificar cada nombre cuidadosamente.
- No incluir el 10 ("diez" = 4 letras). A veces se olvida que 10 esta en el conjunto.

---

### Ejercicio 21 -- Reconstruir relacion de equivalencia a partir de restricciones

**Enunciado:** A = {1, 2, 3, 4, 5, 6}. Hacer el digrafo y escribir la matriz de una relacion R sabiendo que: es de equivalencia, hay 3 clases, 5 pertenece a cl(6), y en total hay 14 pares ordenados en R.

**Identificacion del tipo:** Problema de reconstruccion. Hay que determinar las clases de equivalencia a partir de las restricciones dadas y construir la relacion.

**Resolucion paso a paso:**

**Paso 1: Analizar las restricciones.**
- A tiene 6 elementos.
- Hay 3 clases de equivalencia.
- 5 pertenece a cl(6), es decir, 5 y 6 estan en la misma clase.
- Hay 14 pares ordenados en total.

**Paso 2: Contar pares por clase.**
Si una clase tiene n elementos, contribuye n^2 pares a la relacion (cada elemento se relaciona con todos los demas de su clase y consigo mismo).

Sea n1, n2, n3 los tamanos de las 3 clases. Entonces:
- n1 + n2 + n3 = 6 (cubren todo A)
- n1^2 + n2^2 + n3^2 = 14 (total de pares)

**Paso 3: Resolver el sistema.**
Probamos combinaciones con n1 + n2 + n3 = 6:
- (3, 2, 1): 9 + 4 + 1 = 14. Funciona!
- (2, 2, 2): 4 + 4 + 4 = 12. No.
- (4, 1, 1): 16 + 1 + 1 = 18. No.

La unica solucion es clases de tamanos {3, 2, 1}.

**Paso 4: Asignar elementos a las clases.**
Sabemos que 5 pertenece a cl(6), asi que 5 y 6 estan juntos. Necesitamos una clase de 3, una de 2 y una de 1.

Una posibilidad (hay varias validas):
- Clase de 3: {1, 2, 3}
- Clase de 2: {5, 6}
- Clase de 1: {4}

Otra posibilidad valida: {1, 3, 4}, {5, 6}, {2}... Hay muchas opciones siempre que 5 y 6 esten en la misma clase.

Elegimos una solucion concreta:
- Cl(1) = Cl(2) = Cl(3) = {1, 2, 3}
- Cl(5) = Cl(6) = {5, 6}
- Cl(4) = {4}

**Paso 5: Escribir la relacion por extension.**
R = {(1,1), (1,2), (1,3), (2,1), (2,2), (2,3), (3,1), (3,2), (3,3), (4,4), (5,5), (5,6), (6,5), (6,6)}

Verificacion: son 9 + 1 + 4 = 14 pares. Correcto.

**Paso 6: Matriz de la relacion.**

```
M(R) =
  1 2 3 4 5 6
1[1 1 1 0 0 0]
2[1 1 1 0 0 0]
3[1 1 1 0 0 0]
4[0 0 0 1 0 0]
5[0 0 0 0 1 1]
6[0 0 0 0 1 1]
```

**Paso 7: Digrafo.**
El digrafo tiene:
- Bucles en todos los vertices (reflexiva).
- Flechas dobles entre 1-2, 1-3, 2-3 (clase {1,2,3}).
- Flechas dobles entre 5-6 (clase {5,6}).
- Solo bucle en 4 (clase {4}).

**Respuesta:** Una solucion valida es: clases {1,2,3}, {4}, {5,6} con 14 pares. La matriz es la indicada arriba (bloques diagonales de unos).

**Tips para el examen:**
- La formula clave es: si las clases tienen tamanos n1, n2, ..., nk, el numero total de pares es n1^2 + n2^2 + ... + nk^2.
- En estos problemas, resolver n1 + n2 + ... + nk = |A| y n1^2 + n2^2 + ... + nk^2 = |R| simultaneamente.

**Errores comunes a evitar:**
- Olvidar que la restriccion "5 pertenece a cl(6)" implica que 5 y 6 DEBEN estar en la misma clase.
- Confundir n^2 con n*(n-1). El numero de pares por clase es n^2 (incluye los pares (a,a)).
- La solucion no es unica (hay varias formas de asignar los elementos restantes), pero todas las validas deben cumplir las restricciones.

---

### Ejercicio 22 -- Composicion, union y equivalencia

**Enunciado:** En A = {1, 2, 3, 4, 5}, se define R tal que xRy <=> x + y = 6.
a) Hallar la matriz de R^2 (R compuesta con R) y luego la matriz de S = R U R^2.
b) Analizar si S es de equivalencia. Si lo es, hallar clases y cociente.

**Identificacion del tipo:** Composicion de relaciones, union, y verificacion de equivalencia mediante matrices booleanas.

**Resolucion paso a paso:**

**Paso 1: Determinar R por extension.**
Buscamos pares (x, y) con x, y en {1,2,3,4,5} y x + y = 6:
- (1, 5): 1 + 5 = 6
- (2, 4): 2 + 4 = 6
- (3, 3): 3 + 3 = 6
- (4, 2): 4 + 2 = 6
- (5, 1): 5 + 1 = 6

R = {(1,5), (2,4), (3,3), (4,2), (5,1)}

**Paso 2: Escribir M(R).**

```
M(R) =
  1 2 3 4 5
1[0 0 0 0 1]
2[0 0 0 1 0]
3[0 0 1 0 0]
4[0 1 0 0 0]
5[1 0 0 0 0]
```

**Paso 3: Calcular M(R^2) = M(R) * M(R) (producto booleano).**

Para calcular R^2, necesitamos hallar los pares (x, z) tales que existe y con xRy y yRz, es decir, x + y = 6 y y + z = 6, lo que implica y = 6 - x y z = 6 - y = 6 - (6 - x) = x.

Por lo tanto: R^2 = {(x, x) / x pertenece a A y 6 - x pertenece a A}

Verificamos:
- x = 1: y = 5, y esta en A. (1,1) pertenece a R^2
- x = 2: y = 4, y esta en A. (2,2) pertenece a R^2
- x = 3: y = 3, y esta en A. (3,3) pertenece a R^2
- x = 4: y = 2, y esta en A. (4,4) pertenece a R^2
- x = 5: y = 1, y esta en A. (5,5) pertenece a R^2

R^2 = {(1,1), (2,2), (3,3), (4,4), (5,5)} = identidad

```
M(R^2) =
  1 2 3 4 5
1[1 0 0 0 0]
2[0 1 0 0 0]
3[0 0 1 0 0]
4[0 0 0 1 0]
5[0 0 0 0 1]
```

**Paso 4: Calcular M(S) = M(R) v M(R^2) (OR booleano componente a componente).**

```
M(S) = M(R) v M(R^2) =
  1 2 3 4 5
1[1 0 0 0 1]
2[0 1 0 1 0]
3[0 0 1 0 0]
4[0 1 0 1 0]
5[1 0 0 0 1]
```

S = {(1,1), (1,5), (2,2), (2,4), (3,3), (4,2), (4,4), (5,1), (5,5)}

**Paso 5: Analizar si S es de equivalencia.**

- **Reflexiva:** La diagonal de M(S) tiene todos unos. Si, es reflexiva.
- **Simetrica:** Verificamos que M(S) = M(S)^t. La matriz es simetrica respecto a la diagonal:
  - (1,5) y (5,1) estan ambos. (2,4) y (4,2) estan ambos. Cumple.
- **Transitiva:** Verificamos que M(S) * M(S) <= M(S) (es decir, M(S^2) no tiene unos donde M(S) tenga ceros).
  Calculemos S^2: si xSy y ySz entonces xSz.
  - (1,1) y (1,5) => (1,5). OK, esta en S.
  - (1,5) y (5,1) => (1,1). OK.
  - (1,5) y (5,5) => (1,5). OK.
  - (2,2) y (2,4) => (2,4). OK.
  - (2,4) y (4,2) => (2,2). OK.
  - (2,4) y (4,4) => (2,4). OK.
  - Todos los caminos de longitud 2 llevan a pares que ya estan en S.

S es de equivalencia.

**Paso 6: Clases de equivalencia.**
Mirando M(S):
- Cl(1) = {1, 5} (fila 1 tiene unos en columnas 1 y 5)
- Cl(2) = {2, 4} (fila 2 tiene unos en columnas 2 y 4)
- Cl(3) = {3} (fila 3 solo tiene un 1 en columna 3)

**Paso 7: Conjunto cociente.**

A/S = { {1, 5}, {2, 4}, {3} }

**Respuesta:**
a) M(R^2) = Identidad (5x5). M(S) es la matriz indicada arriba.
b) S es de equivalencia. A/S = { {1, 5}, {2, 4}, {3} }

**Tips para el examen:**
- Cuando R es simetrica (como en este caso, pues x + y = 6 <=> y + x = 6), R^2 suele ser la identidad restringida o algo sencillo.
- Para verificar transitividad matricialmente: calcular M(S) * M(S) y verificar que donde este de 1, M(S) tambien tiene 1 (es decir, M(S)^2 <= M(S)).
- Las clases se leen directamente de las filas de la matriz: los unos en la fila i indican los elementos de Cl(i).

**Errores comunes a evitar:**
- No confundir el producto booleano (*) con el OR booleano (v). Para R^2 se usa producto; para R U R^2 se usa OR.
- Al componer R consigo misma, no olvidar que R^2 NO es R x R, sino la composicion RoR.

---

## Batch 02

---

### Ejercicio 23 -- Hallar k en una matriz para que sea de equivalencia

**Enunciado:** Dada la siguiente matriz de una relacion en A = {1,2,3,4,5,6,7,8}:

```
M(R) =
  1 2 3 4 5 6 7 8
1[1 0 0 1 1 0 0 0]
2[0 1 0 0 0 0 1 0]
3[0 0 1 0 0 0 0 1]
4[1 0 0 1 1 k 0 0]
5[1 0 0 1 1 k 0 0]
6[0 0 0 0 k 1 0 0]
7[0 1 0 0 0 0 1 0]
8[0 0 1 0 0 0 0 1]
```

a) Hallar k (0 o 1) para que R sea de equivalencia. Justificar.
b) Escribir la particion.

**Identificacion del tipo:** Problema de analisis matricial. Se debe usar las propiedades matriciales de reflexividad, simetria y transitividad para determinar k.

**Resolucion paso a paso:**

**Paso 1: Verificar reflexividad.**
La diagonal ya tiene todos unos, independientemente de k. R es reflexiva.

**Paso 2: Verificar simetria.**
Para que sea simetrica, M(R) debe ser igual a M(R)^t, es decir, m(i,j) = m(j,i) para todo i, j.

Observemos las posiciones con k:
- Posicion (4,6) = k y posicion (6,4) = 0.
- Posicion (5,6) = k y posicion (6,5) = k.

Para simetria necesitamos m(4,6) = m(6,4). Es decir, k = 0.

Verificacion con k = 0:
- (4,6) = 0 y (6,4) = 0. OK.
- (5,6) = 0 y (6,5) = 0. OK.
La matriz seria simetrica.

Con k = 1:
- (4,6) = 1 pero (6,4) = 0. NO es simetrica.

**Paso 3: Verificar que con k = 0 se cumple transitividad.**
Con k = 0 la matriz queda:

```
M(R) =
  1 2 3 4 5 6 7 8
1[1 0 0 1 1 0 0 0]
2[0 1 0 0 0 0 1 0]
3[0 0 1 0 0 0 0 1]
4[1 0 0 1 1 0 0 0]
5[1 0 0 1 1 0 0 0]
6[0 0 0 0 0 1 0 0]
7[0 1 0 0 0 0 1 0]
8[0 0 1 0 0 0 0 1]
```

Se observan bloques diagonales perfectos:
- Bloque {1,4,5}: filas 1, 4, 5 son identicas = [1 0 0 1 1 0 0 0]
- Bloque {2,7}: filas 2, 7 son identicas = [0 1 0 0 0 0 1 0]
- Bloque {3,8}: filas 3, 8 son identicas = [0 0 1 0 0 0 0 1]
- Bloque {6}: fila 6 = [0 0 0 0 0 1 0 0]

La matriz tiene la estructura clasica de bloques de una relacion de equivalencia (cada bloque es una submatriz de unos). Por lo tanto es transitiva.

**Paso 4: Justificacion alternativa de por que k = 1 no funciona.**
Si k = 1, tendriamos:
- 4R5 (pues m(4,5) = 1) y 5R6 (pues m(5,6) = k = 1)
- Por transitividad deberia cumplirse 4R6, es decir m(4,6) = 1.
- Pero m(4,6) = k, y si k = 1, m(4,6) = 1. Esto parece OK.
- PERO: 4R6 con k=1, y 6R4 deberia cumplirse (simetria), pero m(6,4) = 0. Contradiccion.

Alternativamente, mirando la transitividad directamente:
- Si k = 1: 5R6 (m(5,6)=1) y 6 solo se relaciona consigo mismo y con 5 (fila 6 con k=1 seria [0 0 0 0 1 1 0 0]), pero 4R5 y 5R6 implicaria 4R6, y necesitariamos m(4,6) = 1. Con k=1 en la fila 4: m(4,6) = k = 1, eso es consistente.
- Sin embargo, m(6,4) = 0 y m(4,6) = 1 con k=1: no es simetrica.

La razon principal es la **falta de simetria** con k = 1.

**Respuesta:**
a) k = 0. Con k = 1 la relacion no seria simetrica (m(4,6) = 1 pero m(6,4) = 0).
b) La particion es: { {1, 4, 5}, {2, 7}, {3, 8}, {6} }

**Tips para el examen:**
- Para hallar k, primero verificar simetria (es la condicion mas facil de chequear en la matriz: m(i,j) = m(j,i)).
- En una matriz de equivalencia, las filas correspondientes a elementos de la misma clase son identicas.
- Los bloques diagonales de unos en la matriz (despues de reordenar filas/columnas) corresponden a las clases.

**Errores comunes a evitar:**
- No verificar TODAS las condiciones. Aunque k = 0 cumpla simetria, hay que confirmar que tambien es transitiva.
- No confundir la posicion (i,j) con (j,i) al verificar simetria.

---

### Ejercicio 24 -- Equivalencia en P(A) con interseccion

**Enunciado:** A = {1, 2, 3, 4}, en P(A) se define XRY <=> X n B = Y n B con B = {2, 4}.
a) Probar que R es de equivalencia.
b) Hallar las clases de equivalencia.
c) Hallar el conjunto cociente.

**Identificacion del tipo:** Equivalencia en el conjunto potencia P(A) definida por una funcion (interseccion con un conjunto fijo). Es un nucleo de funcion: f(X) = X n B.

**Resolucion paso a paso:**

**Paso 1: Entender el contexto.**
P(A) tiene 2^4 = 16 subconjuntos. B = {2, 4}.
Dos subconjuntos X, Y de A estan relacionados si al intersecarlos con B = {2,4} dan el mismo resultado.
Es decir, lo que importa de cada conjunto es cuales de los elementos 2 y 4 contiene.

**Paso 2: Demostrar reflexiva.**
Para todo X en P(A): X n B = X n B.
Por lo tanto XRX. R es reflexiva.

**Paso 3: Demostrar simetrica.**
Si XRY, entonces X n B = Y n B.
La igualdad es simetrica: Y n B = X n B.
Por lo tanto YRX. R es simetrica.

**Paso 4: Demostrar transitiva.**
Si XRY y YRZ:
- X n B = Y n B
- Y n B = Z n B
- Por transitividad de la igualdad: X n B = Z n B
- Por lo tanto XRZ. R es transitiva.

**Paso 5: Hallar las clases de equivalencia.**
Los posibles valores de X n B (con B = {2,4}) son todos los subconjuntos de B:
- X n B = vacio: X no contiene ni 2 ni 4.
- X n B = {2}: X contiene 2 pero no 4.
- X n B = {4}: X contiene 4 pero no 2.
- X n B = {2,4}: X contiene tanto 2 como 4.

Clase 1: X n B = vacio (X no contiene ni 2 ni 4)
- Cl(vacio) = {vacio, {1}, {3}, {1,3}}

Clase 2: X n B = {2} (X contiene 2, no contiene 4)
- Cl({2}) = {{2}, {1,2}, {2,3}, {1,2,3}}

Clase 3: X n B = {4} (X contiene 4, no contiene 2)
- Cl({4}) = {{4}, {1,4}, {3,4}, {1,3,4}}

Clase 4: X n B = {2,4} (X contiene 2 y 4)
- Cl({2,4}) = {{2,4}, {1,2,4}, {2,3,4}, {1,2,3,4}}

Verificacion: 4 + 4 + 4 + 4 = 16 = |P(A)|. Correcto.

**Paso 6: Conjunto cociente.**

P(A)/R = { Cl(vacio), Cl({2}), Cl({4}), Cl({2,4}) }

Donde:
- Cl(vacio) = {vacio, {1}, {3}, {1,3}}
- Cl({2}) = {{2}, {1,2}, {2,3}, {1,2,3}}
- Cl({4}) = {{4}, {1,4}, {3,4}, {1,3,4}}
- Cl({2,4}) = {{2,4}, {1,2,4}, {2,3,4}, {1,2,3,4}}

**Respuesta:** R es de equivalencia. El cociente tiene 4 clases, una por cada subconjunto de B = {2,4}. P(A)/R = { Cl(vacio), Cl({2}), Cl({4}), Cl({2,4}) }

**Tips para el examen:**
- Cuando la relacion es de la forma f(X) = f(Y), la demostracion de equivalencia es casi automatica (reflexiva, simetrica y transitiva se siguen de las propiedades de la igualdad).
- Las clases se determinan por los posibles valores de f. Aqui f(X) = X n B, y los posibles valores son los subconjuntos de B, asi que hay 2^|B| = 4 clases.
- Los elementos "fuera de B" (aqui 1 y 3) pueden estar o no en X sin afectar la clase.

**Errores comunes a evitar:**
- Olvidar algun subconjunto de P(A) al listar las clases.
- No incluir el conjunto vacio en P(A).
- Confundir P(A) (16 elementos) con A (4 elementos).

---

### Ejercicio 25 -- Equivalencia con valor absoluto: |x-1| = |y-1|

**Enunciado:** En R (reales), se define xSy <=> |x - 1| = |y - 1|. Demostrar que es de equivalencia, graficar la relacion, hallar clases y cociente.

**Identificacion del tipo:** Equivalencia inducida por una funcion f(x) = |x - 1|. Incluye componente grafica.

**Resolucion paso a paso:**

**Paso 1: Demostrar reflexiva.**
Para todo x en R: |x - 1| = |x - 1|.
Por lo tanto xSx. S es reflexiva.

**Paso 2: Demostrar simetrica.**
Si xSy, entonces |x - 1| = |y - 1|.
La igualdad es simetrica: |y - 1| = |x - 1|.
Por lo tanto ySx. S es simetrica.

**Paso 3: Demostrar transitiva.**
Si xSy y ySz:
- |x - 1| = |y - 1|
- |y - 1| = |z - 1|
- Por transitividad de la igualdad: |x - 1| = |z - 1|
- Por lo tanto xSz. S es transitiva.

**Paso 4: Graficar la relacion.**
xSy <=> |x - 1| = |y - 1|

Resolvemos el valor absoluto:
|x - 1| = |y - 1| tiene dos casos:
- Caso 1: x - 1 = y - 1 => x = y (la recta identidad)
- Caso 2: x - 1 = -(y - 1) => x - 1 = -y + 1 => y = 2 - x (una recta de pendiente -1)

La grafica de S es la union de dos rectas:
- y = x (la diagonal)
- y = 2 - x (recta con pendiente -1 que pasa por (0,2) y (2,0))

Ambas rectas se cortan en el punto (1, 1).

**Paso 5: Hallar las clases de equivalencia.**
cl(x) = {y en R / |y - 1| = |x - 1|}

Para un x dado, los y que cumplen son:
- y - 1 = x - 1 => y = x
- y - 1 = -(x - 1) => y = 2 - x

Por lo tanto: cl(x) = {x, 2 - x}

Casos especiales:
- Si x = 1: cl(1) = {1, 2 - 1} = {1}. Clase con un solo elemento.
- Si x distinto de 1: cl(x) = {x, 2 - x} con x distinto de 2 - x.

Por ejemplo: cl(3) = {3, -1}, cl(0) = {0, 2}, cl(5) = {5, -3}.

**Paso 6: Conjunto cociente.**
Si elegimos como representante de cada clase el mayor elemento, los representantes son los x >= 1 (pues entre x y 2-x, el mayor es x cuando x >= 1).

Conjunto de indices: [1, +infinito)

R/S = { cl(x) / x pertenece a [1, +infinito) }

**Respuesta:** S es de equivalencia. Las clases son cl(x) = {x, 2-x} (excepto cl(1) = {1}). El cociente es R/S = { cl(x) / x en [1, +infinito) }. La grafica es la union de las rectas y = x e y = 2 - x.

**Tips para el examen:**
- Toda relacion de la forma f(x) = f(y) es automaticamente de equivalencia. La demostracion de las 3 propiedades es identica en todos estos casos.
- Para graficar, resolver la ecuacion |f(x)| = |f(y)| eliminando valores absolutos: se obtienen los casos f(x) = f(y) y f(x) = -f(y).
- El conjunto de indices se elige tomando un representante por clase, generalmente el mayor.

**Errores comunes a evitar:**
- Olvidar el caso especial cuando x = 2 - x (es decir x = 1), donde la clase tiene un solo elemento.
- Al graficar, no olvidar que son DOS rectas, no solo y = x.

---

# TIER 2 -- MEDIA PRIORIDAD

---

## Batch 12

---

### Ejercicio 26 -- Congruencia modulo 5 en Z

**Enunciado:** En Z, se define xRy <=> 5|(x - y). Demostrar equivalencia, hallar clases y cociente.

**Identificacion del tipo:** Relacion de congruencia modulo 5. Modelo clasico que genera Z_5.

**Resolucion paso a paso:**

**Paso 1: Reescribir la condicion.**
5|(x - y) significa x - y = 5k para algun k en Z.
Equivalentemente: x es congruente con y modulo 5.

**Paso 2: Demostrar reflexiva.**
Para todo x en Z: x - x = 0 = 5 * 0.
Como 0 es entero, 5|0, por lo tanto xRx. R es reflexiva.

**Paso 3: Demostrar simetrica.**
Si xRy, entonces x - y = 5k con k en Z.
Entonces y - x = -(x - y) = -5k = 5(-k).
Como -k en Z, 5|(y - x), por lo tanto yRx. R es simetrica.

**Paso 4: Demostrar transitiva.**
Si xRy y yRz:
- x - y = 5k con k en Z
- y - z = 5t con t en Z
- Sumando: (x - y) + (y - z) = 5k + 5t
- x - z = 5(k + t)
- Como k + t en Z, 5|(x - z), por lo tanto xRz. R es transitiva.

**Paso 5: Hallar las clases.**
Los restos posibles al dividir por 5 son {0, 1, 2, 3, 4}:

- Cl(0) = {x = 5k / k en Z} = {..., -10, -5, 0, 5, 10, ...} = 0 con barra (clase 0)
- Cl(1) = {x = 5k + 1 / k en Z} = {..., -9, -4, 1, 6, 11, ...} = 1 con barra
- Cl(2) = {x = 5k + 2 / k en Z} = {..., -8, -3, 2, 7, 12, ...} = 2 con barra
- Cl(3) = {x = 5k + 3 / k en Z} = {..., -7, -2, 3, 8, 13, ...} = 3 con barra
- Cl(4) = {x = 5k + 4 / k en Z} = {..., -6, -1, 4, 9, 14, ...} = 4 con barra

**Paso 6: Conjunto cociente.**

Z/R = {Cl(0), Cl(1), Cl(2), Cl(3), Cl(4)} = Z_5

Se le llama Z_5 (los enteros modulo 5).

**Respuesta:** R es de equivalencia. Z/R = Z_5 = {Cl(0), Cl(1), Cl(2), Cl(3), Cl(4)}, con 5 clases determinadas por el resto de la division por 5.

**Tips para el examen:**
- La congruencia modulo n siempre da exactamente n clases.
- La demostracion de transitividad siempre usa: sumar las dos ecuaciones para eliminar el termino intermedio.
- Notar que Cl(5) = Cl(0), Cl(6) = Cl(1), etc. Cualquier entero tiene la misma clase que su resto modulo 5.

**Errores comunes a evitar:**
- No incluir los numeros negativos en las clases. Cl(0) incluye ..., -10, -5, 0, 5, 10, ...
- Confundir "5 divide a x" con "5 divide a (x - y)".

---

### Ejercicio 27 -- Diferencia entera en R

**Enunciado:** En R, se define xRy <=> x - y pertenece a Z. Demostrar equivalencia, hallar clases y cociente.

**Identificacion del tipo:** Equivalencia basada en la mantisa (parte decimal). Si x - y es entero, x e y tienen la misma parte decimal.

**Resolucion paso a paso:**

**Paso 1: Entender la condicion.**
x - y en Z significa que x e y difieren en un entero, es decir, tienen la misma parte decimal (mantisa).
Recordar: la mantisa de un numero real es la diferencia entre el numero y su parte entera. Por ejemplo: mant(3.45) = 0.45, mant(-12.7) = 0.3.

**Paso 2: Demostrar reflexiva.**
Para todo x en R: x - x = 0, y 0 pertenece a Z.
Por lo tanto xRx. R es reflexiva.

**Paso 3: Demostrar simetrica.**
Si xRy, entonces x - y = k con k en Z.
Entonces y - x = -k, y -k pertenece a Z.
Por lo tanto yRx. R es simetrica.

**Paso 4: Demostrar transitiva.**
Si xRy y yRz:
- x - y = k con k en Z
- y - z = t con t en Z
- Sumando: x - z = k + t, y k + t pertenece a Z.
- Por lo tanto xRz. R es transitiva.

**Nota:** Este ejercicio es un caso particular del ejercicio 28 con f(x) = mant(x), o equivalentemente, es la congruencia modulo 1 en R.

**Paso 5: Hallar las clases.**
cl(x) = {y en R / y - x en Z} = {x + k / k en Z}

Por ejemplo:
- cl(0) = Z = {..., -2, -1, 0, 1, 2, ...}
- cl(0.5) = {..., -1.5, -0.5, 0.5, 1.5, 2.5, ...}
- cl(pi) = {..., pi - 2, pi - 1, pi, pi + 1, pi + 2, ...}

Todos los reales con la misma parte decimal caen en la misma clase.

**Paso 6: Conjunto cociente.**
Un representante natural de cada clase es su unico elemento en [0, 1).
(Todo numero real tiene exactamente una "copia" en [0, 1) obtenida al restarle su parte entera.)

R/R = {cl(x) / x pertenece a [0, 1)}

**Respuesta:** R es de equivalencia. cl(x) = {x + k / k en Z} (misma mantisa). R/R = {cl(x) / x en [0, 1)}.

**Tips para el examen:**
- Este es un caso particular de la equivalencia f(x) = f(y) con f = mantisa.
- El intervalo [0, 1) funciona como conjunto de indices porque cada clase tiene exactamente un representante ahi.

**Errores comunes a evitar:**
- No confundir [0, 1) con [0, 1]. Si usaramos [0, 1], cl(0) y cl(1) serian la misma clase con dos representantes.
- Recordar que la mantisa de numeros negativos puede ser contraintuitiva: mant(-0.3) = 0.7 (no 0.3).

---

### Ejercicio 28 -- Equivalencia inducida por una funcion

**Enunciado:** En R, se define xRy <=> f(x) = f(y) con f: R -> R.
a) Demostrar que R es de equivalencia para cualquier f.
b) Con f(x) = |x^2 - 2|, hallar clases y cociente.
c) Demostrar que el conjunto de indices es un subconjunto donde f es biyectiva.

**Identificacion del tipo:** Nucleo de una funcion. Concepto fundamental que unifica muchos ejercicios de equivalencia.

**Resolucion paso a paso:**

**Parte a) Demostracion general:**

**Reflexiva:** Para todo x en R: f(x) = f(x). Por lo tanto xRx.

**Simetrica:** Si xRy, entonces f(x) = f(y). La igualdad es simetrica: f(y) = f(x). Por lo tanto yRx.

**Transitiva:** Si xRy y yRz, entonces f(x) = f(y) y f(y) = f(z). Por transitividad de la igualdad: f(x) = f(z). Por lo tanto xRz.

R es de equivalencia para cualquier funcion f.

**Parte b) Con f(x) = |x^2 - 2|:**

**Paso 1: Graficar f.**
f(x) = |x^2 - 2| es la parabola y = x^2 - 2 "reflejada" en la parte que queda debajo del eje x.
- f(x) = x^2 - 2 cuando x^2 >= 2 (es decir, |x| >= sqrt(2))
- f(x) = 2 - x^2 cuando x^2 < 2 (es decir, |x| < sqrt(2))

**Paso 2: Graficar la relacion.**
xRy <=> |x^2 - 2| = |y^2 - 2|

Resolviendo: x^2 - 2 = y^2 - 2 o x^2 - 2 = -(y^2 - 2)
- Caso 1: x^2 = y^2 => y = x o y = -x (dos rectas)
- Caso 2: x^2 - 2 = -y^2 + 2 => x^2 + y^2 = 4 (circunferencia de radio 2 centrada en el origen)

La grafica de R es la union de las rectas y = x, y = -x, y la circunferencia x^2 + y^2 = 4.

**Paso 3: Hallar las clases.**
Para un x dado, cl(x) = {y / |y^2 - 2| = |x^2 - 2|}

Los y que cumplen son los que satisfacen y^2 = x^2 o x^2 + y^2 = 4:
- y = x (siempre)
- y = -x (siempre)
- y^2 = 4 - x^2 => y = +/- sqrt(4 - x^2) (solo si 4 - x^2 >= 0, es decir |x| <= 2)

Entonces:
- Si |x| > 2: cl(x) = {x, -x} (solo las rectas, la circunferencia no contribuye)
- Si |x| = 2: cl(2) = {2, -2, 0, 0} = {2, 0, -2} (la circunferencia da y = 0)
- Si sqrt(2) < |x| < 2: cl(x) = {x, -x, sqrt(4-x^2), -sqrt(4-x^2)} (4 elementos)
- Si |x| = sqrt(2): cl(sqrt(2)) = {sqrt(2), -sqrt(2)} (la circunferencia da y = +/- sqrt(2), que coincide con las rectas)
- Si 0 < |x| < sqrt(2): cl(x) = {x, -x, sqrt(4-x^2), -sqrt(4-x^2)} (4 elementos)
- Si x = 0: cl(0) = {0, 2, -2} (de las rectas: y = 0; de la circunferencia: y = +/- 2)

Resumiendo con representantes x >= 0:
- Para x en (2, +infinito): cl(x) = {x, -x}
- cl(2) = {2, 0, -2}
- Para x en (sqrt(2), 2): cl(x) = {x, -x, sqrt(4-x^2), -sqrt(4-x^2)}
- cl(sqrt(2)) = {sqrt(2), -sqrt(2)}

**Paso 4: Conjunto cociente.**
Eligiendo como representantes a los mayores, tomamos x en [sqrt(2), +infinito).

R/R = {cl(x) / x pertenece a [sqrt(2), +infinito)}

**Parte c) El conjunto de indices es un subconjunto donde f es biyectiva.**
El conjunto de indices I (por ejemplo [sqrt(2), +infinito)) contiene exactamente un representante de cada clase. Esto significa:
- f restringida a I es inyectiva: si f(x) = f(y) con x, y en I, entonces x e y estan en la misma clase, pero I tiene un solo elemento por clase, asi que x = y.
- f restringida a I es sobreyectiva sobre Im(f): cada valor de la imagen de f proviene de al menos una clase, y cada clase tiene su representante en I.

Por lo tanto f|_I: I -> Im(f) es biyectiva.

**Respuesta:**
a) R es de equivalencia para cualquier f (se sigue de las propiedades de la igualdad).
b) Con f(x) = |x^2-2|: la grafica es y=x, y=-x, y x^2+y^2=4. R/R = {cl(x) / x en [sqrt(2), +infinito)}.
c) El conjunto de indices I tiene un representante por clase, asi que f|_I es biyectiva sobre Im(f).

**Tips para el examen:**
- TODA relacion de la forma "f(x) = f(y)" es de equivalencia. Si reconoces este patron, la demostracion es inmediata.
- Para hallar clases cuando f involucra valor absoluto, resolver |f(x)| = |f(y)| separando en casos.
- La parte c) es un resultado general: el conjunto de representantes es siempre un subconjunto donde f es biyectiva.

**Errores comunes a evitar:**
- Olvidar soluciones al resolver ecuaciones con valor absoluto. Siempre hay dos casos.
- No verificar que las soluciones de y^2 = 4 - x^2 sean reales (necesitan 4 - x^2 >= 0).
- En el cociente, no confundir el conjunto de indices con el cociente. El cociente es un conjunto de clases, no de numeros.

---

### Ejercicio 29 -- Equivalencia con logaritmo en R+

**Enunciado:** En R+ (reales positivos), se define xRy <=> |log(x)| = |log(y)|.
a) Demostrar que R es de equivalencia.
b) Indicar cual de los siguientes puede considerarse conjunto cociente:
   A = {cl(x) / x en [1, 2)}, B = {cl(x) / x en (0, 1]}, C = {cl(x) / x en (1, +infinito)}, D = {cl(x) / x en [10, +infinito)}

**Identificacion del tipo:** Equivalencia inducida por la funcion g(x) = |log(x)|. Caso particular del Ej. 28.

**Resolucion paso a paso:**

**Parte a) Demostracion:**
Es un caso particular de f(x) = f(y) con f(x) = |log(x)|.

**Reflexiva:** |log(x)| = |log(x)| para todo x en R+. xRx.

**Simetrica:** Si |log(x)| = |log(y)|, entonces |log(y)| = |log(x)|. yRx.

**Transitiva:** Si |log(x)| = |log(y)| y |log(y)| = |log(z)|, entonces |log(x)| = |log(z)|. xRz.

R es de equivalencia.

**Parte b) Determinar el conjunto cociente:**

**Paso 1: Hallar las clases.**
|log(x)| = |log(y)| <=> log(x) = log(y) o log(x) = -log(y) <=> x = y o log(x) = log(1/y) <=> x = y o x = 1/y.

Por lo tanto: cl(x) = {x, 1/x}

Casos especiales:
- cl(1) = {1, 1} = {1} (unica clase con un solo elemento, pues 1/1 = 1)
- cl(2) = {2, 1/2}
- cl(10) = {10, 1/10}

**Paso 2: Analizar cada opcion.**

Para que un conjunto I sea un conjunto de indices valido, debe contener exactamente un representante de cada clase.

**Opcion A: I = [1, 2).** No sirve. Para x > 2 (por ejemplo x = 3), cl(3) = {3, 1/3}. Ni 3 ni 1/3 estan en [1, 2). Entonces la clase cl(3) no tiene representante en A. No cubre todas las clases.

**Opcion B: I = (0, 1].** Veamos si cada clase tiene exactamente un representante en (0, 1]:
- Para x > 1: cl(x) = {x, 1/x}. 1/x esta en (0, 1) que esta en (0, 1]. El representante es 1/x. Pero x no esta en (0, 1] (pues x > 1). Solo un representante.
- Para x = 1: cl(1) = {1}. 1 esta en (0, 1]. Un representante.
- Para 0 < x < 1: cl(x) = {x, 1/x}. x esta en (0, 1), que esta en (0, 1]. 1/x > 1, no esta en (0, 1]. Solo un representante.

Cada clase tiene exactamente un representante. **B es valido.**

**Opcion C: I = (1, +infinito).** No sirve. cl(1) = {1} no tiene representante en (1, +infinito).

**Opcion D: I = [10, +infinito).** No sirve. cl(2) = {2, 1/2} no tiene representante en [10, +infinito).

**Respuesta:**
a) R es de equivalencia (caso particular de f(x) = f(y)).
b) El conjunto cociente es B = {cl(x) / x en (0, 1]}, porque cada clase cl(x) = {x, 1/x} tiene exactamente un representante en (0, 1].

**Tips para el examen:**
- Para verificar si un conjunto I es un conjunto de indices valido, hay que comprobar dos cosas: (1) cada clase tiene al menos un representante en I, y (2) cada clase tiene como maximo un representante en I.
- La relacion |log(x)| = |log(y)| agrupa x con 1/x. Geometricamente, son puntos equidistantes de 1 en escala logaritmica.

**Errores comunes a evitar:**
- No verificar que TODAS las clases tienen representante. Es facil olvidar clases con elementos fuera del rango propuesto.
- Olvidar la clase cl(1) = {1} que es especial.

---

### Ejercicio 30 -- Producto de relaciones de equivalencia

**Enunciado:** Sean R1 en A y R2 en B relaciones de equivalencia. Demostrar que en AxB la relacion (x;y)R(z;t) <=> xR1z y yR2t es una relacion de equivalencia.

**Identificacion del tipo:** Demostracion teorica sobre el producto de equivalencias. Herramienta fundamental para los ejercicios 31, 32, 33.

**Resolucion paso a paso:**

**Paso 1: Demostrar reflexiva.**
Sea (x, y) en AxB. Entonces x pertenece a A e y pertenece a B.
- Como R1 es de equivalencia en A, R1 es reflexiva, por lo tanto xR1x.
- Como R2 es de equivalencia en B, R2 es reflexiva, por lo tanto yR2y.
- Entonces xR1x y yR2y, lo cual implica (x,y)R(x,y).
R es reflexiva.

**Paso 2: Demostrar simetrica.**
Sea (x,y)R(z,t), entonces xR1z y yR2t.
- Como R1 es simetrica: zR1x.
- Como R2 es simetrica: tR2y.
- Entonces zR1x y tR2y, lo cual implica (z,t)R(x,y).
R es simetrica.

**Paso 3: Demostrar transitiva.**
Sean (x,y)R(z,t) y (z,t)R(a,b).
- De (x,y)R(z,t): xR1z y yR2t.
- De (z,t)R(a,b): zR1a y tR2b.
- Como R1 es transitiva: xR1z y zR1a implican xR1a.
- Como R2 es transitiva: yR2t y tR2b implican yR2b.
- Entonces xR1a y yR2b, lo cual implica (x,y)R(a,b).
R es transitiva.

**Respuesta:** R es de equivalencia. La demostracion se basa en aplicar las propiedades de R1 y R2 coordenada a coordenada.

**Tips para el examen:**
- Este resultado se usa frecuentemente: si tienes una relacion en un producto cartesiano definida "coordenada a coordenada", puedes citar este resultado para no volver a demostrar las tres propiedades.
- Las clases del producto son el producto de las clases: cl_R((x,y)) = cl_R1(x) x cl_R2(y).

**Errores comunes a evitar:**
- No olvidar justificar cada paso mencionando cual propiedad de R1 o R2 se usa.
- No confundir la relacion R (en AxB) con R1 (en A) o R2 (en B).

---

## Batch 13

---

### Ejercicio 31 -- Equivalencia en R^2: (a-b)^2 = (c-d)^2

**Enunciado:** En R^2, se define (a;b)R(c;d) <=> (a - b)^2 = (c - d)^2.
a) Hallar Cl((2;1)), Cl((3;3)) e interpretar geometricamente.
b) Conjunto cociente.

**Identificacion del tipo:** Equivalencia inducida por la funcion f(a,b) = (a-b)^2. Notar que (a-b)^2 = (c-d)^2 <=> |a-b| = |c-d|.

**Resolucion paso a paso:**

**Parte a):**

**Paso 1: Simplificar la condicion.**
(a-b)^2 = (c-d)^2 <=> |a-b| = |c-d|

Dos puntos (a,b) y (c,d) estan relacionados si y solo si la distancia de cada uno a la recta y = x (la diagonal) es la misma en valor absoluto. Mas precisamente, |a-b| mide (proporcional a) la distancia del punto (a,b) a la recta y = x.

**Paso 2: Cl((2;1)).**
Cl((2,1)) = {(x,y) en R^2 / (x-y)^2 = (2-1)^2} = {(x,y) / (x-y)^2 = 1}
= {(x,y) / |x-y| = 1}
= {(x,y) / x - y = 1 o x - y = -1}
= {(x,y) / y = x - 1 o y = x + 1}

Geometricamente: son dos rectas paralelas a la diagonal y = x, una por encima (y = x + 1) y otra por debajo (y = x - 1).

**Paso 3: Cl((3;3)).**
Cl((3,3)) = {(x,y) en R^2 / (x-y)^2 = (3-3)^2} = {(x,y) / (x-y)^2 = 0}
= {(x,y) / x - y = 0}
= {(x,y) / y = x}

Geometricamente: es la recta diagonal y = x.

**Interpretacion geometrica general:** Cada clase de equivalencia consiste en un par de rectas paralelas a y = x (equidistantes de la diagonal), excepto la clase de (3,3) que es la diagonal misma. Los puntos de una misma clase estan a la misma distancia de la recta y = x.

**Parte b):**

**Paso 4: Conjunto cociente.**
Las clases estan determinadas por el valor de |a - b|, que puede ser cualquier real no negativo.

Podemos parametrizar tomando representantes (x, 0) con x >= 0:
- cl((0,0)) = recta y = x (para |a-b| = 0)
- cl((x,0)) con x > 0 = las dos rectas y = x - x0 y y = x + x0 donde x0 = |a-b|

R^2/R = {cl((x, 0)) / x pertenece a R+_0} = {cl((x, 0)) / x >= 0}

**Respuesta:**
a) Cl((2,1)) = {(x,y) / y = x-1 o y = x+1} (dos rectas paralelas a la diagonal). Cl((3,3)) = {(x,y) / y = x} (la diagonal). Son rectas equidistantes a y = x.
b) R^2/R = {cl((x,0)) / x >= 0}.

**Tips para el examen:**
- (a-b)^2 = (c-d)^2 es lo mismo que |a-b| = |c-d|. Simplificar siempre.
- Las clases son pares de rectas paralelas a la diagonal, una "arriba" y otra "abajo".

**Errores comunes a evitar:**
- No olvidar que (a-b)^2 = (c-d)^2 incluye el caso a-b = -(c-d), no solo a-b = c-d.
- La clase de los puntos sobre la diagonal es unica (no son dos rectas, es una sola).

---

### Ejercicio 32 -- Equivalencia en ZxZ: 3|(x-z) y y^2 = t^2

**Enunciado:** En ZxZ, se define (x;y)R(z;t) <=> 3|(x-z) y y^2 = t^2.
a) Hallar las clases de (7;4), (0;0), (3;8).
b) Conjunto cociente.

**Identificacion del tipo:** Producto de dos equivalencias: congruencia mod 3 en la primera coordenada e igualdad de cuadrados en la segunda. Aplicacion directa del Ej. 30.

**Resolucion paso a paso:**

**Paso 1: Identificar las componentes.**
- Primera coordenada: xR1z <=> 3|(x-z). Equivalencia modulo 3 en Z.
- Segunda coordenada: yR2t <=> y^2 = t^2 <=> |y| = |t|. Equivalencia por valor absoluto en Z.

Por el Ej. 30, R es de equivalencia.

**Paso 2: Cl((7;4)).**
- Primera coordenada: cl_R1(7) = {x en Z / 3|(x-7)} = {x = 3k + 1 / k en Z} (pues 7 = 3*2 + 1, resto 1)
  = {..., -5, -2, 1, 4, 7, 10, ...}
- Segunda coordenada: cl_R2(4) = {y en Z / y^2 = 16} = {4, -4}

Cl((7,4)) = {(x,y) en Z^2 / x = 3k + 1 con k en Z, y (y = 4 o y = -4)}

**Paso 3: Cl((0;0)).**
- Primera coordenada: cl_R1(0) = {x en Z / 3|x} = {..., -6, -3, 0, 3, 6, ...} = multiplos de 3
- Segunda coordenada: cl_R2(0) = {y en Z / y^2 = 0} = {0}

Cl((0,0)) = {(x,y) en Z^2 / x = 3k con k en Z, y y = 0}

**Paso 4: Cl((3;8)).**
- Primera coordenada: cl_R1(3) = {x en Z / 3|(x-3)} = {x = 3k / k en Z} = multiplos de 3
- Segunda coordenada: cl_R2(8) = {y en Z / y^2 = 64} = {8, -8}

Cl((3,8)) = {(x,y) en Z^2 / x = 3k con k en Z, y (y = 8 o y = -8)}

**Paso 5: Conjunto cociente.**
Las clases en la primera coordenada son: Cl(0), Cl(1), Cl(2) (modulo 3), es decir a pertenece a {0, 1, 2}.
Las clases en la segunda coordenada son: Cl(b) para cada b en Z con b >= 0 (pues cl(b) = {b, -b} y tomamos |b| como representante), es decir b pertenece a Z_0^+ = {0, 1, 2, 3, ...}.

ZxZ/R = {Cl((a, b)) / a pertenece a {0, 1, 2} y b pertenece a Z_0^+}

Es decir, hay 3 * infinito = infinitas clases, indexadas por pares (a, b) con a en {0, 1, 2} y b en {0, 1, 2, 3, ...}.

**Respuesta:**
a) Cl((7,4)) = {3k+1 / k en Z} x {4, -4}; Cl((0,0)) = {3k / k en Z} x {0}; Cl((3,8)) = {3k / k en Z} x {8, -8}.
b) ZxZ/R = {Cl((a,b)) / a en {0,1,2}, b en Z con b >= 0}.

**Tips para el examen:**
- Cuando la relacion es un producto (condiciones independientes en cada coordenada), las clases son productos cartesianos de las clases de cada coordenada.
- Para y^2 = t^2, la solucion es y = t o y = -t, es decir |y| = |t|.

**Errores comunes a evitar:**
- No olvidar y = -t ademas de y = t al resolver y^2 = t^2.
- Al dar el cociente, asegurarse de que los representantes no se repitan (por eso b >= 0, no b cualquiera).

---

### Ejercicio 33 -- Equivalencia que construye los racionales

**Enunciado:** En (Z-{0}) x (Z-{0}), se define (a;b)R(c;d) <=> a*d = b*c.
Demostrar equivalencia, hallar cl(1;2), cl(-3;1), generalizar clases y dar la particion.

**Identificacion del tipo:** Esta es la relacion que define los numeros racionales. Dos fracciones a/b y c/d son equivalentes si representan el mismo numero racional.

**Resolucion paso a paso:**

**Paso 1: Demostrar reflexiva.**
Para todo (a,b) en (Z-{0})^2: a*b = b*a (conmutatividad de la multiplicacion).
Por lo tanto (a,b)R(a,b). R es reflexiva.

**Paso 2: Demostrar simetrica.**
Si (a,b)R(c,d), entonces a*d = b*c.
Entonces c*b = d*a (reescribiendo la misma igualdad).
Por lo tanto (c,d)R(a,b). R es simetrica.

**Paso 3: Demostrar transitiva.**
Si (a,b)R(c,d) y (c,d)R(e,f):
- a*d = b*c ... (i)
- c*f = d*e ... (ii)

Queremos demostrar que a*f = b*e.

De (i): a*d = b*c => a*d*f = b*c*f
De (ii): c*f = d*e => b*c*f = b*d*e

Entonces: a*d*f = b*d*e

Como d es distinto de 0 (pues d pertenece a Z-{0}), podemos dividir por d:
a*f = b*e

Por lo tanto (a,b)R(e,f). R es transitiva.

**Paso 4: Hallar cl(1;2).**
cl((1,2)) = {(x,y) en (Z-{0})^2 / 1*y = 2*x} = {(x,y) / y = 2x}
= {(x, 2x) / x en Z-{0}}
= {..., (-2,-4), (-1,-2), (1,2), (2,4), (3,6), ...}

Estos son todos los pares que representan la fraccion 1/2.

**Paso 5: Hallar cl(-3;1).**
cl((-3,1)) = {(x,y) in (Z-{0})^2 / (-3)*y = 1*x} = {(x,y) / x = -3y}
= {(-3y, y) / y en Z-{0}}
= {..., (6,-2), (3,-1), (-3,1), (-6,2), ...}

Estos son todos los pares que representan la fraccion -3/1 = -3.

**Paso 6: Clases genericas.**
cl((a,b)) = {(x,y) en (Z-{0})^2 / x = (a/b)*y} = {(x,y) / x/y = a/b}

Es decir, la clase de (a,b) contiene todos los pares (ka, kb) con k en Z-{0}:
cl((a,b)) = {(ka, kb) / k en Z-{0}}

Todos los pares (a,b) que representan la misma fraccion a/b.

**Paso 7: Particion y cociente.**
Cada clase corresponde a un numero racional. Los representantes naturales son las fracciones irreducibles (a,b) con mcd(a,b) = 1 (y, por convencion, b > 0 para unicidad).

(Z-{0}) x (Z-{0}) / R = {cl((a,b)) / mcd(|a|, |b|) = 1 y b > 0, con a,b en Z-{0}}

Este conjunto cociente es esencialmente Q (los racionales no nulos, pues 0 no esta representado ya que 0 no pertenece a Z-{0}).

Mas precisamente, no incluye la fraccion 0/n (pues el numerador tambien debe ser no nulo).

Correccion: Como a pertenece a Z-{0}, el numerador nunca es 0. El cociente representa Q - {0} = Q* (racionales no nulos).

**Respuesta:**
R es de equivalencia. cl((1,2)) = {(k, 2k) / k en Z-{0}}. cl((-3,1)) = {(-3k, k) / k en Z-{0}}.
En general, cl((a,b)) = {(ka, kb) / k en Z-{0}} (todos los pares proporcionales a (a,b)).
La particion es isomorfa a Q* (racionales no nulos), con representantes las fracciones irreducibles con denominador positivo.

**Tips para el examen:**
- Esta relacion es la que se usa para CONSTRUIR los numeros racionales a partir de los enteros. Es muy importante conceptualmente.
- a*d = b*c equivale a a/b = c/d (cuando b y d son distintos de 0).
- En la transitividad, la clave es que d es distinto de 0, lo que permite dividir.

**Errores comunes a evitar:**
- Olvidar que 0 no pertenece al dominio. No se puede tener k = 0 en las clases.
- En la transitividad, si d pudiera ser 0, la division no seria valida. La restriccion Z-{0} es esencial.
- No confundir (a,b)R(c,d) <=> ad = bc con ad = b+c u otra condicion.

---

### Ejercicio 34 -- Verdadero o falso sobre equivalencias

**Enunciado:** Indicar V o F, demostrando o justificando:
a) Si S es equivalencia entonces S^{-1} tambien es de equivalencia.
b) Las clases de equivalencia son disjuntas dos a dos.
c) Si R y S son de equivalencia, entonces R interseccion S es de equivalencia.
d) Si R y S son de equivalencia, entonces R union S es de equivalencia.

**Identificacion del tipo:** Preguntas teoricas sobre propiedades de relaciones de equivalencia.

**Resolucion paso a paso:**

**Parte a) VERDADERO.**

Demostracion:
- **Reflexiva:** Si S es reflexiva, para todo a: aSa. Entonces aS^{-1}a (pues (a,a) pertenece a S implica (a,a) pertenece a S^{-1}). S^{-1} es reflexiva.
- **Simetrica:** Si aS^{-1}b, entonces bSa (por definicion de inversa). Como S es simetrica, aSb. Entonces bS^{-1}a. S^{-1} es simetrica.
- **Transitiva:** Si aS^{-1}b y bS^{-1}c, entonces bSa y cSb. Como S es simetrica: aSb y bSc. Como S es transitiva: aSc. Entonces cS^{-1}a. Como S^{-1} es simetrica: aS^{-1}c. S^{-1} es transitiva.

Nota: De hecho, como S es simetrica, S = S^{-1}, por lo que es trivialmente cierto. La inversa de una relacion simetrica es ella misma.

**Parte b) VERDADERO.**

Demostracion:
Sean cl(a) y cl(b) dos clases de equivalencia distintas. Queremos demostrar que cl(a) interseccion cl(b) = vacio.

Supongamos por absurdo que existe c perteneciente a cl(a) interseccion cl(b).
- c pertenece a cl(a) => cRa (y por simetria aRc)
- c pertenece a cl(b) => cRb (y por simetria bRc)
- Entonces aRc y cRb, por transitividad aRb.
- Pero si aRb, entonces cl(a) = cl(b), contradiciendo que sean distintas.

Por lo tanto, dos clases distintas son disjuntas.

**Parte c) VERDADERO.**

Demostracion:
Sean R y S equivalencias en A. Probemos que T = R interseccion S es equivalencia.

- **Reflexiva:** Para todo a en A: aRa (R reflexiva) y aSa (S reflexiva). Por lo tanto aTa.
- **Simetrica:** Si aTb, entonces aRb y aSb. Como R es simetrica: bRa. Como S es simetrica: bSa. Por lo tanto bTa.
- **Transitiva:** Si aTb y bTc:
  - aRb y aRc (pues aTb => aRb y aTc... espera, corrijamos)
  - aTb => aRb y aSb
  - bTc => bRc y bSc
  - Como R es transitiva: aRb y bRc => aRc
  - Como S es transitiva: aSb y bSc => aSc
  - Entonces aRc y aSc, por lo tanto aTc.

T = R interseccion S es de equivalencia.

**Parte d) FALSO.**

Contraejemplo:
En A = {1, 2, 3}:
- R1 = {(1,1), (2,2), (3,3), (1,2), (2,1)} (equivalencia con clases {1,2} y {3})
- R2 = {(1,1), (2,2), (3,3), (2,3), (3,2)} (equivalencia con clases {1} y {2,3})

R1 union R2 = {(1,1), (2,2), (3,3), (1,2), (2,1), (2,3), (3,2)}

Verificamos transitividad: 1R2 (de R1) y 2R3 (de R2), pero (1,3) no pertenece a R1 union R2.
No es transitiva, por lo tanto NO es de equivalencia.

**Respuesta:**
a) VERDADERO (S^{-1} = S cuando S es simetrica).
b) VERDADERO (se prueba por absurdo).
c) VERDADERO (se hereda cada propiedad).
d) FALSO (la union puede perder transitividad).

**Tips para el examen:**
- La interseccion de equivalencias siempre es equivalencia; la union NO necesariamente.
- Para demostrar que algo es FALSO, basta un contraejemplo.
- El contraejemplo clasico para d) usa dos equivalencias en un conjunto de 3 elementos con clases "cruzadas".

**Errores comunes a evitar:**
- En la parte a), no complicarse. Si S es simetrica, S^{-1} = S y listo.
- En la parte d), no asumir que es verdadero. La union falla casi siempre que las clases no se contienen.

---

### Ejercicio 35 -- Equivalencia de parabolas por vertice

**Enunciado:** Se considera la relacion de equivalencia definida en el conjunto P de parabolas con eje vertical: p1 S p2 <=> tienen el mismo vertice.
a) Senalar dos elementos de la clase de la parabola p: y = 2(x+3)^2 - 1.
b) Hallar las clases de equivalencia y el conjunto cociente.

**Identificacion del tipo:** Equivalencia geometrica. La "funcion" que induce la equivalencia es f(p) = vertice de p.

**Resolucion paso a paso:**

**Parte a):**

**Paso 1: Identificar el vertice de p.**
p: y = 2(x+3)^2 - 1

Esta en forma canonica y = a(x - h)^2 + k con:
- a = 2
- h = -3
- k = -1

Vertice: V = (-3, -1)

**Paso 2: Dar dos parabolas con el mismo vertice.**
Cualquier parabola de eje vertical con vertice (-3, -1) esta en la clase de p.
Basta cambiar el coeficiente "a" (que debe ser distinto de 0):

- p1: y = 3(x+3)^2 - 1 (a = 3)
- p2: y = -4(x+3)^2 - 1 (a = -4)

Verificacion: ambas tienen vertice (-3, -1).

**Parte b):**

**Paso 3: Clases de equivalencia.**
Toda parabola de eje vertical se puede escribir como y = m(x - a)^2 + b con m distinto de 0.

Cl(p: y = m(x-a)^2 + b) = {q: y = k(x-a)^2 + b / k pertenece a R - {0}}

Es decir, la clase contiene todas las parabolas de eje vertical con el mismo vertice (a, b), variando la "apertura" k.

**Paso 4: Conjunto cociente.**
Cada clase queda determinada por el vertice (a, b) con a, b en R.

P/S = {cl(p) / p: y = (x-a)^2 + b, con a, b pertenecientes a R}

El conjunto cociente es isomorfo a R^2 (cada punto del plano es el vertice de exactamente una clase).

**Respuesta:**
a) Dos parabolas de la clase: y = 3(x+3)^2 - 1 y y = -4(x+3)^2 - 1.
b) Cl(p) = {todas las parabolas con el mismo vertice}. P/S = {cl(p) / p: y = (x-a)^2 + b, a, b en R}. El cociente se identifica con R^2 (el conjunto de vertices posibles).

**Tips para el examen:**
- Para hallar el vertice de y = a(x-h)^2 + k, el vertice es (h, k) directamente.
- Si la parabola esta en forma general y = ax^2 + bx + c, el vertice es (-b/(2a), c - b^2/(4a)).
- La relacion "tener el mismo vertice" es claramente de equivalencia (es f(p) = f(q) con f = vertice).

**Errores comunes a evitar:**
- Confundir el signo en y = 2(x+3)^2 - 1. El vertice es (-3, -1), no (3, -1).
- Olvidar que m debe ser distinto de 0 (si m = 0, no es una parabola).
- Dar parabolas con eje horizontal como ejemplo (el enunciado dice eje vertical).

---

## Batch 14

---

### Ejercicio 36 -- Identificar particiones

**Enunciado:** A = {1, 2, 3, 4, 5, 6, 7}. Indicar cuales de los siguientes son particiones de A:
a) P = {{3, 4, 5}, {1, 7}, {2}}
b) P = {{2, 4, 5}, {1}, {3, 7}, {6}}
c) P = {{4, 6}, {1, 2, 3, 7}, {2, 5}}
d) P = {{x en A / x > 3}, {x en A / x <= 3}}
e) P = {{x en A / x <= 4}, {x en A / x > 4 y x < 5}, {x en A / x >= 5}}

**Identificacion del tipo:** Verificacion de las tres condiciones de particion: (1) las celdas no son vacias, (2) son disjuntas dos a dos, (3) su union es A.

**Resolucion paso a paso:**

**Recordatorio: Condiciones para ser particion.**
Un conjunto P = {C1, C2, ..., Ck} es particion de A si y solo si:
1. Ci es no vacio para todo i.
2. Ci interseccion Cj = vacio para todo i distinto de j (celdas disjuntas).
3. C1 union C2 union ... union Ck = A (cubren todo A).

---

**Parte a) P = {{3, 4, 5}, {1, 7}, {2}}**

Verificacion:
1. Celdas no vacias: {3,4,5} tiene 3 elementos, {1,7} tiene 2, {2} tiene 1. OK.
2. Disjuntas: {3,4,5} interseccion {1,7} = vacio. {3,4,5} interseccion {2} = vacio. {1,7} interseccion {2} = vacio. OK.
3. Union: {3,4,5} union {1,7} union {2} = {1, 2, 3, 4, 5, 7}. Falta el 6.

**NO es particion.** La union de las celdas no cubre todo A (falta el 6).

---

**Parte b) P = {{2, 4, 5}, {1}, {3, 7}, {6}}**

Verificacion:
1. Celdas no vacias: todas tienen al menos un elemento. OK.
2. Disjuntas: no hay elementos repetidos entre celdas. OK.
3. Union: {2,4,5} union {1} union {3,7} union {6} = {1, 2, 3, 4, 5, 6, 7} = A. OK.

**SI es particion.**

Relacion de equivalencia asociada:
Las clases son {2,4,5}, {1}, {3,7}, {6}.

R = {(2,2),(2,4),(2,5),(4,2),(4,4),(4,5),(5,2),(5,4),(5,5), (1,1), (3,3),(3,7),(7,3),(7,7), (6,6)}

Digrafo: bucles en todos los vertices; flechas dobles entre 2-4, 2-5, 4-5; flechas dobles entre 3-7; vertices 1 y 6 aislados (solo bucles).

---

**Parte c) P = {{4, 6}, {1, 2, 3, 7}, {2, 5}}**

Verificacion:
1. Celdas no vacias: OK.
2. Disjuntas: {1, 2, 3, 7} interseccion {2, 5} = {2} que es distinto de vacio. FALLA.

**NO es particion.** Las celdas no son disjuntas (el 2 aparece en dos celdas).

---

**Parte d) P = {{x en A / x > 3}, {x en A / x <= 3}}**

Calculemos las celdas:
- {x en A / x > 3} = {4, 5, 6, 7}
- {x en A / x <= 3} = {1, 2, 3}

Verificacion:
1. Celdas no vacias: ambas tienen elementos. OK.
2. Disjuntas: {4,5,6,7} interseccion {1,2,3} = vacio. OK.
3. Union: {4,5,6,7} union {1,2,3} = {1,2,3,4,5,6,7} = A. OK.

**SI es particion.**

Relacion de equivalencia asociada:
Las clases son {1,2,3} y {4,5,6,7}.

R tiene todos los pares dentro de {1,2,3} (9 pares) y todos los pares dentro de {4,5,6,7} (16 pares). Total: 25 pares.

Digrafo: grupo de 3 vertices (1,2,3) totalmente conectados entre si (con bucles); grupo de 4 vertices (4,5,6,7) totalmente conectados entre si (con bucles).

---

**Parte e) P = {{x en A / x <= 4}, {x en A / x > 4 y x < 5}, {x en A / x >= 5}}**

Calculemos las celdas:
- {x en A / x <= 4} = {1, 2, 3, 4}
- {x en A / x > 4 y x < 5} = vacio (no hay enteros entre 4 y 5 exclusivos)
- {x en A / x >= 5} = {5, 6, 7}

Verificacion:
1. Celdas no vacias: la segunda celda es VACIA. FALLA.

**NO es particion.** Una de las celdas es el conjunto vacio, lo cual viola la primera condicion.

---

**Respuesta:**
a) NO es particion (la union no cubre A, falta el 6).
b) SI es particion.
c) NO es particion (las celdas no son disjuntas, el 2 esta repetido).
d) SI es particion.
e) NO es particion (una celda es vacia).

**Tips para el examen:**
- Verificar las 3 condiciones en orden: (1) no vacias, (2) disjuntas, (3) union = A.
- Para las celdas definidas por comprension (como d y e), primero calcular los elementos explicitos.
- En conjuntos finitos, la forma mas rapida de verificar es listar los elementos de cada celda.

**Errores comunes a evitar:**
- En e), no darse cuenta de que {x en A / x > 4 y x < 5} = vacio (A contiene solo enteros, y no hay enteros en el intervalo abierto (4, 5)).
- En a), olvidar verificar que la union cubra todo A. Es facil no notar que falta un elemento.
- Confundir particion con cubrimiento. Un cubrimiento permite solapamiento; una particion NO.

---

# Resumen de conceptos clave

## Como demostrar que R es de equivalencia
Siempre se deben probar las 3 propiedades:
1. **Reflexiva:** Para todo a en A, aRa.
2. **Simetrica:** Para todo a, b en A, si aRb entonces bRa.
3. **Transitiva:** Para todo a, b, c en A, si aRb y bRc entonces aRc.

## Atajo: relaciones de la forma f(x) = f(y)
Si R se define como xRy <=> f(x) = f(y) para alguna funcion f, entonces R es **automaticamente** de equivalencia (las 3 propiedades se heredan de la igualdad). Ejercicios que usan este patron: 20a, 20b, 20c, 24, 25, 27, 28, 29, 33, 35.

## Como hallar clases de equivalencia
- En conjuntos finitos: tomar un elemento, encontrar todos los que se relacionan con el.
- Con funciones f(x) = f(y): resolver la ecuacion f(x) = c para cada valor c en Im(f).
- Con valor absoluto: recordar que |f(x)| = |f(y)| da dos casos: f(x) = f(y) y f(x) = -f(y).

## Como verificar particiones
Tres condiciones: celdas no vacias, celdas disjuntas, union = A.

## Relacion entre particion y equivalencia
Toda equivalencia induce una particion (las clases), y toda particion define una equivalencia (estar en la misma celda). Es una correspondencia biyectiva.

## Formula para contar pares
Si las clases tienen tamanos n1, n2, ..., nk, el numero total de pares en R es:
|R| = n1^2 + n2^2 + ... + nk^2
