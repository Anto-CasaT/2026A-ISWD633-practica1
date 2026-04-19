# Mi Aprendizaje

- `docker pull <imagen>` descarga una imagen desde Docker Hub 
y que si no se especifica un tag, se descarga la versión `latest` por defecto.

- `docker inspect <imagen>` muestra información detallada en 
formato JSON y que el ID de la imagen se genera con el algoritmo **SHA256**.

- `docker images` lista todas las imágenes descargadas y que 
en Windows el comando `grep` no está disponible, por lo que se usa 
`findstr` como alternativa.

-  `docker create` crea un contenedor sin iniciarlo, mientras 
que `docker run` lo crea y ejecuta en un solo paso.

- `docker run -d` ejecuta un contenedor en segundo plano 
(modo detach), permitiendo seguir usando la terminal.

- el mapeo de puertos con `-p <host>:<contenedor>` debe 
especificarse al momento de crear el contenedor, no después.

-  `docker exec -it <contenedor> bash` permite ingresar a la 
terminal interactiva de un contenedor en ejecución.

-  `docker rm -f` permite eliminar un contenedor que está 
en ejecución forzadamente pero que lo mejor es primero detener el contenedor
y luego eliminarlo solo con `docker rm`.
