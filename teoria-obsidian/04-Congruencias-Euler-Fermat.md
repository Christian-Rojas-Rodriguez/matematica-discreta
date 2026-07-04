---
tags: [matematica-discreta, tema-4, teoria-de-numeros, congruencias, unsam]
aliases: ["Congruencias", "Euler-Fermat", "Tema 4"]
---

# Congruencias y Teorema de Euler-Fermat

> [!info] Ubicación en la materia
> Esta unidad formaliza la aritmética "módulo n" que ya usábamos intuitivamente al hablar de restos, y se apoya directamente en la relación de equivalencia de [[02-Relaciones-de-Equivalencia]] y en la estructura de divisores de [[03-Redes-y-Algebras-de-Boole]]. Es, además, la puerta de entrada a criptografía (RSA) y a los algoritmos recursivos de [[05-Relaciones-de-Recurrencia]].

## 1. Introducción y motivación

Cuando dividimos un número entero $a$ por un entero positivo $n$, el algoritmo de división nos da un cociente $q$ y un resto $r$ únicos tales que $a = nq + r$ con $0 \le r < n$. La idea central de esta unidad es que, para muchísimos problemas, **lo único que importa es el resto**, no el número completo. Dos números que dejan el mismo resto al dividirlos por $n$ se comportan "igual" respecto de la suma, la resta y el producto módulo $n$. Esta observación, tan simple, es el germen de toda la teoría de congruencias.

¿Para qué sirve esto en la práctica?

- Para calcular el resto de una potencia enorme (por ejemplo $7^{122}$ dividido $11$, o $8^{1{,}791{,}485}$ dividido $21$) sin tener que calcular el número gigantesco que resulta de elevar a esa potencia. El Pequeño Teorema de Fermat y su generalización, el Teorema de Euler-Fermat, nos dan un atajo: alcanza con conocer el resto del **exponente** al dividirlo por $p-1$ (si el módulo es primo) o por $\varphi(n)$ (en general).
- Para resolver ecuaciones del tipo $ax \equiv b \pmod{n}$, que son el análogo discreto de "despejar $x$" cuando no podemos dividir libremente (en $\mathbb{Z}_n$ no todo elemento tiene inverso multiplicativo).
- Para estructurar el conjunto de clases de restos $\mathbb{Z}_n$ como un conjunto con operaciones propias, que es exactamente el conjunto cociente que aparece en la teoría de relaciones de equivalencia.
- Como base de la criptografía de clave pública (RSA se construye literalmente sobre el Teorema de Euler-Fermat).

Es una unidad muy algorítmica: casi todo se resuelve con un procedimiento de pasos fijos (Euclides para el mcd, reducción de exponentes con $\varphi(n)$, etc.), pero **hay que entender por qué funciona cada paso**, porque los ejercicios del final suelen pedir justificar, no solo aplicar la fórmula.

## 2. Definiciones formales

### 2.1. Congruencia módulo $n$

Sea $n \in \mathbb{N}$, $n \ge 1$. Decimos que dos enteros $a, b \in \mathbb{Z}$ son **congruentes módulo $n$**, y escribimos

$$a \equiv b \pmod{n}$$

si se cumple cualquiera de estas dos condiciones equivalentes (más adelante probamos que son equivalentes):

$$a \equiv b \pmod n \iff n \mid (a-b) \iff a \text{ y } b \text{ tienen el mismo resto al dividir por } n.$$

La primera caracterización ($n \mid (a-b)$, es decir, existe $k \in \mathbb{Z}$ tal que $a - b = nk$) es la definición **algebraica**, la que se usa para demostrar propiedades. La segunda (mismo resto en la división entera) es la caracterización **operativa**, la que se usa para verificar rápido si dos números son congruentes.

### 2.2. Clase residual (clase de equivalencia módulo $n$)

Dado $x \in \mathbb{Z}$, la **clase residual de $x$ módulo $n$** es el conjunto de todos los enteros congruentes con $x$:

$$\bar{x} = \{ y \in \mathbb{Z} \ / \ y \equiv x \pmod n \} = \{ y \in \mathbb{Z} \ / \ y = nk + x, \ k \in \mathbb{Z}\}.$$

Cada clase $\bar x$ queda representada por cualquiera de sus elementos: si $y \in \bar x$ entonces $\bar y = \bar x$ (mismo argumento que en cualquier relación de equivalencia). Hay exactamente $n$ clases distintas, una por cada resto posible $0, 1, \dots, n-1$.

### 2.3. El conjunto $\mathbb{Z}_n$ y sus operaciones

El **conjunto cociente** de $\mathbb{Z}$ por la relación de congruencia módulo $n$ se nota

$$\mathbb{Z}_n = \{\bar 0, \bar 1, \bar 2, \dots, \overline{n-1}\},$$

y tiene exactamente $n$ elementos (una clase por cada resto). Sobre $\mathbb{Z}_n$ definimos dos operaciones, suma y producto de clases, **eligiendo representantes**:

$$\bar a + \bar b := \overline{(a+b) \bmod n}, \qquad \bar a \cdot \bar b := \overline{(a \cdot b) \bmod n}.$$

