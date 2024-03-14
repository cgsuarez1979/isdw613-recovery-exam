# Introduccion

El proyecto es un template básico para correr la aplicación con la invocación de servicios REST saltándose la restricción de CORS.

# Servicios Rest

Existen dos servicios REST disponibles para el Exámen de Reuperación:

- ***Listar Compras***: Este servicio proporciona una lista de compras realizadas en una tienda en línea en formato JSON.

En términos generales este será el Output de ésta llamada:

```json
[
   {
      "id":1,
      "name":"Product 1",
      "purchase-date":"2024-03-21 03:05:06.602686",
      "price":631,
      "category":"Toys"
   },
   {
      "id":2,
      "name":"Product 2",
      "purchase-date":"2024-03-16 01:18:18.276286",
      "price":672,
      "category":"Books"
   },
   {
      "id":3,
      "name":"Product 3",
      "purchase-date":"2024-03-23 21:29:20.252457",
      "price":531,
      "category":"Home"
   },
   {
      "id":4,
      "name":"Product 4",
      "purchase-date":"2024-03-20 08:53:01.644337",
      "price":429,
      "category":"Electronics"
   }
]
```

***Cada item está asociado con una categoría específica.***

- ***Crear Productos***: Este servicio expone el proceso de creacion de Productos en la misma tienda en línea.

La creación de productos requiere un body de tipo JSON similar al del siguiente ejemplo:

```json
{
    "name": "Product 1",    
    "price": "123342",
    "category": "Home"
}
```

Ambos endpoints se los accede mediante la siguiente URL:


```
https://pje4h805t4.execute-api.us-west-2.amazonaws.com/dev/purchases
```
***Es potestad del estudiante escoger el metodo HTTP mas apropiado dependiendo del caso***

## Prerequisitos

- Tener Docker instalado en el sistema operativo al cual se va a desarrollar.

## Utilizacion

- Ejecutar el siguiente comando, este sirve para crear una imagen propietaria con las configuraciones del Reverse Proxy necesarias para correr la aplicacion.

```

docker build -t my-exam-custom-image .

```

- Ejecutra el siguiente comando para correr la imagen de Docker con el Reverse Proxy y el contexto por defecto la carpeeta del proyecto:

    - En Linux/Mac
        ```
        docker run -p 8080:8080 -v $(pwd):/usr/share/nginx/html my-exam-custom-image
        ```

    - En Windows
        ```
        docker run -p 8080:8080 -v %cd%:/usr/share/nginx/html my-exam-custom-image
        ```

Se puede acceder a la siguiente URL para acceder al servidor NGINX que se encuentra ejecutando con el comando anterior:

```
    http://localhost:8080/
```

***Al utilizar un Reverse Proxy los servicios REST se encuentran disponibles bajo el mismo servidor NGINX con el siguiente endpoint (Por lo que se evitará tener errores de tipo CORS en el Exámen):***

```
http://localhost:8080/dev/purchases
```


Automáticamente cualquier cambio que se haga en el directorio o en archivos dentro del proyecto se verán reflejados.

## Rubrica para la calificación

| Aspecto a Implementar      | % de Peso |
| ----------- | ----------- |
| Listado de Productos      | 25%       |
| Filtrado de Productos   | 25%        |
| Implementación de Tabla Resumen   | 25%        |
| Invocación de Creación de Productos  | 25%        |
