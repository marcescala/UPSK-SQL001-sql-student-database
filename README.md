# Student Database


### [Learn SQL by Building a Student Database: Part 1](https://github.com/Laboratoria/learn-sql-by-building-a-student-database-part-1)

En el primer tutorial, aprenderás a construir y gestionar una base de datos de
estudiantes utilizando SQL y PostgreSQL. Comenzarás configurando el entorno
necesario, que incluye la instalación de PostgreSQL y el uso de máquinas
virtuales. A través de comandos SQL, te guiarás en la creación de tablas con
claves primarias y foráneas, la inserción y consulta de datos, y la
actualización y eliminación de registros. Además, explorarás el uso de
scripts Bash para automatizar tareas y gestionar permisos de archivos.

Haz clic [aquí para iniciar el primer tutorial](https://gitpod.io/new/?autostart=true#CODEROAD_TUTORIAL_URL=https%3A%2F%2Fraw.githubusercontent.com%2FLaboratoria%2Flearn-sql-by-building-a-student-database-part-1%2Fmain%2Ftutorial.json,CODEROAD_DISABLE_RUN_ON_SAVE=true/https://github.com/Laboratoria/learn-sql-by-building-a-student-database-part-1).

---
## Registro de Actividades
### Paso 1: Inicio del Terminal
1. **Acción**: Abre un nuevo terminal en tu entorno de desarrollo.
   - **Cómo hacerlo**:
     1. Haz clic en el menú "hamburger" en la parte superior izquierda de la pantalla.
     2. Ve a la sección "terminal" y selecciona "nuevo terminal".
   - **Comando Ejecutado**:
     ```bash
     echo hello SQL
     ```
   - **Resultado Esperado**: El terminal debería mostrar el mensaje `hello SQL`.
### Paso 2: Ingreso a PostgreSQL
1. **Acción**: Revisa los archivos `.csv` con información sobre los estudiantes de ciencias de la computación.
   - **Descripción**: Los archivos `.csv` contienen datos sobre los estudiantes. La primera fila de cada archivo tiene los títulos, y las filas restantes contienen los valores correspondientes a esos títulos.
2. **Acción**: Ingresar al terminal interactivo de PostgreSQL.
   - **Cómo hacerlo**:
     1. Abrir un nuevo terminal (si no está ya abierto).
     2. Ejecutar el siguiente comando para iniciar sesión en PostgreSQL:
        ```bash
        psql --username=freecodecamp --dbname=postgres
        ```
   - **Resultado Esperado**: Deberías ver el prompt de PostgreSQL listo para aceptar comandos SQL.
### Paso 3: Ver las Bases de Datos Existentes
1. **Acción**: Visualizar las bases de datos existentes utilizando el comando abreviado `\l`.
   - **Cómo hacerlo**:
     1. En el prompt de PostgreSQL, ejecuta el siguiente comando:
        ```psql
        \l
        ```
   - **Resultado Esperado**: Deberías ver una lista de todas las bases de datos actuales en el servidor PostgreSQL.
### Paso 4: Crear la Base de Datos de Estudiantes
1. **Acción**: Toda la información de los archivos CSV se almacenará en una sola base de datos. Crea una nueva base de datos llamada `students`.
   - **Cómo hacerlo**:
     1. En el prompt de PostgreSQL, ejecuta el siguiente comando:
        ```psql
        CREATE DATABASE students;
        ```
   - **Resultado Esperado**: La base de datos `students` debería ser creada exitosamente.
### Paso 5: Verificar la Creación de la Base de Datos
1. **Acción**: Verifica que la base de datos haya sido creada correctamente.
   - **Comando Ejecutado**:
     ```psql
     \l
     ```
   - **Resultado Esperado**: Deberías ver la base de datos `students` listada entre las bases de datos existentes.
     
### Paso 6: Conectar a la Nueva Base de Datos
1. **Acción**: Conéctate a la base de datos `students` para comenzar a agregar tablas.
   - **Comando**:
     ```psql
     \c students
     ```
   - **Resultado Esperado**: Deberías estar conectado a la base de datos `students`, lista para agregar tablas.
     
### Paso 7: CREAR TABLA
Los archivos CSV contienen una serie de estudiantes con información sobre ellos, y algunos cursos y especialidades. Tendrás cuatro tablas: una para `students` y su información, una para cada especialidad `majors`, otra para cada curso `courses` y una última para mostrar qué cursos están incluidos en cada especialidad `majors_courses`.

**Consejos**
- Utiliza las palabras clave `CREATE TABLE`.
- Debe haber paréntesis después del nombre de la tabla.
- He aquí un ejemplo: `CREATE TABLE <table_name>();`

**Acción**

Escribe  en el indicador psql.

`CREATE TABLE students();`
`CREATE TABLE majors();`
`CREATE TABLE courses();` 
`CREATE TABLE majors_courses();`

### Paso 8: VERIFICAR TABLAS
Utiliza el comando de atajo `\d` para visualizar tus tablas y asegurarte de que estás satisfecho con ellas.
**Consejos**
- Es el comando de atajo `\d`.
- Escribe `\d` en el indicador psql.
  
### Paso 9: CREAR COLUMNAS

Vamos a agregar columnas a la tabla `students` utilizando datos del archivo `students.csv`. Este archivo tiene cuatro campos, y agregaremos una columna para cada uno de esos campos, así como una columna ID.

**Consejos:**
- Utiliza la sentencia `ALTER TABLE` para agregar columnas a una tabla existente.
- Asegúrate de especificar el tipo de datos y cualquier restricción necesaria para cada columna.

1. **Agregar Columna `student_id`:**
   Agrega una columna `student_id` a la tabla `students`. Asigna a esta columna el tipo `SERIAL` para que se incremente automáticamente y conviértela en `PRIMARY KEY`.
   ```psql
   ALTER TABLE students ADD COLUMN student_id SERIAL PRIMARY KEY;
   ```
2. **Agregar Columna `first_name:`:**
   Agrega una columna `first_name` a la tabla `students`. Asigna a esta columna el tipo `VARCHAR(50)` y dale la restricción `NOT NULL`.
   ```psql
   ALTER TABLE students ADD COLUMN first_name VARCHAR(50) NOT NULL;
   ```
3. **Agregar Columna `last_name:`:**
   Agrega una columna `last_name` a la tabla `students`. Asigna a esta columna el mismo tipo de datos y longitud máxima que first_name y asegúrate de que tenga la restricción `NOT   NULL`.
   ```psql
   ALTER TABLE students ADD COLUMN last_name VARCHAR(50) NOT NULL;
   ```
4. **Agregar Columna `major_id:`:**
   Agrega una columna `major_id` a la tabla `students`. Asigna a esta columna el tipo de datos `INT`. Estableceremos la clave foránea más adelante.
   ```psql
   ALTER TABLE students ADD COLUMN major_id INT;
   ```
5. **Agregar Columna `gpa:`:**
   Agrega una columna `gpa` a la tabla `students`. Los datos en el CSV muestran que son decimales con una longitud de 2 y 1 número a la derecha del decimal, así que asígnale un tipo de datos `NUMERIC(2,1`).
