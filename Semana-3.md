# Algoritmos de Ordenamiento

En la semana 1 vimos algunos algoritmos de búsqueda como Linear Search, Binary Search, ahora vamos a ver los algoritmos de ordenamiento.

El ordenamiento es el proceso de reorganizar una secuencia de objetos para ponerlos en un orden lógico. Este además juega un papel importante en el procesamiento de datos comerciales y en la computación científica moderna. Las aplicaciones abundan en el procesamiento de transacciones, la optimización combinatoria, la astrofísica, la dinámica molecular, la lingüística, la genómica, la predicción meteorológica y muchos otros campos.

<p align="center"> 
<img src="https://i.imgur.com/fq0A8hx.gif">
</p>


Si deseas ver como funcionan de manera interactiva visitar esta [página](https://visualgo.net/es/sorting).


A la hora de usar un algoritmo de ordenamiento existen algunos criterios de clasificación como:

* Complejidad computacional
* Uso de memoria
* Recursividad
* Estabilidad

La clasificación estable y no estable se refieren a que si un algoritmo de clasificación, después de ordenar los elementos, no cambia la secuencia de contenido similar en el que aparecen, se denomina __clasificación estable__. En el caso contrario si después de ordenar los elementos, cambia la secuencia de contenido similar en el que aparecen, se denomina __clasificación inestable__.


<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/stability.png">
</p>

## Ordenamiento por Inserción (Insertion Sort)

Es una manera muy natural de ordenar para un ser humano, y puede usarse fácilmente para ordenar un mazo de cartas numeradas en forma arbitraria. 

<p align="center"> 
<img src="https://ds055uzetaobb.cloudfront.net/image_optimizer/5fc8daa9296837453ccbc8c7f9c2494bbd1fcdda.gif">
</p>

### Implementación

[codigo](https://ideone.com/7MuH48)

```c++
#include <iostream>
#include <vector>

using namespace std;

// Algoritmo Insertion Sort
void insertionSort(vector<int>& a)
{
    int i,key,j;
    for (i = 1; i < a.size(); i++)
    {
        key = a[i];
        j = i-1;

        /* Mueve los elementos de a[0..i-1], que son mayores que key, a una posicion delante de su posicion actual
        */
        while (j >= 0 && a[j] > key)
        {
            a[j+1] = a[j];
            j = j-1;
        }
        a[j+1] = key;
    }
}

// Función auxiliar para imprimir el vector
void printVector(vector<int> a){
    for (int i=0; i < a.size(); i++)
        cout<<a[i]<<" ";
    cout<<endl;
}

int main()
{
    vector<int> a {20,14,17,15,18,24,15,5};
    printVector(a);
    insertionSort(a);
    printVector(a);

    return 0;
}
```

## Ordenamiento de Burbuja (Bubble Sort)

El ordenamiento de burbuja es un algoritmo basado en la comparación que compara cada par de elementos en una matriz y los intercambia si están desordenados hasta que se ordena toda la matriz. Para cada elemento en la lista, el algoritmo compara cada par de elementos. 

<p align="center"> 
<img src="https://ds055uzetaobb.cloudfront.net/image_optimizer/4f60337caedcc96ffeb08692e4f8d00f5cb3fd58.gif">
</p>

### Implementación

[codigo](https://ideone.com/PdGbIY)

```c++
#include <iostream>
#include <vector>

using namespace std;

// Algoritmo BubbleSort
void bubbleSort(vector<int>& a)
{
    bool swapp = true;
    while(swapp)
    {
        swapp = false;
        for (int i = 0; i < a.size()-1; i++) {
            if (a[i]>a[i+1]){
                int temp = a[i];
                a[i] = a[i+1];
                a[i+1] = temp;
                swapp = true;
            }
        }
    }
}

// Función auxiliar para imprimir el vector
void printVector(vector<int> a){
    for (int i=0; i < a.size(); i++)
        cout<<a[i]<<" ";
    cout<<endl;
}

int main()
{
    vector<int> a {20,14,17,15,18,24,15,5};
    printVector(a);
    bubbleSort(a);
    printVector(a);

    return 0;
}
```

## Ordenamiento por mezcla (MergeSort)

Es un algoritmo que usa la técnica [divide y vencerás](https://es.wikipedia.org/wiki/Algoritmo_divide_y_vencer%C3%A1s), divide la matriz de entrada en dos, luego se llama a sí misma para las dos mitades y al final fusiona las dos mitades ordenadas. La función merge () se usa para unir dos mitades. La fusión (arr, l, m, r) es un proceso clave que asume que arr [l..m] y arr [m + 1..r] están ordenados y fusiona las dos sub-matrices ordenadas en una.

<p align="center"> 
<img src="https://ds055uzetaobb.cloudfront.net/image_optimizer/8c074d46d4c96077d11f9e8cab9ff5d95bdc3da0.gif">
</p>

### Implementación

[codigo](https://ideone.com/fdALbq)

```c++
#include <iostream>
#include <vector>

using namespace std;

void merge(vector<int>& arr, int l, int m, int r)
{
    int i, j, k;
    int n1 = m - l + 1;
    int n2 =  r - m;
 
    /* Creo 2 arrays temporales */
    int L[n1], R[n2];
 
    /* Copio la data a los dos arrays temporales L[] y R[] */
    for (i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (j = 0; j < n2; j++)
        R[j] = arr[m + 1+ j];
 
    /* Mezcla los arrays temporales en arr[]l..r*/
    i = 0; // Indice inicial del primer subarray
    j = 0; // Indice inicial del segundo subarray
    k = l; // Indice inicial del array mezclado

    while (i < n1 && j < n2)
    {
        if (L[i] <= R[j])
        {
            arr[k] = L[i];
            i++;
        }
        else
        {
            arr[k] = R[j];
            j++;
        }
        k++;
    }
 
    /* Copia los elementos faltantes de L[] si es que hay alguno */
    while (i < n1)
    {
        arr[k] = L[i];
        i++;
        k++;
    }
 
    /* Copia los elementos faltantes de R[] si es que hay alguno */
    while (j < n2)
    {
        arr[k] = R[j];
        j++;
        k++;
    }
}

// Algoritmo MergeSort
void mergeSort(vector<int>& arr, int l, int r)
{
    if (l < r)
    {
        // Igual que (l+r)/2 pero evita que haya un desbordamiento
        // para h y l grandes

        int m = l+(r-l)/2;
 
        // Ordena la primera y segunda mitad
        mergeSort(arr, l, m);
        mergeSort(arr, m+1, r);
        merge(arr, l, m, r);
    }
}

// Función auxiliar para imprimir el vector
void printVector(vector<int> a){
    for (int i=0; i < a.size(); i++)
        cout<<a[i]<<" ";
    cout<<endl;
}

int main()
{
    vector<int> a {20,14,17,15,18,24,15,5};
    printVector(a);
    mergeSort(a,0,a.size()-1);
    printVector(a);

    return 0;
}
```

## Ordenamiento rápido (QuickSort)

Al igual que el MergeSort, QuickSort es un algoritmo que usa la técnica divide y vencerás, selecciona un elemento como pivote y divide el conjunto dado alrededor del pivote elegido. Hay muchas versiones diferentes de quickSort que eligen pivotar de diferentes maneras.


<p align="center"> 
<img src="https://ds055uzetaobb.cloudfront.net/image_optimizer/904290ba2b43687554b1d074d091367f370a0c08.gif">
</p>

### Implementación

[codigo](https://ideone.com/FPERqf)

```c++
#include <iostream>
#include <vector>

using namespace std;

// Esta funcion toma el ultimo elemento como pivote
// Establece el elemento pivot en la posicion correcta en el array ordenado
// Y coloca todos los elementos menores al pivot a la izuqierda y los mayores a la derecha del pivote
int partition(vector<int>& arr, int low, int high)
{
    int pivot = arr[high];    // pivot
    int i = (low - 1);  // Index of smaller element
 
    for (int j = low; j <= high- 1; j++)
    {
        // Si el elemento actual es menor o igual que el pivote
        if (arr[j] <= pivot)
        {
            i++;    // incrementa el indice del elemento pequeño
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
    int temp2 = arr[i+1];
    arr[i+1] = arr[high];
    arr[high] = temp2;
    return (i + 1);
}

// Algoritmo QuickSort
void quickSort(vector<int>& arr, int low, int high)
{
    if (low < high)
    {
        int pi = partition(arr, low, high);
 
        // Separa los elementos ordenados antes de la particion y luego de la particion
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

// Función auxiliar para imprimir el vector
void printVector(vector<int> a){
    for (int i=0; i < a.size(); i++)
        cout<<a[i]<<" ";
    cout<<endl;
}

int main()
{
    vector<int> a {20,14,17,15,18,24,15,5};
    printVector(a);
    quickSort(a,0,a.size()-1);
    printVector(a);

    return 0;
}

```

## Ordenamiento por montículos (HeapSort)

Heap sort es una técnica de clasificación basada en comparación basada en la estructura de datos [Binary Heap](https://en.wikipedia.org/wiki/Binary_tree#Types_of_binary_trees). Es similar al tipo de selección donde primero encontramos el elemento máximo y colocamos el elemento máximo al final. Repetimos el mismo proceso para el elemento restante.

#### ¿Qué es Binary Heap?

Primero definamos un árbol binario completo. Un árbol binario completo es un árbol binario en el que cada nivel, excepto posiblemente el último, está completamente lleno, y todos los nodos están lo más a la izquierda posible (Fuente Wikipedia )

Un Binary Heap es un árbol binario completo donde los elementos se almacenan en un orden especial tal que el valor en un nodo padre es mayor (o menor) que los valores en sus dos nodos secundarios. El primero se llama como máximo monticulo y el último se llama monticulo mínimo. El monticulo se puede representar mediante un árbol binario o matriz.

<p align="center"> 
<img src="https://ds055uzetaobb.cloudfront.net/image_optimizer/c1fc9fb4a40d810259ea8291ffde0eef182e7d57.gif">
</p>

### Implementación

[codigo](https://ideone.com/pKGf98
)

```c++
#include <iostream>
#include <vector>

using namespace std;

// Crea un subarbol con raiz con nodo i
void heapify(vector<int>& arr, int n, int i)
{
    int largest = i;  // Inicializar el más grande como raíz
    int l = 2*i + 1;  // left = 2*i + 1
    int r = 2*i + 2;  // right = 2*i + 2
 
    // Si el hijo izquierdo es más grande que la raíz
    if (l < n && arr[l] > arr[largest])
        largest = l;
 
    // Si el hijo correcto es más grande que el más grande hasta el momento
    if (r < n && arr[r] > arr[largest])
        largest = r;
 
    // Si el más grande no es raiz
    if (largest != i)
    {
        swap(arr[i], arr[largest]);
 
        // Heapify recursivamente el subárbol afectado
        heapify(arr, n, largest);
    }
}

// Algoritmo HeapSort
void heapSort(vector<int>& arr, int n)
{
    // Construye el heap (reordena el array)
    for (int i = n/2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // Extra un a un elemento del heap
    for (int i=n-1; i>=0; i--)
    {
        // Mueve la raiz al final
        int temp = arr[0];
        arr[0] = arr[i];
        arr[i] = temp;

        // Llama el maximo heapify en el heap reducido
        heapify(arr, i, 0);
    }
}

// Función auxiliar para imprimir el vector
void printVector(vector<int> a){
    for (int i=0; i < a.size(); i++)
        cout<<a[i]<<" ";
    cout<<endl;
}

int main()
{
    vector<int> a {20,14,17,15,18,24,15,5};
    printVector(a);
    heapSort(a,a.size());
    printVector(a);

    return 0;
}
```

## Comparación de Algoritmos

En la siguiente tabla se puede observar la complejidad de cada algoritmo en cada caso, y además si este es estable:

<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/tabla.png">
</p>

De esta gráfica podemos observar que algunos algoritmos son más lentos cuando el tamaño de entrada empieza a crecer:

<p align="center"> 
<img src="https://ka-perseus-images.s3.amazonaws.com/8cd7b462a39017c99f86558ff3256aca517837c3.png">
</p>

Podemos observar que algoritmos como BubbleSort e InsertioSort tienden a demorarse más cuando el conjunto de entrada es muy grande y en el peor de los casos toma más tiempo que otros algoritmos como MergeSort y QuickSort, en la siguiente semana veremos por qué estos algoritmos son más eficientes en algunos casos.
