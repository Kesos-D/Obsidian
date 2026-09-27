
# 1. ¿Que es el DML?

El **DML** (por sus siglas en inglés, *Lenguaje de Manipulación de Datos*) es un conjunto de instrucciones de SQL cuyo objetivo principal es permitir al usuario interactuar con los datos almacenados dentro de las estructuras de una base de datos.

> [!info] Propósito
> Utiliza palabras clave que el motor de base de datos comprende para consultar, insertar, modificar o eliminar registros de manera eficiente.

---

### Comandos Principales

En la mayoría de los motores de bases de datos relacionales, el DML se conforma principalmente por cuatro comandos fundamentales:

*   **`SELECT`**: Permite consultar y recuperar información existente en las tablas según los filtros deseados *(nota: técnicamente a veces se separa como [[DQL]], pero opera sobre los datos)*.
*   **`INSERT`**: Permite agregar o crear **nuevos registros** (filas) dentro de una tabla.
*   **`UPDATE`**: Permite **actualizar o modificar** los datos ya existentes en una o varias filas de una tabla.
*   **`DELETE`**: Permite **borrar** registros existentes de una tabla de forma definitiva (a menos que se use una transacción o respaldo).

---
> [!warning] Cuidado con **DELETE, UPDATE**
> Es importante avisar al lector, de que estos comandos **NUNCA** se ejecutan sin el comando *where*, ya que estos afectan a toda una tabla si no se implementa.
## Notas addicionales

- Ver también: [[DQL]]