```psql
ALTER TABLE students ADD COLUMN gpa NUMERIC(2,1);
```


### Paso 10: AÑADIR COLUMNAS A LA TABLA majors
Completa la tabla `majors`. Añade una columna `major_id` a esta tabla. Configúrala como un tipo `SERIAL` y hazla la PRIMARY KEY para esta tabla.

1. **Acción**
```psql
ALTER TABLE majors ADD COLUMN major_id SERIAL PRIMARY KEY;
```

Añade una columna a la tabla `majors` llamada `major`. Configúrala como `VARCHAR` con una longitud máxima de 50 y dale la restricción `NOT NULL`.

2. **Acción**
```psql
ALTER TABLE majors ADD COLUMN major VARCHAR(50) NOT NULL;
```

### Paso 11: ESTABLECER CLAVE FORÁNEA EN LA TABLA students
Configurar la columna `major_id` de la tabla `students` como una clave foránea que hace referencia a la columna `major_id` de la tabla `majors`.

1. **Acción**

  ```psql
  ALTER TABLE students ADD FOREIGN KEY (major_id) REFERENCES majors (major_id);
```

### Paso 21: CREAR COLUMNA course_id
Agregue una columna course_id. Dale un tipo de SERIAL y conviértelo en la clave principal.

**Acción**

 Escribe:
  ```psql
  ALTER TABLE coursesADD COLUMN course_id SERIAL PRIMARY KEY;
  ```

