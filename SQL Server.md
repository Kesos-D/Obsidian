## 1. ¿Qué es SQL Server?

Es un sistema administrador de base de datos, desarrollador por Microsoft, su principal objetivo es la manipulación de los datos, y el resguardo de estos.

Además de usar [[T-SQL]] para comunicarse a la base de datos mediante [[DML (Data Manipulation Langauge)]], esta extension es unica para este gestor de base de datos.

---
## 2. Creación básica de base de datos y tablas

Al momento de 

[[SQLServer Arquitectura]]
[[Gestion de Usuarios]]

## 2. Base de datos auto contenida

Una base de datos auto contenida es aquella que minimiza las dependencias externas, además que es de fácil portabilidad ya que esta misma posee toda la información y configuración para poder ejecutarse.

Esto además permite que los usuarios que ya se hayan creado con anterioridad puedan usarse nuevamente. Existen diferentes tipos de contención según el contexto.

- **NONE:** La base de datos depende del servidor.
- **PARTIAL:** Habilita el uso de usuarios contenidos en la base de datos.