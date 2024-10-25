# Dockerized Spring Web Application

Este repositorio contiene una aplicación web básica de Spring, configuración de Docker e instrucciones para desplegar la aplicación tanto localmente como en AWS utilizando Docker. Este proyecto demuestra cómo contenerizar una aplicación Spring, subir la imagen del contenedor a DockerHub y desplegarla usando Docker Compose.

## Tabla de Contenidos

1. Arquitectura del Proyecto
2. Proceso de Configuración
3. Creación de Imagen Docker
4. Ejecución de Contenedores Localmente
5. Configuración de Docker Compose
6. Despliegue en AWS
7. Subida de Imagen a DockerHub
8. Pruebas
9. Capturas de Pantalla y Logs

---

## Ejecución de Contenedores Localmente

Para ejecutar el contenedor de la aplicación Spring en tu entorno local, sigue estos pasos:

1. Asegúrate de haber creado la imagen Docker utilizando el siguiente comando:

   ```
   docker build -t spring-app:1.0 .
   ```

2. Luego, ejecuta el contenedor con el siguiente comando:

   ```
   docker run -p 8080:8080 spring-app:1.0
   ```

3. Ahora, puedes acceder a la aplicación visitando `http://localhost:8080/greeting` en tu navegador web. Verás una respuesta JSON con el mensaje de saludo.

4. Para ver los logs del contenedor mientras está en ejecución:

   ```
   docker logs <container-id>
   ```

---

## Configuración de Docker Compose

Docker Compose permite orquestar contenedores de forma más sencilla, definiendo todos los servicios que tu aplicación necesita en un solo archivo (`docker-compose.yml`).

1. Verifica que el archivo `docker-compose.yml` esté correctamente configurado en el proyecto. Un ejemplo de archivo puede ser el siguiente:

   ```
   version: '3'
   services:
     web:
       image: spring-app:1.0
       ports:
         - "8080:8080"
   ```

2. Ejecuta el siguiente comando para iniciar la aplicación con Docker Compose:

   ```
   docker-compose up
   ```

3. Esto iniciará la aplicación y expondrá el puerto 8080. Puedes acceder nuevamente a `http://localhost:8080/greeting`.

---

## Despliegue en AWS

### Pasos para Desplegar la Aplicación en AWS ECS (Elastic Container Service)

1. **Crear un clúster de ECS en AWS**:
   - Accede a la consola de AWS y navega a ECS.
   - Crea un nuevo clúster y selecciona "EC2 Linux + Networking" para desplegar contenedores en instancias EC2.

2. **Subir la imagen a un repositorio**:
   - Sube la imagen de Docker a DockerHub o Amazon ECR (Elastic Container Registry).
   - Si prefieres DockerHub, utiliza el siguiente comando:
     ```
     docker tag spring-app:1.0 <dockerhub-username>/spring-app:1.0
     docker push <dockerhub-username>/spring-app:1.0
     ```

3. **Configurar la tarea en ECS**:
   - Crea una definición de tarea en ECS.
   - Proporciona la URL de la imagen de Docker desde DockerHub o ECR.
   - Configura los recursos y el número de tareas que deseas ejecutar.

4. **Configurar las reglas de seguridad**:
   - Configura el grupo de seguridad de la instancia EC2 para permitir tráfico en el puerto 8080 (o cualquier otro puerto que hayas expuesto).
   - Asegúrate de que las instancias de EC2 estén configuradas con una política de IAM que les permita extraer imágenes de Docker desde el registro.

5. **Iniciar el servicio**:
   - Inicia el servicio ECS para ejecutar las tareas basadas en tu definición.
   - Accede a la aplicación en la dirección pública del clúster de ECS.

---

## Subida de Imagen a DockerHub

Sigue estos pasos para subir tu imagen de Docker a DockerHub:

1. Inicia sesión en DockerHub desde tu terminal:

   ```
   docker login
   ```

2. Etiqueta tu imagen local con tu nombre de usuario en DockerHub:

   ```
   docker tag spring-app:1.0 <dockerhub-username>/spring-app:1.0
   ```

3. Sube la imagen a DockerHub:

   ```
   docker push <dockerhub-username>/spring-app:1.0
   ```

4. Ahora tu imagen está disponible en DockerHub y puede ser utilizada para desplegar la aplicación en cualquier entorno.

---

## Pruebas

La opción de pruebas para el sistema es en el link de acceso de AWS con el puerto 42000 y debe aparecer una imagen como esta

![image](https://github.com/user-attachments/assets/41e13bf7-4a32-4b8c-9500-caff8b11662b)


---

## Capturas de Pantalla y Logs

![image](https://github.com/user-attachments/assets/f30c9c71-c085-41f0-a1e8-9626008854de)


### Capturas de Pantalla

Aquí tienes una captura de pantalla que muestra la aplicación Spring en ejecución:

![image](https://github.com/user-attachments/assets/5fd95dc5-332f-4eb9-bb98-edfb2b09617f)

## Contacto

Para cualquier duda o pregunta sobre este proyecto, puedes contactarme en: [edward.francia-g@mail.escuelaing.edu.co](mailto:edward.francia-g@mail.escuelaing.edu.co)