Estas definiciones tienen un problema potencial: la clase $\bar a$ tiene infinitos representantes ($a, a+n, a-n, a+2n, \dots$), así que hay que garantizar que el resultado **no dependa de qué representante elegimos** para calcular. Esto es lo que se llama que la operación está **bien definida**, y se demuestra en la Sección 3.

### 2.4. Función $\varphi$ de Euler

Para $n \in \mathbb{N}$, la función de Euler cuenta cuántos números entre $1$ y $n$ son coprimos con $n$:

$$\varphi(n) = |\{x \in \mathbb{N} \ / \ x \le n \ \wedge \ \operatorname{mcd}(x,n)=1\}|.$$

Equivalentemente, $\varphi(n)$ es el cardinal del conjunto de clases **inversibles** de $\mathbb{Z}_n$ (las que tienen inverso multiplicativo), lo cual no es casual: $\bar a$ tiene inverso en $\mathbb{Z}_n$ si y solo si $\operatorname{mcd}(a,n) = 1$.

### 2.5. Ecuación lineal de congruencia y "solución principal"

Una **ecuación lineal de congruencia** es una expresión de la forma

$$a \cdot x \equiv b \pmod n,$$

donde $a, b, n$ son datos conocidos y buscamos los $x \in \mathbb{Z}$ que la satisfacen. Como las clases módulo $n$ se repiten cada $n$ enteros, conviene describir el conjunto solución dando representantes en el rango $\{0, 1, \dots, n-1\}$: a esos representantes (hay finitos, entre $0$ y $d-1$ soluciones "esencialmente distintas", donde $d = \operatorname{mcd}(a,n)$) se los llama **soluciones principales**. Toda otra solución entera se obtiene sumando múltiplos de $n$ a una solución principal. Es un error común confundir "cuántas soluciones principales hay" (que es $d$) con "cuáles son esas soluciones" (que hay que calcular aparte).

## 3. Teoremas y demostraciones

### 3.1. Equivalencia de las dos caracterizaciones de congruencia

**Afirmación:** $n \mid (a-b) \iff a$ y $b$ tienen el mismo resto al dividir por $n$.

**Demostración.** Por el algoritmo de división, $a = nq_1 + r_1$ y $b = nq_2 + r_2$, con $0 \le r_1, r_2 < n$. Entonces $a - b = n(q_1 - q_2) + (r_1 - r_2)$.

($\Leftarrow$) Si $r_1 = r_2$, entonces $a - b = n(q_1-q_2)$, que es múltiplo de $n$, o sea $n \mid (a-b)$.

($\Rightarrow$) Si $n \mid (a-b)$, entonces $n \mid \big( (a-b) - n(q_1-q_2)\big) = r_1 - r_2$. Pero $-n < r_1 - r_2 < n$ (porque ambos restos están en $[0,n)$), y el único múltiplo de $n$ estrictamente entre $-n$ y $n$ es el $0$. Luego $r_1 - r_2 = 0$, es decir $r_1 = r_2$. $\blacksquare$

### 3.2. Propiedades operativas de la congruencia

Sean $a \equiv b \pmod n$ y $c \equiv d \pmod n$.

**(i) Suma:** $a + c \equiv b + d \pmod n$.

*Demostración.* Por hipótesis $n \mid (a-b)$ y $n \mid (c-d)$. La suma de dos múltiplos de $n$ es múltiplo de $n$, luego $n \mid \big((a-b)+(c-d)\big) = (a+c)-(b+d)$. Por definición, $a+c \equiv b+d \pmod n$. $\blacksquare$

**(ii) Producto:** $a \cdot c \equiv b \cdot d \pmod n$.

*Demostración.* Escribimos, sumando y restando $bc$:
$$ac - bd = ac - bc + bc - bd = c(a-b) + b(c-d).$$
Como $n \mid (a-b)$, también $n \mid c(a-b)$; y como $n \mid (c-d)$, también $n \mid b(c-d)$. La suma de dos múltiplos de $n$ es múltiplo de $n$, luego $n \mid (ac-bd)$, es decir $ac \equiv bd \pmod n$. $\blacksquare$

**(iii) Potencia:** $a^k \equiv b^k \pmod n$ para todo $k \in \mathbb{N}$.

*Demostración por inducción en $k$.* Caso base $k=1$: es la hipótesis $a \equiv b \pmod n$. Paso inductivo: supongamos $a^k \equiv b^k \pmod n$. Como también $a \equiv b \pmod n$, aplicamos la propiedad del producto (ii) a las congruencias $a^k \equiv b^k \pmod n$ y $a \equiv b \pmod n$, obteniendo $a^k \cdot a \equiv b^k \cdot b \pmod n$, es decir $a^{k+1} \equiv b^{k+1} \pmod n$. Por inducción, vale para todo $k \in \mathbb{N}$. $\blacksquare$

**(iv) Cancelación (con hipótesis de coprimalidad):** si $a\cdot c \equiv b \cdot c \pmod n$ y $\operatorname{mcd}(c,n) = 1$, entonces $a \equiv b \pmod n$.

