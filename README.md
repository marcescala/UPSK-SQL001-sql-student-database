# Student Database


### [Learn SQL by Building a Student Database: Part 1](https://github.com/Laboratoria/learn-sql-by-building-a-student-database-part-1)

En el primer tutorial, aprendimos a construir y gestionar una base de datos de
estudiantes utilizando SQL y PostgreSQL. configurando el entorno
necesario, que incluia la instalación de PostgreSQL y el uso de máquinas
virtuales. A través de comandos SQL, se crearon tablas con
claves primarias y foráneas,  inserción y consulta de datos, y la
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

### Paso 24 Agrega un comentarios

Es útil planificar lo que desea que suceda. Para cada bucle, deberá agregar la especialidad a la base de datos si aún no está allí. Lo mismo para el curso. Luego, agregue una fila a la tabla majors_courses. Agregue estos comentarios de una sola línea en su bucle en este orden: `get major_id`, `if not found`, `insert major`, `get new major_id`, `get course_id`, `if not found`, `insert course`,`get new course_id`, `insert into majors_courses`.

   1. **Acción**:
      
      Agregue los nueve comentarios de una sola línea sugeridos, cada uno en su propia línea, en el orden indicado
      Debería verse así:
      ```sh
      do
      # get major_id

      # if not found

      # insert major

      # get new major_id

      # get course_id

      # if not found

      # insert course

      # get new course_id

      # insert into majors_courses

      done
      ```
### Paso 25 Agregar variable PSQL

Utilizó el comando `psql` para iniciar sesión e interactuar con la base de datos. Puede usarlo para ejecutar un solo comando y salir. Encima de su bucle, agregue una variable `PSQL` que se vea así: `PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"`. Esto le permitirá consultar su base de datos desde su script. Las partes importantes son `username`, `dbname` y el indicador `-c` que es para ejecutar un solo comando y salir. El resto de las banderas son para formatear.

   1. **Acción**:

      Agrega la variable sugerida entre tu primer comentario y el bucle.
      
      El área sugerida debería verse así:

      ```sh
      PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
      ```
      
### Paso 26 Agrega MAJOR_ID

puedes consultar tu base de datos usando la variable `PSQL` de esta manera: `$($PSQL "<query_here>")`. El código entre paréntesis se ejecutará en un subshell, que es un proceso bash separado. Debajo del comentario `get major_id` en tu bucle, crea una variable `MAJOR_ID`. Establécela igual al resultado de una consulta que obtenga el `major_id` del `MAJOR` actual en el bucle. Asegúrate de poner tu variable `MAJOR` entre comillas simples.

 1. **Acción**:
    ejemplo: `MAJOR_ID=$($PSQL "<query_here>")`,

     ```sh
     MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")
     ```
    
### Paso 27 Agrega echo MAJOR_ID

Debajo de la variable que acabas de crear, usa echo para imprimirla y así poder ver su valor cuando ejecutes el script.

   1. **Acción**:
      
      Agrega `echo $MAJOR_ID` debajo de la variable MAJOR_ID que creaste
      
### Paso 28 Agregue if -z MAJOR_ID

Debajo de su primer comentario `if not found`, agregue una condición `if` que verifique si la variable `MAJOR_ID` está vacía. Puede hacerlo con esta prueba: `[[ -z $MAJOR_ID ]]`. Coloque los dos comentarios siguientes en el área de declaraciones del `if`.

   1. **Acción**:

      Ejemplo:
      
      if CONDITION
      
      then
      
      STATEMENTS
      
      fi

      ```sh
      if [[ -z $MAJOR_ID ]]
      then
      # insert major

      # get new major_id

      fi
      ```

### Paso 29 Agregue INSERT_MAJOR_RESULT

