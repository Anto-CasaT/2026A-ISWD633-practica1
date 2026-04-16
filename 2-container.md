# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine
```
docker create --name srv-web nginx:alpine
```

<img width="785" height="128" alt="image" src="https://github.com/user-attachments/assets/c1c2f5aa-0c76-442c-b5e7-52d9e41e7e91" />


Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world
```
docker create hello-world
```
<img width="1027" height="253" alt="image" src="https://github.com/user-attachments/assets/a72f5601-f344-47eb-8f3e-279f9b883196" />



### Listar los contenedores ejecutándose o no

```
docker ps -a
```
<img width="1392" height="118" alt="image" src="https://github.com/user-attachments/assets/727f81cd-0ad7-4715-a057-ee14155ad324" />

### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```
Iniciar el contenedor srv-web 
```
docker start srv-web
```
<img width="500" height="135" alt="image" src="https://github.com/user-attachments/assets/b1a64452-d059-450d-a9d8-332aa90543f4" />


### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```
<img width="1355" height="84" alt="image" src="https://github.com/user-attachments/assets/f870d114-bee5-4aa5-91e0-d0a1b1420abb" />


### Para detener un contenedor

```
docker stop <nombre contenedor>
```
<img width="426" height="93" alt="image" src="https://github.com/user-attachments/assets/62a69fc1-7da0-4fb3-aa6c-910cf08db8b3" />


### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](dockerRun.PNG)
Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine

```
docker run --name srv-web2 nginx:alpine
```
<img width="1177" height="719" alt="image" src="https://github.com/user-attachments/assets/d38216a2-8fcc-42c5-9cfd-0364c1a638ec" />

<img width="1542" height="245" alt="image" src="https://github.com/user-attachments/assets/571c0511-8e36-4f83-8e0c-9a659fde99e9" />

**¿Qué sucede luego de la ejecución del comando?**

La terminal no permite ingresar comandos ya que el contenedor se está ejecutando en primer plano y este captura todas las entradas de la terminal

Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine

```
docker run -d --name srv-web-3 nginx:alpine
```
<img width="911" height="106" alt="image" src="https://github.com/user-attachments/assets/0fb65215-6daa-4c5c-b9b1-bd44ad85cd5a" />

<img width="1638" height="167" alt="image" src="https://github.com/user-attachments/assets/ec048550-8a75-4bda-8d72-9a7791df9d9f" />

### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 
```
docker rm optimistic_antonelli
```
<img width="886" height="218" alt="image" src="https://github.com/user-attachments/assets/2d238af7-1ffa-46af-87e0-ec5b48893daa" />


Verificar que el contenedor que se eliminó
```
docker ps -a
```

<img width="1679" height="186" alt="image" src="https://github.com/user-attachments/assets/0bc76800-c042-49ff-8a95-de2653d4102c" />


### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 
```
docker rm -f srv-web-3
```

<img width="549" height="88" alt="image" src="https://github.com/user-attachments/assets/60f213fe-428f-4e0e-a2e9-7851c0349e4f" />


Verificar que el contenedor que se eliminó
```
docker ps -a
```

<img width="1649" height="189" alt="image" src="https://github.com/user-attachments/assets/323a5dd4-0f13-41cb-8fa3-f18ab6ac1f10" />


### Para inspecionar un contenedor 
```
docker inspect srv-web
```
Inspeccionar el contenedor **srv-web** 
<img width="1699" height="888" alt="image" src="https://github.com/user-attachments/assets/731146fb-8f43-4b96-890a-a6ca58e6b6b0" />
