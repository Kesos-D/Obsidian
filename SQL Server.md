 ## 1. ¿Qué es SQL Server?

Es un sistema administrador de base de datos, desarrollador por Microsoft, su principal objetivo es la manipulación de los datos, y el resguardo de estos.

Además de usar [[T-SQL]] para comunicarse a la base de datos mediante [[DML (Data Manipulation Langauge)]], esta extensión es única para este gestor de base de datos.

---
## 2. Instalación y SQL Server

Cuanto nosotros queramos usar **SQL Server** es importante destacar que la instalación puede depender si es para un entorno profesional o de aprendizaje. Esto cambia mucho las cosas ya que existen varias versiones de este motor que son usadas para propósitos distintos, entre estas se encuentran:

- **Enterprise:** Se usa para empresas *grandes* las cuales manejan altos volúmenes de datos.
- **Standard:** Empresas *medianas* que no necesitan una infraestructura tan grande.
- **Web:** Se usa principalmente para *hosting* de paginas web, es bastante económica.
- **Express:** Es *gratis* lo que permite usarla para proyectos personales o muy pequeños.
- **Developer:** Esta hecha para estudiantes, desarrolladores y laboratorios de clase.
- **Azure SQL:** Los datos se guardan directamente en la *nube*, lo que ahorra infraestructura.

>[!tip]
> Siempre es recomendable instalar la **version estandar** que existe en ese entonces, ya que las ultimas versiones son de prueba.
>

Cuando se instala por primera vez se usa una configuración básica, esto es practico para empezar a aprender, pero es bastante inseguro en un entorno laboral.

Sin embargo una [[Instalación personalizada]] es mejor, pero requiere unos conocimientos técnicos acerca del gestor de bases de datos.

---
## 3. Bases de datos complementarias

[[Estructura SQL Sever]]

---
## 4. Creación básica de base de datos y tablas

Al momento de 

[[SQLServer Arquitectura]]
[[Gestion de Usuarios]]

## 5. Base de datos auto contenida

Una base de datos auto contenida es aquella que minimiza las dependencias externas, además que es de fácil portabilidad ya que esta misma posee toda la información y configuración para poder ejecutarse.

Esto además permite que los usuarios que ya se hayan creado con anterioridad puedan usarse nuevamente. Existen diferentes tipos de contención según el contexto.

- **NONE:** La base de datos depende del servidor.
- **PARTIAL:** Habilita el uso de usuarios contenidos en la base de datos.