*Demostración.* Por hipótesis $n \mid (ac - bc) = c(a-b)$. Como $\operatorname{mcd}(c,n)=1$, el Lema de Euclides (generalizado) garantiza que si $n$ divide a un producto $c \cdot (a-b)$ y $n$ es coprimo con uno de los factores, entonces $n$ divide al otro factor. Luego $n \mid (a-b)$, es decir $a \equiv b \pmod n$. $\blacksquare$

> [!warning] Por qué hace falta la hipótesis $\operatorname{mcd}(c,n)=1$
> Sin esa hipótesis la cancelación falla: por ejemplo $2\cdot 3 \equiv 2 \cdot 0 \pmod 6$ (ambos son $6 \equiv 0$), pero $3 \not\equiv 0 \pmod 6$. El problema es que $\operatorname{mcd}(2,6) = 2 \ne 1$.

### 3.3. Buena definición de las operaciones en $\mathbb{Z}_n$

**Afirmación:** si $\bar a = \bar{a'}$ y $\bar b = \bar{b'}$ en $\mathbb{Z}_n$, entonces $\overline{a+b} = \overline{a'+b'}$ y $\overline{a \cdot b} = \overline{a' \cdot b'}$. Es decir, el resultado de sumar o multiplicar dos clases no depende de qué representante se use dentro de cada clase.

