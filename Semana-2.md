# Estructuras de Datos

Luego de haber visto una introducción acerca de los algoritmos y el análisis de la complejidad de los mismos pasemos a otro tema muy importante, ahora vamos a hablar acerca de las estructuras de datos y su importancia a la hora de solucionar un problema.

Una estructura de datos es una forma particular de organizar datos en una computadora para que pueda ser utilizada de manera eficiente. De manera más precisa, una estructura de datos es una colección de valores de datos, las relaciones entre ellos y las funciones u operaciones que se pueden aplicar a los datos.

Diferentes tipos de estructuras de datos son adecuados para diferentes tipos de aplicaciones, y algunos son altamente especializados para tareas específicas por ello para diseñar algoritmos eficientes debemos saber que tipo de estructura de datos usar para cada problema.

En la siguiente imagen veremos algunas estructuras de datos:

<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/datastructures.png">
</p>

## Implementación 

Para la implementacion de las estructuras de datos usaremos la Standard Template Library (STL) es una colección de estructuras de datos genéricas y algoritmos escritos en C++.

## Ejemplos de Estructuras de Datos
Algunas estructuras de datos conocidas:

### Arrays

Es una estructura de datos utilizada para almacenar elementos homogéneos en ubicaciones contiguas. El tamaño de un array debe proporcionarse antes de almacenar datos.

<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/arrays.jpg">
</p>

#### Implementación