### Paso 12 Crear clave primaria compuesta
Puede crear una clave primaria compuesta que utilice más de una columna como un par único como este: `ALTER TABLE <nombre_tabla> ADD PRIMARY KEY(<nombre_columna>, <nombre_columna>);` 

1. **Acción**
   

Escribe:
  ```psql
  ALTER TABLE majors_courses ADD PRIMARY KEY(major_id, course_id);
  ```



### [Learn SQL by Building a Student Database: Part 2](https://github.com/Laboratoria/learn-sql-by-building-a-student-database-part-2)

En el segundo tutorial, profundizarás en la administración y análisis
de bases de datos de estudiantes usando SQL y PostgreSQL. Aprenderás a
realizar consultas avanzadas mediante JOIN para combinar datos de múltiples
tablas y a utilizar funciones de agrupamiento (GROUP BY) y ordenamiento
(ORDER BY). Se cubrirán también las funciones agregadas para sumarizar
datos y la modificación de estructuras de tablas existentes con ALTER TABLE.
Esta parte incluye la creación de copias de seguridad y restauración
de bases de datos, y el uso de scripts Bash para una gestión más
eficiente y segura de tu entorno.

Haz clic [aquí para iniciar el segundo tutorial](https://gitpod.io/new/?autostart=true#CODEROAD_TUTORIAL_URL=https%3A%2F%2Fraw.githubusercontent.com%2FLaboratoria%2Flearn-sql-by-building-a-student-database-part-2%2Fmain%2Ftutorial.json,CODEROAD_DISABLE_RUN_ON_SAVE=true/https://github.com/Laboratoria/learn-sql-by-building-a-student-database-part-2)


## 5. Entregable

Haz fork a este repositorio. Luego ajustar el README para registrar
todos los comandos ejecutados durante los tutoriales. Puede usar
el siguiente formato:

```md
# Tutorial 1

## Paso 1

   `echo sql Hello`

## Paso 2

   `psql --username=freecodecamp --dbname=psql`
```

Puedes obtener un historial de los comandos ejecutados en una terminal
con el comando `history`.

## 6. Consideraciones para pedir tu Project Feedback

Antes de agendar tu Project Feedback con tu coach, asegúrate de:

* [ ] Completar los 2 tutoriales propuestos
* [ ] Tener un fork con un entorno de Gitpod completo

## 7. Objetivos de aprendizaje


Reflexiona y luego marca los objetivos que has llegado a entender y aplicar en tu proyecto. Piensa en eso al decidir tu estrategia de trabajo.

### SQL

- [ ] **Realizar operaciones básicas de consulta de una base de datos utilizando las cláusulas SELECT y WHERE**

  <details><summary>Links</summary><p>

  * [Querying a Table](https://www.postgresql.org/docs/current/tutorial-select.html)
  * [SELECT reference](https://www.postgresql.org/docs/16/sql-select.html)
</p></details>

- [ ] **CREATE TABLE**

  <details><summary>Links</summary><p>

  * [SQL CREATE TABLE Statement - W3Schools](https://www.w3schools.com/sql/sql_create_table.asp)
</p></details>

- [ ] **INSERT**

  <details><summary>Links</summary><p>

  * [Inserting Data](https://www.postgresql.org/docs/current/dml-insert.html)
</p></details>

- [ ] **UPDATE**

  <details><summary>Links</summary><p>

  * [Updating Data](https://www.postgresql.org/docs/current/dml-update.html)
</p></details>

- [ ] **DELETE**

  <details><summary>Links</summary><p>

  * [DELETE](https://www.postgresql.org/docs/current/dml-delete.html)
</p></details>

- [ ] **Primary Key**

  <details><summary>Links</summary><p>

  * [Primary Keys](https://www.postgresql.org/docs/current/ddl-constraints.html#DDL-CONSTRAINTS-PRIMARY-KEYS)
</p></details>

- [ ] **Foreign key**

  <details><summary>Links</summary><p>

  * [Foreign Keys](https://www.postgresql.org/docs/current/ddl-constraints.html#DDL-CONSTRAINTS-FK)
</p></details>

- [ ] **ALTER TABLE**

  <details><summary>Links</summary><p>

  * [Modifying Tables](https://www.postgresql.org/docs/current/ddl-alter.html)
</p></details>

- [ ] **Comprender y utilizar cláusulas JOIN para combinar datos de múltiples tablas.**

  <details><summary>Links</summary><p>

  * [Joins Between Tables](https://www.postgresql.org/docs/current/tutorial-join.html)
</p></details>

- [ ] **Condensar resultados con cláusulas de agrupación de datos como GROUP BY y HAVING**

  <details><summary>Links</summary><p>

  * [SELECT reference](https://www.postgresql.org/docs/16/sql-select.html)
  * [Aggregate Functions](https://www.postgresql.org/docs/current/tutorial-agg.html)
</p></details>

- [ ] **Ordernar el resultado utilizando la cláusula ORDER BY**

  <details><summary>Links</summary><p>

  * [SELECT reference](https://www.postgresql.org/docs/16/sql-select.html)
</p></details>

- [ ] **Trabajar con funciones de agregación como COUNT, SUM, AVG, MAX y MIN**

  <details><summary>Links</summary><p>

  * [Aggregate Functions](https://www.postgresql.org/docs/current/tutorial-agg.html)
</p></details>

- [ ] **Constraints**

  <details><summary>Links</summary><p>

  * [Constraints](https://www.postgresql.org/docs/current/ddl-constraints.html)
</p></details>

### Virtual Machines

- [ ] **Virtual Machines Setup**

  <details><summary>Links</summary><p>

  * [Creating a Virtual Machine - Oracle VM](https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/vboxmanage-createvm.html)
  * [Setting Up a Virtual Machine - Microsoft](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine)
</p></details>

### PostgreSQL

- [ ] **PostgreSQL Setup**

  <details><summary>Links</summary><p>

  * [PostgreSQL Installation - PostgreSQL Docs](https://www.postgresql.org/download/)
  * [How To Install and Use PostgreSQL on Ubuntu - DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-20-04)
</p></details>

- [ ] **PostgreSQL Commands**

  <details><summary>Links</summary><p>

  * [PostgreSQL psql Commands - PostgreSQL Docs](https://www.postgresql.org/docs/current/app-psql.html)
  * [Commonly Used PostgreSQL Commands - Verta.ai](https://www.verta.ai/resources/tutorials/database/postgresql-commands)
</p></details>

- [ ] **PostgreSQL Backup**

- [ ] **PostgreSQL Restore**

### Shell

- [ ] **Shell Scripts**

  <details><summary>Links</summary><p>

  * [Shell Scripting Guide - LinuxCommand.org](http://linuxcommand.org/lc3_writing_shell_scripts.php)
</p></details>

- [ ] **File Permissions**

  <details><summary>Links</summary><p>

  * [Understanding Linux File Permissions - DigitalOcean](https://www.digitalocean.com/community/tutorials/understanding-linux-file-permissions)
  * [File Permissions in Linux - Red Hat](https://www.redhat.com/sysadmin/linux-file-permissions)
</p></details>
