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
   Los archivos CSV contienen una serie de estudiantes con información sobre ellos, y algunos cursos y especialidades. Tendrás cuatro tablas: una para `students` y su información, una    para cada especialidad `majors`, otra para cada curso `courses` y una última para mostrar qué cursos están incluidos en cada especialidad `majors_courses`.

   Ejemplo:
  `CREATE TABLE <table_name>();`

   1. **Acción:**

      Escribe  en el indicador psql.

      `CREATE TABLE students();`
      
      `CREATE TABLE majors();`
      
      `CREATE TABLE courses();`
      
      `CREATE TABLE majors_courses();`

### Paso 8: VERIFICAR TABLAS
   Utiliza el comando de atajo `\d` para visualizar tus tablas y asegurarte de que estás satisfecho con ellas.

   Escribe `\d` en el indicador psql.
  
### Paso 9: CREAR COLUMNAS

   Agregar columnas a la tabla `students` utilizando datos del archivo `students.csv`. Este archivo tiene cuatro campos, y agregaremos una columna para cada uno de esos campos, así       como una columna ID.

   Utiliza la sentencia `ALTER TABLE` para agregar columnas a una tabla existente.
   Especifica el tipo de datos y cualquier restricción necesaria para cada columna.

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
      Agrega una columna `last_name` a la tabla `students`. Asigna a esta columna el mismo tipo de datos y longitud máxima que first_name y asegúrate de que tenga la restricción `NOT         NULL`.
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

   1. **Acción:**
      ```psql
      ALTER TABLE majors ADD COLUMN major_id SERIAL PRIMARY KEY;
      ```

Añade una columna a la tabla `majors` llamada `major`. Configúrala como `VARCHAR` con una longitud máxima de 50 y dale la restricción `NOT NULL`.

   2. **Acción:**
      ```psql
      ALTER TABLE majors ADD COLUMN major VARCHAR(50) NOT NULL;
      ```

### Paso 11: ESTABLECER CLAVE FORÁNEA EN LA TABLA students
   Configurar la columna `major_id` de la tabla `students` como una clave foránea que hace referencia a la columna `major_id` de la tabla `majors`.

   1. **Acción:**
      ```psql
        ALTER TABLE students ADD FOREIGN KEY (major_id) REFERENCES majors (major_id);
       ```

### Paso 12: CREAR COLUMNA course_id
Agregue una columna course_id. Dale un tipo de SERIAL y conviértelo en la clave principal.

1. **Acción:**
    ```psql
     ALTER TABLE coursesADD COLUMN course_id SERIAL PRIMARY KEY;
     ```

### Paso 13 Crear clave primaria compuesta
Puede crear una clave primaria compuesta que utilice más de una columna como un par único.

Ejemplo:

`ALTER TABLE <nombre_tabla> ADD PRIMARY KEY(<nombre_columna>, <nombre_columna>);` 

1. **Acción:**
    ```psql
     ALTER TABLE majors_courses ADD PRIMARY KEY(major_id, course_id);
     ```
### Paso 14 INSERT EN majors

Sólo necesita el nombre de una especialización. La ID se agregará automáticamente. Agregue la primera especialización del archivo cursos.csv a la tabla de especialidades. Es un VARCHAR, así que asegúrese de poner el valor entre comillas simples. La especialidad es Administración de Bases de Datos.

Utilice las palabras clave `INSERT INTO` y `VALUES`

Ejemplo:

`INSERT INTO <nombre_tabla>(<nombre_columna>) VALUES(<valor>);`

   1. **Acción:**
      ```psql
      INSERT INTO majors(principales) VALUES('Administración de bases de datos');
      ```
### Paso 15 SELECT - FROM 

Utilice las palabras clave SELECT y FROM con * para ver todas las columnas y asegurarse de que se hayan insertado correctamente.

   Ejemplo: 

   `SELECT <columnas> FROM <nombre_tabla>;`

   1. **Acción:**
      ```psql
      SELECT * FROM majors;
      ```
      ```psql
      SELECT * FROM courses;
      ```
      ```psql
      SELECT * FROM majors_courses;
      ```
      ```psql
      SELECT * FROM students;
      ```
### Paso 16 touch insert_data.sh

Añadir el resto de la información de a uno por vez sería tedioso. Vas a crear un script que lo haga por ti. Te recomiendo "dividir" la terminal para esta parte. Utiliza el comando `touch` para crear un archivo llamado `insert_data.sh` en la carpeta de tu proyecto.

   1. **Acción:**
   
   Escribe `touch insert_data.sh` en la nueva terminal y presiona enter.
   Asegúrate de que estás en la carpeta del proyecto primero.
   Puedes llegar allí ingresando cd ~/project en la terminal.

### Paso 17 chmod +x insert_data.sh

En la terminal de comandos, usa el comando `chmod` con el indicador `+x` para darte nuevos permisos de ejecución de scripts.

Ejemplo: `chmod +x <filename>`

   1. **Acción:**

   Escribe `chmod +x insert_data.sh` en la terminal y presiona enter.
   
### Paso 18 Agrega shebang 

Abre tu nuevo archivo y agrega un "shebang" que use bash en la parte superior. 

   1. **Acción:**
   
      Añade el texto: `#!/bin/bash.`
   
### Paso 19 Agrega un comentario 
Agrega un comentario de una sola línea con el texto `Script para insertar datos de courses.csv y students.csv en la base de datos students`.

   1. **Acción:**

      Agrega `# Script para insertar datos de courses.csv y students.csv en la base de datos students` debajo del "shebang" en tu archivo `insert_data.sh`

### Paso 20 Agrega cat courses.csv
`cat` es un comando de terminal para imprimir el contenido de un archivo. Debes agregar toda la información del archivo courses.csv ya que necesitas el major_id para insertar la información del estudiante.

Ejemplo: `cat <filename>`. 
   
   1. **Acción:**
      
      Agregue `cat courses.csv` a su archivo insert_data.sh debajo de su comentario.

### Paso 21 ./insert_data.sh
Ejecute su script para ver si se imprime el contenido del archivo.

   1. **Acción:**
      
      Escriba `./insert_data.sh` en la terminal y presione enter. Asegúrese de estar en la carpeta del proyecto primero.

### Paso 22 Agregue while read
En lugar de imprimir el contenido, puede redirigir esa salida en un bucle while para poder recorrer las filas una a la vez. 
Cada nueva línea se leerá en las variables `MAJOR` y `COURSE`, use `echo` para imprimir la variable `MAJOR`.

   1. **Acción:**
    
      El bucle completo debería verse así:

      ```sh 
      cat courses.csv | while read MAJOR COURSE
      do
        echo $MAJOR
      done
      ```
      
### Paso 23 Declarar -p IFS y Añadir IFS
La variable `MAJOR` solo está capturando la primera palabra de cada línea. Esto se debe a la variable predeterminada `IFS` en bash. `IFS` significa "Internal Field Separator" (Separador de Campos Interno) y define cómo se separan los campos en bash. Para ver el valor actual de IFS, puedes usar el siguiente comando en la terminal:

   1. **Acción**:
    
   Ingresa `declare -p IFS` en la terminal.
    
   Entre los comandos `while`y `read`, establezca el IFSen una coma de la siguiente manera:`IFS=","`

   2. **Acción**:
   
   ```sh
   cat courses.csv | while IFS="," read MAJOR COURSE
   do
     echo $MAJOR
   done
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