El bucle se ejecutará de esta manera siempre que no se encuentre una especialidad. Aquí, deberá insertar la especialidad y luego obtener el nuevo `ID`. Necesitará el `ID` para insertar datos en la tabla majors_courses más adelante. Debajo del comentario de inserción de especialidad, cree una variable `INSERT_MAJOR_RESULT`. Establezca su valor en una consulta que inserte la especialidad actual en la base de datos. No olvide usar comillas simples alrededor del valor.

   1. **Acción**:

      Ejemplo: `INSERT_MAJOR_RESULT=$($PSQL "<query_here>")`

      Así es como debería verse toda la línea:
      
      ``` sh
      INSERT_MAJOR_RESULT=$($PSQL "INSERT INTO majors(major) VALUES('$MAJOR')")
      ```
      
   2. **Acción**:
   
      Debajo de la variable que acaba de crear, utilice echo para imprimirla.

      ``` sh
      $INSERT_MAJOR_RESULT
      ```
      
### Paso 30 cp courses.csv

Cree algunos datos de prueba. En la terminal, utilice el comando copy (`cp`) para copiar el archivo `courses.csv` en un nuevo archivo llamado `courses_test.csv`.

   1. **Acción**:

      Ejemplo: `cp <filename> <new_name>`
      
      Escriba ` courses.csv courses_test.csv` en la terminal bash y presione Enter
      
   2. **Acción**:

      En su nuevo archivo, elimine todos los datos excepto las primeras cinco líneas. Asegúrese de que haya una sola línea vacía en la parte inferior.
      
      El archivo `courses_test.csv` debería verse así:
      
      `major,course
      
      Database Administration,Data Structures and Algorithms
      
      Web Development,Web Programming
      
      Database Administration,Database Systems
      
      Data Science,Data Structures and Algorithms

      `

### Paso 31 Cambie a cat courses_test.csv

De vuelta en el script `insert_data.sh`, cambie su comando `cat` para que recorra el archivo de prueba en lugar del archivo completo.

   1. **Acción**:

      La línea sugerida debería verse así:
      
      ```sh
      cat courses_test.csv | while IFS="," read MAJOR COURSE
      ```
### Paso 32 Eliminar echo MAJOR_ID

Ya no necesita imprimir el `ID`, así que elimine la línea `echo $MAJOR_ID`.

### Paso 33 SELECT * FROM majors

En el indicador de psql, use SELECT para ver todos los datos de la tabla majors para ver lo que agregó el script.

   1. **Acción**:

      Ingrese :

      ```psql
      SELECT * FROM majors;
      ```

### Paso 34 TRUNCATE majors
Puedes usar `TRUNCATE` para eliminar todos los datos de una tabla. En el indicador de `psql`, intenta eliminar todos los datos de la tabla `majors` ingresando `TRUNCATE majors;`

   1. **Acción**:
      
       Ingresa en el indicador de psql
      ```psql
      TRUNCATE majors; 
      ```

### Paso 35 TRUNCATE majors, students, majors_courses

Dice que "no puedes truncar una tabla a la que se hace referencia en una restricción de clave externa". Las tablas `students` y `majors_courses` usan el `major_id` de `majors` como clave externa. Por lo tanto, si desea eliminar los datos de las carreras, debe eliminar los datos de esas dos tablas al mismo tiempo. Utilice `TRUNCATE` para eliminar los datos de esas tres tablas. Separe las tablas con comas.

   1. **Acción**:

      Ingrese en el indicador de psql
      
      ```psql
      TRUNCATE majors, students, majors_courses;
      ```
   2. **Acción**

      Vea todos los datos de la tablas `majors`, `majors_courses`, `students`, `courses` para asegurarte de que esten vacias.
      
      ejemplo: Ingresa en el indicador de psql
      
      ```psql
      SELECT * FROM majors_courses;
      ```

### Paso 36 Agregar if major

