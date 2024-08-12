#### Apuntes de clases de Autómatas Finitos, 2024

#### Índice:

1. [Definición formal](#definicion-formal)
    1.1. [Agrupación de estados](#agrupacion-de-estados)
2. [Autómatas finitos deterministas](#automatas-finitos-deterministas)
    2.1. [Qué nos dice un autómata finito determinista?](#que-nos-dice-un-automata-finito-determinista)
    2.2. [Concepto de función de transición extendida](#concepto-de-funcion-de-transicion-extendida)

---

# Definición formal {#definicion-formal}

![Image](./imagenes/representacion-automata-finito.png)

<span style="color:#333333">Esta imagen representa una serie de estados y transiciones entre ellos.</span>

- <span style="color:#333333">**q0**: estado inicial donde recibe sus símbolos de entrada.</span>
- <span style="color:#333333">**q1**: estado intermedio.</span>
- <span style="color:#333333">**q2**: estado de aceptación. Si el autómata llega a este estado, se acepta la cadena de entrada.</span>
- <span style="color:#333333">**Transiciones**: son las flechas que unen los estados. Cada transición tiene un símbolo de entrada y un estado de destino.</span>

---

#### Agrupación de estados {#agrupacion-de-estados}

<span style="color:#333333">Podemos agrupar en conjuntos los estados de un autómata finito.</span>

- <span style="color:#333333">**Q**: conjunto de estados. = {q0, q1, q2}</span>
- <span style="color:#333333">**Σ**: alfabeto de entrada. = {0, 1}</span>
- <span style="color:#333333">**δ**: función de transición. = { 
        (q0, 1) -> q0, 
        (q0, 0) -> q1, 
        (q1, 0) -> q1, 
        (q1, 1) -> q2, 
        (q2, 0) -> q2, 
        (q2, 1) -> q2 
      }</span>
- <span style="color:#333333">**q0**: estado inicial.</span>
- <span style="color:#333333">**F**: conjunto de estados de aceptación. = {q2}</span>

<span style="color:#333333">Con todo esto, podemos definir un autómata finito **A**.</span>

- <span style="color:#333333">**A** = (Q, Σ, δ, q0, F)</span>  
  <span style="color:#333333">ó</span>  
- <span style="color:#333333">**A** = ({q0, q1, q2}, {0, 1}, δ, q0, {q2})</span>

---

# Autómatas finitos deterministas {#automatas-finitos-deterministas}

![Image](./imagenes/representacion-automata-finito.png)

<span style="color:#333333">Partimos de la definición de autómata finito determinista.</span>

    A = (Q, Σ, δ, q0, F)  
    ó
    A = ({q0, q1, q2}, {0, 1}, δ, q0, {q2})

<span style="color:#333333">Una forma de representar la función **δ** es mediante una tabla.</span>

| <span style="color:#333333">Edo</span> | <span style="color:#333333">δ</span>  | <span style="color:#333333">0</span>  | <span style="color:#333333">1</span>  |
|-----|----|----|----|
|  <span style="color:#333333">-></span> | <span style="color:#333333">q0</span> | <span style="color:#333333">q1</span> | <span style="color:#333333">q0</span> |
|     | <span style="color:#333333">q1</span> | <span style="color:#333333">q1</span> | <span style="color:#333333">q2</span> |
|  <span style="color:#333333">*</span> | <span style="color:#333333">q2</span> | <span style="color:#333333">q2</span> | <span style="color:#333333">q2</span> |

    Edo: Estado
    δ: Función de transición
    0, 1: Símbolos de entrada
    -> Estado inicial
    * Estado de aceptación

<span style="color:#333333">La tabla se rellena en función de la función de transición **δ**.</span>

    { 
        (q0, 1) -> q0, 
        (q0, 0) -> q1, 
        (q1, 0) -> q1, 
        (q1, 1) -> q2, 
        (q2, 0) -> q2, 
        (q2, 1) -> q2 
    }

---

#### Qué nos dice un autómata finito determinista? {#que-nos-dice-un-automata-finito-determinista}

![Image](./imagenes/representacion-automata-finito.png)

<span style="color:#333333">Esta imagen nos dice que si el autómata recibe una cadena de entrada, la procesa y llega a un estado de aceptación, entonces la cadena de entrada es aceptada.</span>

- <span style="color:#333333">**Ejemplo 1**:</span>

        Cadena de entrada: 01
        Estado inicial: q0
        Procesamiento: q0 -> q1 -> q2
        Estado de aceptación: q2
        Cadena aceptada.

- <span style="color:#333333">**Ejemplo 2**:</span>

        Cadena de entrada: 100
        Estado inicial: q0
        Procesamiento: q0 -> q1 -> q1
        Estado de aceptación: q2
        Cadena no aceptada.

<span style="color:#333333">Ya que se tiene una cadena de entrada que hay que recorrer en base a las funciones **δ** y si se llega a un estado de aceptación, entonces la cadena es aceptada, de lo contrario es rechazada.</span>

---

#### Concepto de función de transición extendida {#concepto-de-funcion-de-transicion-extendida}

<span style="color:#333333">La función de transición extendida **δ*** es una función que nos dice cómo se comporta el autómata finito determinista con una cadena de entrada.</span>

        W = 11100001001010
        δ*: (q0, W) = q2

<span style="color:#333333">Básicamente, escoge como entradas un estado y una cadena de entrada y devuelve un estado.</span>

<span style="color:#333333">Es importante la función de transición extendida porque nos permite llegar a la definición del lenguaje aceptado por un autómata finito determinista.</span>

        L(A) = { W | δ*(q0, W) ∈ F }

<span style="color:#333333">**L(A)** se le llama también "Lenguaje Regular" que son aceptados por un autómata finito determinista.</span>

---
