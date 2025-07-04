Aplicación API de Gestión de Artículos
Esta aplicación es una API RESTful desarrollada con Spring Boot para gestionar un catálogo de artículos. Actualmente, permite realizar operaciones CRUD completas sobre los artículos. La funcionalidad de gestión de pedidos (carrito de compras) está en desarrollo.

Características Principales
Gestión de Artículos (API Operativa):

Crear nuevos artículos.

Listar todos los artículos existentes.

Obtener detalles de un artículo específico por su ID.

Actualizar información de un artículo existente.

Eliminar artículos.

Gestión de Pedidos (En Desarrollo):

La API para el carrito de compras (pedidos) está en proceso de implementación.

Tecnologías Utilizadas
Backend:

Java 17

Spring Boot 3.2.5

Spring Data JPA

Hibernate 6.4.4.Final

Maven (Gestor de dependencias)

Base de Datos:

MySQL / MariaDB (configurado para articulos_db)

MySQL Connector/J (Driver JDBC)

HikariCP (Pool de conexiones)

Estructura del Proyecto
El proyecto sigue una arquitectura en capas (controller, service, repository, model) para una clara separación de responsabilidades:

src/main/java/com/ejemplo/
├── articulos/
│   ├── controller/       # Controladores REST para Artículos
│   ├── model/            # Entidades JPA para Artículos (Articulo.java)
│   ├── repository/       # Repositorios Spring Data JPA para Artículos
│   └── service/          # Lógica de negocio para Artículos
│       └── ArticuloApiApplication.java # Clase principal de la aplicación
└── pedidos/              # Paquete para la funcionalidad de Pedidos (en desarrollo)
    ├── controller/
    ├── model/
    ├── repository/
    └── service/
src/main/resources/
├── application.properties  # Configuración de la aplicación y la base de datos
└── ...
pom.xml                   # Archivo de configuración de Maven

Configuración y Ejecución
Requisitos Previos
Java Development Kit (JDK) 17 o superior.

Apache Maven (instalado y configurado en el PATH del sistema).

Un servidor MySQL o MariaDB en ejecución (por defecto, se espera en localhost:3306).

Una base de datos llamada articulos_db creada en tu servidor MySQL/MariaDB.

Pasos de Instalación
Clonar dos Repositorios:


Repositorio Para el Front
git clone <https://github.com/P4154N0/Proyecto_front_java_talentotech.git>

Repositorio Para el Back
git clone <https://github.com/P4154N0/Proyecto_api_back_java_talentotech.git>
cd articulo-api-mysql-funcional # Navega a la carpeta raíz del proyecto

Configurar la Base de Datos:

Asegúrate de que tu servidor MySQL/MariaDB esté en ejecución.

Crea la base de datos articulos_db si aún no existe. Puedes usar un cliente SQL (phpMyAdmin, MySQL Workbench, etc.) o la línea de comandos:

Comando SQL:
CREATE DATABASE IF NOT EXISTS articulos_db;

La aplicación se conectará con el usuario root y contraseña vacía (por defecto, si no la has cambiado en application.properties).

Configurar application.properties:
Abre src/main/resources/application.properties y verifica la configuración de la base de datos:

spring.datasource.url=jdbc:mysql://localhost:3306/articulos_db?useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update # Esto creará/actualizará las tablas automáticamente
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect # Se recomienda MySQLDialect para MySQL 8+

Nota: Si tu MySQL es versión 8 o superior, puedes cambiar org.hibernate.dialect.MySQL8Dialect a org.hibernate.dialect.MySQLDialect como sugiere el log de Spring Boot.

Construir el Proyecto:
Desde la carpeta raíz del proyecto (articulo-api-mysql-funcional), ejecuta Maven para compilar y empaquetar:

mvn clean install

Esto descargará las dependencias, compilará el código y generará el archivo JAR ejecutable.

Ejecutar la Aplicación:
Una vez que el build sea exitoso, puedes iniciar la aplicación Spring Boot:

mvn spring-boot:run

La aplicación se iniciará en http://localhost:8080.

Endpoints de la API
Puedes usar herramientas como Postman, Insomnia o curl para probar los endpoints.

Artículos
Base URL: http://localhost:8080/api/articulos

POST /api/articulos

Descripción: Crea un nuevo artículo.

Body (JSON):

{
    "nombre": "Laptop Gamer",
    "descripcion": "Potente laptop para juegos de última generación.",
    "precio": 1200.00,
    "stock": 5
}

Respuesta: 201 Created y el objeto artículo creado.

GET /api/articulos

Descripción: Obtiene todos los artículos.

Respuesta: 200 OK y una lista de objetos artículo.

GET /api/articulos/{id}

Descripción: Obtiene un artículo por su ID.

Ejemplo: GET http://localhost:8080/api/articulos/1

Respuesta: 200 OK y el objeto artículo, o 404 Not Found.

PUT /api/articulos/{id}

Descripción: Actualiza un artículo existente.

Ejemplo: PUT http://localhost:8080/api/articulos/1

Body (JSON)::

{
    "nombre": "Laptop Gamer Pro",
    "descripcion": "Laptop de alto rendimiento para juegos y diseño.",
    "precio": 1350.00,
    "stock": 4
}

Respuesta: 200 OK y el objeto artículo actualizado, o 404 Not Found.

DELETE /api/articulos/{id}

Descripción: Elimina un artículo por su ID.

Ejemplo: DELETE http://localhost:8080/api/articulos/1

Respuesta: 204 No Content, o 404 Not Found.

Pedidos (Carrito de Compras)
Base URL: http://localhost:8080/api/pedidos

Descripción: Los endpoints para la gestión de pedidos están en desarrollo. Una vez implementados, permitirán operaciones como obtener el carrito activo, añadir/actualizar/eliminar ítems y confirmar la compra.

Contribución
¡Las contribuciones son bienvenidas! Si deseas contribuir, por favor, sigue estos pasos:

Haz un fork del repositorio.

Crea una nueva rama (git checkout -b feature/nueva-funcionalidad).

Realiza tus cambios y commitea (git commit -am 'feat: Añadir nueva funcionalidad X').

Haz push a la rama (git push origin feature/nueva-funcionalidad).

Abre un Pull Request.

Licencia
Este proyecto está bajo la licencia MIT License.
