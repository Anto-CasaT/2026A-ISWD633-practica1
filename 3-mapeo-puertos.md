# Mapeo de puertos
El mapeo de puertos es un mecanismo que permite redirigir el tráfico de red desde un puerto en el host (tu máquina local o servidor) hacia un puerto específico en un contenedor Docker.
Por ejemplo, supongamos que tienes un contenedor que ejecuta un servidor web en el puerto 80 dentro del contenedor, pero quieres acceder a ese servidor desde tu navegador en la máquina host. Puedes usar el mapeo de puertos para redirigir el tráfico del puerto 80 del contenedor al puerto 3000 en el host. De esta manera, cuando accedas a http://localhost:3000 en tu navegador, el tráfico se dirigirá al servidor web dentro del contenedor en el puerto 80.

![mapeo](mapeoPuertos.PNG)

### Para crear un mapeo de puertos (puerto host y puerto contenedor)
El mapeo de puertos se especifica al ejecutar un contenedor Docker utilizando la opción -p o --publish seguida de los puertos que deseas mapear
```
docker run -d --name <nombre contenedor> -p <puerto host>:<puerto contenedor> <nombre imagen>:<tag>

```
Crear un contenedor a partir de la imagen nginx version alpine con el mapeo de puertos del ejemplo gráfico, host 3000 y contenedor 80
```
docker run -d --name serv-web -p 3000:80 nginx:alpine
```

<img width="866" height="97" alt="image" src="https://github.com/user-attachments/assets/fd8cfded-9ca5-400f-9a87-c3c938966908" />


# COLOCAR UNA CAPTURA DE PANTALLA  DEL ACCESO http://localhost:3000
<img width="1870" height="648" alt="image" src="https://github.com/user-attachments/assets/1482b10f-9a13-4e52-8fb3-3d16a745287d" />


### Para mapear más de un puerto

```
docker run -d --name <nombre contenedor> -p <puerto host 01>:<puerto contenedor 01> -p <puerto host 02>:<puerto contenedor 02> <nombre imagen>:<tag>
```

Crear un contenedor a partir de la imagen rabbitmq version management-alpine, para este mapeo de puertos usar en el host los mismos puertos del contenedor.
```
docker run -d --name srv-rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:management-alpine
```
<img width="1262" height="486" alt="image" src="https://github.com/user-attachments/assets/919a4794-d2f6-41f3-935d-f8f38f861856" />
<img width="1919" height="756" alt="image" src="https://github.com/user-attachments/assets/0257a2ea-d5a1-465f-a907-090c31bdecfd" />
<img width="1919" height="1121" alt="image" src="https://github.com/user-attachments/assets/ac33e502-c280-42a6-ba07-b08f48873d51" />



### Usando una forma más semántica cuando se especifican puertos

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> <nombre imagen>:<tag> 
```
### Publicando todos los puertos
```
docker run -P -d --name <nombre contenedor> <nombre imagen>:<tag> 
```

-P: le indica a Docker que asigne automáticamente puertos aleatorios en tu host para todos los puertos expuestos por el contenedor.

**Recordar**
No puedes mapear puertos a un contenedor existente directamente después de su creación con Docker. El mapeo de puertos debe especificarse en el momento de crear y ejecutar el contenedor.

### Crear contenedor de Jenkins puertos contenedor: 8080 (interface web) y 50000 (comunicación entre nodos) imagen: jenkins/jenkins:alpine3.18-jdk11
```
docker run -d --name srv-jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins
```
<img width="1303" height="976" alt="image" src="https://github.com/user-attachments/assets/98929b34-feaf-4891-b335-f2390cd7e622" />
<img width="1894" height="1094" alt="image" src="https://github.com/user-attachments/assets/9bc7d8d9-0354-43b6-9752-ebc96463d798" />


### ¿Cómo obtener la contraseña solicitada?
Para obtener la contraseña solicitada es necesario ingresar al contenedor.

![Imagen](jenkins.PNG)

```
docker exec srv-jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```
<img width="1102" height="127" alt="image" src="https://github.com/user-attachments/assets/8124ad88-428c-43eb-a869-a06ce9308288" />


<img width="1915" height="1067" alt="image" src="https://github.com/user-attachments/assets/8e4c26ab-5791-407e-8926-1aba3cf62715" />


