## 1. De ejemplos de otras estructuras de datos no vistas en esta semana, y sus respectivos ejemplos de uso. (maximo 3)

## 2. Problema (Usar pilas)

Dada un vector, imprima el Siguiente Gran Elemento (SGE) para cada elemento. El siguiente elemento mayor para un elemento x es el primer elemento mayor en el lado derecho de x en el conjunto. Elementos para los que no existe un elemento mayor, considere el siguiente elemento más grande como -1.

Ejemplos: 
* Para cualquier vector, el elemento situado más a la derecha siempre tiene el siguiente elemento más grande como -1. 
* Para un vector ordenado en orden decreciente, todos los elementos tienen el siguiente elemento más grande como -1. 
* Para el vector de entrada {4, 5, 2, 25}, los siguientes elementos mayores para cada elemento son los siguientes.
Siguiente Gran Elemento:
```c++
   4 - 5
   5 - 25
   2 - 25
   25 - -1
```
* Para el vector de entrada {13, 7, 6, 12}, los siguientes elementos mayores para cada elemento son los siguientes.
Siguiente Gran Elemento:
```c++
   13 - -1
   7 - 12
   6 - 12
   12 - -1
```
