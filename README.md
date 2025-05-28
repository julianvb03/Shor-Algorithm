# Algoritmo de Shor

### Objetivo:
Descomponer un número dado en sus factores primos (problema con gran importancia en la criptografía).
$$
N = p \cdot q
$$
## Principios matematicos
### Primer principio
Para lograr este objetivo se usara como herramienta principal aritmetica modular, un concepto particularmente importante para este fin es el de raiz cuadrada no trivial modulo N, matematicamente expresa lo siguiente.
$$
X^2\equiv1(N) \\
X \in (2, N-2)
$$
El algoritmo de Shor se resume principalmente en 2 cosas, la primera de ella es  dado un número `N` siendo el producto de 2 número primos `p` y `q`, encontrar la raiz cuadrada no trivial de `N` es equivalente a encontrar `p` y `q`
$$
X^2 \equiv 1 (N) \\
X^2 - 1 \equiv 0 (N) \\
(X-1)(X+1) \equiv 0 (N) \\
(X-1)(X+1) = k \cdot N 
$$
Esa expresión factorizada es la clave para encontrar tanto a `p` como a `q`, siguiendo el siguiente razonamiento, primero descompongamos ambas expresiones en factores y usemos la definición de raiz cuadrada no trivial.
$$
(X-1) = X_1 \cdot X_2 \cdot X_3 \cdot ...\cdot X_n \\
(X+1) = Y_1 \cdot Y_2 \cdot Y_3 \cdot ...\cdot Y_n  \\
\text{Además puesto a que X es raiz cuadrada no trivial} \\
(X-1) \lt N \\
(X+1) \lt N \\
$$
Que ambos factores no puedan ser multiplos de `N` nos deja solo una alternativa, que dentro de los factores de `(X-1)` y `(X+1)` se encuentren tanto `p` como `q`, uno en cada uno, y podemos encontrarlo hayando el maximo comun divisor, que es una operación relativamente sencilla.
$$
mcd(X-1,N)=q \\
mcd(X+1,N)=p
$$
Lo anterior es solo ilustrativo no es como que importe quien es `p` o `q` volviendonos a una expresión anterior todos los demás factores son los que componen la `k`.
### Segundo principio
Siguiendo con lo anterior y para lograr encontrar dicha `X` usamos otro concepto importante. El orden de `m` module `N`, que significa que al elevar `r` veces `m` el resto va a ser 1 cuando se divida entre `N`.
$$
m^r \equiv 1 (N)
$$
Esto es fundamental puesto que nos lleva al siguiente proceso en el algoritmo, al ser una función periodica podemos plantear nuestro problema como encontrar `i (el periodo)` para la siugiente función.
$$
f(i) = m^i(N)
$$
Esto nos lleva a lo siguiente, si nosotros cogemos un número al azar entre `(2, N-2)` y el periodo nos da `2`, estariamos cumpliendo la definición de la raiz cuadrada no trivial y abriamos encontrado satisfactorimente ese `X` que buscabamos, que en conjunto con el principio 1 nos permite obtener tanto a `p` como a `q`. Además lo que permite que el algoritmo sea consistente es que si conseguimos un `r` par ya con eso es suficiente, ya que podemos hacer algo como lo siguiente.
$$
m^8 \equiv 1(N) \\
(m^4)^2 \equiv 1(N) \\
$$

## Computación cuantica en el algoritmo
Para poder ejecutar lo planteado anteriormente hay una fase fundamental del proceso, este es encontrar el periodo de una función, y es precisamente este aspecto el que se realiza con computación cuantica, el proceso general es el siguiente.