[codigo](https://ideone.com/OlmeJh)

```c++
#include <iostream>
#include <array>

using namespace std;
 
int main()
{
    // Creación del array 
    array<int, 5> arr = {2,5,6,8,3};

    cout << "Tamaño del array: " << arr.size() << endl;

    cout << "El primer elemento es: " << arr.front() << endl;   // 2

    cout << "El ultimo elemento es: " << arr.back() << endl;     // 3

    for (int i = 0; i < arr.size(); i++)
        cout << arr.at(i) << " ";

    // Otra forma de recorrer el array 
    for(auto& j: arr)
        cout << j << ' ';

    return 0;
}

```

### Listas Enlazadas

Es una estructura de datos lineal (como los arrays) donde cada elemento es un objeto separado. Cada elemento (es decir, nodo) de una lista se compone de dos elementos: los datos y una referencia al siguiente nodo, además este crece de manera dinámica.

<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/linkedlist.jpg">
</p>

#### Implementación

[codigo](https://ideone.com/pA4PNZ)

```c++
#include <iostream>
#include <list>

using namespace std;

// función que imprime los elementos de una lista
void imprimeLista(list <int> g)
{
    // Crea un iterador para recorrer la lista
    list <int> :: iterator it;
    for(it = g.begin(); it != g.end(); ++it)
        cout << '\t' << *it;

    cout << '\n';
}
 
int main()
{
    // Crea 2 listas 
    list<int> L1, L2;

    for (int i=0; i<10; i++)
    {
        L1.push_back(i*2); // Añade elementos al final de la lista
        L2.push_front(i*3); // Añade elementos al comienzo de la lista
    }

    cout << "Imprimiendo Lista L1 : \n";
    imprimeLista(L1);
    cout << "Imprimiendo Lista L2 : \n";
    imprimeLista(L2);

    cout << "\n L1.pop_front() : " << endl;
    L1.pop_front(); // remueve el primer elemento
    imprimeLista(L1);

    cout << "\n L2.pop_back() : " << endl;
    L2.pop_back(); // remueve el ultimo elemento
    imprimeLista(L2);

    cout << "Ordenando la lista L2" << endl;
    L2.sort();
    imprimeLista(L2);

    return 0;
}
```

### Pilas

Una pila o LIFO  (last in, first out)  `último en entrar, primero en salir` es un tipo de dato abstracto que sirve como una colección de elementos,con dos operaciones principales: push, que agrega un elemento a la colección, y pop, que elimina el último elemento que se agregó. 

<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/pila.png">
</p>

#### Implementación

[codigo](https://ideone.com/FdcnA2)

```c++
#include <iostream>
#include <stack>

using namespace std;

// función que imprime los elementos de una pila
void imprimePila(stack <int> pila)
{
    stack <int> s = pila;
    while (!s.empty())
    {
        cout << '\t' << s.top() << '\n';
        s.pop();
    }
    cout << '\n';
}
 
int main()
{
    // Creamos la pila
    stack <int> pila;
    pila.push(100);
    pila.push(300);
    pila.push(200);
    pila.push(322);
    pila.push(911);
 
    cout << "La pila es: \n";
    imprimePila(pila);
 
    // Tamaño de la pila
    cout << "\n pila.size() : " << pila.size();
    // Ultimo elemento de la pila
    cout << "\n pila.top() : " << pila.top();
  
    cout << "\n pila.pop() : \n";
    pila.pop(); // Removemos el elemento de arriba
    imprimePila(pila);

    return 0;
}
```

### Colas 

Una cola o FIFO (first in, first out) `primero en entrar, primero en salir` es un tipo de dato abstracto que sirve como una colección de elementos, con dos operaciones principales: enqueue (agregar un elemento a la cola, el elemento se agrega al final) y dequeue (eliminar un elemento de la cola, el elemento a eliminar es el primero que se agrego).

<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/cola.png">
</p>

#### Implementación

[codigo](https://ideone.com/Sxw4pw)

```c++
#include <iostream>
#include <queue>

using namespace std;

// función que imprime los elementos de una pila
void imprimeCola(queue <int> cola)
{
    queue <int> s = cola;
    while (!s.empty())
    {
        cout << '\t' << s.front();
        s.pop();
    }
    cout << '\n';
}
 
int main()
{
    // Creamos la cola
    queue <int> cola;
    cola.push(100);
    cola.push(300);
    cola.push(200);
    cola.push(322);
    cola.push(911);
 
    cout << "La cola es: \n";
    imprimeCola(cola);
 
    // Tamaño de la cola
    cout << "\n cola.size() : " << cola.size();
    // El primer elemento de la cola es
    cout << "\n cola.front() : " << cola.front();
    // Ultimo elemento de la cola
    cout << "\n cola.back() : " << cola.back();
  
    cout << "\n cola.pop() : \n";
    cola.pop(); // Removemos el prime elemento de la cola
    imprimeCola(cola);

    return 0;
}
```

## Estructuras de datos no lineales

La estructura de datos donde los elementos de datos no están organizados secuencialmente se denomina estructura de datos no lineal. En otras palabras, los elementos de datos A de la estructura de datos no lineales podrían estar conectados a más de un elemento para reflejar una relación especial entre ellos. Todos los elementos de datos en la estructura de datos no lineal no pueden atravesarse en una sola ejecución.

Ejemplos de estas estructuras de datos son los grafos y los árboles.

### Grafos

Un grafo G se define como un par (V, E), donde V es un conjunto cuyos elementos son denominados vértices o nodos y E es un subconjunto de pares no ordenados de vértices y que reciben el nombre de aristas o arcos.

Los grafos se utilizan para representar muchas aplicaciones de la vida real: los grafos se utilizan para representar redes. Las redes pueden incluir rutas en una ciudad o red telefónica o red de circuito. Los grafos también se usan en redes sociales como linkedIn, facebook. Por ejemplo, en Facebook, cada persona está representada con un vértice (o nodo). Cada nodo es una estructura y contiene información como ID de persona, nombre, género y lugar de nacimiento. 

#### Representación

Los grafos suelen ser representado como un conjunto de vertices unidos por aristas

<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/grafo.png">
</p>

Otra manera de representarlo es mediante el uso de listas de adyacencia:

<p align="center"> 
<img src="https://github.com/gersongams/HackSpaceAlgorithms/blob/master/images/grafo-lista.png">
</p>

#### Implementación

Ahora vamos a implementar un grafo usando la libreria stl usada anteriormente, más adelante veremos algunos algoritmos muy importantes para la busqueda de la ruta más corta como BFS, DFS, Dijsktra, etc. Estos algoritmos son muy importantes en la Ciencia de la computación.

Para recorrer el grafo usaremos el algoritmo DFS, por ahora no entraremos en detalle acerca de este algoritmo, si deseas más [información](https://en.wikipedia.org/wiki/Depth-first_search):

En el siguiente ejemplo usaremos el vector de STL para implementar nuestro grafo usando la lista de adyacencia de todos los vertices.

[codigo](https://ideone.com/F8dghr)


```c++
#include <iostream>
#include <vector>

using namespace std;

// Esta función añade una arista al grafo no dirigido
void addEdge(vector<int> adj[], int u, int v)
{
    adj[u].push_back(v);
    adj[v].push_back(u);
}

// Una funcion de utilidad para recorrer el grafo usando DFS
void DFSUtil(int u, vector<int> adj[], vector<bool> &visited)
{
    visited[u] = true;
    cout << u << " ";
    for (int i=0; i<adj[u].size(); i++)
        if (visited[adj[u][i]] == false)
            DFSUtil(adj[u][i], adj, visited);
}
 
// Funcion que se encarga de hacer el recorrido del grafo
void DFS(vector<int> adj[], int V)
{
    vector<bool> visited(V, false);
    for (int u=0; u<V; u++)
        if (visited[u] == false)
            DFSUtil(u, adj, visited);
}

int main()
{
    int V = 5;
    vector<int> adj[V];
    addEdge(adj, 0, 1);
    addEdge(adj, 0, 4);
    addEdge(adj, 1, 2);
    addEdge(adj, 1, 3);
    addEdge(adj, 1, 4);
    addEdge(adj, 2, 3);
    addEdge(adj, 3, 4);
    DFS(adj, V);

    return 0;
}
```
