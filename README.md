# AOS_Practica2

En esta practica se planea desplegar y testear los tres servicios utilizados para el "Sistema de gestión de talleres de mecánica rápida."

La primera forma de despliegue es mediante docker-compose y las imagenes creadas y subidas al DockerHub. Ver apartado de Docker.

La sefunda forma de despliegue es mediante un cluster de kubernetes. Para eelo se ha hecho uso de software adicional. Ver apartado de Kubernetes.

## Software adicional para utilizar kubernetes
- [Minikube]()
- [Kompose](https://kompose.io/installation/)


# Docker

En el fichero de docker-compose.yaml estan los tres servicios que utilizan las imagenes creadas.

## Imagenes utilizadas de dockerHub
- [Frontend](https://hub.docker.com/r/geanf13/frontend)
- [Backend](https://hub.docker.com/r/geanf13/backend)
- [Proxy](https://hub.docker.com/r/geanf13/proxy)

## Comprobacion de los servicios

Para levantar el servicio:
```bash
docker compose up
```
Dos maneras de comprobar el funcionamiento:
- Interfaz grafica con el servicio de Swagger en la siguiente direccion: http://127.0.0.1:8000 
- Con Postman, haciendo la siguiente peticion: 

    ``` postman
    GET http://0.0.0.0:4010/clientes/P02-039-C
    ```

# Kubernetes

Antes de espezar minikube se debe comprobar que el driver predefinido para minikube es docker. Se puede configurar con la siguiente instruccion.
```bash
minikube config set driver docker
```
Los archivos necesarios para minikube se han creado utilizando Kompose y se encuentran en la carpeta minikube del repositorio. 
## Instrucciones de despliegue
1. Iniciar minikube
    ```bash
    minikube start
    ```
2. Creacion de recursos en Kubernetes
    ```bash
    kubectl apply -f
    ```
3. Comprocacion de correcta creacion de pods y servicios
    ```bash
    kubectl get pods
    kubectl get svc
    ```

## Comprobacion de los servicios    

Dos maneras de comprobar el funcionamiento, pero primero es necesario encontrar la direccion del frontend y del backend con las siguientes instrucciones, respectivamente
```bash
minikube service frontend --url
minikube service backend --url
```
- Interfaz grafica con el servicio de Swagger en la direccion proporcionada en la primera instruccion. 
- Con Postman, haciendo un GET en la direccion proporcionada en la segunda instruccion. 
