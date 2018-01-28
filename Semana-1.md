# Introducción

Hoy en día hacemos uso de dispositivos digitales en casi todo lo que hacemos, pero antes de que existiera si quiera el primer computador, los algoritmos ya estaban allí, y estos son el alma de la computación como la conocemos actualmente.

Para poder entender este material es necesario como mínimo conocer un lenguaje de programación y tener fundamentos básicos de programación como variables,instrucciones de control, bucles y funciones.

El lenguaje usado para los ejemplos será C++, sin embargo esto no quiere decir que los algoritmos sólo pueden escribirse en dicho lenguaje, puede usar cualquiera de su preferencia como Python, Java, C, la eficacia de un algoritmo es independiente del lenguaje usado.

No es necesario que aprendas C++ pero si deseas referencias de este lenguaje puedes investigar más de ello en los siguientes enlaces:

* http://www.cplusplus.com/doc/tutorial/
* https://www.cprogramming.com/tutorial/c++-tutorial.html
* http://www.learncpp.com/
* https://www.tutorialspoint.com/cplusplus/

En caso de no tener un compilador para C++ pueden usar:

* https://ideone.com/
* https://www.onlinegdb.com/online_c++_compiler
* http://cpp.sh
* https://www.codechef.com/ide

Pero __¿Qué es un algoritmo?__

La respuesta más común sería es una serie de pasos para lograr resolver un problema.  Sin embargo esto también abarcaría tareas de la vida cotidiana como leer una receta para cocinar.

Algunos algoritmos famosos como hacer videollamadas a cualquier parte del mundo haciendo uso de algoritmos de compresión de audio y video. O cuando hacemos uso de Uber y este escoge la ruta más corta para llegar a nuestro destino más rápido es otro ejemplo, existen numerosos ejemplos de usos de algoritmos en nuestra vida cotidiana.

Por ello nos vamos a enfocar en algoritmos de programación, que tienen ciertas carácterísticas que lo diferencian.

## Carácteristica de un algoritmo

No toda secuencia de pasos puede ser llamada un algoritmo. Las características fundamentales que debe cumplir todo algoritmo son:

* Un algoritmo debe ser preciso e indicar el orden de realización de cada paso.
* Un algoritmo debe estar definido. Si se sigue un algoritmo dos veces, se debe obtener el mismo resultado cada vez.
* Un algoritmo debe ser finito. el algoritmo se debe terminar en algún momento; o sea, debe tener un número finito de pasos.

## ¿Por qué debemos aprender algoritmos?

Los algoritmos son la razón por la cuál actualmente programamos, en una computadora cualquier cosa no trivial usa algoritmos para realizar su trabajo. Sin embargo los algoritmos no sólo deben solucionar un problema o realizar una tarea, sino tambien debe hacerlo de manera eficiente ya que los recursos computacionales varían mucho por cada dispositivo, puede ser desde un microcontrolador hasta una supercomputadora, por ello aprender algoritmos nos da la capacidad de resolver un problema sin importar el hardware a usar, valiendonos solo de nuestra capacidad de razonamiento.

Ahora ¿Cómo medimos la eficacia de un algoritmo?

## Complejidad Algoritmica

Para saber que tan eficaz y rápido es un algoritmo definimos la complejdad como una función numérica __T(n)__ donde __n__ es el tamaño de nuestra entrada y __T(n)__ es el tiempo de ejecución usado para procesar dicha entrada. Un algoritmo puede tomar tiempos distintos con el mismo tamaño de entrada dependiendo de factores como: velocidad del procesador, conjunto de instrucciones, velocidad del disco, etc.

La manera más común para estimar la eficiencia de un algoritmo es usando la notación asintótica.

### Notación Asintótica

El objetivo de la complejidad computacional es clasificar algoritmos de acuerdo a su desempeño y para ello haremos uso de la notación asintótica que es una manera matemática de representar la eficacia de dicho algoritmo.

Como dijimos anteriormente vamos a representar el tiempo __T(n)__ usando la notación __"Big-O"__ para expresar la complejidad del tiempo de ejecución de un algoritmo.

#### Definición de "Big-O"

La notación "Big-O" describe el __peor caso__ y puede ser usado para describir el tiempo de ejecución requerido o el espacio usado (en memoria o en el disco) por un algoritmo.

<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/time-complexity.png">
</p>

Como podemos observar, a medida que aumenta la complejidad, el tiempo necesario para completar la tarea crece mucho, pudiendo llegar a aumentar enormemente en algunos casos en cuanto hay más datos a manejar.

