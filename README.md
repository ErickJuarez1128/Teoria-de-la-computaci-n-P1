<div align="center">
  <h1>Práctica 1.- Operaciones Básicas sobre Lenguajes con Interfaz Gráfica</h1>
  <p><i>Reporte de práctica hecho en Java Swing</i></p>
   <p><i>Juárez Velázquez Erick Daniel 2025630052</i></p>
   <p><i>Placencia Murguia Juan Emilio 2025630024</i></p>
</div>

---

##  Introducción

En la asignatura de Teoría de la Computación, el estudio de los lenguajes formales comienza con la comprensión de cómo se estructuran y generan las cadenas a partir de un alfabeto dado ($\Sigma$). Una cadena es una secuencia finita de símbolos, y su manipulación es fundamental para áreas como la construcción de compiladores y el procesamiento de lenguajes.

Esta práctica consiste en una herramienta desarrollada con una Interfaz Gráfica de Usuario  utilizando Java Swing. La aplicación permite automatizar operaciones lógicas y generativas sobre alfabetos y cadenas, dividiéndose en dos módulos principales:

### 1. Análisis de Cadenas 
El sistema descompone una cadena de entrada para identificar sus componentes esenciales mediante algoritmos de manipulación de arreglos y sub-secuencias:
* **Prefijos:** Cadenas obtenidas al eliminar cero o más símbolos del final.
* **Sufijos:** Cadenas obtenidas al eliminar cero o más símbolos del inicio.
* **Subcadenas:** Secuencias de símbolos contiguos dentro de la cadena original.

### 2. Generación de Lenguajes 
Se implementa la lógica para generar conjuntos de cadenas basados en las potencias de un alfabeto. Para efectos de esta práctica, las operaciones se presentan de forma explícita según las siguientes definiciones matemáticas:

<div align="center">

**Cerradura de Kleene ($A^*$)**
$$A^* = A^0 \cup A^1 \cup A^2 \cup A^3 \cup \dots \cup A^n$$



**Cerradura Positiva ($A^+$)**
$$A^+ = A^1 \cup A^2 \cup A^3 \cup \dots \cup A^n$$

</div>

## Instrucciones de Ejecución

Para poder ejecutar esta aplicación, es necesario contar con el **Java Development Kit (JDK)** instalado en el equipo.

### Desde el IDE (NetBeans versión más reciente de preferencia)
### Requisitos del Sistema 
Para compilar y ejecutar este proyecto correctamente, se requiere el siguiente entorno: **Lenguaje:** Java 8 (JDK 1.8) o superior. 
 **Entorno de Desarrollo (IDE):** NetBeans IDE 8.2 o cualquier versión reciente de Apache NetBeans.
1. Abre tu entorno de desarrollo Apache NetBeans.
2. Dirígete al menú superior y selecciona `File` > `Open Project...` para abrir la carpeta contenedora del proyecto.
3. En el panel lateral izquierdo (*Projects*), despliega las carpetas del proyecto hasta llegar a los paquetes fuente (`Source Packages`).
4. Localiza el archivo principal del proyecto llamado `Lenguajes.java`.
5. Haz clic derecho sobre el archivo `Lenguajes.java` y selecciona la opción **"Run File"** (o utiliza el atajo de teclado `Shift + F6`).
6. El programa compilará y desplegará el Menú Principal para usar el programa.


## Desarrollo de la Práctica

Para abordar los requerimientos de la práctica, el proyecto se dividió en tres ventanas principales utilizando la biblioteca Java Swing para la interfaz gráfica. La clase principal `Lenguajes.java` se encarga de instanciar y hacer visible el menú de inicio, estableciendo el punto de partida de la ejecución.

### 1. Menú Principal e Interfaz de Navegación
Se diseñó una pantalla de inicio intuitiva que permite al usuario seleccionar qué tipo de operación desea realizar. Esta ventana actúa como un enrutador hacia los dos módulos principales de la aplicación.
(Ver Figura 1)

<p align="center">
  <img src="https://github.com/user-attachments/assets/b9247299-8dbd-4aa3-8850-49ffb0b6efe4">
  <br>
  Figura 1
