# TDA ABB

## Repositorio de Nicolas Ignacio Scopel - 111305 - nscopel@fi.uba.ar

- Para compilar:

```bash
gcc -std=c99 -Wall -Wconversion -Wtype-limits -pedantic -Werror -O2 -g src/*.c abb.c -o abb.c -I./include

```

- Para ejecutar:

```bash
./abb.c
```

- Para ejecutar con valgrind:
```bash
valgrind --leak-check=full ./abb.c
```
---
##  Funcionamiento

Este código implementa un árbol binario de búsqueda (ABB) junto con algunas funciones auxiliares para crear, insertar, buscar, eliminar, recorrer y destruir el árbol. Aquí hay una explicación general del funcionamiento y las estructuras utilizadas:

### Estructuras de datos:

1. **estructura_vectorial_t**: Esta estructura se utiliza para almacenar un array y su tamaño. Se usa para la implementación de la estructura de pruebas del árbol.

2. **nodo_abb_t**: Estructura que representa un nodo en el árbol binario de búsqueda. Contiene un puntero al elemento almacenado en el nodo, así como punteros a sus nodos hijo izquierdo y derecho.

3. **abb_t**: Estructura que representa un árbol binario de búsqueda. Contiene un puntero a la función de comparación de elementos, el tamaño del árbol y un puntero a la raíz del árbol.

### Funciones principales:

1. **abb_crear**: Crea un nuevo árbol binario de búsqueda. Toma como argumento una función de comparación de elementos.

2. **abb_insertar**: Inserta un elemento en el árbol manteniendo la propiedad de orden. Utiliza una función auxiliar recursiva para encontrar la posición correcta.

3. **abb_buscar**: Busca un elemento en el árbol utilizando una función auxiliar recursiva.

4. **abb_quitar**: Busca y elimina un elemento del árbol. Puede eliminar nodos con cero, uno o dos hijos.

5. **abb_destruir**: Libera la memoria utilizada por el árbol. Utiliza una función auxiliar recursiva para eliminar todos los nodos del árbol.

6. **abb_con_cada_elemento**: Recorre el árbol en un orden específico (inorden, preorden o postorden) y llama a una función dada con cada elemento.

7. **abb_recorrer**: Recorre el árbol en un orden específico (inorden, preorden o postorden) y almacena los elementos en un array hasta que se llene o se completen todos los elementos del árbol.

### Funciones auxiliares:

1. **funcion_insertar_recursiva**: Función auxiliar utilizada por `abb_insertar` para insertar recursivamente un elemento en el árbol.

2. **funcion_aux_buscar**: Función auxiliar utilizada por `abb_buscar` para buscar recursivamente un elemento en el árbol.

3. **buscar_nodo_y_padre**: Función auxiliar utilizada por `abb_quitar` para encontrar el nodo a eliminar y su padre.

4. **eliminar_nodo**: Función auxiliar utilizada por `abb_quitar` para eliminar un nodo del árbol.

5. **funcion_aux_destruir**: Función auxiliar utilizada por `abb_destruir` para destruir recursivamente todos los nodos del árbol.

6. **funcion_aux_destruir_todo**: Función auxiliar utilizada por `abb_destruir_todo` para destruir recursivamente todos los nodos del árbol y aplicar una función destructora a cada elemento.

7. **Funciones de recorrido (inorden, preorden, postorden)**: Funciones auxiliares utilizadas por `abb_con_cada_elemento` y `abb_recorrer` para recorrer el árbol en el orden especificado.

Durante el desarrollo del trabajo práctico, encontré algunos desafíos al implementar la función de inserción en el vector. Inicialmente, mi idea era reutilizar la función iteradora que ya tenía implementada para recorrer el árbol binario de búsqueda. Sin embargo, me encontré con varios errores al intentar adaptar esta función para la inserción en el vector. Después de intentar resolver estos problemas durante un tiempo, decidí optar por una solución más directa, creando tres funciones adicionales específicamente para la inserción en el vector. Aunque esta solución funcionó, no considero que sea la más óptima, ya que idealmente deberíamos buscar reutilizar el iterador interno del árbol para maximizar la eficiencia y la claridad del código.

