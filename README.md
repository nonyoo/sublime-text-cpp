# C++ build system para Sublime Text

Compile and run in a external terminal. Only for Windows.

Compila y ejecuta en una terminal externa. Solo para Windows.

## Este documento contiene información importante del código

El código lo comparto para hacer más fácil el trabajo y aprendizaje de las personas interesadas en aprender el lenguaje de programación C++.

En primer lugar, el código es de autoría propia, hecho y re-hecho y el que mejor me ha servido.

### **IMPORTANTE:**

Si revisaron el archivo (cmd_C++.sublime-build) verán que hay dos códigos, ambos funcionan igual, la única diferencia se encuentra en donde se guarda el programa compilado.

**1. DEFAULT BUILD SYSTEM:**

Guarda el programa en la misma carpeta donde se encuentra el archivo. Si cuando programas usas pocos archivos está es la mejor opción.

![Screenshot](Screenshots/1.png)

Caso contrario te puede interesar el segundo código.

**2. SECONDARY BUILD SYSTEM:**

Se encarga de guardar el programa compilado en una carpeta diferente. Este es el sistema de compilación que yo uso, me permite ordenar mejor mis diferentes archivos.

![Screenshot](Screenshots/2.png)

**Cómo funciona lo de guardar en otra carpeta:**

Todo es gracias a esta parte del código:

                "$folder/bin/$file_base_name.exe"
Primero explicaré un poco el código, para qué tengas en cuenta lo que necesitas para usar esta opción:

**"$folder/bin/"**: Es la dirección en donde se guarda el archivo compilado y de donde se ejecutará el programa. Si te das cuenta, leyendo ambos códigos, esta parte es la única que cambia, pero permite una organización de archivos diferente u ordenada.

**"$folder"**: hace referencia a la carpeta general del proyecto. Como verán en la captura de pantalla, mis archivos se encuentran en la carpeta "cpp", pero la carpeta general es "C++", el comando hacer referencia a esa misma carpeta.

![Screenshot](Screenshots/3.png)

**"/bin/"**: hace referencia a la carpeta donde se guardan los programas. "bin" es un nombre aleatorio que yo mismo puse y puede ser cambiado por cualquier otro nombre, eso sí, aseguranse de crear primero la carpeta junto a su carpeta de archivos.

![Screenshot](Screenshots/4.png)

Si quieres usar esta opción, debes asegurarte de crear una carpeta general, dentro debes crear dos carpetas uno para los archivos y otra para los programas (el nombre puede ser cualquier, pero asegúrate de cambiar en el código).

Así mismo, puedes crear una carpeta dentro de tu carpeta de archivos y cambiar el código, tal que así:

                "$folder/cpp/bin/$file_base_name.exe"
    
En mi caso, mi carpeta de archivos es "cpp" y dentro he creado una carpeta "bin" entonces, ahí se guardarán los programas.


### **COMPILAR:**

Una vez que terminas de crear tu archivo " .cpp", el siguiente paso es compilarlo, y para ello, se usa el siguiente comando:

                "g++", "$file_name", "-o", "${file_path}/$file_base_name.exe"

Esta linea de código, permite que tu archivo " .cpp" pase a ser un programa ejecutable " .exe"; en pocas palabras eso es compilar. Muy bien, para ello necesitaremos tener los compiladores ya instalados en nuestra pc, y haber agregado la carpeta donde están los compiladores en la variable de entorno "path". Para obtener los archivos puedes usar Mingw, buscar en internet el que mejor se ajuste a tu entorno de trabajo y cómo instalarlo correctamente.

Explicaré un poco el código:

**"g++"**: Es el compilador que vamos a usar para transformar, por así decirlo, nuestros archivos " .cpp" a ejecutables " .exe".

**"$file_name"**: Es el nombre del archivo a compilar, en otras palabras, el archivo con el que talvez te encuentras trabajando.

**"-o"**: Significa "renombrar", permite cambiar el nombre y extensión del archivo.

**"${file_path}/$file_base_name.exe"**: Es la dirección donde se guardará el programa y el nombre completo del mismo.

Cabe mencionar, que en el código original, entre "g++" y "$file_name" se encuentran 2 herramientas. La forma literaria correcta de expresar sería la siguiente:

                 "g++", [...] "$file_name"
                