No querrá agregar la primera línea del archivo CSV a la base de datos, ya que son solo títulos. En su secuencia de comandos, agregue una condición `if` en la parte superior de su bucle que verifique si `$MAJOR != major`. Coloque todo el código y los comentarios existentes en su bucle en su área de declaraciones para que solo realice lo que no sea la primera línea.

   1. **Acción**:
      
      Su área de bucle debería verse así:

      ```sh
      do
        if [[ $MAJOR != major ]]
        then
         # get major_id
         MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")

         # if not found
         if [[ -z $MAJOR_ID ]]
            then
            # insert major
            INSERT_MAJOR_RESULT=$($PSQL "INSERT INTO majors(major) VALUES('$MAJOR')")
            echo $INSERT_MAJOR_RESULT

            # get new major_id

          fi

          # get course_id

          # if not found

          # insert course

          # get new course_id
   
          # insert into majors_courses

       fi
      done
      ```

### Paso 37 Borrar echo INSERT_MAJOR_RESULT
Borra la línea donde imprimes `INSERT_MAJOR_RESULT`.

   1. **Acción**:
      
      Borra la línea `echo $INSERT_MAJOR_RESULT`

### Paso 38 Agrega if INSERT_MAJOR_RESULT

Para que sea más informativo debajo de tu variable `INSERT_MAJOR_RESULT`, agrega una declaración `if` que verifique si la variable es igual a `INSERT 0 1`, que era lo que estaba imprimiendo. Usa `echo` para imprimir `Inserted into majors`, `$MAJOR` en el área de declaraciones del `if`.

   1. **Acción**:

      Todo debería verse así:
      
      ```sh
      if [[ $INSERT_MAJOR_RESULT == "INSERT 0 1" ]]
      then
      echo "Inserted into majors, $MAJOR"
      fi
      ```
      
### Paso 39 Agregue MAJOR_ID, COURSE_ID, if -z COURSE_ID

Debajo del comentario para obtener el nuevo `major_id`, configure la variable `MAJOR_ID` en una consulta que obtenga el nuevo `major_id` de la base de datos.

   1. **Acción**:

      Así es como debería verse toda la línea, asegúrese de que esté en el área de declaraciones `if [[ -z $MAJOR_ID ]]`:
      
      ```sh
      MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")
      ```
      
   2. **Acción**:

      Debajo del comentario `get course_id`, agrega una variable `COURSE_ID` que obtenga el `course_id` de la base de datos.
      
      Así es como debería verse toda la línea:

      ```sh
      COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")
      ```
   
   3. **Acción**:

         Debajo del segundo comentario `if not found`, agregue una declaración `if` que verifique si la consulta estaba vacía para que pueda insertar el curso si es necesario. Coloque los comentarios de inserción de curso y obtención de nuevo `course_id` existentes en el área de declaraciones del `if`.
         
         Así es como debería verse:
         
         ```sh
         if [[ -z $COURSE_ID ]]
            then
            # insert course

            # get new course_id

         fi
         ```

### Paso 40 Agregue INSERT_COURSE_RESULT e if INSERT_COURSE_RESULT

Debajo del comentario de inserción del curso, cree una variable `INSERT_COURSE_RESULT` que inserte el curso en la base de datos.

   1. **Acción**:

      Así es como debería verse toda la línea:

      ```sh
      INSERT_COURSE_RESULT=$($PSQL "INSERT INTO courses(course) VALUES('$COURSE')")
      ```
   2. **Acción**:

      Debajo de la variable que acaba de crear, agregue una condición `if` que verifique si se insertó e `Inserted into courses, $COURSE` usando `echo` en su área de declaraciones.

      Todo debería verse así:

      ```sh
      if [[ $INSERT_COURSE_RESULT == "INSERT 0 1" ]]
         then
            echo "Inserted into courses, $COURSE"
         fi
      ```

### Paso 41 Agregue echo TRUNCATE tables

En lugar de eliminar manualmente los datos cada vez que desee ejecutar el script, agregue el comando para que lo haga por usted. Cerca de la parte superior del archivo, debajo de la variable `PSQL`, use `echo` para consultar la base de datos. En la consulta, quite las filas de las cuatro tablas en este orden: `students`, `majors`, `courses`, `majors_courses`.

   1. **Acción**:

      Toda la línea debería verse así:

      ```sh
      echo $($PSQL "TRUNCATE students, majors, courses, majors_courses")
      ```

