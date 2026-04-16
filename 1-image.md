# Imagen
### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**
```
docker pull hello-world
```

<img width="1132" height="242" alt="image" src="https://github.com/user-attachments/assets/a7fa8a3d-c15b-4559-ad44-4f2cea4f3c9b" />




**¿Qué es nginx?**

Es un servidor web de código abierto, proxy inverso, balanceador de carga y caché de contenido de alto rendimiento.
# COMPLETAR 

Descargar la imagen  **nginx** en la versión **alpine**
```
docker pull nginx:alpine
```
<img width="1126" height="481" alt="image" src="https://github.com/user-attachments/assets/dcd94938-489c-4af0-babd-f2d30ef28161" />


### Listar imágenes

```
docker images
```
<img width="1698" height="231" alt="image" src="https://github.com/user-attachments/assets/20cc30e6-2382-418c-b38a-0757b759216e" />


**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 
<img width="1185" height="938" alt="image" src="https://github.com/user-attachments/assets/a9367c3f-7b9b-481a-8360-33ce118c1fae" />


# COMPLETAR

**¿Con qué algoritmo se está generando el ID de la imagen?**

El ID de la imagen se genera con el algoritmo SHA256. Esto se puede verificar en la salida del comando docker inspect hello-world, donde el campo "Id" muestra el prefijo sha256: seguido del hash de la imagen.


### Filtrar imágenes

```
docker images | grep <termino a buscar>

```
**Nota:** En Windows, el comando `grep` no está disponible, por lo que se utilizó  `findstr` como alternativa equivalente:
<img width="1278" height="184" alt="image" src="https://github.com/user-attachments/assets/c4fb2129-0126-4693-9c2b-3f8bb642f6ac" />


### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 

<img width="984" height="139" alt="image" src="https://github.com/user-attachments/assets/44ac2a54-0841-42ea-b508-3be847584e6b" />

# COMPLETAR

-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```