En la siguiente tabla se tiene como se representan algunos funciones con la notación "Big-O"

funcion | Notación O() 
--- | --- 
T(n) = 1 | O(1)
T(n) = 5124 | O(1)
T(n) = 3n + 5 | O(n)
T(n) = 92n + 2 | O(n)
T(n) = 2*log(n) + 12 | O(log(n))
T(n) = n*log(n) + log(n) + 12 | O(n*log(n))
T(n) = 4n^2 + 7 | O(n^2)
T(n) = 5n^2 + 6n + 123 | O(n^2)
T(n) = n^3 + log(n) + 12 | O(n^3)
T(n) = 2^n + n^10 + log(n) | O(2^n)

Lo interesante de esta notación es que nos permite comparar varios algoritmos equivalentes sin preocuparnos de hacer pruebas de rendimiento que dependen del hardware utilizado. Es decir, ante resultados equivalentes podemos elegir el algoritmo que sea más eficaz, que lo será siempre independientemente del hardware si el conjunto de datos es lo suficientemente grande.


Ahora veamos algunos ejemplos de casos de tiempo de ejecución.

### Tiempo Constante O(1)

Un algoritmo se dice que correrá a tiempo constante si requiere el mismo tiempo independientemente del tamaño de entrada.

[código](https://ideone.com/Qbaz9F)

```c++
#include <iostream>
using namespace std;

// Esta función devuelve el primer elemento de un array
// Vemos que se ejecutará en tiempo constante ya que no importa si el array tiene el tamaño de un millón de entrada.
int returnFirstElement (int ArrayExample[]){
    return ArrayExample[0];
}

int main () {
    int arr[] = {3, 8, 20, 34, 52, 322};
    int result = returnFirstElement(arr);
    cout<<"El primer numero del array es: "<< result <<endl;

    return 0;
}
```

### Tiempo Lineal O(n)

Se dice que un algoritmo correrá con tiempo lineal si el tiempo de ejecución es directamente proporcional al tamaño de entrada.

En el siguiente ejemplo es el algoritmo de búsqueda lineal:

[codigo](https://ideone.com/n4laat)

```c++
#include <iostream>
using namespace std;

// Esta función devolverá la posición en la que se encuentra el número en el array arr[]
// n es el tamaño del array
// X es el número a buscar
int LinearSearch (int arr[],int n, int x){
    int i;
    // Hará un recorrido por todo el array de tamaño "n" en el peor de los casos
    for (i=0; i<n; i++) {
        if(arr[i] == x){
            return i;
        }
    }
    return -1;
}

int main (){
    int arr[] = {3, 8, 20, 34, 52, 322};
    // de esta forma obtenemos el tamaño del array
    int n = sizeof(arr)/ sizeof(arr[0]);
    int x = 52;
    int result = LinearSearch(arr, n, x);

    if(result == -1){
        cout<<"El numero no se encuentra en el array"<<endl;
    }else{
        cout<<"El numero se encuentra en la posición: "<< result <<endl;
    }

    return 0;
}
```

### Tiempo Logaritmico O(log n)

Se dice que un algoritmo correrá en tiempo logaritmico si el tiempo de ejecución es proporcional al logaritmo del tamaño de entrada.

El siguiente ejemplo es el algoritmo de [búsqueda binaria](https://es.wikipedia.org/wiki/B%C3%BAsqueda_binaria#Rendimiento):

[código](https://ideone.com/HQ2ac3)

```c++
#include <iostream>
using namespace std;

// Algoritmo de búsqueda binaria en un intervalo arr[l..r] nos retorna la posición de x en el array 
// arr es el array
// l es posición izquierda
// r es posición derecha
// x es el número a buscar
int binarySearch (int arr[],int l,int r, int x)
{
    if(r >= l)
    {
        int mid = l + (r-l)/2;

        if( arr[mid] == x)
            return mid;
        // Si el elemento es menor que el elemento del medio 
        //entonces debe estar en el lado izquierdo del subarray
        if( arr[mid] > x)
            return binarySearch(arr,l,mid-1,x);
        // En caso contrario estará en el lado derecho del subarray
        return binarySearch(arr,mid+1,r,x);
    }
    // Si el elemento no se encuentra en el array
    return -1;
}

int main () {
    int arr[] = {3, 8, 20, 34, 52, 322};
    int n = sizeof(arr)/ sizeof(arr[0]);
    int x = 34;
    int result = binarySearch(arr, 0, n-1, x);

    if(result == -1){
        cout<<"El numero no se encuentra en el array"<<endl;
    }else{
        cout<<"El numero se encuentra en la posición: "<< result <<endl;
    }
    return 0;
}
```
### Tiempo cuadrático O(n^2)

Se dice que un algoritmo correrá en tiempo cuadrático si el tiempo de ejecución es proporcional al cuadrado del tamaño de entrada.

Esto es común en algoritmos que involucran iteraciones anidadas sobre el conjunto de datos. Mientras más anidada sea la iteración el resultado va creciendo en O(n^3), O(n^4), etc.

[código](https://ideone.com/xBv7rI)

```c++
#include <iostream>
using namespace std;
// Esta función verifica si un array contiene duplicados
bool contieneDuplicados(int arr[], int n){
    int i,j;
    // Este bucle hace n*n recorridos para encontrar duplicados
    for (i=0;i<n;i++){
        for (j=0;j<n;j++){
            if( i==j )
                continue;
            if( arr[i] == arr[j])
                return true;
        }
    }
    return false;
}

int main () {
    int arr[] = {3, 8, 20, 34, 52, 322, 322};
    int n = sizeof(arr)/ sizeof(arr[0]);
    bool result = contieneDuplicados(arr, n);

    if(result == false){
        cout<<"No hay duplicados en el array"<<endl;
    }else{
        cout<<"Hay duplicados en el array"<<endl;
    }
    return 0;
}
```

### Tiempo Exponencial O(2^n)

Se dice que un algoritmo correrá en tiempo exponencial si el tiempo de ejecución crece de manera exponencial es decir que su complejidad se va duplicando en cada paso.

El siguiente ejemplo es la clásica y famosa función de fibonacci (recursiva):
[codigo](https://ideone.com/wFCfvW)

```c++
#include <iostream>
using namespace std;

int fibonacci(int n){
    if( n<=1 ){
        return n;
    }
    // En este caso se hace una llamada recursiva a la función de fibonacci
    // En cada llamada se hacen 2 llamadas más y asi recursivamente es decir tenemos
    // 1+2+4+8+16... = 2^n -1 llamadas = O(2^n) 
    return fibonacci(n-1) + fibonacci(n-2);
}

int main () {
    // Si probamos con N=100 vemos que demora bastante 
    // ya que empieza a llamar de manera recursiva a la función fibonacci
    // int N = 100;
    int N = 5;

    int result = fibonacci(N);
    cout << result << endl;

    return 0;
}
```

Por ello se recomienda no usar el método recursivo de fibonacci ya que si el número es muy grande este algoritmo es muy ineficiente.

De estos ejemplos podemos observar que los algoritmos que se ejecutan en un tiempo constantes son más rápidos ya que requieren de menos tiempo de ejecución, pero en la práctica no es posible resolver todo problema en este tiempo, por ello se trata de buscar algoritmos que sean lo más eficientes posibles. 

## ¿Cómo calculamos la complejidad de un algoritmo?

Para calcular la complejidad de un algoritmo vamos a usar la notación "Big-O" explicada anteriormente.

#### Tiempo de Complejidad O(1)
```c++
    // Ejemplos de complejidad O(1)
    int b = 10; // Complejidad O(1)
    int a = 3 + b; // Complejidad O(1)
    bool c = a < b;
    
    // Un bucle tambien se considera que tiene complejidad O(1)
    // Si a es una constante
    for (int i=0; i<a; i++ ){
        // Alguna expresion con complejidad O(1)
    }
```
#### Tiempo de Complejidad O(n)
```c++
    // Ejemplos de complejidad O(n)
    // En este ejemplo c es una constante
    for (int i=0; i<=n; i+=c ){ 
        // Alguna expresion con complejidad O(1)
    }
    for (int i=n; i>0; i-=c ){
        // Alguna expresion con complejidad O(1)
    }
```
#### Tiempo de Complejidad O(n^c)
```c++
    // Ejemplos de complejidad O(n^c)
    // En este ejemplo c es una constante
    for (int i = 1; i <=n; i += c) {
        for (int j = 1; j <=n; j += c) {
            // Alguna expresion con complejidad O(1)
        }
    }

    for (int i = n; i > 0; i += c) {
        for (int j = i+1; j <=n; j += c) {
            // Alguna expresion con complejidad O(1)
    }
```
#### Tiempo de Complejidad O(log(n))
```c++
    // Ejemplos de complejidad O(log(n))
    // En este ejemplo c es una constante
    for (int i = 1; i <=n; i *= c) {
        // Alguna expresion con complejidad O(1)
    }

    for (int i = n; i > 0; i /= c) {
        // Alguna expresion con complejidad O(1)
    }
```
