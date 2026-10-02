# Bases de Datos y Seguridad: Roles y Privilegios

## 1. Principio de Menor Privilegio
> [!tip] Buenas prácticas
> Consiste en **negar todo por defecto** al usuario y otorgarle únicamente los permisos estrictamente necesarios para sus tareas. Esto facilita la auditoría y el control de accesos.

---

## 2. Niveles de Privilegios
Los privilegios definen los objetos a los que pueden acceder los usuarios, agrupándose en tres niveles:

* **A nivel de Servidor:**
  * `ALTER ANY LOGIN`: Crear o modificar inicios de sesión.
* **A nivel de Base de Datos:**
  * `CONTROL DATABASE`: Control total sobre toda la base de datos.
* **A nivel de Objeto:**
  * **DML (Data Manipulation Language):** Permite ejecutar operaciones sobre los datos (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) o procedimientos almacenados.

---

## 3. Comandos de Control de Acceso
* `GRANT`: Otorga privilegios a un usuario o rol.
* `REVOKE`: Quita o remueve los privilegios otorgados (no afecta los roles).
* `DENY`: Niega explícitamente los privilegios (tiene máxima prioridad sobre permisos concedidos).

### Ejemplo de uso:
```sql
GRANT SELECT, UPDATE ON dbo.Clientes TO Usuario1;
-- Permite hacer SELECT y UPDATE al Usuario1 dentro de la tabla dbo.Clientes.
```

Bases de datos autocontenidas para iniciar sesión en la base de datos.
## 1. Privilegios y gestión de roles

Los privilegios permiten definir los objetos a los que pueden acceder los usuarios, se usan *roles* para agrupar los accesos a los usuarios. Existen privilegios para el servidor, bases de datos y por ultimo objetos.
### Permisos a nivel de servidor
- **Alter any login:** Crear o modificar logins.
### Privilegios para la base de datos
- **Control database:** Control total sobre la base.
### Privilegios a nivel de objeto
- **DML:** Permite la ejecución de procedimientos almacenados.

**GRANT:** Otorga privilegios a un usuario.
**REVOKE:** Quita o deja sin privilegios al usuario, no afecta a los roles.
**DENY:** Niega los privilegios a través de roles.

- **Asignar roles:** Funcionan como contenedores de permisos que pueden ser reutilizados por los usuarios.

De cierta manera es un perfil de seguridad que nos permite *establecer con seguridad* que pueden hacer los usuarios cuales no.

>[!tip] Mínimo privilegio
>Negarle todo al usuario y luego dar los privilegios necesarios, esto permite facilidad para saber que privilegios asignar.

```sql
grant select update on dbo.Clientes to Usuario1;
```

Permite hacer `select` al `Usuario1` dentro de la tabla `dbo.Clientes`. Existen privilegios directos vs heredados.

- **Directos:** Asignar privilegios directamente a un usuario.
- **Heredados:** Recibidor por pertenecer a un *rol*.

db_owner: Prácticamente dios dentro de la base de datos.
db_securityadmin: Administrar roles y otorgar permisos.
db_backupoperator: Realizar copias de la base de datos.
db_datareader: Lectura global de los datos.
db_datawriter: Todas las DML.

```sql
create role role_1;
```

Permite crear roles en la base de datos.

revert revierte lo que se ha hecho
execute as user = 'cambiar de contexto'

## 2. Perfiles y políticas de seguridad

Implementas mecanismos para registrar y rastrear actividades del sistema. **SQL Audit** es un mecanismo que permite registrar actividades y accesos.

**Cumplimiento normativo:** SOX, HIPAA y PCIDSS.
**Control de acceso a datos:** Control de acceso a tablas de clientes y sueldos y tarjetas.
**Detección de actividades sospechosas:** Detección de intentos de inicio de sesión fallidos y cambios de permisos.
**Auditar cambios de seguridad:** Auditar la creación de roles y cambios de privilegios.

```sql
use master;
go

create server audit pubsAuditoria
to file (filepath = '/audit/', maxsize = 10MB, max_files = 5)
with (on_failure = continue);
go

alter server audit pubsAuditoria
with (state = ON);

create database audit specification a_AutoresTitulos
for server audit pubsAuditoria
Add (select, insert, update, delet on dbo.authors by public),
Add (select, insert, update, delet on dbo.titles by public);
go

alter database specification a_AutoresTitulos
with (state = ON);

execute as user = 'James'; --Cambiar de contexto
revert; --Volver al contexto original

select *
from sys.fn_get_audit_file('/audit/pubsAuditoria*', default, default)
order by event_time desc;
```