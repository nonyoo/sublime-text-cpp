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
Se encarga de guardar el programa compilado en una carpeta diferente. Este es el sistema de compilación que yo uso, me permite ordenar mejor mis diferentes archivos.

![Screenshot](Screenshots/2.png)

Cómo funciona lo de guardar en otra carpeta:

Todo es gracias a esta parte del código:

                "$folder/bin/$file_base_name.exe"
Primero explicaré un poco el código, para qué tengas en cuenta lo que necesitas para usar esta opción:

"$folder/bin/": Es la dirección en donde se guarda el archivo compilado y de donde se ejecutará el programa. Si te das cuenta, leyendo ambos códigos, esta parte es la única que cambia, pero permite una organización de archivos diferente u ordenada.

"$folder": hace referencia a la carpeta general del proyecto. Como verán en la captura de pantalla, mis archivos se encuentran en la carpeta "cpp", pero la carpeta general es "C++", el comando hacer referencia a esa misma carpeta.

![Screenshot](Screenshots/3.png)

"/bin/": hace referencia a la carpeta donde se guardan los programas. "bin" es un nombre aleatorio que yo mismo puse y puede ser cambiado por cualquier otro nombre, eso sí, aseguranse de crear primero la carpeta junto a su carpeta de archivos.

![Screenshot](Screenshots/4.png)

Si quieres usar esta opción, debes asegurarte de crear una carpeta general, dentro debes crear dos carpetas uno para los archivos y otra para los programas (el nombre puede ser cualquier, pero asegúrate de cambiar en el código).

Así mismo, puedes crear una carpeta dentro de tu carpeta de archivos y cambiar el código, tal que así:

    "$folder/cpp/bin/$file_base_name.exe"
    
En mi caso, mi carpeta de archivos es "cpp" y dentro he creado una carpeta "bin" entonces, ahí se guardarán los programas.


TERMINAL EXTERNO:

Como sabrán el código llama una consola externa que ejecuta el programa ya compilado, en este casco, la orden es:

                "&&", "start", "cmd eme", "$folder/bin/$file_base_name.exe"
Bien, vamos explicando lo más importante:

"&&": Significa "y", permite conectar el código.

"star": Como el nombre lo dice inicia la consola donde se ejecutará nuestro programa.

"cmd eme": Es la consola que ejecuta el programa. La consola se llama "cmd eme" porque así la renombré yo. Pueden poner cualquier nombre, por ejemplo: "cmd /myproject" "cmd myproject", " myproject"), o dejar solo " ". Ten en cuenta que siempre hay un espacio en medio de las comillas dobles. Eso es lo que permite abrir una consola que puedes personalzar. 

![Screenshot](Screenshots/5.png)

Si vas a poner otro nombre asegúrate de dejar un espacio después de la primera comilla, el código debería verse así:

                "&&", "start", " Myproject", "$folder/bin/$file_base_name.exe"
                
De esa forma se generará una consola con el nombre que hayas puesto y que se puede personalizar.

![Screenshot](Screenshots/6.png)

¿Porque renombrar la consola con la que trabajo?.
En pocas palabras porque es más cómodo. Esta consola la puedes editar a tu entorno de trabajo. 
Dando click derecho en la parte superior de la ventana y yendo a "propiedades" puedes modificar el tamaño y posición de la ventana, el tipo y tamaño de la fuente y el color del fondo y la letra. Y lo mejor, es que si abres un nuevo projecto, la consola seguirá siendo la misma. Debido a que los cambios se guardan en un registro del sistema, como un nuevo perfil.

![Screenshot](Screenshots/7.png)

Sin embargo, si quieres la consola por defecto, solo elimina "cmd eme", tal cual, tu código quede:

                "&&", "start", "$folder/bin/$file_base_name.exe"

De esta manera, tu programa se ejecutará en la consola predeterminada. No recomiendo esta opción porque sucede un error con algunos archivos.