### Paso 42 Agrega COURSE_ID, INSERT_MAJORS_COURSES_RESULT, if INSERT_MAJORS_COURSES_RESULT

Debajo del comentario para obtener el nuevo `course_id`, establece el `COURSE_ID` en el `course_id` recién insertado.

   1. **Acción**:

      Así es como debería verse toda la línea, Asegúrese de que esté en el área de declaraciones `if [[ -z $COURSE_ID ]]`:
      
      ```sh
      COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")
      ```

   2. **Acción**:

      Debajo del comentario de inserción en cursos de `majors_courses`, crea una variable `INSERT_MAJORS_COURSES_RESULT`. Úsala junto con las variables `MAJOR_ID` y `COURSE_ID` que creaste para insertar una fila en la tabla `majors_courses`. Asegúrate de que la consulta tenga primero la columna `major_id`. Además, no necesitarás comillas alrededor de los valores de los identificadores.
      Así es como debería verse toda la línea:

      ```sh
      INSERT_MAJORS_COURSES_RESULT=$($PSQL "INSERT INTO majors_courses(major_id, course_id) VALUES($MAJOR_ID, $COURSE_ID)")
      ```

   3. **Acción**:

      Debajo de la variable que acaba de crear, agregue una condición `if` que verifique si es igual a `INSERT 0 1` como las demás. En su área de declaraciones, use `echo` para imprimir `Inserted into majors_courses, $MAJOR : $COURSE`.

      Todo debería verse así:

      ```sh
      if [[ $INSERT_MAJORS_COURSES_RESULT == "INSERT 0 1" ]]
         then
         echo "Inserted into majors_courses, $MAJOR : $COURSE"
         fi
      ```

### Paso 43 cp students.csv, cat students_test.csv

A continuación, debes agregar todo lo del archivo `students.csv`. Crea algunos datos de prueba nuevamente. En la terminal, usa el comando `copy` para copiar `students.csv` en un archivo llamado `students_test.csv`.

   1. **Acción**:

      Ingresa `cp students.csv students_test.csv` en la terminal
      
   2. **Acción**:

      En el archivo `students_test.csv`, elimina todo excepto las primeras cinco líneas como lo hiciste para el otro archivo de prueba. Asegúrate de que haya una línea vacía en la parte inferior nuevamente.

   3. **Acción**:
      
      Debajo del bucle existente, use `cat` para imprimir su nuevo archivo de prueba. Convierte los resultados en un bucle `while`, configurando `IFS` en una coma nuevamente y luego usa `read` para crear las variables `FIRST`, `LAST`, `MAJOR` y ``GPA a partir de los datos. En el bucle, usa `echo` para imprimir la variable `FIRST`.
      
      Así es como se ve:

      ```sh
      cat students_test.csv | while IFS="," read FIRST LAST MAJOR GPA
      do
         echo $FIRST
      done
      ```
      
   4. **Acción**:

      Borra la línea echo $FIRST

      
### Paso 44 Agrega if first_name y comentarios

Agrega una condición `if` al bucle que verifique si la variable `FIRST` no es igual a `first_name` para que no haga nada en la primera línea del archivo. Agregue cuatro comentarios de una sola línea en su bucle; `get major_id`, `if not found`, `set to null`, e `insert student` en ese orden.

   1. **Acción**:

      Su segundo bucle debería verse así:

      ```sh
      cat students_test.csv | while IFS="," read FIRST LAST MAJOR GPA
      do
         if [[ $FIRST != "first_name" ]]
         then
         # get major_id

         # if not found

         # set to null

         # insert student
      
         fi
      done
      ```
      
  
### Paso 45 Agregue MAJOR_ID, echo MAJOR_ID, if -z MAJOR_ID, establezca MAJOR_ID en null y Elimine echo MAJOR_ID

