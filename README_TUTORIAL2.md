# Student Database

### [Learn SQL by Building a Student Database: Part 2](https://github.com/Laboratoria/learn-sql-by-building-a-student-database-part-2)

Este documento proporciona un registro detallado de las actividades realizadas y los comandos ejecutados durante la segunda parte del proyecto de base de datos de estudiantes.

Haz clic [aquí para iniciar el segundo tutorial](https://gitpod.io/new/?autostart=true#CODEROAD_TUTORIAL_URL=https%3A%2F%2Fraw.githubusercontent.com%2FLaboratoria%2Flearn-sql-by-building-a-student-database-part-2%2Fmain%2Ftutorial.json,CODEROAD_DISABLE_RUN_ON_SAVE=true/https://github.com/Laboratoria/learn-sql-by-building-a-student-database-part-2)

---
## Registro de Actividades

### Paso 1: Inicio del Terminal y Login en psql

Lo primero que debes hacer es iniciar la terminal.

Escribe `echo hello SQL` en la terminal y presiona enter.

Luego, para iniciar sesión en psql, escribe `psql --username=freecodecamp --dbname=postgre`s en el terminal y presiona enter 
para acceder a la base de datos que creaste en la Parte 1 del tutorial.

### Paso 2: Reconstruir la base de datos

Su base de datos no está aquí. Puede usar el archivo `.sql` que creó al final de la Parte 1 para reconstruirla. 
Recomiendo "dividir" la terminal. Una vez que haya hecho eso, ingrese `psql -U postgres < students.sql` para reconstruir la base de datos.

### Paso 3: Short command

Comando `\l`

Use el comando de acceso directo `list`

Escriba `\l` en el indicador psql y presione enter.

Comando `\c students `

Use el comando de acceso directo `connect` con el nombre de la base de datos después.

Escriba `\c students` en el indicador psql y presione enter.

Comando `\d`

Ahora que está conectado, muestre las tablas y relaciones que están aquí para ver si todo está correcto.

Escriba `\d` en el indicador psql y presione enter.

Comando `\d students`

Vea los detalles de la tabla `students` para asegurarse de que la estructura sea correcta.

Escriba \d students en el indicador psql y presione enter.

### Paso 4: select * from students

Asegúrese también de que todos los datos estén en la tabla.

  1. **Acción**:
     
     Escribe `SELECT * FROM students;` en el indicador de psql

### Paso 5: touch student_info.sh

Usa touch en la terminal bash para crear `student_info.sh`. Vas a crear un script para imprimir información sobre tus estudiantes.

  1. **Acción**:

     Ingrese `touch student_info.sh` en la terminal bash

### Paso 6: chmod +x student_info.sh

Déle permisos de ejecución a su nuevo archivo.

  1. **Acción**:

     Ingrese `chmod +x student_info.sh` en la terminal y presione enter.

### Paso 7: Agregue shebang y un comentario

Agregue un shebang que use bash en la parte superior de su nuevo script.

  1. **Acción**:

     Agregue a su archivo `student_info.sh`

     ```sh
     #!/bin/bash
     ```

  2. **Acción**:
     
     Agregue  debajo del "shebang" en su archivo `student_info.sh`

     ```sh
     # Info about my computer science students from students database
     ```

### Paso 8: Agregue el título echo

En el nuevo script, use `echo` para imprimir ~~ My Computer Science Students ~~. Use el indicador `-e` para colocar una nueva línea al principio y al final del texto.

El carácter de nueva línea es \n

  1. **Acción**:

     Agregue debajo del comentario en su archivo `student_info.sh`:
     
     ```sh
     echo -e "\n~~ My Computer Science Students ~~\n"` debajo del comentario en su archivo `student_info.sh
     ```

### Paso 9: ./student_info.sh

Ejecute el script para asegurarse de que funciona.

  1. **Acción**:

     Escriba `./student_info.sh` en la terminal y presione enter

### Paso 10: Agregue la variable PSQL

Deberá consultar la base de datos nuevamente para obtener información sobre los estudiantes que desea mostrar. 
Agregue la misma variable PSQL que usa en el script `insert_data.sh.` 

  1. **Acción**:

     Agregue la variable sugerida al final del archivo `student_info.sh:`

      ```sh
     PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
      ```

### Paso 11: Agregue echo students with 4.0

Debajo de la variable `PSQ`L que acaba de agregar, use echo para imprimir `First name, last name, and GPA of students with a 4.0 GPA:`. 
Use el indicador `-e` para colocar una nueva línea al comienzo de la oración.

  1. **Acción**:

     En la parte inferior del archivo student_info.sh, agregue lo siguiente:

     ```sh
     echo -e "\nNombre, apellido y GPA de los estudiantes con un GPA de 4.0:"
     ```
     
### Paso 12 psql Consultas

`SQL` significa "lenguaje de consulta estructurado". Es el lenguaje que ha estado utilizando para administrar sus bases de datos relacionales. En el indicador de `psql`, visualice todos los datos en la tabla `students` como lo ha hecho muchas veces.

  1. **Acción**:

     Ingrese `SELECT * FROM students;` en el indicador de psql

  2. **Acción**:

     En el indicador de psql, vea solo la columna `first_name` de la tabla `students`.

     Ingrese `SELECT first_name FROM students;` en el indicador de psql

  3. **Acción**:

     Vea las columnas `first_name`, `last_name` y `gpa` de la tabla students.
     
     Ingrese `SELECT first_name, last_name, gpa FROM students;` en el indicador de psql
     
  4. **Acción**:

     Puede devolver solo las filas que desee agregando `WHERE <condition>` a su consulta. Una condición puede constar de una columna, un operador y un valor. Use uno de estos para ver las mismas columnas que antes, pero solo las filas `WHERE gpa < 2.5`.

     Ingrese `SELECT first_name, last_name, gpa FROM students WHERE gpa < 2.5;` en el indicador de psql

  5. **Acción**:

     El `<` solo devuelve filas donde la columna gpa fue menor que 2.5. Otros operadores son: `<`, `>`, `<=`, `>=`. Vea las mismas columnas, pero solo las filas de los estudiantes con un gpa mayor o igual a 3.8.

     Ingrese `SELECT first_name, last_name, gpa FROM students WHERE gpa >= 3.8;` en el indicador de psql

  6. **Acción**: psql SELECT WHERE != 4.0

     También hay operadores de igual (`=`) y no igual (`!=`). Vea las mismas columnas para los estudiantes que no tienen un GPA de 4.0.

     Ingrese `SELECT first_name, last_name, gpa FROM students WHERE gpa != 4.0;` en el indicador de psql
