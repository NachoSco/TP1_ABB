# TDA ABB

## Repositorio de (Nombre Apellido) - (Padrón) - (Mail)

- Para compilar:

```bash
línea de compilación
```

- Para ejecutar:

```bash
línea de ejecución
```

- Para ejecutar con valgrind:
```bash
línea con valgrind
```
---
##  Funcionamiento

Explicación de cómo funcionan las estructuras desarrolladas en el TP y el funcionamiento general del mismo.

Aclarar en esta parte todas las decisiones que se tomaron al realizar el TP, cosas que no se aclaren en el enunciado, fragmentos de código que necesiten explicación extra, etc.

Incluír **EN TODOS LOS TPS** los diagramas relevantes al problema (mayormente diagramas de memoria para explicar las estructuras, pero se pueden utilizar otros diagramas si es necesario).

### Por ejemplo:

El programa funciona abriendo el archivo pasado como parámetro y leyendolo línea por línea. Por cada línea crea un registro e intenta agregarlo al vector. La función de lectura intenta leer todo el archivo o hasta encontrar el primer error. Devuelve un vector con todos los registros creados.

<div align="center">
<img width="70%" src="img/diagrama1.svg">
</div>

En el archivo `sarasa.c` la función `funcion1` utiliza `realloc` para agrandar la zona de memoria utilizada para conquistar el mundo. El resultado de `realloc` lo guardo en una variable auxiliar para no perder el puntero original en caso de error:

```c
int *vector = realloc(vector_original, (n+1)*sizeof(int));

if(vector == NULL)
    return -1;
vector_original = vector;
```


<div align="center">
<img width="70%" src="img/diagrama2.svg">
</div>

---

## Respuestas a las preguntas teóricas

### Busqueda

<div align="center">
<img width="70%" src="img/diagrama2.svg">
</div>

Ahora, vamos a realizar una búsqueda en este árbol para encontrar el número 13.

1. Comenzamos en el nodo raíz, que contiene el número 4.
2. Comparamos el número que estamos buscando (13) con el número en el nodo actual (4).
   - Como 13 es mayor que 4, nos movemos al hijo derecho del nodo actual.
3. Ahora estamos en el nodo con el número 12.
4. Comparamos el número que estamos buscando (13) con el número en el nodo actual (12).
   - Como 13 es mayor que 12, nos movemos al hijo derecho del nodo actual.
5. Ahora estamos en el nodo con el número 15.
6. Comparamos el número que estamos buscando (13) con el número en el nodo actual (15).
   - Como 13 es menor que 15, nos movemos al hijo izquierdo del nodo actual.
7. Ahora estamos en el nodo con el número 13.
8. Comparamos el número que estamos buscando (13) con el número en el nodo actual (13).
   - Hemos encontrado el número que estábamos buscando.

Entonces, la búsqueda en este árbol binario de búsqueda para el número 13 implicó seguir un camino descendente desde el nodo raíz, tomando decisiones basadas en comparaciones de valores, hasta encontrar el nodo que contenía el valor buscado.

La complejidad de la búsqueda en un ABB es O(h), donde h es la altura del árbol. En este caso, la altura del árbol es relativamente baja porque es un árbol balanceado, por lo que la búsqueda es bastante eficiente.
