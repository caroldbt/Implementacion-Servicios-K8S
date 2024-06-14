# Implementación de Servicios en Kubernetes con MySQL, PhpMyAdmin y una Aplicación Web PHP

## Descripción:
Esta práctica tiene como objetivo la implementación de un entorno de desarrollo completo utilizando Kubernetes. El entorno incluye un servicio MySQL, una interfaz de administración de bases de datos con PhpMyAdmin, y una aplicación web PHP conectada a la base de datos. A continuación, se describen los archivos de configuración y las imágenes de Docker necesarias para desplegar este entorno.

## Instrucciones:
1. Despliegue de MySQL: Aplique los manifiestos de Kubernetes para el despliegue, PVC, PV y servicio de MySQL.
2. Despliegue de PhpMyAdmin: Aplique los manifiestos de Kubernetes para el despliegue y servicio de PhpMyAdmin.
3. Despliegue de la Aplicación Web PHP: Aplique los manifiestos de Kubernetes para el despliegue y servicio de la aplicación web PHP.
4. Configuración del Dockerfile: Construya la imagen Docker usando el Dockerfile provisto y publíquela en su registro Docker local o remoto.

## Configuración
Iniciamos nustro cluster minikube:
```
minikube start

```
Configure el entorno Docker para usar el demonio Docker de Minikube:
```
eval $(minikube docker-env)

```
Obtenga la dirección IP de Minikube y reemplácela en el archivo deployment-weapp.yaml, línea 17
```
minikube ip

```
Habilitar las Métricas en Minikube:
```
minikube addons enable metrics-server

```
## Construcción e implementación
Construir imagen Docker, ubicandonos detro de nuestra carpeta weapp:
```
docker build --tag $(minikube ip):5000/php-webserver .
```
# Escalando
Dentro de nuestra carpeta Despligue lanzamos el siguiente comando:
```
kubectl apply -k ./

```
Espere unos minutos hasta que Autoescale la implementación y luego verifique la cantidad de los nuevos pods creados:
```
kubectl get pods
```
Revisamos los servicios:
```
kubectl get services
```
Probamos y verificamos el servicio desplegado:
```
minikube service php-webserver
minikube service phpmyadmin
```

