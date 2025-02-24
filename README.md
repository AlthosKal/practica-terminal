# practica-terminal

En este archivo README.md se describirá el proceso evaluativo planteado por el Instructor Carlos Navia

### **Nota
Para ingresar al codespace presione "." en la ventana principal del repositorio en GitHub.

### **Ejercicio 1:Navegacion y visualización de Directorios
```bash
@AlthosKal ➜ /workspaces $ pwd
/workspaces
@AlthosKal ➜ /workspaces $ ls -lah
total 20K
drwxr-xrwx+ 5 codespace root      4.0K Feb 24 17:34 .
drwxr-xr-x  1 root      root      4.0K Feb 24 17:32 ..
drwxr-xr-x+ 4 codespace root      4.0K Feb 24 17:32 .codespaces
drwxrwxrwx+ 2 codespace codespace 4.0K Feb 24 17:34 .oryx
drwxrwxrwx+ 3 codespace root      4.0K Feb 24 17:34 practica-terminal
@AlthosKal ➜ /workspaces $ cd practica-terminal/
@AlthosKal ➜ /workspaces/practica-terminal (main) $ pwd
/workspaces/practica-terminal
@AlthosKal ➜ /workspaces/practica-terminal (main) $ cd ~
@AlthosKal ➜ ~ $ 
```

### **Ejercicio 2: Creación y Manipulación de Srchivos y Directorios
```bash
@AlthosKal ➜ ~ $ mkdir ProyectoCLI
@AlthosKal ➜ ~ $ cd ProyectoCLI/
@AlthosKal ➜ ~/ProyectoCLI $ mkdir src docs
@AlthosKal ➜ ~/ProyectoCLI $ cd docs/
@AlthosKal ➜ ~/ProyectoCLI/docs $ echo "Este es el README del ProyectoCLI" > README.txt
@AlthosKal ➜ ~/ProyectoCLI/docs $ cp README.txt ../src/
@AlthosKal ➜ ~/ProyectoCLI/docs $ cd ../src
@AlthosKal ➜ ~/ProyectoCLI/src $ mv README.txt INFO.txt
@AlthosKal ➜ ~/ProyectoCLI/src $ rm -rf ../docs/
@AlthosKal ➜ ~/ProyectoCLI/src $ cd ..
@AlthosKal ➜ ~/ProyectoCLI $ ls
src
```

### **Ejercicio 3: Enlaces Simbólicos y Manejo de Rutas
```bash
@AlthosKal ➜ /workspaces/practica-terminal (main) $ cd ..
@AlthosKal ➜ ~ $ echo "Hello World" > archivo_original.txt
@AlthosKal ➜ ~ $ ln -s archivo_original.txt enlace.txt
@AlthosKal ➜ ~ $ readlink enlace.txt 
archivo_original.txt
@AlthosKal ➜ ~ $ basename archivo_original.txt
archivo_original.txt
@AlthosKal ➜ ~ $ dirname "$(realpath archivo_original.txt)"
/home/codespace
```

## **Ejercicio 4: Búsqueda y Filtrado de Archivos
```bash
@AlthosKal ➜ ~ $ find *.txt
archivo_original.txt
enlace.txt
@AlthosKal ➜ ~ $ sudo updatedb
@AlthosKal ➜ ~ $ locate archivo_original.txt
/home/codespace/archivo_original.txt
@AlthosKal ➜ ~ $ whereis bash
bash: /usr/bin/bash /etc/bash.bashrc /usr/share/man/man1/bash.1.gz
```

## **Ejercicio 5: Visualizacion y Redirección de contenido

```bash
@AlthosKal ➜ ~ $ cat archivo_original.txt 
Hello World
@AlthosKal ➜ ~ $ less archivo_original.txt
@AlthosKal ➜ ~ $ more archivo_original.txt
Hello World
@AlthosKal ➜ ~ $ cat archivo_original.txt | tee copia.txt
Hello World
@AlthosKal ➜ ~ $ cat copia.txt
Hello World
```

## **Ejercicio 6: Gestión de Atributos y Eliminación Segura

```bash
@AlthosKal ➜ ~ $ sudo chattr +i copia.txt
@AlthosKal ➜ ~ $ lsattr copia.txt 
----i---------e----- copia.txt
@AlthosKal ➜ ~ $ echo "Intento de modificación" >> copia.txt
bash: copia.txt: Operation not permitted
@AlthosKal ➜ ~ $ rm copia.txt
rm: cannot remove 'copia.txt': Operation not permitted
@AlthosKal ➜ ~ $ sudo chattr -i copia.txt
@AlthosKal ➜ ~ $ shred -u -v copia.txt 
shred: copia.txt: pass 1/3 (random)...
shred: copia.txt: pass 2/3 (random)...
shred: copia.txt: pass 3/3 (random)...
shred: copia.txt: removing
shred: copia.txt: renamed to 000000000
shred: 000000000: renamed to 00000000
shred: 00000000: renamed to 0000000
shred: 0000000: renamed to 000000
shred: 000000: renamed to 00000
shred: 00000: renamed to 0000
shred: 0000: renamed to 000
shred: 000: renamed to 00
shred: 00: renamed to 0
shred: copia.txt: removed
```

## **Ejercicico 7: Script Interactivo con ```read```
```bash
@AlthosKal ➜ ~ $ vim saludo.sh
@AlthosKal ➜ ~ $ cat saludo.sh 
#!/bin/bash
echo "Por favor Ingresa tu nombre"
read NOMBRE
echo "Hola $NOMBRE. ¡Bienvenido al mundo de la linea de comandos!"
@AlthosKal ➜ ~ $ chmod 777 saludo.sh 
@AlthosKal ➜ ~ $ ./saludo.sh 
Por favor Ingresa tu nombre
Yeferson Agudelo Castaño
Hola Yeferson Agudelo Castaño. ¡Bienvenido al mundo de la linea de comandos!
```