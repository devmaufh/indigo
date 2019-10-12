---
title: "Introduccion a dart"
layout: post
date: 2019-10-10 10:50
image: https://cdn-images-1.medium.com/max/1200/1*knHF_qpxdtS8h0Z8EeqowA.png
headerImage: true
tag:
- Python
- Data
category: blog
author: johndoe
description: This is simple example for how to read a data set from a url using python and Pandas
---
# Dart: Sintáxis báscia

## ¿Qué es dart?
Dart es un lenguaje de código abierto, estructurado y flexible, orientado a objetos, basado en clases, con herencia simple y sporte de interfaces, clases abstractas y tipado opcional de datos.

Está compuesto por: 

* Variables y operadores.
* Clases.
* Funciones.
* Estructuras de control como:
  * Condicionales.
  * Ciclos.
* Librerías y paquetes.
* Estructuras genéricas y colecciones.

## Hola mundo
Cuando comenzamos a aprender un nuevo lenguaje de programación, se ha vuelto una costumbre entre desarrolladores crear el famoso: "Hola mundo". *Dart* no es la excepción.

Ejemplo
```dart
void main(){
    print("Hello world!");
}
```
La función **main()** es un método predefinido en *Dart*. Este método actúa como el punto de entrada para nuestra aplicación. Un programa escrito en *Dart* siempre tiene que incluir éste método para poder ser ejecutado. **print()** es otro método predefinido que imprime en consola la cadena de texto que se le pasa de parámetro dentro de los paréntesis.

Podemos ejecutar éste código en nuestro equipo, siempre y cuando tengamos instalado el SDK de *Dart*, si este no es el caso, podemos acceder al siguiente [link](https://dartpad.dartlang.org) en donde encontraremos un compilador *Dart* online.

La salida del código anterior es:
```
Hello world!
```

## Tipos de datos
Una de las características más fundamentales no solo en *Dart* sino en cualquier otro lenguaje de programación, son los tipos de datos que soporta para manipular la información.

En *Dart*, contamos con los siguientes tipos de datos:
* Numéricos
  * Enteros
  * De punto flotante
* Cadenas de texto. 
* Booleanos
* Listas

### Definición de variables
Antes de entrar en detalle con los tipos de datos, necesitamos saber como definir una variable. En éste lenguaje, tenemos que escribir primero el tipo de dato de nuestra variable, seguido por el nombre de la variable y terminar la instrucción con un punto y coma. 

Es posible definir una variable e inicializarla con un valor por defecto.

Ejemplo
```dart
TipoDato nombre_variable;

TipoDato nombre_variable = valor_incial;
```
También podemos sustituir el tipo de dato por la palabra reservada **var** y cuando se le asigna un valor, el compilador infiere automáticamente de qué tipo de dato es dicha variable.

Ejemplo
```dart
var variable;

var variable = valor_inicial;
```


### Numéricos 
Para representar valores enteros es necesario hacer uso del tipo **int**. Por otra parte, para los valores que involucran punto flotante, usamos **double**. Es importante recalcar que en *Dart* no existe un tipo de dato **float** como en otros lenguajes tales como **Java**.
<br><br>
Definición de variable **entera**

```dart
int edad; //Sin valor inicial

int edad = 21; //Convalor inicial

var edad = 21; 
```

Definición de variable **double**

```dart
double estatura; //Sin valor inicial

double estatura = 172.0; //Con valor inicial

var estatura = 172.0; 
```

### Cadenas
Las cadenas nos permiten almacenar caracteres alfanuméricos. Para definir una cadena usamos la palabra reservada **String**.

Ejemplo 
```dart
String cadena; //Sin valor inicial

String cadena = "Cadena de texto"; //Con valor inicial

var cadena = "Cadena de texto";

``` 

### Booleanos
Las variables de tipo booleano solo nos permiten almacenar dos valores: **true** o **false**, usamos la palabra reservada **bool** para indicar que una variable es booleana.

Ejemplo 
```dart
bool booleano; //Sin valor inicial

bool booleano = true; //Con valor inicial

var booleano = false;

``` 

### Listas
En muchos lenguajes, la colección más común de datos son los arreglos (arrays). En *Dart*, los arreglos son el objeto **List**, por lo que los llamamos listas. 

Una lista se construye usando la palabra reservada **List** en seguida del tipo de datos que almacenará esa lista (es opcional) y el nombre de la lista, también es posible declarar una lista con valores iniciales.

Sintáxis
```dart
List<tipo_dato> nombreLista = List<tipo_dato>();

List<tipo_dato> nombreLista = [valor1, valor2,valor3,valor4,... valor n]

```
Ejemplo
```dart
List<String> nombres = List<String>();

List<String> nombres = ['Mauricio','Pedro', 'Carlos'];

var nombres = ['Pedro', 'José', 'Miguel'];
```

Para añadir nuevos elementos a la lista después de declararla o inicializarla, se hace uso del método propio del objeto **List** llamado **add()**.

Ejemplo
```dart
nombres.add('Nuevo nombre');
```
