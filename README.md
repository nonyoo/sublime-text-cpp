# C++ build system for Sublime Text.

Compile and run in a external terminal. Only for Windows.

INFORMACIÓN:

Es de autoría propia y el que mejor me ha servido.

IMPORTANTE:

Si revisaron el archivo verán que hay dos códigos, ambos funcionan igual, la única diferencia se encuentra en donde se guarda el programa compilado.

1. DEFAULT SYSTEM BUILT:
Guarda el programa en la misma carpeta donde se encuentra el archivo. Si cuando programas usas pocos archivos está es la mejor opción. Caso contrario te puede interesar el segundo código.

![Screenshot](Screenshots/1.png)

2. SECOND SYSTEM BUILT:
Se encarga de guardad el programa compilado en una carpeta diferente. Este es el sistema de compilación que yo uso, me permite ordenar mejor mis diferentes archivos.

![Screenshot](Screenshots/2.png)

Explicación minusciosa del código:

                "$folder/bin/$file_base_name.exe"

"$folder": hace referencia a la carpeta general del proyecto. Como verán en la captura de pantalla, mis archivos se encuentran en la carpeta "cpp", pero la carpeta general es "C++".

![Screenshot](Screenshots/3.png)

"/bin/": hace referencia a la carpeta donde se guardan los programas. "bin" es un nombre aleatorio que yo mismo puse y puede ser cambiado por cualquier otro nombre, eso sí, aseguranse de crear primero la carpeta junto a su carpeta de archivos.

![Screenshot](Screenshots/4.png)

TERMINAL EXTERNO:

Como sabrán el código llama una consola externa que ejecuta el programa ya compilado, en este casco, la orden es:

                "&&", "start", "cmd eme", "$folder/bin/$file_base_name.exe"
Bien, vamos explicando lo más importante:

"&&": Significa "y", permite conectar el código.

"star": Como el nombre lo dice inicia la consola donde se ejecutará nuestro programa.

"cmd eme": Es la consola que ejecuta el programa. La consola se llama "eme" porque así la renombré yo, pueden poner cualquier nombre (ejemplo: "cmd /myproject" "cmd myproject"), o dejar solo "cmd ",  no olviden poner el espacio.

![Screenshot](Screenshots/5.png)

¿Porque renombrar la consola con la que trabajo?.
En pocas palabras porque es más cómodo. Esta consola la puedes editar a tu entorno de trabajo. 
Dando click derecho en la parte superior de la ventana y yendo a "propiedades" puedes modificar el tamaño y posición de la ventana, el tipo y tamaño de la fuente y el color del fondo y la letra. Y lo mejor, es que si abres un nuevo projecto, la consola seguirá siendo la misma. Debido a que los cambios se guardan en un registro de sistema, como un nuevo perfil.

Sin embargo, si quieres la consola por defecto, solo elimina "cmd eme", tal cual, tu código quede:

                "&&", "start", "$folder/bin/$file_base_name.exe"

Tu programa se ejecutará en la consola predeterminada. No recomiendo esta opción porque sucede un error con algunos archivos.
