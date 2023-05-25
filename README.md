# Lab_03
Integrantes: Roger Infa Sanchez, Frank Duarte Oruro, Olger Quispe Vilca
# Árbol Binario de Búsqueda en C++

## Introducción
¡Hola a todos! En esta ocasión, quiero explicarles el código de un Árbol Binario de Búsqueda en C++. Este código nos permitirá crear un árbol binario de búsqueda y visualizarlo en forma de árbol. 

## Descripción del código
```cpp
#include <iostream>
#include <cstdlib>
using namespace std;
```

Aquí estamos incluyendo las bibliotecas estándar necesarias para la entrada y salida de datos, así como para utilizar la función `system()`.

```cpp
struct nodo{
     int nro;
     struct nodo *izq, *der;
};
```

En estas líneas, definimos una estructura llamada `nodo` que representa un nodo en el árbol binario de búsqueda. Cada nodo contiene un número (`nro`) y dos punteros a otros nodos, uno para el hijo izquierdo (`izq`) y otro para el hijo derecho (`der`).

```cpp
typedef struct nodo *ABB;
```

Aquí estamos creando un tipo de dato `ABB` que es un puntero a la estructura `nodo`. Esto nos permitirá crear fácilmente variables del tipo árbol binario de búsqueda.

```cpp
ABB crearNodo(int x)
{
     ABB nuevoNodo = new(struct nodo);
     nuevoNodo->nro = x;
     nuevoNodo->izq = NULL;
     nuevoNodo->der = NULL;

     return nuevoNodo;
}
```

En esta función `crearNodo()`, creamos un nuevo nodo y le asignamos el valor `x` proporcionado. Inicializamos los punteros `izq` y `der` como `NULL` y devolvemos el nuevo nodo creado.

```cpp
void insertar(ABB &arbol, int x)
{
     if(arbol==NULL)
     {
           arbol = crearNodo(x);
     }
     else if(x < arbol->nro)
          insertar(arbol->izq, x);
     else if(x > arbol->nro)
          insertar(arbol->der, x);
}
```

La función `insertar()` se encarga de insertar un nuevo nodo en el árbol. Si el árbol está vacío, se crea un nuevo nodo con el valor `x`. Si `x` es menor que el valor del nodo actual, se llama recursivamente a `insertar()` con el hijo izquierdo. Si `x` es mayor, se llama recursivamente a `insertar()` con el hijo derecho.

```cpp
void verArbol(ABB arbol, int n)
{
     if(arbol==NULL)
          return;
     verArbol(arbol->der, n+1);

     for(int i=0; i<n; i++)
         cout<<"   ";

     cout<< arbol->nro <<endl;

     verArbol(arbol->izq, n+1);
}
```

La función `verArbol()` muestra el árbol en forma de árbol binario. Utiliza un recorrido en orden inverso, comenzando desde el hijo derecho, y va imprimiendo los nodos con un esp

aciado adecuado para visualizar la estructura de árbol.

```cpp
int main()
{
    ABB arbol = NULL;   // creado Arbol

    int n;  // numero de nodos del arbol
    int x; // elemento a insertar en cada nodo

    cout << "\n\t\t  ..[ ARBOL BINARIO DE BUSQUEDA ]..  \n\n";

    cout << " Numero de nodos del arbol:  ";
    cin >> n;
    cout << endl;

    for(int i=0; i<n; i++)
    {
        cout << " Numero del nodo " << i+1 << ": ";
        cin >> x;
        insertar( arbol, x);
    }

    cout << "\n Mostrando ABB \n\n";
    verArbol( arbol, 0);

    cout << endl << endl;

    system("pause");
    return 0;
}
```

En la función `main()`, creamos un árbol binario de búsqueda llamado `arbol` y leemos el número de nodos (`n`) del árbol. Luego, en un bucle, solicitamos al usuario que ingrese los números de los nodos uno por uno y los insertamos en el árbol llamando a la función `insertar()`. Después de insertar todos los nodos, mostramos el árbol utilizando la función `verArbol()`. Finalmente, pausamos la ejecución del programa antes de salir.

## Conclusión
En conclusión, este código implementa un Árbol Binario de Búsqueda en C++ y nos permite visualizarlo en forma de árbol. Espero que esta explicación haya sido clara y útil para comprender cómo funciona este tipo de árbol y cómo se implementa en C++. ¡Gracias por su atención!
