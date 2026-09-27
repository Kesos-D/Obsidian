## 1. Login y Usuario

El **login** encarga de permitir el acceso al motor de base de datos mediante usuarios que se hayan creado en ese momento, sin embargo no asegura una conexión directa a la base de datos, existen dos mecanismos para conectarse:
- **SQL Server:**
- **Windows Authentication:**

Por otro lado existe el **usuario** el ente que se conecta a la base de datos, para acceder a un usuario es necesario que este vinculado con un **login**, la diferencia es que podemos ejecutar consultas *select* y acceder a recursos de la base de datos, existen ciertas recomendaciones al momento de crear los usuarios:

1. Credenciales únicas.
2. Planear roles y perfiles.
3. Deshabilitar la cuenta **sa (Master)**.
4. Usar autenticación de Windows.
5. Asignar menor privilegio.
6. Auditar accesos.