Debajo del nuevo comentario `get major_id`, configure la variable `MAJOR_ID` en una consulta que obtenga el `major_id` de la especialidad del estudiante actual.

   1. **Acción**:

      Así es como debería verse toda la línea:
      
      ```sh
      MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")
      ```

   2. **Acción**:

      Agregue `echo $MAJOR_ID` debajo de la variable `MAJOR_ID` que acaba de crear.

   3. **Acción**:

      Debajo del comentario `if not found`, agregue un `if` que verifique si la variable está vacía. Coloque el comentario `set to null` en su área de declaraciones.

      Debería verse así:

      ```sh
      if [[ -z $MAJOR_ID ]]
      then
         # set to null

      fi
      ```

   4. **Acción**:

      Debajo del comentario `set to null`, establezca la variable `MAJOR_ID` en `null` para que pueda usarla para insertar los datos.

      Debería verse así:

      ```sh
      if [[ -z $MAJOR_ID ]]
      then
         # set to null
         MAJOR_ID=null
      fi
      ```

   5. **Acción**:

      Elimine la línea `echo $MAJOR_ID` del archivo.

### Paso 46 Agregue INSERT_STUDENT_RESULT, if INSERT_STUDENT_RESULT

Deberá configurar las cuatro columnas al agregar la información del estudiante. Todas excepto `student_id`. Debajo del comentario de inserción del estudiante, cree una variable `INSERT_STUDENT_RESULT` que agregue al estudiante a la base de datos. Agregue las columnas en el orden en que aparecen en los datos y asegúrese de poner solo las dos columnas `VARCHAR` entre comillas simples.

   1. **Acción**:

      Así es como debería verse toda la línea:

      ```sh
      INSERT_STUDENT_RESULT=$($PSQL "INSERT INTO students(first_name, apellido, id_major, gpa) VALUES('$FIRST', '$LAST', $MAJOR_ID, $GPA)")
      ```
   2. **Acción**:

      Debajo de la variable que acaba de crear, agregue una declaración `if` que verifique si es igual a `INSERT 0 1` como las demás. Si lo es, use `echo` para imprimir `Inserted into students, <first_name> <last_name>`.

      Todo debería verse así:

      ```sh
      if [[ $INSERT_STUDENT_RESULT == "INSERT 0 1" ]]
      then
         echo "Inserted into students, $FIRST $LAST"
      fi
      ```
   3. **Acción**:

      Vea todos los datos en la tabla de estudiantes para asegurarse de que coincidan con el archivo CSV.

      Ingrese `SELECT * FROM students;` en el indicador de psql


### Paso 47 Cambiar a cat courses.csv y cat students.csv

Agregó todos los estudiantes de los datos de la prueba. Es hora de probarlo con los archivos originales. Cambie la línea `cat courses_test.csv` y `cat students_test.csv` para usar el archivo original nuevamente.

   1. **Acción**:

      Cambie `cat courses_test.csv` a `cat courses.csv`
      
      La línea sugerida debería verse así: `cat courses.csv | while IFS="," read MAJOR COURSE`

   2. **Acción**:

      Cambie `cat students_test.csv` a `cat students.csv`
      
      La línea sugerida debería verse así: `cat students.csv | mientras IFS="," leer PRIMERO ÚLTIMO PROMEDIO DE CALIDAD`

   3. **Acción**:

      Ejecute el script y vea si funciona. Escriba `./insert_data.sh` en la terminal bash y presione enter.

      Después de ejecutar el script, las tablas deberían tener esta cantidad de filas: `majors` tiene 7, `courses` tiene 17, `majors_courses` tiene 28 y `students` debería tener 31.

### Paso 48 SELECT * FROM students, SELECT * FROM majors, SELECT * FROM courses, SELECT * FROM majors_courses

