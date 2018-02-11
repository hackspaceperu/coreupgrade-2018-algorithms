## 1. ¿Cual es la complejidad de tiempo de la función example()?

```c++
int example(int n)
{
  int count = 0;
  for (int i = n; i > 0; i /= 2)
     for (int j = 0; j < i; j++)
        count += 1;
  return count;
}
```

## 2. ¿Cual es la complejidad de tiempo de la función example2()?

```c++
void example2(int n, int arr[])
{
    int i = 0, j = 0;
    for(; i < n; ++i)
        while(j < n && arr[i] < arr[j])
            j++;
}
```

## 3. ¿Cuál es la mejor complejidad de tiempo de bubbleSort?


## Entrega tu reto

Finalmente solo debes subir un documento con tu respuesta a [Google Drive](https://drive.google.com), [Dropbox](https://www.dropbox.com/) o hasta [Pastebin](https://pastebin.com/). Simplemente obtén el link de tu documento y ponlo en el formulario que está disponible cuando te logueas en el [CoreUpgrade](https://www.hackspace.la).

* Paso 1: Haces clic en Algoritmos.
![Clic en Algoritmos](send-a.png)

* Paso 2: Seleccionas `Enviar Reto` y envias el URL.
![Llena el campo con la URL de tu documento](send-b.png)