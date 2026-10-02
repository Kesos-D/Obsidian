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

Cuando instalamos por primera vez *SQL Server* vendrán previamente instaladas algunas bases de datos, hay que tener en cuenta que estas son **OBLIGATORIAS**, es un requisito que estas existan para que el gestor de bases de datos funcione de manera adecuada. Cada una desempaña un rol distinto, son un total de cuatro y sus objetivos son:

- **Master:** Registra toda la información del sistema que se este utilizando y despliega una instancia para que funcione.
- **Model:** Cuando queramos crear una base de datos nueva, tomara la configuracion que tenga *model*, a su vez si esta se configura en el futuro, solo afectara a las bases de datos posteriores.
- **MSDB:** Es usada por el [[SQL Agent]] para registrar alertas y trabajos.
- **TempDB:** Es una zona de trabajo donde podemos tener objetos creados de manera temporal.

>[!warning]
> **Master** es clave, si deja de funcionar o se corrompe por cualquier motivo, deja de funcionar todo el entorno.


[[Estructura SQL Sever]]

---

## 4. Creación básica de base de datos y tablas

Cuando queramos crear una nueva base de datos, con las configuraciones iniciales que existen en *model* solo basta escribir el siguiente comando:

```sql
-- Se trabaja en 'Master'
create database MyDatabase;

-- Nos cambiamos a nuestra base de datos creada
use MyDatabase;
go

-- Creacion de tabla
create table dbo.User(
	UserID int not null,
	Name varchar(100) not null,
	age int default 0
)
```

Al momento de querer relacionar las tablas hay que determinar si es una **FK** o **PK** en este caso la relación podría ir de la siguiente manera:

```sql
create table dbo.User(
	UserID int identity(1,1) not null, -- Valor unicor
	Name varchar(100) not null,
	age int default 0,
	
	-- Declaramos el 'ID'
	constraint pk_dboUser_UserID primary key (UserID)
)
```

`constraint` no sirve únicamente para declarar las llaves de una tabla, también sirve para corroborar que los datos de una tabla siempre sigan una lógica de negocio establecida.

[[SQLServer Arquitectura]]
[[Gestion de Usuarios]]

## 5. DML | DDL | TCL | DQL (Principios)

El propósito principal de un gestor de base de datos aparte de asegurar de contener la información de manera segura, también debe cumplir con diferentes criterios, entre ellos, facilitar el acceso a los datos, podes modificarlos, crear nueva información de manera eficiente, y automatizar procesos repetitivos.

De esto se encarga el mismo gestor, proporcionando herramientas para solucionar estas problemáticas.

- **[[DML (Data Manipulation Langauge)]]:** Nos permite manejar los datos ya almacenados en la base de datos mediante *update, delete e insert.*
- **[[DDL (Data Definition Language)]]:** Nos permite alterar la base de datos y objetos que ya fueron creados, con comandos como *create, drop, alter, etc.*
- **[[TCL (Transaction Control Language)]]:** Nos permite ejecutar [[transacciones]], algunos comandos son *commit, rollback, savepoint*.
- **[[DQL (Data Query Language)]]:** 

---
## 6. Base de datos auto contenida

Una base de datos auto contenida es aquella que minimiza las dependencias externas, además que es de fácil portabilidad ya que esta misma posee toda la información y configuración para poder ejecutarse.

Esto además permite que los usuarios que ya se hayan creado con anterioridad puedan usarse nuevamente. Existen diferentes tipos de contención según el contexto.

- **NONE:** La base de datos depende del servidor.
- **PARTIAL:** Habilita el uso de usuarios contenidos en la base de datos.