**Demostración.** Decir $\bar a = \bar{a'}$ es, por definición de clase residual, decir $a \equiv a' \pmod n$; análogamente $\bar b = \bar{b'}$ equivale a $b \equiv b' \pmod n$. Por la propiedad (i) de la suma (Sección 3.2), de $a \equiv a' \pmod n$ y $b \equiv b' \pmod n$ se deduce $a + b \equiv a' + b' \pmod n$, es decir $\overline{a+b} = \overline{a'+b'}$. Análogamente, por la propiedad (ii) del producto, $a \cdot b \equiv a' \cdot b' \pmod n$, es decir $\overline{a\cdot b} = \overline{a' \cdot b'}$. $\blacksquare$

Esto es exactamente lo que hace falta para que las fórmulas $\bar a + \bar b = \overline{a+b}$ y $\bar a \cdot \bar b = \overline{a \cdot b}$ definan **funciones** (y no relaciones ambiguas) sobre $\mathbb{Z}_n$: da lo mismo calcular con $a$ que con cualquier otro elemento de su clase.

### 3.4. Criterio de existencia de solución de $ax \equiv b \pmod n$

**Teorema.** La ecuación $ax \equiv b \pmod n$ tiene solución entera si y solo si $d = \operatorname{mcd}(a,n)$ divide a $b$. Cuando tiene solución, tiene exactamente $d$ soluciones principales (módulo $n$).

**Demostración de la existencia (usando Bézout).** Por la identidad de Bézout, existen enteros $s, t$ tales que
$$as + nt = d, \qquad d = \operatorname{mcd}(a,n).$$

($\Leftarrow$, si $d \mid b$) Escribimos $b = d \cdot b'$ con $b' \in \mathbb{Z}$. Multiplicando la identidad de Bézout por $b'$:
$$a(sb') + n(tb') = db' = b.$$
Esto dice que $a(sb') - b = -n(tb')$, es decir $n \mid \big(a(sb') - b\big)$, o sea $x_0 = sb'$ es solución de $ax \equiv b \pmod n$.

($\Rightarrow$, si hay solución entonces $d \mid b$) Si $x$ es solución, $n \mid (ax - b)$, es decir existe $y \in \mathbb{Z}$ con $ax - ny = b$. Como $d = \operatorname{mcd}(a,n)$ divide tanto a $a$ como a $n$, divide a cualquier combinación entera de ellos, en particular $d \mid (ax - ny) = b$. $\blacksquare$

**Sobre la cantidad de soluciones ($d$ soluciones principales).** Si $d \mid b$, dividimos toda la congruencia por $d$: $ax \equiv b \pmod n$ es equivalente a
$$\frac{a}{d} x \equiv \frac{b}{d} \pmod{\frac{n}{d}},$$
donde ahora $\operatorname{mcd}(a/d,\, n/d) = 1$ (propiedad del mcd). Esta ecuación reducida tiene solución **única** módulo $n/d$ (por el caso de coprimalidad, ver 3.4.1 más abajo), llamémosla $x_0 \in \{0,1,\dots, n/d - 1\}$. Pero la ecuación original está planteada módulo $n$, que es $d$ veces más grande que $n/d$; por lo tanto, dentro del rango $\{0,1,\dots,n-1\}$, la clase $x_0$ módulo $n/d$ se "reparte" en exactamente $d$ representantes distintos módulo $n$:
$$x_0, \quad x_0 + \frac{n}{d}, \quad x_0 + 2\frac{n}{d}, \quad \dots, \quad x_0 + (d-1)\frac{n}{d}.$$
Estas son las $d$ soluciones principales de la ecuación original. $\blacksquare$

**3.4.1. Caso particular $\operatorname{mcd}(a,n)=1$ (solución única).** Cuando $d=1$ la ecuación ya viene "simplificada". Usando el Teorema de Euler-Fermat (que probamos en 3.6), $a^{\varphi(n)} \equiv 1 \pmod n$. Multiplicando ambos lados de $ax \equiv b \pmod n$ por $a^{\varphi(n)-1}$:
$$a^{\varphi(n)-1} \cdot a \cdot x \equiv a^{\varphi(n)-1} \cdot b \pmod n \implies a^{\varphi(n)} x \equiv a^{\varphi(n)-1} b \pmod n \implies x \equiv a^{\varphi(n)-1} b \pmod n,$$
usando que $a^{\varphi(n)} \equiv 1$. Esto justifica la fórmula $x = a^{\varphi(n)-1} \cdot b \pmod n$ dada en la Sección 4.

### 3.5. Pequeño Teorema de Fermat

**Teorema.** Sea $p$ primo y $a \in \mathbb{Z}$ con $\operatorname{mcd}(a,p) = 1$. Entonces
$$a^{p-1} \equiv 1 \pmod p.$$

**Demostración (demostración clásica, "de la permutación de restos").**

Consideremos los $p-1$ múltiplos de $a$:
$$a, \ 2a, \ 3a, \ \dots, \ (p-1)a.$$

**Paso 1 — ninguno es congruente a $0$ módulo $p$.** Si $ka \equiv 0 \pmod p$ para algún $k \in \{1,\dots,p-1\}$, entonces $p \mid ka$. Como $p$ es primo y $p \nmid a$ (porque $\operatorname{mcd}(a,p)=1$), por el Lema de Euclides $p$ tendría que dividir a $k$; pero $1 \le k \le p-1 < p$, imposible. Entonces ningún $ka$ es congruente a $0$.

**Paso 2 — son todos distintos módulo $p$.** Supongamos $ka \equiv ja \pmod p$ con $1 \le j < k \le p-1$. Como $\operatorname{mcd}(a,p)=1$, por la propiedad de cancelación (3.2.iv) podemos cancelar $a$: $k \equiv j \pmod p$. Pero $0 < k - j < p$, así que $p \nmid (k-j)$, contradicción. Luego los $p-1$ números $a, 2a, \dots, (p-1)a$ son **todos distintos** módulo $p$.

**Paso 3 — son una permutación de $\{1, 2, \dots, p-1\}$.** Por los pasos 1 y 2, los restos módulo $p$ de $a, 2a, \dots, (p-1)a$ son $p-1$ valores distintos, todos no nulos, todos en $\{1, \dots, p-1\}$ (que tiene exactamente $p-1$ elementos). Al ser la misma cantidad de valores distintos que de elementos del conjunto, deben coincidir exactamente: $\{a \bmod p, 2a \bmod p, \dots, (p-1)a \bmod p\} = \{1, 2, \dots, p-1\}$.

**Paso 4 — multiplicar todo y cancelar.** Como es la misma colección de números (en otro orden), el producto de un lado es congruente al producto del otro:
$$a \cdot 2a \cdot 3a \cdots (p-1)a \equiv 1 \cdot 2 \cdot 3 \cdots (p-1) \pmod p,$$
es decir
$$a^{p-1} \cdot (p-1)! \equiv (p-1)! \pmod p.$$
Como $p$ es primo, $p$ no divide a ningún factor de $(p-1)! = 1 \cdot 2 \cdots (p-1)$ (todos son menores que $p$), luego $\operatorname{mcd}\big((p-1)!,\, p\big) = 1$. Aplicando la cancelación (3.2.iv) con $c = (p-1)!$:
$$a^{p-1} \equiv 1 \pmod p. \qquad \blacksquare$$

**Versión alternativa (multiplicando por $a$).** Multiplicando ambos lados por $a$ se obtiene $a^p \equiv a \pmod p$, versión que vale incluso sin pedir $\operatorname{mcd}(a,p)=1$ (si $p \mid a$, ambos lados son $\equiv 0$).

### 3.6. Teorema de Euler-Fermat (generalización)

**Teorema.** Si $\operatorname{mcd}(a,n) = 1$, entonces $a^{\varphi(n)} \equiv 1 \pmod n$.

**Demostración (mismo esquema que Fermat, cambiando $\{1,\dots,p-1\}$ por el sistema reducido de restos).**

Sea $R = \{r_1, r_2, \dots, r_{\varphi(n)}\}$ el conjunto de los $\varphi(n)$ representantes en $\{1,\dots,n\}$ que son coprimos con $n$ (el "sistema reducido de restos módulo $n$").

**Paso 1 — cada $a r_i$ es coprimo con $n$.** Si $\operatorname{mcd}(a,n)=1$ y $\operatorname{mcd}(r_i,n)=1$, entonces $\operatorname{mcd}(a r_i, n) = 1$ (el producto de dos números coprimos con $n$ es coprimo con $n$, porque ningún primo que divide a $n$ puede dividir ni a $a$ ni a $r_i$, luego tampoco a su producto).

**Paso 2 — son todos distintos módulo $n$.** Si $a r_i \equiv a r_j \pmod n$ con $i \ne j$, como $\operatorname{mcd}(a,n)=1$ cancelamos $a$ (propiedad 3.2.iv) y obtenemos $r_i \equiv r_j \pmod n$; pero $r_i, r_j \in \{1,\dots,n\}$ son representantes distintos de restos distintos, contradicción.

**Paso 3 — permutación del sistema reducido.** Los $\varphi(n)$ valores $a r_1, \dots, a r_{\varphi(n)}$ módulo $n$ son coprimos con $n$ (Paso 1) y todos distintos (Paso 2); como hay exactamente $\varphi(n)$ clases coprimas con $n$, deben ser —en algún orden— exactamente los restos $r_1, \dots, r_{\varphi(n)}$.

**Paso 4 — multiplicar y cancelar.** Igual que antes:
$$\prod_{i=1}^{\varphi(n)} (a r_i) \equiv \prod_{i=1}^{\varphi(n)} r_i \pmod n \implies a^{\varphi(n)} \prod_i r_i \equiv \prod_i r_i \pmod n.$$
Como cada $r_i$ es coprimo con $n$, el producto $\prod_i r_i$ también es coprimo con $n$, así que podemos cancelarlo (3.2.iv):
$$a^{\varphi(n)} \equiv 1 \pmod n. \qquad \blacksquare$$

Fermat es el caso particular $n = p$ primo, donde el sistema reducido de restos es exactamente $\{1, 2, \dots, p-1\}$ (todos los números menores que $p$ son coprimos con $p$ por ser primo) y $\varphi(p) = p - 1$.

### 3.7. Multiplicatividad de $\varphi$ y fórmula general

**Teorema (multiplicatividad).** Si $\operatorname{mcd}(n,m) = 1$, entonces $\varphi(nm) = \varphi(n)\varphi(m)$.

**Idea de la demostración (argumento tipo Teorema Chino del Resto).** Como $\operatorname{mcd}(n,m)=1$, el Teorema Chino del Resto establece que la correspondencia
$$x \bmod nm \ \longleftrightarrow\ (x \bmod n,\ x \bmod m)$$
es una **biyección** entre $\mathbb{Z}_{nm}$ y $\mathbb{Z}_n \times \mathbb{Z}_m$: cada clase módulo $nm$ corresponde a un único par de clases (una módulo $n$, otra módulo $m$), y viceversa, todo par se realiza. Como $n$ y $m$ no comparten factores primos, los primos que dividen a $nm$ son exactamente la unión (disjunta) de los primos que dividen a $n$ con los que dividen a $m$. Entonces:
$$\operatorname{mcd}(x, nm) = 1 \iff \operatorname{mcd}(x,n)=1 \ \wedge\ \operatorname{mcd}(x,m) = 1.$$
Es decir, la biyección de arriba manda exactamente las clases coprimas con $nm$ a los pares donde ambas coordenadas son coprimas (una con $n$, otra con $m$). Contando: el lado izquierdo tiene $\varphi(nm)$ elementos, el lado derecho tiene $\varphi(n) \cdot \varphi(m)$ pares (por regla del producto), y como es una biyección entre esos dos subconjuntos, $\varphi(nm) = \varphi(n)\varphi(m)$. $\blacksquare$

**Fórmula para potencias de primo.** Si $p$ es primo, $\varphi(p^k) = p^{k-1}(p-1)$.

*Demostración.* Entre $1$ y $p^k$, los números que **no** son coprimos con $p^k$ son exactamente los múltiplos de $p$ (porque el único primo que divide a $p^k$ es $p$). Los múltiplos de $p$ entre $1$ y $p^k$ son $p, 2p, 3p, \dots, p^{k-1}\cdot p$, es decir hay exactamente $p^{k-1}$ de ellos. Por lo tanto:
$$\varphi(p^k) = p^k - p^{k-1} = p^{k-1}(p-1). \qquad \blacksquare$$

**Fórmula general.** Si $n = p_1^{k_1} p_2^{k_2} \cdots p_r^{k_r}$ es la factorización prima de $n$ (con $p_i$ primos distintos), como los $p_i^{k_i}$ son coprimos entre sí de a pares, aplicando la multiplicatividad repetidas veces:
$$\varphi(n) = \prod_{i=1}^r \varphi(p_i^{k_i}) = \prod_{i=1}^r p_i^{k_i - 1}(p_i - 1) = \prod_{i=1}^r p_i^{k_i}\left(1 - \frac{1}{p_i}\right) = n \prod_{i=1}^r \left(1 - \frac{1}{p_i}\right).$$

Esta es exactamente la fórmula $\varphi(n) = n \cdot \prod (1 - 1/p_i)$ usada en los ejemplos de $\varphi(48)$, $\varphi(75)$, $\varphi(100)$.

## 4. Fórmulas clave (tabla de repaso rápido)

| Concepto | Fórmula / enunciado |
|---|---|
| Congruencia | $a \equiv b \pmod n \iff n \mid (a-b) \iff$ mismo resto al dividir por $n$ |
| Suma | $a\equiv b, c\equiv d \pmod n \implies a+c \equiv b+d \pmod n$ |
| Producto | $a\equiv b, c\equiv d \pmod n \implies ac \equiv bd \pmod n$ |
| Potencia | $a \equiv b \pmod n \implies a^k \equiv b^k \pmod n$ |
| Cancelación | $ac \equiv bc \pmod n, \ \operatorname{mcd}(c,n)=1 \implies a \equiv b \pmod n$ |
| Clase residual | $\bar x = \{y \in \mathbb{Z} : y \equiv x \pmod n\} = \{nk+x : k \in \mathbb{Z}\}$ |
| $\mathbb{Z}_n$ | $\{\bar 0, \bar 1, \dots, \overline{n-1}\}$, con $\bar a + \bar b = \overline{(a+b)\bmod n}$, $\bar a \cdot \bar b = \overline{(ab)\bmod n}$ |
| $\varphi(p)$, $p$ primo | $\varphi(p) = p-1$ |
| $\varphi(p^k)$ | $\varphi(p^k) = p^{k-1}(p-1)$ |
| $\varphi$ multiplicativa | $\operatorname{mcd}(n,m)=1 \implies \varphi(nm)=\varphi(n)\varphi(m)$ |
| $\varphi(n)$ general | $\varphi(n) = n \displaystyle\prod_{p_i \mid n} \left(1 - \frac{1}{p_i}\right)$ |
| Pequeño Teorema de Fermat | $p$ primo, $\operatorname{mcd}(a,p)=1 \implies a^{p-1} \equiv 1 \pmod p$ (o bien $a^p \equiv a \pmod p$) |
| Teorema de Euler-Fermat | $\operatorname{mcd}(a,n)=1 \implies a^{\varphi(n)} \equiv 1 \pmod n$ |
| Reducción de exponentes | $k = \varphi(n) \cdot q + r \implies a^k \equiv a^r \pmod n$ (con $p-1$ en vez de $\varphi(n)$ si $n=p$ primo) |
| Existencia de solución de $ax\equiv b (n)$ | Tiene solución $\iff d = \operatorname{mcd}(a,n) \mid b$ |
| Cantidad de soluciones | Exactamente $d = \operatorname{mcd}(a,n)$ soluciones principales |
| Ecuación reducida | $\dfrac{a}{d}x \equiv \dfrac{b}{d} \pmod{\dfrac{n}{d}}$, con $\operatorname{mcd}(a/d,\,n/d)=1$ |
| Solución cuando $\operatorname{mcd}(a,n)=1$ | $x = a^{\varphi(n)-1} \cdot b \pmod n$ |
| Solución principal (caso general) | $x_0 = (a/d)^{\varphi(n/d)-1} \cdot (b/d) \bmod (n/d)$; las $d$ soluciones son $x_0,\ x_0+\frac{n}{d},\ \dots,\ x_0+(d-1)\frac{n}{d}$ |

## 5. Ejemplos resueltos paso a paso

### Ejemplo (a): ecuación con $\operatorname{mcd}(a,n) > 1$

Resolver $12x \equiv 18 \pmod{30}$.

**Paso 1 — mcd por Euclides.** $\operatorname{mcd}(12,30)$: $30 = 12\cdot 2 + 6$; $12 = 6 \cdot 2 + 0$. El último resto no nulo es $6$, así que $d = \operatorname{mcd}(12,30) = 6$.

**Paso 2 — ¿$d \mid b$?** $b = 18$, y $6 \mid 18$ (porque $18 = 6\cdot 3$). Sí divide, entonces hay solución, y hay exactamente $d=6$ soluciones principales módulo $30$.

**Paso 3 — simplificar.** Dividimos $a$, $b$ y $n$ por $d=6$:
$$\frac{12}{6}x \equiv \frac{18}{6} \pmod{\frac{30}{6}} \implies 2x \equiv 3 \pmod 5,$$
con $\operatorname{mcd}(2,5)=1$, como corresponde.

**Paso 4 — resolver la ecuación reducida.** $\varphi(5) = 4$ (porque $5$ es primo). Entonces:
$$x_0 = 2^{\varphi(5)-1}\cdot 3 \bmod 5 = 2^3 \cdot 3 \bmod 5 = 8 \cdot 3 \bmod 5 = 24 \bmod 5 = 4.$$
Verificación: $2 \cdot 4 = 8 \equiv 3 \pmod 5$. Correcto.

**Paso 5 — las $6$ soluciones principales módulo $30$.** Partiendo de $x_0 = 4$ y sumando $n/d = 30/6 = 5$ cada vez:
$$4,\ 9,\ 14,\ 19,\ 24,\ 29.$$

**Verificación cruzada:** $12 \cdot 4 = 48 \equiv 18 \pmod{30}$ (porque $48-18=30$). $12\cdot 9 = 108 \equiv 18 \pmod{30}$ (porque $108-18=90=30\cdot3$). Se puede chequear que las seis dan resto $18$.

### Ejemplo (b): resto de una potencia grande con Fermat

Calcular el resto de $7^{122}$ al dividir por $11$.

**Paso 1.** $11$ es primo y $\operatorname{mcd}(7,11)=1$, así que aplica el Pequeño Teorema de Fermat: $7^{10} \equiv 1 \pmod{11}$.

**Paso 2 — reducir el exponente módulo $p-1=10$.** Dividimos $122$ por $10$: $122 = 10 \cdot 12 + 2$.

**Paso 3.** $7^{122} = 7^{10\cdot 12 + 2} = (7^{10})^{12} \cdot 7^2 \equiv 1^{12} \cdot 7^2 \equiv 7^2 \pmod {11}$.

**Paso 4.** $7^2 = 49 = 44 + 5 \equiv 5 \pmod{11}$.

**Conclusión:** el resto de $7^{122}$ al dividir por $11$ es $5$.

### Ejemplo (c): resto de una potencia grande con Euler-Fermat (módulo no primo)

Calcular el resto de $8^{1{,}791{,}485}$ al dividir por $21$.

**Paso 1.** $21 = 3 \cdot 7$ no es primo, así que no puedo usar Fermat directamente; necesito Euler-Fermat. Verifico $\operatorname{mcd}(8,21)=1$ (sí, porque $8=2^3$ y $21=3\cdot7$ no comparten factores).

**Paso 2 — calcular $\varphi(21)$.** Por multiplicatividad, $\varphi(21) = \varphi(3)\cdot\varphi(7) = 2 \cdot 6 = 12$.

**Paso 3 — Euler-Fermat.** $8^{12} \equiv 1 \pmod{21}$.

**Paso 4 — reducir el exponente módulo $12$.** $1{,}791{,}485 = 12 \cdot 149{,}290 + 5$.

**Paso 5.** $8^{1{,}791{,}485} = \left(8^{12}\right)^{149{,}290} \cdot 8^5 \equiv 1^{149{,}290}\cdot 8^5 \equiv 8^5 \pmod{21}$.

**Paso 6 — calcular $8^5 \bmod 21$ con productos parciales.** $8^2 = 64 = 63 + 1 \equiv 1 \pmod{21}$ (porque $63 = 21\cdot 3$). Entonces:
$$8^5 = 8^2 \cdot 8^2 \cdot 8 \equiv 1 \cdot 1 \cdot 8 = 8 \pmod{21}.$$

**Conclusión:** el resto de $8^{1{,}791{,}485}$ al dividir por $21$ es $8$.

### Ejemplo (d): $\varphi(n)$ para un $n$ con tres factores primos distintos

Calcular $\varphi(105)$.

**Paso 1 — factorizar.** $105 = 3 \cdot 5 \cdot 7$ (tres primos distintos, cada uno con exponente $1$; es un número **libre de cuadrados**).

**Paso 2 — aplicar la fórmula general.**
$$\varphi(105) = 105 \cdot \left(1-\frac13\right)\left(1-\frac15\right)\left(1-\frac17\right) = 105 \cdot \frac23 \cdot \frac45 \cdot \frac67.$$

**Paso 3 — cuentas.** $105 \cdot \frac23 = 70$; $\ 70\cdot\frac45 = 56$; $\ 56 \cdot \frac67 = 48$.

**Verificación por multiplicatividad:** $\varphi(3)=2$, $\varphi(5)=4$, $\varphi(7)=6$, y $\varphi(105)=\varphi(3)\varphi(5)\varphi(7)=2\cdot4\cdot6=48$. Coincide.

**Conclusión:** $\varphi(105) = 48$.

## 6. Conectores con otras unidades

- **Con [[02-Relaciones-de-Equivalencia]]:** este es el vínculo más fuerte de toda la unidad. La congruencia módulo $n$ **es** la relación de equivalencia canónica que se estudia ahí: es reflexiva ($n \mid 0$), simétrica ($n\mid(a-b) \Rightarrow n\mid(b-a)$) y transitiva ($n\mid(a-b)$ y $n\mid(b-c) \Rightarrow n\mid(a-c)$, sumando). El conjunto $\mathbb{Z}_n$ definido acá **es exactamente** el conjunto cociente $\mathbb{Z}/{\equiv_n}$ de esa unidad, y las clases residuales $\bar x$ **son** las clases de equivalencia $[x]$, sin ninguna diferencia de fondo, solo de notación.

- **Con [[03-Redes-y-Algebras-de-Boole]]:** el conjunto de divisores $D_n$ con la relación de divisibilidad, $(D_n; \mid)$, es el objeto central de esa unidad, y ahí el ínfimo de dos elementos es su $\operatorname{mcd}$ y el supremo es su $\operatorname{mcm}$ — exactamente el mismo $\operatorname{mcd}$ que calculamos acá con Euclides para decidir si $ax\equiv b \pmod n$ tiene solución. Además, la factorización en primos distintos que usamos para $\varphi(n) = n\prod(1-1/p_i)$ es la misma que determina si $(D_n;\mid)$ es álgebra de Boole: eso ocurre precisamente cuando $n$ es **libre de cuadrados** (como el $n=105=3\cdot5\cdot7$ del Ejemplo (d)).

- **Con [[01-Razonamientos-Categoricos]]:** tanto el Pequeño Teorema de Fermat como su generalización de Euler-Fermat son proposiciones categóricas universales de la forma "para todo $a$ tal que $\operatorname{mcd}(a,n)=1$, se cumple $a^{\varphi(n)}\equiv 1 \pmod n$". Las demostraciones que dimos en la Sección 3 (la de la permutación de restos) son razonamientos deductivos formales, con la misma estructura de premisas encadenadas lógicamente hasta la conclusión que se analiza en esa unidad al validar silogismos y esquemas de inferencia.

- **Con [[05-Relaciones-de-Recurrencia]]:** el algoritmo de Euclides para calcular $\operatorname{mcd}(a,b)$ es, en sí mismo, una relación de recurrencia: $r_{k+1} = r_{k-1} \bmod r_k$, que arranca de $r_{-1}=a$, $r_0=b$ y termina en un número finito de pasos porque la sucesión de restos es estrictamente decreciente y acotada por abajo por $0$. Y la lista de soluciones principales de $ax \equiv b \pmod n$ — $x_0,\ x_0+\frac{n}{d},\ x_0+2\frac{n}{d},\dots$ — es una progresión aritmética de paso constante $n/d$, es decir, la solución explícita de una recurrencia de primer orden $x_{k+1} = x_k + n/d$ con $x_0$ como condición inicial.

## 7. Errores comunes y trampas del examen

1. **Usar el Pequeño Teorema de Fermat con un módulo que no es primo.** Fermat exige $p$ primo; si el módulo es compuesto (como $21 = 3\cdot 7$) hay que usar Euler-Fermat con $\varphi(n)$, nunca "$n-1$".
2. **Olvidar verificar $\operatorname{mcd}(a,n)=1$ antes de aplicar Euler-Fermat (o Fermat).** Si $a$ y $n$ (o $p$) no son coprimos, el teorema simplemente no aplica y $a^{\varphi(n)}$ puede no ser congruente a $1$.
3. **Confundir la cantidad de soluciones principales con el valor de las soluciones.** Que $d=\operatorname{mcd}(a,n)$ te diga que hay "3 soluciones" no te dice cuáles son: hay que resolver la ecuación reducida y después generar la progresión aritmética $x_0, x_0+n/d, \dots$.
4. **Calcular $\varphi(n)$ olvidando algún factor primo o usando un primo repetido de más.** Por ejemplo, para $n=60=2^2\cdot3\cdot5$ hay que usar los primos **distintos** $\{2,3,5\}$ una sola vez cada uno en el producto $\prod(1-1/p_i)$, aunque el $2$ aparezca elevado al cuadrado en la factorización.
5. **No reducir bien el exponente con el resto de la división.** El atajo es $a^k \equiv a^r \pmod n$ donde $r$ es el **resto** de dividir $k$ por $\varphi(n)$ (o por $p-1$), no el cociente; si se confunden cociente y resto el resultado da mal.
6. **Aplicar la fórmula de solución única $x=a^{\varphi(n)-1}b \bmod n$ sin haber simplificado primero cuando $\operatorname{mcd}(a,n)\ne 1$.** Esa fórmula solo vale tal cual cuando $a$ y $n$ ya son coprimos; si no lo son, primero hay que dividir por $d=\operatorname{mcd}(a,n)$ y trabajar con el módulo reducido $n/d$.
7. **Pensar que "$a\equiv b \pmod n$" implica $a=b$ o que hay una única forma de escribir la clase.** Una clase $\bar x$ tiene infinitos representantes; cualquier $y \equiv x \pmod n$ sirve para calcular, y el resultado va a ser el mismo (esto es justamente la buena definición demostrada en 3.3).
8. **Olvidar que $\varphi(1)=1$ y que $\varphi(p)=p-1$ solo vale si $p$ es primo**, tratando por error algún número compuesto pequeño (como $4$, $6$, $8$, $9$) como si fuera primo al calcular $\varphi$.

## 8. Preguntas de autoevaluación

1. Demostrá que la relación "$a \equiv b \pmod n$" es reflexiva, simétrica y transitiva usando la caracterización $n \mid (a-b)$.
2. ¿Por qué la propiedad de cancelación en congruencias necesita la hipótesis $\operatorname{mcd}(c,n)=1$? Dé un contraejemplo si esa hipótesis no se cumple.
3. Explicá con tus palabras por qué hace falta demostrar que $\bar a + \bar b$ está "bien definida" en $\mathbb{Z}_n$, y qué significaría que no lo estuviera.
4. Calculá $\varphi(360)$ mostrando la factorización prima completa y aplicando la fórmula general.
5. ¿Por qué el Pequeño Teorema de Fermat no se puede aplicar directamente para calcular el resto de $5^{200}$ al dividir por $15$? ¿Qué herramienta corresponde usar en ese caso?
6. Resolvé la ecuación $8x \equiv 12 \pmod{20}$ indicando cuántas soluciones principales tiene y hallándolas todas.
7. Enunciá y demostrá el paso clave de la demostración de Fermat donde se prueba que $\{a, 2a, \dots, (p-1)a\}$ es una permutación de $\{1,\dots,p-1\}$ módulo $p$.
8. ¿Qué relación hay entre el conjunto de clases inversibles de $\mathbb{Z}_n$ y el valor $\varphi(n)$?
9. Si $n$ es libre de cuadrados con $k$ factores primos distintos, ¿qué se puede decir de la estructura $(D_n; \mid)$ además de calcular $\varphi(n)$?
10. Mostrá, usando el algoritmo de Euclides, que $\operatorname{mcd}(252, 105)$ se calcula en una recurrencia de restos, y relacioná ese proceso con las relaciones de recurrencia de la Unidad 5.

## 9. Referencias

- Teoría original: `../04_congruencias_euler_fermat/readme.md`
- Ejercicios resueltos: `../ejercicios-resueltos/tema4_congruencias.md`

---
Volver al índice: [[00-Indice-Matematica-Discreta]]