Otro desafío que enfrenté fue al implementar la función para eliminar un nodo del árbol cuando el elemento a eliminar era un puntero nulo. Originalmente, intenté reutilizar la función abb_buscar para determinar si el elemento estaba presente en el árbol antes de eliminarlo. Sin embargo, esto resultó problemático, ya que la función abb_buscar no maneja explícitamente el caso del elemento nulo. Para resolver este problema, tuve que crear una función booleana adicional que verificara si el elemento estaba presente en el árbol antes de intentar eliminarlo. Aunque esta solución funcionó, creo que sería más elegante si pudiéramos reutilizar la función existente abb_buscar y manejar correctamente el caso del puntero nulo dentro de esa función.

En resumen, aunque enfrenté algunos desafíos al implementar estas funciones, pude encontrar soluciones alternativas que permitieron que mi programa funcionara correctamente. Sin embargo, reconozco que hay margen para mejorar la eficiencia y la claridad del código, especialmente buscando formas de reutilizar funciones existentes en lugar de crear nuevas.

## Respuestas a las preguntas teóricas

### Árbol Binario (AB):

**Un Árbol Binario** es una estructura de datos jerárquica en forma de árbol en la que cada nodo tiene como máximo dos hijos, denominados hijo izquierdo y hijo derecho. Cada nodo puede contener un elemento de datos y apuntadores a sus hijos. Si un hijo está ausente, el apuntador correspondiente puede ser nulo. Los árboles binarios se utilizan comúnmente en informática para organizar y gestionar datos de manera eficiente, ya que permiten una rápida búsqueda, inserción y eliminación de elementos.

### Árbol Binario de Búsqueda (ABB):

**Un Árbol Binario de Búsqueda (ABB)** es una variante del Árbol Binario en la que se impone una restricción adicional: para cada nodo, todos los elementos en el subárbol izquierdo son menores que el elemento del nodo, y todos los elementos en el subárbol derecho son mayores que el elemento del nodo. Esta propiedad hace que la búsqueda, inserción y eliminación en un ABB sean altamente eficientes, ya que permite realizar operaciones en tiempo logarítmico en promedio. Los ABB se utilizan ampliamente en aplicaciones donde se necesita un acceso rápido a los datos, como en la implementación de diccionarios, bases de datos y algoritmos de búsqueda y ordenamiento.

### Inserción:

<div align="center">
<img width="50%" src="img/ABB_Insercion.PNG">
</div>

**Comparación con el nodo raíz (4):**
- Empezamos comparando el elemento que queremos insertar (8) con el nodo raíz (4).
- Como 8 es mayor que 4, nos movemos al hijo derecho del nodo raíz.

**Movimiento al subárbol derecho:**
- Ahora estamos en el nodo con valor 6.

**Comparación con el nodo actual (6):**
- Comparamos 8 con el valor del nodo actual (6).
- Como 8 es mayor que 6, nos movemos al hijo derecho del nodo actual.

**Movimiento al subárbol derecho:**
- Ahora estamos en el nodo con valor 7.

**Comparación con el nodo actual (7):**
- Comparamos 8 con el valor del nodo actual (7).
- Como 8 es mayor que 7 y el nodo actual no tiene un hijo derecho, sabemos que debemos insertar el elemento 8 como el hijo derecho de este nodo.

**Inserción del nuevo nodo (8):**
- Insertamos el elemento 8 como hijo derecho del nodo 7.
  
Así es como se realiza la inserción del elemento 8 en el ABB. La inserción en un ABB implica encontrar el lugar adecuado para el nuevo elemento siguiendo las comparaciones basadas en el valor de los nodos, y luego insertarlo como un nuevo nodo en la posición correcta del árbol para mantener la propiedad de orden de un ABB.

En un ABB bien balanceado, la altura del árbol tiende a ser logarítmica en función del número de nodos, lo que resulta en una complejidad de inserción de O(log n), donde n es el número de nodos en el árbol. Esto significa que, en promedio, la inserción tomará un tiempo proporcional al logaritmo del número de elementos en el árbol.

Sin embargo, si el árbol está desbalanceado, la inserción podría requerir recorrer una cantidad lineal de nodos en el peor de los casos, lo que llevaría a una complejidad de O(n), donde n es el número de nodos en el árbol. Esto podría ocurrir, por ejemplo, si los elementos se insertan en orden ascendente o descendente, lo que daría como resultado un árbol degenerado en una lista enlazada.

En resumen, la complejidad de la inserción en un ABB puede variar dependiendo de la estructura del árbol, pero en promedio es eficiente, con una complejidad de O(log n) en un árbol bien balanceado.

### Busqueda:

