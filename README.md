# Instrucciones

**1.** Renombrar los archivos .env.example de las carpetas ui y api por .env
**2.** En la carpeta api, rellenar los datos correspondientes en las variables de entorno del archivo .env con los valores correctos (tenemos que tener nuestra base de datos creada en Mongo Atlas).
**3.** Ir a la carpeta api. Hacer el build de docker: `sudo docker build -t backend -f Dockerfile.dev .`
**4.** Ya tenemos la imagen del backend. Subirla a ECR. Crear el servicio del backend en APP Runner con esta imagen (crear variables de entorno en el propio APP Runner durante la creación del servicio con los mismos valores del archivo .env). El backend tiene configurado el puerto 3080 en el Dockerfile, configurar este puerto también en APP Runner. Copiar la dirección que nos da AWS para este backend tras crear el servicio (lo necesitamos para configurar .env en la carpeta ui).
**5.** En la carpeta ui, en el archivo .env, rellenar la variable REACT_APP_BACKEND_URI con la url del punto 4 (por ej. `REACT_APP_BACKEND_URI="https://ladirecciondeAWSparaelbackend.com"`).
**6.** En la carpeta ui. Hacer el build de docker: `sudo docker build -t frontend -f Dockerfile.dev .`
**7.** Subir la imagen del frontend a ECR. Crear el servicio del frontend en APP Runner con esta imagen (el frontend usa el puerto 80, configurar en APP Runner). No hace falta configurar variables de entorno en APP Runner.
**8.** Abrir la dirección que nos da APP Runner para el frontend. La aplicación ya debería funcionar correctamente.