Para una mejor explicación de este tema, he decidido ocultarlas. Las mismas serán explicadas a continuación:

### **OPCIONES GENERALES**:

Cuando se llama al compilador gcc, g++, etc., normalmente realiza el preprocesamiento, la compilación, el ensamblaje y la vinculación. Las "opciones generales" o mejor conocidas como **"overall options"**, le permiten detener este proceso en una etapa intermedia, así también optimizar y resaltar debidos procesos.

En resumen, son herramientas que permiten crear un entorno seguro, donde pueda correr nuestro programa, te dan control sobre los diferentes procesos a la hora de ejecutar tu porgrama.

Para el código que vamos a usar, he agregado uno, que me parece importante: 

**"-Wall"**: Es la abreviatura de "warn all"; activa algunas advertencias que g++ puede informarle sobre su compilado. Por lo general, es una buena idea, especialmente si es un principiante, porque comprender y corregir esas advertencias puede ayudarlo a solucionar muchos tipos diferentes de problemas en su código. (*Obtenido de [Stackoverflow](https://stackoverflow.com/questions/2408038/what-does-wall-in-g-wall-test-cpp-o-test-do)*)

Existen muchos tipos de "opciones generales", mientras siga aprendiendo sabrá cuáles son mejores para su entorno de trabajo y cuáles no, se pueden agregar un sin número de opciones. 

Este es un tema que no abarcaré a profundidad, porque depende mucho de la necesidad, el tipo de programa, el número de tareas, la extensibilidad, etc., que se use en su proyecto. Sea el caso, en la siguiente página [Linux die net](https://linux.die.net/man/1/gcc) encontrará más información (*demasiada*).

Ahora bien, el siguiente no es una herramienta en sí, sino más bien, una etiqueta:

![Screenshot](Screenshots/10.png)

Obtenido de [Riptutorial](www.riptutorial.com/Download/cplusplus.pdf).

**"stc=c++17"**: Esto representa la versión del compilador que se está usando. Puede cambiar a cualquier versión siempre que tenga las actualizaciones correspondientes. 

En caso que no le funcione el código, puede que sea por esto, aseguresé de tener actualizado su fichero. Otra alternativa, es usar otra versión, la versión más usada es la del 2011 y 2014, porque implementan muchas características nuevas.

Si desea modificar el código, debería quedarle así:

Para la versión de 2011:

                "g++", "-Wall", "-std=c++11", "$file_name"
                
Para la versión de 2014:
              
                "g++", "-Wall", "-std=c++14", "$file_name"

Si está empezando, dejarlo así por defecto es la mejor opción. Para más información consulte el siguiente enlace [Riptutorial C++](www.riptutorial.com/cplusplus)


### **TERMINAL EXTERNO:**

Como ya muchos sabrán, Sublime Text, tiene una consola integrada, el problema con esta consola es que no permite insertar datos, haciendo imposible interactuar con nuestros programas. Por eso, la mejor opción es usar la consola externa o "cmd".

Muy bien, el código llama una consola externa que ejecuta el programa antes compilado, en este casco, la orden es:

                "&&", "start", "cmd eme", "${file_path}/$file_base_name.exe"
                
Bien, vamos explicando lo más importante:

**"&&"**: Significa "y", permite conectar el código. En otras palabras, gracias a este operador, podemos compilar y ejecutar nuestro programa.

**"star"**: Como el nombre lo dice, inicia la consola donde se ejecutará nuestro programa.

**"cmd eme"**: Es la consola que ejecuta el programa. La consola se llama "cmd eme" porque así la renombré yo. Pueden poner cualquier nombre, por ejemplo: "cmd /myproject" "cmd myproject", " myproject"), o dejar solo " ". Ten en cuenta que siempre hay un espacio en medio de las comillas dobles. Eso es lo que permite abrir una consola que puedes personalizar.

![Screenshot](Screenshots/5.png)

Si vas a poner otro nombre asegúrate de dejar un espacio después de la primera comilla, el código debería verse así:

                "&&", "start", " Myproject", "${file_path}/$file_base_name.exe"
                
De esa forma se generará una consola con el nombre que hayas puesto y que se puede personalizar.

![Screenshot](Screenshots/6.png)

### **¿Porque renombrar la consola con la que trabajo?**

En pocas palabras porque es más cómodo. Esta consola la puedes editar a tu entorno de trabajo y gusto personal.
Dando click derecho en la parte superior de la ventana y yendo a "propiedades" puedes modificar el tamaño y posición de la ventana, el tipo, tamaño y color de la fuente y fondo. Y lo mejor, es que si abres un nuevo proyecto la consola seguirá siendo la misma, gracias a que los cambios se guardan en el registro del sistema, como un nuevo perfil.

![Screenshot](Screenshots/7.png)

Sin embargo, si quieres la consola por defecto, solo elimina "cmd eme", tal cual, tu código quede:

                "&&", "start", "$folder/bin/$file_base_name.exe"

De esta manera, tu programa se ejecutará en la consola predeterminada. No recomiendo esta opción porque sucede un error cuando vas a guardar un archivo.

Te explicaré en qué consiste y cómo se puede solucionar.

### **CÓMO NOMBRAR A TUS ARCHIVOS:**

Es importante la manera en cómo nombras a los archivos con los que trabajas y existen muchas formas de hacerlo.

No obstante, cuando se programa es posible que un compilador no sepa diferenciar entre "espacios", "puntos", "guiones", etc. Por lo que, cómo muchos sabrán, lo mejor es nombrar a tu archivo con guiones bajos, una sola palabra o nombre, como: main.cpp, myproject.cpp, mycat_and_mydog.cpp, A.cpp; o incluso con números: 1.cpp, 1_3.cpp.

Si nombras así tus archivos no tendrás problemas eliminando "cmd eme" (visto en la sección anterior) de tu código, ya que el compilador y la consola predeterminada podrán reconocer tu programa. Tú codigo puede quedar así sin ningún problema.
    
                "&&", "start", "${file_path}/$file_base_name.exe"

Sin embargo, si eliminas el comando "cmd eme" y estás acostumbrado a nombrar a tus archivos de la siguiente manera: "My project.cpp", "ultimo intento.cpp", "Ejercicio 02.cpp" "1.5.3.cpp"; tendrás un problema, el archivo se compilará normalmente en tu fichero, **pero**, la consola por defecto no reconocerá el programa debido a que tiene espacios y si el nombre tiene puntos, te saldrá un error el cual no reconoce la extensión del fichero.

Ahora bien, **¿cómo soluciono este inconveniente?**

La respuesta obvia es, debes aprender a nombrar a tus archivos usando guiones bajos y nombres de una sola palabra o que estén unidos.

Por otro lado, puedes crear una consola personalizada (visto en la sección anterior). Esto a más de que se ve bonita y la puedes personalizar. Admite los nombres a los que estás acostumbrado, ya sea con guiones, puntos, espacios, etc., entonces, si no quieres lidiar con el problema de los nombres, tu código debería verse así:
               
               "&&", "start", " Myproject" "$folder/bin/$file_base_name.exe"
               
De esa forma podrás guardar, compilar y ejecutar tus programas sin ningún problema desde el editor de texto.

![Screenshot](Screenshots/8.png)

**Sin embargo**, si todavía deseas borrar "cmd eme", otra forma de solucionar este inconveniente es agregando el comando "call" a cualquiera de los dos códigos, así debería quedarte:

               "&&", "start", "call", "$folder/bin/$file_base_name.exe"

Este comando inicia la consola predeterminada y después hace un llamado a tu programa, en pocas palabras, puedes ejecutar tu programa así tenga un nombre con puntos o espacios.

![Screenshot](Screenshots/9.png)

El único problema (esto es un problema personal) es el extenso título que tiene la ventana.

Cómo podrán apreciar en la imagen anterior, el programa nos muestra la dirección completa de la consola y del programa que se ejecuta. Esto no es malo, es muy bueno si te interesa esa información, te permite saber de dónde se ejecuta el programa y puede ayudarte a tener un mejor control en tu trabajo. Además, también la puedes personalizar, son todas ventajas. A pesar de ello, prefiero una consola limpia, incluso en el título.

### **INSTRUCCIONES:**


