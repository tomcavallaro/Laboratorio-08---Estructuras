>## Laboratorio#08 - Estructuras

1. Dada la siguiente definición de una estructura de datos, ¿cómo se declara un vector de 10 elementos de tipo product y se asignan valores al primer elemento?

``` cpp
    struct product{
        int id;
        string name;
        char description[100];
        float price;
        int quantity;
    };

 ```

 #### respuesta: 
 
 ``` cpp
 int main() {
    // Declarar un vector de 10 elementos de tipo product
    product products[10];

    // Asignar valores al primer elemento del vector
    products[0].id = 1;
    products[0].name = "pruebaproducto";
    products[0].description[] = "esto es una prueba";
    products[0].price = 100;
    products[0].quantity = 10;

    // Imprimir los valores del primer producto para verificar
    cout << "id: " << products[0].id << endl;
    cout << "Name: " << products[0].name << endl;
    cout << "Description: " << products[0].description << endl;
    cout << "Price: " << products[0].price << endl;
    cout << "Quantity: " << products[0].quantity << endl;

    return 0;
}

```

2. Indique qué afirmación en relación con el siguiente programa es correcta:

```cpp
struct person{
        char name[50];
        int age;
    };

    struct filming {
        char place[50];
        float budget;
    };

    struct movie {
        struct person director;
        struct person actor1;
        struct person actor2;
        struct filming location;
    };
```

• a) Se producirá un error de compilación porque la estructura person está repetida en tres miembros de la estructura movie.

• b) Se produce un error de compilación porque un miembro de una estructura no puede ser otra estructura.

• c) La sentencia strcpy(my_movie.director.name, "Federico Fellini");genera un error en tiempo de compilación.

• d) Todas las afirmaciones anteriores son falsas.

#### Respuesta: 

a) Se producirá un error de compilación porque la estructura person está repetida en tres miembros de la estructura movie.

<div style="border: 2px solid black; padding: 10px; background-color: red; color:black; border-radius: 15px; font-fammily: serif ;  ">FALSO. No se produce un error de compilación por tener la misma estructura repetida en diferentes miembros de otra estructura. Es completamente válido en C y C++ utilizar la misma estructura como miembro en diferentes partes de otra estructura.</div>

b) Se produce un error de compilación porque un miembro de una estructura no puede ser otra estructura.

<div style="border: 2px solid black; padding: 10px; background-color: red; color:black; border-radius: 15px; ">FALSO. En C y C++, es completamente válido que un miembro de una estructura sea otra estructura. En este caso, la estructura movie contiene varias instancias de la estructura person y una instancia de la estructura filming, lo cual es perfectamente legal.</div>

c) La sentencia strcpy(my_movie.director.name, "Federico Fellini"); genera un error en tiempo de compilación.

<div style="border: 2px solid black; padding: 10px; background-color: red; color:black; border-radius: 15px; ">FALSO. La función strcpy se usa para copiar cadenas de caracteres en C y C++, y es válida para manipular los miembros de tipo char[] en estructuras. La sentencia strcpy(my_movie.director.name, "Federico Fellini"); es correcta y no debería generar un error de compilación, siempre que my_movie sea una instancia válida de la estructura movie y #include <cstring> esté incluido para usar strcpy.</div>

d) Todas las afirmaciones anteriores son falsas.

<div style="border: 2px solid black; padding: 10px; background-color: green; color:black; border-radius: 15px; ">VERDADERO. Todas las afirmaciones anteriores son incorrectas. El código dado es válido en C y C++, y la sentencia strcpy es una operación válida si se incluyen las bibliotecas adecuadas y se cumplen las condiciones correctas. </div>

3. Utilizando la estructura del punto 1a, analizá el siguiente programa.

``` cpp

    cout << "enter product: " << endl;
    struct product p1;
    cout <<"enter id" << endl;
    cin >> p1.id;
    cout << "enter name" << endl;
    getline(cin, p1.name);
    cout << "enter description" << endl;
    cin.getline(p1.description, 100);
    cout << "enter price" << endl;
    cin >> p1.price;
    cout << "enter quantity" << endl;
    cin >> p1.quantity;
    cout << p1.id << endl;
    cout << p1.name << endl;
    cout << p1.description << endl;
    cout << p1.price << endl;
    cout << p1.quantity << endl;
    cout << "------------------" << endl;

```
#### Respuesta:

``` cpp
#include <iostream>
#include <string>
#include <cstring>  // Para std::strcpy y std::strlen

using namespace std;

// Definición de la estructura
struct product {
    int id;
    string name;
    char description[100];
    float price;
    int quantity;
};

int main() {
    cout << "Enter product details:" << endl;
    
    struct product p1;
    
    // Leer el id
    cout << "Enter id: ";
    cin >> p1.id;
    
    // Limpiar el buffer de entrada para poder usar getline correctamente
    cin.ignore();
    
    // Leer el nombre
    cout << "Enter name: ";
    getline(cin, p1.name);
    
    // Leer la descripción
    cout << "Enter description: ";
    cin.getline(p1.description, 100);
    
    // Leer el precio
    cout << "Enter price: ";
    cin >> p1.price;
    
    // Leer la cantidad
    cout << "Enter quantity: ";
    cin >> p1.quantity;
    
    // Mostrar los detalles del producto
    cout << "Product Details:" << endl;
    cout << "ID: " << p1.id << endl;
    cout << "Name: " << p1.name << endl;
    cout << "Description: " << p1.description << endl;
    cout << "Price: " << p1.price << endl;
    cout << "Quantity: " << p1.quantity << endl;
    cout << "------------------" << endl;
    
    return 0;
}

```
Para que el programa funcione correctamente se debe poner un "cin.ignore();"  para ignorar o descartar caracteres en el buffer de entrada. Esto es útil para limpiar el buffer de entrada y evitar que datos no deseados interfieran con la lectura de datos posteriores.

# Ejercicio practico

Te piden que realices un programa para la gestion de una biblioteca. Los datos de los libros son los siguiente:

título
autor
ISBN (cadena de 17 caracteres)
prestado (true/false)
Escribir el programa en C++ que:

Defina una estructura para almacenar los datos de cualquier libro.
Ingresa los datos de 2 libros por teclado y almacenarlos en un arreglo
Verificar que los datos ingresados no representan ejemplares de un mismo tipo
Imprimir los datos por pantalla

Nota:
Utilizar funciones para todas las operaciones

``` cpp
#include <iostream>
#include <string>
using namespace std;

// Estructura para almacenar los datos de un libro
struct Libro {
    string titulo;
    string autor;
    int anioPublicacion;
};

// Función para ingresar los datos de un libro
void ingresarLibro(Libro &libro) {
    cout << "Ingrese el título del libro: ";
    getline(cin, libro.titulo);
    cout << "Ingrese el autor del libro: ";
    getline(cin, libro.autor);
    cout << "Ingrese el año de publicación del libro: ";
    cin >> libro.anioPublicacion;
    cin.ignore(); // Limpiar el buffer
}

// Función para verificar si dos libros son del mismo tipo
bool sonLibrosIguales(Libro libro1, Libro libro2) {
    return (libro1.titulo == libro2.titulo && libro1.autor == libro2.autor && libro1.anioPublicacion == libro2.anioPublicacion);
}

// Función para imprimir los datos de un libro
void imprimirLibro(Libro libro) {
    cout << "Título: " << libro.titulo << endl;
    cout << "Autor: " << libro.autor << endl;
    cout << "Año de Publicación: " << libro.anioPublicacion << endl;
}

int main() {
    Libro libros[2]; // Arreglo para almacenar dos libros

    // Ingresar los datos de los dos libros
    for (int i = 0; i < 2; i++) {
        cout << "Ingrese los datos del libro " << i + 1 << ":" << endl;
        ingresarLibro(libros[i]);
        cout << endl;
    }

    // Verificar si los libros son iguales
    if (sonLibrosIguales(libros[0], libros[1])) {
        cout << "Los dos libros son iguales. No se pueden ingresar dos ejemplares del mismo tipo." << endl;
    } else {
        // Imprimir los datos de los libros
        for (int i = 0; i < 2; i++) {
            cout << "Datos del libro " << i + 1 << ":" << endl;
            imprimirLibro(libros[i]);
            cout << endl;
        }
    }

    return 0;
}
```