# AOS_Practica2

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