Vea todos los datos en la tabla `students`, `majors`, `courses` y `majors_courses` para ver con qué terminó.

   1. **Acción**:

      Ingrese  en el indicador de psql

      `SELECT * FROM students;`
      
      `SELECT * FROM majors;`

      `SELECT * FROM courses;`

      `SELECT * FROM majors_courses;`


### Paso 49 ls, rm students_test.csv, rm courses_test.csv

Ya no necesitas tus archivos de prueba. En la terminal, usa el comando `list` para verificar qué archivos hay en la carpeta de tu proyecto.

   1. **Acción**:

      Ingresa ls en la terminal

   2. **Acción**:

      Utilice el comando `remove` (`rm`) para eliminar el archivo `students_test.csv` y `courses_test.csv`.
      
      Introduzca `rm students_test.csv`
      
      Introduzca `rm courses_test.csv` en la terminal

   3. **Acción**:

      Vuelva a enumerar el contenido de la carpeta para asegurarse de que no haya más contenido. Introduzca `ls` en la terminal.

      
### Paso 50 pg_dump --help, dump database

La base de datos está terminada por ahora. Lo último que vas a hacer es crear un "dump" de la base de datos. El comando `pg_dump` puede hacerlo por ti. Usa el indicador `--help` con el comando para ver lo que puede hacer.

   1. **Acción**:

      Ingresa `pg_dump --help` en la terminal bash

      Presiona enter hasta que hayas visto todo el manual

   2. **Acción**:
      
      Este es el último paso.

      Ingresa `pg_dump --clean --create --inserts --username=freecodecamp students > students.sql` en la terminal para volcar la base de datos en un archivo `students.sql`. Guardará todos los comandos necesarios para reconstruirla. Echa un vistazo rápido al archivo cuando hayas terminado.

## ARCHIVO insert_data.sh

```sh
#!/bin/bash

# Script to insert data from courses.csv and students.csv into students database

PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
echo $($PSQL "TRUNCATE students, majors, courses, majors_courses")

cat courses.csv | while IFS="," read MAJOR COURSE
do
  if [[ $MAJOR != "major" ]]
  then
    # get major_id
    MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")

    # if not found
    if [[ -z $MAJOR_ID ]]
    then
      # insert major
      INSERT_MAJOR_RESULT=$($PSQL "INSERT INTO majors(major) VALUES('$MAJOR')")
      if [[ $INSERT_MAJOR_RESULT == "INSERT 0 1" ]]
      then
        echo Inserted into majors, $MAJOR
      fi

      # get new major_id
      MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")
    fi

    # get course_id
    COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")

    # if not found
    if [[ -z $COURSE_ID ]]
    then
      # insert course
      INSERT_COURSE_RESULT=$($PSQL "INSERT INTO courses(course) VALUES('$COURSE')")
      if [[ $INSERT_COURSE_RESULT == "INSERT 0 1" ]]
      then
        echo Inserted into courses, $COURSE
      fi

      # get new course_id
      COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")
    fi

    # insert into majors_courses
    INSERT_MAJORS_COURSES_RESULT=$($PSQL "INSERT INTO majors_courses(major_id, course_id) VALUES($MAJOR_ID, $COURSE_ID)")
    if [[ $INSERT_MAJORS_COURSES_RESULT == "INSERT 0 1" ]]
    then
      echo Inserted into majors_courses, $MAJOR : $COURSE
    fi
  fi
done

cat students.csv | while IFS="," read FIRST LAST MAJOR GPA
do
  if [[ $FIRST != "first_name" ]]
  then
    # get major_id
    MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'") 

    # if not found
    if [[ -z $MAJOR_ID ]]
    then
      # set to null
      MAJOR_ID=null
    fi

    # insert student
    INSERT_STUDENT_RESULT=$($PSQL "INSERT INTO students(first_name, last_name, major_id, gpa) VALUES('$FIRST', '$LAST', $MAJOR_ID, $GPA)")
    if [[ $INSERT_STUDENT_RESULT == "INSERT 0 1" ]]
    then
      echo Inserted into students, $FIRST $LAST
    fi
  fi
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


