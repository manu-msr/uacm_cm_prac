# Estructuras de datos

## OBJETIVO

- Comprender el uso de los distintos tipos de estructuras de datos que provee Kotlin.
- Usar las operaciones y formas más más comunes sobre estructuras de datos en en Kotlin.

## REQUISITOS

1. Completar la  Sesión 1 y especialmente haber comprendido los temas:
    - Tipos de datos.
    - Operadores.

## DESARROLLO

Una estructura de datos generalmente contiene una cantidad de objetos (este número también puede ser cero) del mismo tipo. Los objetos en una estructura se llaman elementos. Por ejemplo, todos los estudiantes en un departamento forman una estructura de datos que se puede usar para calcular su edad promedio. Kotlin nos ofrece las siguientes estructuras:

### Listas
Una **lista** es una estructura ordenada con acceso a elementos por índices, números enteros que reflejan su posición. Los elementos pueden aparecer más de una vez en una lista. Un ejemplo de una lista es una oración: es un grupo de palabras, su orden es importante y pueden repetirse.
    Los elementos en una lista están ordenados y sus índices van desde 0 que es el primer elemento hasta`list.size - 1` que es el último elemento.

>Declaración de una lista.
```kotlin
    val numeros = listOf("uno", "dos", "tres", "cuatro", "cinco")
```
Una lista puede imprimirse directamente

```kotlin
println(numeros)
```
Y se muestra de la siguiente forma:

> [uno, dos, tres, cuatro, cinco]

Es realmente sencillo hacerlo, pero veamos qué hay detrás de la lista en cuanto a los índices se refiere.

```kotlin
    println("Numero de elementos: ${numeros.size}")
    println("Segundo elemento: ${numeros.get(1)}") 
    println("Cuarto elemento: ${numeros[3]}")
    println("Ultimo elemeto: ${numeros.get(numeros.size - 1)}")
    println("Índice del elemento \"cuatro\": ${numeros.indexOf("cuatro")}")
```

Si usamos este tipo **List<T>** tenemos que saber que no es mutable, es decir **no podemos alterar sus elementos**, para ello tenemos **MutableList<T>** lo cual representa una lista sobre la cual sí podemos agregar, eliminar o modificar sus elementos:

```kotlin

    val numeros = mutableListOf(1, 2, 3, 4)
    //Abrebar nuevos elementos
    numeros.add(5)
    //Remover elementos
    numeros.removeAt(1)
    //Modificar elementos
    numeros[0] = 0
    
    println(numeros)

```

### Conjuntos

Un **set** es una colección que regresa una serie de elementos **únicos**, es decir, que no se repiten. Por ejemplo, el alfabeto es un **set** de letras.

Un conjunto almacena elementos únicos, incluso con los valores null.
Para definiri un conjunto usamos la funcion setOf(). Esto nos creará una instancia de un conjunto, en el cual no podremos realizar operaciones de escritura. Para realizar operaciones de escritura sobre un set lo creamos con la funcion mutableSetOf()

>Creando sets.
```kotlin
    //Creamos dos sets con valores únicos y desordenados en comparación entre ambos.
    val numSet: Set<Int> = setOf(0, 1, 2, 3, 4, 5)
    val reverseNumSet: Set<Int> = setOf(5, 4, 3, 2, 1, 0)

    //Creamos un set mutable
    var names: Set<String> = mutableSetOf("Nombre 1", "Nombre 2")
```
Si comparamos los dos sets inmutables del principio del ejemplo anterior, el resultado será true, ya que no importa el orden de los elementos.

### Diccionarios 
El mapa (o diccionario) es un conjunto de pares clave-valor. Las claves son únicas y cada una de ellas se asigna exactamente a un valor. Los valores pueden ser duplicados. Los diccionarios son útiles para almacenar conexiones lógicas entre objetos, por ejemplo, la identificación de un empleado y su posición.

Para crear una colección Map inmutable o de solo lectura en Kotlin, usamos la función **mapOf()**. Creamos un mapa con esta función dándole una lista de pares. El primer valor es la clave, y el segundo es el valor. Llamar a esta función devuelve una interfaz tipo **Kotlin Map**.

Supongamos que queremos crear un mapa en el que asociemos el nombre de usuario con la edad, es decir, cada edad corresponde a un nombre de usuario. Recordando tipos de datos, es importante notar que el nombre de usuario es un String y que la edad es un Int, de modo que nuestro mapa quedaría de la siguiente forma.
```kotlin
    val nombresAEdades: Map<String, Int> = mapOf("usuario_1" to 20, "usuario_2" to 23)
```
Observa que como definimos nuestro mapa, el primer elemento es un **String** y el segundo es un **Int**, por esto, cuando creamos la instancia de nuestro mapa con la función mapOf() asignamos un elemento Int a una clave String con la palabra reservada **to**.

Un punto importante es que cuando iteramos sobre un mapa, o sea, recorrer cada uno de sus elementos, podremos acceder tanto a la clave como al valor, un ciclo for nos permite hacerlo de la siguiente forma.
>Iterando un mapa
```kotlin
    for ((key, value) in nombresAEdades) {
        println("$key tiene $value años")
    }
```
Al igual que las listas (list) y los conjuntos (set) la función mapOf() nos crea un mapa inmutable. Si queremos hacer operaciones de escritura sobre un mapa tenemos que crearlo con la función mutableMapOf().
