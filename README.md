# Code_Weaver's Hangman game
En este repositorio se explica el desarrollo y la ejecución del proyecto final para el curso de Programación de Computadores
### Integrante: Yazney Alejandra Arenas Garrido
### Logo
![logo](https://github.com/alejayz/Proyecto-final-Code_Weaver/assets/124609988/3e251612-f218-4771-a9b1-5fc80c994236)
## Objetivo del proyecto
Este proyecto tiene el fin de implementar distintas herramientas o conceptos vistos durante el curso de Programación de Computadores para solucionar un problema/situación desarrollando un programa en Python.
## Problema/situación
El problema a solucionar es desarrollar un programa en python que simule un juego, en este caso, un ahorcado el cual se llamará Code_Weaver's Hangman game, mediante la aplicación de las herramientas o conceptos vista en el curso de Programación de Computadores.
### ¿Cómo se abordó el problema?
### 1) Diagrama de flujo:
Para entender cómo desarrollar el programa se planteó una serie de pasos, utilizando la herramienta Mermaid para realizar un diagrama con los pasos a seguir. 
```flowchart TD
    A(Bienvenida al juego) --> B[Elegir el idioma]
    B --> C[1.Español]
    B --> D[2.Inglés]
    C & D --> E[Elegir el modo de juego]
    E --> F[1.Individual]
    E --> G[2.Vs]
    F & G --> H[Escoger la categoría 1/9]
    H--> K[El programa elige una palabra al azar]
    K --> L[Escoger el nivel del juego]
    L --> M[Facil = 10 vidas]
    L --> N[Medio = 6 vidas]
    L--> O[Dificil = 4 vidas]
    M & N & O --> P[Se muestra la lista de guiones de acuerdo a la palabra escogida]
    P--> Q[Se pide a el/los jugador/es que ingresen una letra]
    Q --> R{Verificar: ¿la letra está en la palabra oculta?}
    R --> |sí| S[Se muestra la ubicación de la letra]
    R --> |no| T{¿la letra ya se había ingresado?}
    T --> |sí| U[Mostrar mensaje que indica repetición de letra]
    T --> |no| V[Vidas - 1]
    U & V & S--> W[se pide ingresar una nueva letra] --> R
    S --> X{¿letras ingresadas = palabra oculta?}
    X --> |sí| AB[Juego ganado] --> IJ[Mensaje de felicitaciones y se muestra la palabra oculta]
    X --> |no| W
    V --> EF{¿Vidas = 0?}
   EF --> |sí| GH[Juego perdido] --> KL[Mensaje de consolación y se muestra la palabra oculta]
   EF --> |no| W
   IJ & KL --> MN[Fin del juego]
```
![image](https://github.com/alejayz/Proyecto-final-Code_Weaver/assets/124609988/c657329c-43f2-4cbc-a01c-67416a256d37)
![image](https://github.com/alejayz/Proyecto-final-Code_Weaver/assets/124609988/a69f3192-3224-42e5-8ee3-72d2d7e60a23)


### 2) import
Se utiliza el sistema de importación (import) para traer las bibliotecas time y random, los cuales permiten aplicar diferentes funciones de tiempo y aleatoriedad, respectivamente en el codigo del programa.
```python
import random
import time
```
**random.choice():** esta función permite elegir un elemento de forma aleatoria de un conjunto de elementos, ya sea lista, tupla, diccionario,etc.
En este caso se eutilza esta función para escoger una palabra al azar de las listas de palabras para el juego.
```python
aleatoria=list(random.choice(profesiones).upper())
```
**time.sleep():** esta función permite realizar ratrdos de tiempo en cualquier parte del codigo del programa el cual se sguirá ejecuntando luego del tiempo indicado.
Dentro de este programa se utiliza esta fundción para establecer tiempos de espera entre distintos mensajes que arroja el programa.
```python
nombre = input("nombre jugador: ")
        time.sleep(2)
        print("¡Bienvenido " + nombre + ", empieza a divertirte!")
```
## Desarrollo
## Requisitos para ejecutar el programa

