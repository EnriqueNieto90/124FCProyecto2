ique90# Fundamentos de contenerización
## Actividad 2. Modificar un sitio web en ejecución

Paso 1. Partimos de la imagen construida en la acitividad anterior:
```
sudo docker image build --tag 124fcproyecto1:1.0 .
```
-Comprobar que la imagen está bien contstruida del proyecto anterior:
```
sudo docker image ls | grep 124fcproyecto1
```
-Borrar imagen:
```
sudo docker image rmi --force 124FCProyecto1
```
	
Paso 2. Ejecutar el contenedor en el puerto 8080, con el nombre 124fcproyecto2, es importante montar el directorio actual del host en el directorio /usr/share/nginx/html/ dentro del contenedor:
```
sudo docker run -d -p 8080:80 --name 124fcproyecto2 -v "$(pwd)":/usr/share/nginx/html 124fcproyecto1:1.0
```
-Comprobar que se ha ejecutado el contenedor
```
sudo docker container ls
```
-Borrar contenedor (prueba)
```
sudo docker container rm --force 124fcproyecto1
```

Paso 3. Comprobación: http://localhost:8080

	
Paso 4. Se pide modificar el fichero index.html desde el host usando visual studio code:

- Entrar en Visual Studio Code 
- Abrir el fichero index.html
- Modificar el index.html añadiendo un párrafo nuevo
- Guardar cambios

Paso 5. Se han producido cambios, http://localhost:8080

## Crear y subir imagen a dockerHub

- Creamos la imagen del contenedor editado y comprobamos que se ha creado
```
sudo docker commit 124FCProyecto2 124fcproyecto2:1.0
docker images
```
- Guardamos la imagen en un archivo.tar
```
sudo docker save -o 124fcproyecto2version2.tar 124fcproyecto2:1.0
```
- Iniciamos sesión en dockerHub con el navegador
```
sudo docker login
```
- Creamos el repositorio 124fcproyecto2 en dockerHub desde su web
- Creamos una etiqueta a la imagen que vamos a subir
```
sudo docker tag 124fcproyecto2:1.0 enriquenieto90/124fcproyecto2:1.0
```
- Subimos la imagen a dockerHub
```
sudo docker push enriquenieto90/124fcproyecto2:1.0
```
- Enlace a la imagen del proyecto2 en dockerHub
```

```