</p>
Al presionar cualquiera de los botones, el sistema oculta la ventana actual e instancia la clase correspondiente (`Subcadenas` o `Cerraduras`), centrando la nueva ventana en pantalla.

### 2. Módulo de Operaciones: Subcadenas, Prefijos y Sufijos
Para el primer requerimiento, se desarrolló una interfaz donde el usuario ingresa una cadena de texto base. Mediante un componente `JComboBox`, se puede elegir la operación específica a realizar. (Ver Figura 2)

<p align="center">
  <img src="https://github.com/user-attachments/assets/e19c2dc1-cf26-4e74-9437-9b8287f733f3">
  <br>
  Figura 2
</p>
La lógica detrás de este módulo se controló mediante una estructura `if-else` que evalúa la opción seleccionada. Para los prefijos y sufijos, se implementaron ciclos `for` anidados que extraen los caracteres según los límites correspondientes, contemplando siempre el símbolo vacío ($\lambda$). (Ver Figura 3 y 4)

<p align="center">
![Image](https://github.com/user-attachments/assets/407d7e3a-c27f-4d68-8bd0-2abe463a4338)

</p>
<div align="center"> Figura 3</div>
<p align="center">
![Image](https://github.com/user-attachments/assets/690ec703-5275-4240-8a29-111f6c6b9d73)

</p>
<div align="center"> Figura 4</div>

### 3. Módulo de Generación: Cerradura de Kleene y Positiva 
El cálculo de lenguajes formales se gestionó en una ventana independiente. Aquí, el usuario ingresa un alfabeto (separado por comas) y un límite numérico para la longitud máxima de las cadenas a generar. (Ver Figura 5)

<p align="center">
![Image](https://github.com/user-attachments/assets/7e0da5cf-b953-4743-8895-367e9008c040)
</p>
 <div align="center">Figura 5</div> 
Para generar las combinaciones de la Cerradura de Kleene y la Positiva, se extrae el alfabeto y se convierte el límite a un número entero. Dado el crecimiento exponencial, la generación se resolvió mediante un método recursivo que construye las cadenas carácter por carácter hasta alcanzar la longitud máxima ingresada por el usuario. (Ver Figura 6)

<p align="center">
![Image](https://github.com/user-attachments/assets/6a0dbc3c-6c87-4486-b298-be15e1968cbb)

</p>
 <div align="center">Figura 6</div> 
 
### 4. Exportación de Resultados en archivo tipo .txt
Para cumplir con el requerimiento de persistencia de datos, se implementó una función de exportación en ambas ventanas de la aplicación. Esta funcionalidad permite al usuario guardar el histórico de las operaciones mostradas en pantalla para su posterior revisión.

El sistema extrae el texto contenido en el área de resultados (`JTextArea`) y lo escribe directamente en un archivo con extensión `.txt` (como `Resultados_Subcadenas.txt` o `Resultados_Cerraduras.txt`). 

Para garantizar la estabilidad del programa, el proceso de escritura se encapsuló dentro de un bloque `try-catch`, el cual previene que la aplicación se cierre inesperadamente si ocurre un error de entrada/salida (`IOException`). Finalmente, mediante un `JOptionPane`, se le muestra al usuario un cuadro de diálogo confirmando el éxito de la operación y la ruta absoluta donde se guardó el archivo en su equipo.


##  Conclusión

Desarrollar esta herramienta en Java Swing nos permitió consolidar la transición de la teoría pura a una aplicación práctica y tangible. Durante el proceso, logramos representar la estructura de las cadenas matemáticamente y en código, entendiendo a fondo cómo los prefijos y sufijos sientan las bases del análisis léxico. Además, al momento de implementar las cerraduras, comprobamos de primera mano la importancia de la eficiencia computacional, pues se vuelve vital controlar los límites de iteración cuando se trabaja con lenguajes que crecen de forma exponencial. Todo este trabajo lógico se complementó muy bien con la interfaz gráfica, la cual terminó facilitando la interacción y permitiendo probar diferentes alfabetos de manera intuitiva.
