#28/09/2026

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