<div align="center">
<img width="70%" src="img/ABB_Busqueda.PNG">
</div>

**Ahora, vamos a realizar una búsqueda en este árbol para encontrar el número 13:**

**Comparación con el nodo raíz (4):**
- Empezamos comparando el número buscado (13) con el nodo raíz (4).
- Como 13 es mayor que 4, nos movemos al hijo derecho del nodo raíz.

**Movimiento al subárbol derecho:**
- Ahora estamos en el nodo con el número 12.

**Comparación con el nodo actual (12):**
- Comparamos el número buscado (13) con el número en el nodo actual (12).
- Como 13 es mayor que 12, nos movemos al hijo derecho del nodo actual.

**Movimiento al subárbol derecho:**
- Ahora estamos en el nodo con el número 15.

**Comparación con el nodo actual (15):**
- Comparamos el número buscado (13) con el número en el nodo actual (15).
- Como 13 es menor que 15, nos movemos al hijo izquierdo del nodo actual.

**Movimiento al subárbol izquierdo:**
- Ahora estamos en el nodo con el número 13.

**Comparación con el nodo actual (13):**
- Hemos encontrado el número que estábamos buscando.

Entonces, la búsqueda en este árbol binario de búsqueda para el número 13 implicó seguir un camino descendente desde el nodo raíz, tomando decisiones basadas en comparaciones de valores, hasta encontrar el nodo que contenía el valor buscado.

La complejidad de la búsqueda en un ABB es O(n), donde n es la altura del árbol. En este caso, la altura del árbol es relativamente baja porque es un árbol balanceado, por lo que la búsqueda es bastante eficiente.

### Eliminación:
#### Eliminación hoja 
<div align="center">
<img width="50%" src="img/ABB_eliminacion_hoja.PNG">
</div>

**Comenzamos desde la raíz**:  

**Búsqueda del nodo 8**:  
   - Buscamos el nodo con el valor 8 en el árbol.

**Identificación del nodo 8 como hoja**:  
   - El nodo 8 es una hoja, es decir, no tiene hijos.

**Eliminación del nodo 8**:  
   - Eliminamos el nodo 8 del árbol.

Así es como se realiza la eliminación de la hoja 8 en el árbol. La eliminación de una hoja en un árbol binario implica simplemente eliminar el nodo hoja del árbol, ajustando los enlaces adecuadamente para mantener la estructura del árbol.

Eliminar una hoja en un árbol binario de búsqueda es relativamente sencillo, ya que solo implica ajustar los enlaces del nodo padre para eliminar el nodo hoja. La complejidad es O(h).

#### Eliminación nodo con hijos 
<div align="center">
<img width="50%" src="img/ABB_eliminacion_nodo_hijos.PNG">
</div>

**Comenzamos desde la raíz**:  

**Búsqueda del nodo con valor 12**:  
   - Buscamos el nodo con el valor 12 en el árbol.

**Identificación del nodo 12 con hijos**:  
   - El nodo 12 tiene dos hijos.

**Búsqueda del sucesor inmediato**:  
   - Para eliminar un nodo con dos hijos, necesitamos encontrar su sucesor inmediato. El sucesor inmediato es el nodo más pequeño en el subárbol derecho del nodo que estamos eliminando.

**Sucesor inmediato del nodo 12**:  
   - El sucesor inmediato del nodo 12 es el nodo con valor 13.

**Reemplazo del nodo 12 con su sucesor inmediato 13**:  
   - Reemplazamos el valor del nodo 12 con el valor del sucesor inmediato, es decir, 13.

**Eliminación del nodo 13 del subárbol derecho**:  
   - Ahora, eliminamos el nodo 13, que se convierte en la nueva hoja o nodo con un solo hijo.

Así es como se realiza la eliminación del nodo con hijos 12 en el árbol. La eliminación de un nodo con dos hijos en un árbol binario implica encontrar su sucesor inmediato y reemplazar el nodo a eliminar con este sucesor. Luego, se elimina el sucesor inmediato del subárbol derecho, manteniendo así la estructura y la propiedad de orden del árbol.

Eliminar un nodo con dos hijos es un poco más complejo. Implica encontrar y reemplazar el valor del nodo con su sucesor inmediato (el menor valor en el subárbol derecho), y luego eliminar este sucesor. La complejidad también es O(h).

### Grafico de memoria
<div align="center">
<img width="100%" src="img/memoria.png">
</div>

