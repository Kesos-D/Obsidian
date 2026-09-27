# Arquitectura y Funcionamiento de SQL Server

SQL Server utiliza una arquitectura clásica de tipo **cliente -> servidor**, dividida en tres capas principales que procesan las peticiones desde que el usuario las escribe hasta que se guardan en el disco.

---

## 1. Capa de Protocolo (Comunicación)
Es la encargada de gestionar la conexión inicial entre el cliente y el servidor. Admite tres tipos de arquitectura de red/comunicación:

* [[Memoria Compartida]]: Utilizada para conexiones **locales** (cuando el cliente y la base de datos están en la misma máquina).
* [[TCP-IP]]: Utilizada para conexiones **remotas** a través de la red.
* [[Named Pipes]]: Utilizada para redes locales o intranets en la comunicación cliente-servidor.

---

## 2. Motor Relacional (Consultas y Gestión)
Se encarga de procesar, analizar y preparar las consultas antes de enviarlas al almacenamiento. Su flujo de trabajo es el siguiente:

1. **Analizador CMD:** Valida la sintaxis y la corrección de la consulta.
2. **Creación del Plan de Ejecución:** Se generan los planes para consultas [[DML (Data Manipulation Langauge)]] (`INSERT`, `DELETE`, `UPDATE`, `SELECT`).
3. **Optimización:** Las consultas se optimizan y **el costo de cada consulta depende del uso de la CPU**.
4. **Caché de Planes:** Existe un apartado en la caché que permite la **reutilización de planes de ejecución** previos para agilizar consultas idénticas o similares y facilitar su acceso.

---

## 3. Motor de Almacenamiento
Una vez procesada la consulta, el motor de almacenamiento interactúa con el disco duro. Los datos se organizan internamente mediante **[[páginas]] de 8 KB**.

Los archivos principales que utiliza son:
* `[[Archivo .mdf]]`: Archivo de datos principal. Almacena la información central, vistas e índices.
* `[[Archivo .ndf]]`: Archivo de datos secundario (opcional). Se usa si el usuario necesita dividir la base de datos en varios archivos.
* `[[Archivo .ldf]]`: Archivo de transacciones (Log). Donde se registran cronológicamente todas las transacciones realizadas.

Existen también las **extensiones** que son una colección de 8 paginas, por lo que nos daría como resultado **64kb**, esto permite el almacenamiento de paginas de manera mas eficiente.

Pero se organizas mediante dos extensiones:
- **Uniformes:** Son propiedad de un único objeto.
- **Mixtas:** Pueden compartir hasta ocho objetos.

Los componentes que conforman este motor de almacenamiento son:
1. **Métodos de acceso:** Es el puente que conecta al *administrador de buffer* con el *administrador de transacciones*.
2. **Administrador del buffer:** Se encarga de mantener los datos de acceso frecuente en la [[memoria RAM]] para un acceso rápido, además se encarga de coordinar las [[páginas]].
3. **Administrador de transacciones:** Debe garantizar el registro de los datos, almacenar todas sus modificaciones, y tener un respaldo de operaciones.

---
## 4. Servicios adicionales

Además de ser un gestor de bases de datos, SQLServer ofrece herramientas útiles para facilitar la gestion y seguridad de los datos.

1. **SQL Server Agent:** Permite automatizar trabajos y alertas.
2. **SSIS:** Extracción de información y carga de datos.
3. **SSRS:** Creación de informes a partir de datos.
4. **SSAS:** Cubos OLAP y modelos tabulares para análisis.

## 5. Diccionario de bases de datos

Es el repositorio de metadatos, es como un índice que engloba todos los aspectos importantes que el informático debe saber para operar con la base de datos.
- Información sobre tablas, columnas, restricciones, etc.
- Usuarios, roles y permisos que existen.
- Restricciones y dependencias para hacer funcionar la base de datos.

Esto permite mantener un orden claro sobre la base de datos, además que facilita las auditorias que se realicen.
## Notas Relacionadas
* Ver también: [[Optimización de Consultas SQL]]