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

     Ingrese `SELECT first_name, last_name, gpa FROM students WHERE gpa < 2.5;` en el indicador de `psql`

  5. **Acción**:

     El `<` solo devuelve filas donde la columna gpa fue menor que 2.5. Otros operadores son: `<`, `>`, `<=`, `>=`. Vea las mismas columnas, pero solo las filas de los estudiantes con un gpa mayor o igual a 3.8.

     Ingrese `SELECT first_name, last_name, gpa FROM students WHERE gpa >= 3.8;` en el indicador de `psql`

  6. **Acción**: psql SELECT WHERE != 4.0

     También hay operadores de igual (`=`) y no igual (`!=`). Vea las mismas columnas para los estudiantes que no tienen un GPA de 4.0.

     Ingrese `SELECT first_name, last_name, gpa FROM students WHERE gpa != 4.0;` en el indicador de `psql`

### Paso 13 Agregar resultado de consulta con echo

En su archivo `student_info.sh`, agregue un comando `echo` al final que imprima lo que solicita la oración anterior. Coloque comillas dobles alrededor de él de esta manera: `echo "$($PSQL "<query_here>")"`. Esto hará que el resultado no esté todo en una sola línea.

  1. **Acción**:

     Agregue  al final del archivo `student_info.sh`
     
     ```sh
     echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE gpa = 4.0")"
     ```
 2. **Acción**:

    Ejecute la secuencia de comandos para ver a sus estudiantes con los `GPA` más altos.
    
    Escriba `./student_info.sh` en la terminal y presione enter


### Paso 14 Agregue echo courses before D

Agregue otra declaración `echo` al final del script. `All course names whose first letter is before 'D' in the alphabet:`. Coloque una nueva línea delante de ella como la primera oración.

  1. **Acción**:

     En la parte inferior del archivo `student_info.sh`, agregue lo siguiente:

     ```sh
     echo -e "\nAll course names whose first letter is before 'D' in the alphabet:"
     ```

### Paso 15 psql consultas

Practique primero. En el indicador `psql`.

  1. **Acción**:

     Vea todos los datos en la tabla `majors`.
     
     Ingrese `SELECT * FROM majors;`

  2. **Acción**:

     Utilice el `=` para ver todas las carreras nombradas `Game Design`.
     No olvide que necesita comillas simples alrededor de los valores de texto.
     
     Ingrese `SELECT * FROM majors WHERE major = 'Game Design';`

  4. **Acción**:

     A continuación, visualiza todas las filas que no sean iguales a `Game Design`.

     Ingresa `SELECT * FROM majors WHERE major != 'Game Design';`

  5. **Acción**:

     Usa el operador mayor que para ver las carreras que vienen después en orden alfabético.

     Ingresa `SELECT * FROM majors WHERE major > 'Game Design';`

  6. **Acción**:

     `Game Design` no se incluyó en los resultados porque no es `>'Game Design'`. Pruébalo con el operador mayor o igual a.

     Ingresa `SELECT * FROM majors WHERE major >= 'Game Design';` 

  7. **Acción**:

     Si quieres ver resultados que comiencen con `G` o después, puedes usar major `>= 'G'`. Mira las carreras que vienen antes de `G`.

     Ingresa `SELECT * FROM majors WHERE major < 'G';` 


### Paso 16: Agregar resultado de consulta con echo

En su secuencia de comandos, agregue un `echo` en la parte inferior para imprimir la información sugerida como lo hizo antes. Asegúrese de usar comillas dobles donde sea necesario.

  1. **Acción**:

     Agregue al final del archivo `student_info.sh`

     ```sh
     echo "$($PSQL "SELECT course FROM courses WHERE course < 'D'")"
     ```

  2. **Acción**:

     Ejecute la secuencia de comandos para ver qué nombres de cursos vienen antes de la letra `D`.

     Escriba `./student_info.sh` en la terminal y presione enter

### Paso 17: Agregue echo 

Agrega otra oración como las otras que dice: `First name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:`

  1. **Acción**:

     En la parte inferior del archivo `student_info.sh`, agrega lo siguiente:

     ```sh
     echo -e "\nFirst name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:"
     ```

### Paso 18: psql consultas

  1. **Acción**:

     Use el indicador `psql` para ver todos los datos en la tabla `students`.

     Ingrese `SELECT * FROM students;`

  2. **Acción**:

     Use el mismo comando, pero solo devuelva las filas de los estudiantes cuyo apellido aparece antes de `M` en el alfabeto.

     Ingrese `SELECT * FROM students WHERE last_name < 'M';`

  3. **Acción**:

     Puedes usar múltiples condiciones después de `WHERE` con `AND` u `OR`, entre otras. Solo agrega la palabra clave y otra condición. En el indicador de `psql`, usa el mismo comando que antes, pero agrega un `OR` para devolver también las filas de estudiantes con un `GPA` de 3.9.
     
     Ingresa `SELECT * FROM students WHERE last_name < 'M' OR gpa = 3.9;`

  5. **Acción**:

     Ingresa el comando anterior, pero usa `AND` para ver solo los estudiantes que cumplen con ambas condiciones.

     Ingrese `SELECT * FROM students WHERE last_name < 'M' AND gpa = 3.9;`

  6. **Acción**:

     Ingrese el comando anterior, pero agregue una tercera condición de `OR gpa < 2.3`.

     Ingresa `SELECT * FROM students WHERE last_name < 'M' AND gpa = 3.9 OR gpa < 2.3;`.

  7. **Acción**:
    
     Puede agrupar las condiciones con paréntesis de esta manera: `WHERE <condition_1> AND (<condition_2> OR <condition_2>)`. Esto solo devolvería filas donde `<condition_1>` sea verdadera y una de las otras sea verdadera. Vea los estudiantes cuyo apellido esté antes de `M` que tengan un `GPA` de 3.9 o menor que 2.3.

     Ingresa `SELECT * FROM students WHERE last_name < 'M' AND (gpa = 3.9 OR gpa < 2.3);` 

### Paso 19: Agrega el resultado de la consulta echo

De regreso en el archivo de información del estudiante, agrega un comando `echo` en la parte inferior para imprimir las filas sugeridas.

  1. **Acción**:

     Agrega

     ```sh
     echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE last_name >= 'R' AND (gpa > 3.8 OR gpa < 2.0)")" al final del archivo student_info.sh
     ```

   2. **Acción**:

      Ejecute  el script para ver los resultados.

      Escriba `./student_info.sh` en la terminal y presione enter

### Paso 20: Agregue echo


Agregue otro comando `echo`, como los demás, con una oración que diga: `Last name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:`

  1. **Acción**:

     En la parte inferior del archivo `student_info.sh`, agregue lo siguiente:

     ```sh
     echo -e "\nLast name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:"
     ```
     
### Paso 21: psql consultas

  1. **Acción**:
  
     Comience por ver todo lo que aparece en la tabla `courses` en el indicador `psql`

     Ingrese `SELECT * FROM courses;`

  2. **Acción**:

     Hay algunos que contienen la palabra `Algoritmos`. Puedes usar `LIKE` para buscar patrones en el texto como este: `WHERE <column> LIKE '<pattern>'.` Un guión bajo (`_`) en un patrón devolverá filas que tengan cualquier carácter en ese lugar. Mira las filas en esta tabla con un nombre de curso que coincida con el patrón `'_lgorithms'`.

     Ingresa `SELECT * FROM courses WHERE course LIKE '_lgorithms';`

  3. **Acción**:

     Otro carácter del patrón es `%`. Significa que puede haber cualquier cosa allí. Para buscar nombres que comiencen con `W`, puedes usar `W%`. Ver los cursos que terminan en `lgorithms`.

     Ingresa `SELECT * FROM courses WHERE course LIKE '%lgorithms';`

  4. **Acción**:

     Intenta ver los cursos que comienzan con `Web`.

     Ingresa `SELECT * FROM courses WHERE course LIKE 'Web%';`

  5. **Acción**:

     Combina los dos caracteres de coincidencia de patrones para mostrar los cursos que tienen una segunda letra `e`.

     Ingrese `SELECT * FROM courses WHERE course LIKE '_e%';`

  6. **Acción**:

     Intente ver los cursos con un espacio en sus nombres.

     Ingrese `SELECT * FROM courses WHERE course LIKE '% %';`

  7. **Acción**:

     Puede usar `NOT LIKE` para buscar cosas que no coincidan con un patrón. Vea los cursos que no contienen un espacio.

     Ingrese `SELECT * FROM courses WHERE course NOT LIKE '% %';`

  8. **Acción**:

     Intente encontrar los que contienen una `A`.

     Ingrese `SELECT * FROM courses WHERE course LIKE '%A%';`

  9. **Acción**:

     `ILIKE` ignorará el uso de mayúsculas y minúsculas al hacer una coincidencia. Úsalo para ver los cursos con `A` o `a`.

     Ingresa `SELECT * FROM courses WHERE course ILIKE '%A%';`

  10. **Acción**:
     
      También puedes poner `NOT` delante de `ILIKE`. Úsalo para ver los cursos que no contienen una `A` o una `a`.

      Ingresa `SELECT * FROM courses WHERE course NOT ILIKE '%A%';`

  11. **Acción**:

      Combina estas condiciones como cualquier otra. Visualiza los cursos que no tienen `A` mayúscula o minúscula y tienen un espacio.

      Ingresa `SELECT * FROM courses WHERE course NOT ILIKE '%A%' AND course LIKE '% %';`

### Paso 22: Agregar resultado de consulta con echo

En el script de información del estudiante, agrega una declaración `echo` en la parte inferior como la otra para imprimir los resultados de la consulta sugerida.

  1. **Acción**:

     Agregue al final del archivo `student_info.sh`
     
     ```sh
     echo "$($PSQL "SELECT last_name FROM students WHERE last_name ILIKE '%sa%' OR last_name LIKE '%r_'")"
     ```

  2. **Acción**:

      Ejecute  el script para ver los resultados.

      Escriba `./student_info.sh` en la terminal y presione enter

### Paso 23: Agregue echo

Agregue otro comando `echo` en la parte inferior, como los demás. Haga que este diga: `First name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0:`

  1. **Acción**:

     En la parte inferior del archivo student_info.sh, agregue lo siguiente:

     ```sh
     echo -e "\nFirst name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0:"
     ```
### Paso 24: psql consultas

  1. **Acción**:

     Comience por ver todos los datos de la tabla students.

     Ingrese `SELECT * FROM students;`

  2. **Acción**:

     Todos los campos que están vacíos o en blanco son nulos. Puede acceder a ellos usando `IS NULL` como condición de esta manera: `WHERE <column> IS NULL`. Vea los estudiantes que no tienen un GPA.

     Ingrese `SELECT * FROM students WHERE gpa IS NULL;`

  3. **Acción**:

     A la inversa, puede usar `IS NOT NULL` para ver filas que no son nulas. Vea toda la información sobre los estudiantes que sí tienen un `GPA`.
     
     Ingrese `SELECT * FROM students WHERE gpa IS NOT NULL;`

  4. **Acción**:

     Ver toda la información sobre los estudiantes que no han elegido una especialidad.

     Ingresa `SELECT * FROM students WHERE major_id IS NULL;`

  5. **Acción**:

     Vea los estudiantes que no tienen una especialidad, pero no incluya a los estudiantes sin un GPA.

     Ingrese `SELECT * FROM students WHERE major_id IS NULL AND gpa IS NOT NULL;`

  6. **Acción**:

     Mira los estudiantes que no tienen una especialidad y un promedio de calificaciones.

     Ingresa `SELECT * FROM students WHERE major_id IS NULL AND gpa IS NULL;`

### Paso 25: Agrega el resultado de la consulta echo

En tu script, agrega un comando echo en la parte inferior para imprimir los resultados que busca la oración.

  1. **Acción**:

     Agregue al final del archivo `student_info.sh`
     
     ```sh
     echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE major_id IS NULL AND (first_name LIKE 'D%' OR gpa > 3.0)")"
     ```
     
  2. **Acción**:

      Ejecute  el script para ver los resultados.

      Escriba `./student_info.sh` en la terminal y presione enter
     
### Paso 26: Agregue echo

Agregue otra oración, como las otras, que diga `Course name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':`

   1. **Acción**:
     
      En la parte inferior del archivo student_info.sh, agregue lo siguiente:
      ```sh
      echo -e "\nCourse name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':"
      ```
### Paso 27: psql consultas

  1. **Acción**:

     Puede especificar el orden en el que desea que aparezcan los resultados agregando `ORDER BY <column_name>` al final de una consulta. En el indicador `psql`, visualice toda la información en la tabla de estudiantes ordenada por `GPA`.

     Ingrese `SELECT * FROM students ORDER BY gpa; `   

  2. **Acción**:

     Al usar `ORDER BY`, estará en orden ascendente (`ASC`) de manera predeterminada. Agregue `DESC` (descendente) al final de la última consulta para colocar los más altos en la parte superior.

     Ingresa `SELECT * FROM students ORDER BY gpa DESC;`
     
  3. **Acción**:

     Puedes agregar más columnas al orden separándolas con una coma de esta manera: `ORDER BY <column_1>, <column_2>`. Los valores coincidentes en la primera columna ordenada se ordenarán por la siguiente. Mira toda la información de los estudiantes con los promedios de calificaciones más altos en la parte superior y en orden alfabético por `first_name` si los promedios de calificaciones coinciden.

     Ingrese `SELECT * FROM students ORDER BY gpa DESC, first_name;`
     
  4. **Acción**:

     Puede agregar `LIMIT <number>` al final de la consulta para obtener solo la cantidad que desea. Vea los estudiantes en el mismo orden que el último comando, pero solo devuelva las primeras 10 filas.

     Ingrese `SELECT * FROM students ORDER BY gpa DESC, first_name LIMIT 10;`

  5. **Acción**:

     El orden de las palabras clave en su consulta es importante. No puede colocar `LIMIT` antes de `ORDER BY`, ni ninguna de ellas antes de `WHERE`. Vea la misma cantidad de estudiantes, en el mismo orden, pero no obtenga los que no tienen un `GPA`.

     Ingrese `SELECT * FROM students WHERE gpa IS NOT NULL ORDER BY gpa DESC, first_name LIMIT 10;`

### Paso 28: Agregue el resultado de la consulta echo

En su secuencia de comandos, agregue el comando echo para imprimir las filas que solicita la oración.

  1. **Acción**:

     Agregue al final del archivo `student_info.sh`
     
     ```sh
     echo "$($PSQL "SELECT course FROM courses WHERE course LIKE '_e%' OR course LIKE '%s' ORDER BY course DESC LIMIT 5")"
     ```
     
  2. **Acción**:

      Ejecute  el script para ver los resultados.

      Escriba `./student_info.sh` en la terminal y presione enter.

### Paso 29: Agrega echo

😎 Agrega otro comando `echo` al final del script como los demás. Haz que este diga, `Average GPA of all students rounded to two decimal places:`

  1. **Acción**:

     En la parte inferior del archivo student_info.sh, agrega esto:

     ```sh
     echo -e "\nAverage GPA of all students rounded to two decimal places:"
     ```
     
### Paso 30: consultas psql

  1. **Acción**:

     Existen varias funciones matemáticas para usar con columnas numéricas. Una de ellas es `MIN`, puedes usarla al seleccionar una columna de esta manera: `SELECT MIN(<column>) FROM <table>`. Encontrará el valor más bajo en la columna. En el indicador `psql`, visualice el valor más bajo en la columna `gpa` de la tabla `students`.

     Ingrese `SELECT MIN(gpa) FROM students;` 
     
  2. **Acción**:

     Otro es `MAX`, úselo para ver el `GPA` más alto de la misma tabla.

     Ingrese `SELECT MAX(gpa) FROM students;`
     
  3. **Acción**:

     Usa una función `SUM` para averiguar cuánto suman todos los valores de la columna `major_id` en la tabla `students`.

     Ingresa `SELECT SUM(major_id) FROM students;`
     
  4. **Acción**:

     `AVG` te dará el promedio de todos los valores en una columna. Úsalo para ver el promedio de la misma columna.

     Ingrese `SELECT AVG(major_id) FROM students;`
     
  5. **Acción**:

     Puede redondear decimales hacia arriba o hacia abajo al número entero más cercano con `CEIL` y `FLOOR`, respectivamente. Use `CEIL` para redondear el promedio de `major_id` hacia arriba al número entero más cercano. Aquí hay un ejemplo: `CEIL(<number_to_round>)`.

     Ingresa `SELECT CEIL(AVG(major_id)) FROM students;`
     
  6. **Acción**:

     Puedes redondear un número al número entero más cercano con `ROUND`. Úsalo para redondear el promedio de la columna `major_id` al número entero más cercano.

     Ingresa `SELECT ROUND(AVG(major_id)) FROM students;` 

  7. **Acción**:

     Puedes redondear a una cantidad específica de decimales agregando una coma y un número a `ROUND`, de esta manera: `ROUND(<number_to_round>, <decimals_places>)`. Redondea el promedio de `major_id` a cinco decimales.

     Ingresa `SELECT ROUND(AVG(major_id), 5) FROM students;`

### Paso 31: Agrega el resultado de la consulta echo

Ahora deberías poder encontrar lo que tu script está pidiendo. Agrega el comando para imprimirlo.

  1. **Acción**:

     Agregue al final del archivo `student_info.sh`
     
     ```sh
     echo "$($PSQL "SELECT ROUND(AVG(gpa), 2) FROM students")"
     ```

  2. **Acción**:

      Ejecute  el script para ver los resultados.

      Escriba `./student_info.sh` en la terminal y presione enter.

### Paso 32: Agrega echo

Lo están haciendo bastante bien. Agregue otro comando para `Major ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:`

  1. **Acción**:

     En la parte inferior del archivo student_info.sh, agrega esto:

     ```sh
     echo -e "\nMajor ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:"
     ```
     
### Paso 33: Consultas psql

  1. **Acción**:

     Otra función es `COUNT`. Puedes usarlo de esta manera: `COUNT(<column>)`. Te dirá cuántas entradas hay en una tabla para la columna. Pruébalo en el indicador `psql` usando `COUNT(*)` para ver cuántas especialidades hay.

     Ingresa SELECT COUNT(*) FROM especialidades; en el indicador psql

  2. **Acción**:. Usando el mismo método, verifica cuántos estudiantes tienes.

     Introduzca SELECT `COUNT(*) FROM students;`
     
  3. **Acción**:

     Al utilizar  `*` de esa manera, podrá saber cuántas filas totales hay en la tabla. Vea el recuento de la columna `major_id` en la tabla `students` para ver cuántos de sus estudiantes han elegido una especialidad.

     Introduzca `SELECT COUNT(major_id) FROM students;`

  4. **Acción**:.

     El uso de `major_id` no contó los valores nulos en esa columna. 23 estudiantes tienen una especialidad. `DISTINCT` es una función que te mostrará solo valores únicos. Puedes usarla de esta manera: `DISTINCT(<column>)`. Observa los valores únicos de major_id en la tabla students.

     Ingresa `SELECT DISTINCT(major_id) FROM students;`
     
  
  5. **Acción**:

     Puede obtener los mismos resultados con `GROUP BY`. Aquí hay un ejemplo de cómo usarlo: `SELECT <column> FROM <table> GROUP BY <column>`. Use este método para ver nuevamente los valores `major_id` únicos en la tabla `students`.
     
     Ingrese `SELECT major_id FROM students GROUP BY major_id;`
     
  6. **Acción**:
    
     El resultado fue el mismo que `DISTINCT`, pero con `GROUP BY` puedes agregarle cualquiera de las funciones agregadas (`MIN, MAX, COUNT, etc.`) para encontrar más información. Por ejemplo, si quisieras ver cuántos estudiantes había en cada especialidad, podrías usar `SELECT COUNT(*) FROM students GROUP BY major_id`. Observa la columna `major_id` y la cantidad de estudiantes en cada `major_id`.

     Ingrese `SELECT major_id, COUNT(*) FROM students GROUP BY major_id;`
     
  7. **Acción**:

     Al usar `GROUP BY`, todas las columnas del área `SELECT` deben incluirse en el área `GROUP BY`. Las demás columnas deben usarse con cualquiera de las funciones de agregación (`MAX, AVG, COUNT, etc.`). Vuelve a ver los valores únicos de `major_id con GROUP BY`, pero observa cuál es el `GPA` más bajo en cada uno de ellos.
     Ingresa `SELECT major_id, MIN(gpa) FROM students GROUP BY major_id;`

  8. **Acción**:

     Ingresa la misma consulta, pero agrega una columna que también te muestre el `GPA` más alto en cada especialidad.

     Ingresa `SELECT major_id, MIN(gpa), MAX(gpa) FROM students GROUP BY major_id;`

  9. **Acción**:

     Otra opción con `GROUP BY es HAVING`. Puede agregarlo al final de esta manera: `SELECT <column> FROM <table> GROUP BY <column> HAVING <condition>`. La condición debe ser una función de agregación con una prueba. Un ejemplo podría ser usar `HAVING COUNT(*) > 0` para mostrar solo qué columna está agrupada y que tiene al menos una fila. Use `HAVING` para mostrar solo las filas de la última consulta que tienen un `GPA máximo de 4.0`.

     Ingrese `SELECT major_id, MIN(gpa), MAX(gpa) FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;`

  10. **Acción**:

      Puede cambiar el nombre de una columna con `AS` de esta manera: `SELECT <column> AS <new_column_name>` Ingrese el mismo comando, pero cambie el nombre de la columna `min` a `min_gpa`.

      Ingrese `SELECT major_id, MIN(gpa) AS min_gpa, MAX(gpa) FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;`

  11. **Acción**:

      Introduce el mismo comando, pero renombra también la columna `max` a `max_gpa`:

      Ingresa `SELECT major_id, MIN(gpa) AS min_gpa, MAX(gpa) AS max_gpa FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;`.

  12. **Acción**:
     
      Visualiza `major_id` y el número de estudiantes en cada `major_id` en una columna llamada `'number_of_students'`

      Ingresa `SELECT major_id, COUNT(*) AS number_of_students FROM students GROUP BY major_id;`.

  13. **Acción**:

      Usa `HAVING` con la última consulta para mostrar solo las filas con menos de ocho estudiantes en la especialidad

      Ingresa `SELECT major_id, COUNT(*) AS number_of_students FROM students GROUP BY major_id HAVING COUNT(*) < 8;`.
      
### Paso 34  Agrega echo para mostrar el resultado de la consulta

Agregar el comando `echo "$($PSQL "<consulta_aquí>")"` al final del archivo `student_info.sh` para imprimir los resultados sugeridos.

  1. **Acción**:

     - Agrega
     
       ```sh
       echo "$($PSQL "SELECT major_id, COUNT(*) AS number_of_students, ROUND(AVG(gpa),2) AS average_gpa FROM students GROUP BY major_id HAVING COUNT(*) > 1")"
       ```
       
  2. **Acción**:

     - Ejecutar el script `./student_info.sh` en la terminal de comandos.
       
### Paso 35 Agregar echo

Agrega un comando `echo` a tu script, como los otros, que imprima: `List of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':`

  1. **Acción**:
     
     Al final del archivo `student_info.sh`, agrega esto:

     ```sh
     echo -e "\nList of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':"
     ```

### Paso 36 Comandos JOIN

**psql students FULL JOIN majors:**

La unión FULL JOIN incluirá todas las filas de ambas tablas, tengan o no una fila que use esa clave foránea en la otra. A partir de ahí, podrías usar cualquiera de los métodos anteriores para filtrar, agrupar, ordenar, etc.

  1. **Acción**:
    Si deseas ver el nombre de una especialidad que un estudiante está tomando, necesitas unir las dos tablas en una. Aquí tienes un ejemplo de cómo hacerlo: `SELECT * FROM <table_1> FULL JOIN <table_2> ON <table_1>.<foreign_key_column> = <table_2>.<foreign_key_column>;`
    Ingresa: `SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id;`

**psql students LEFT JOIN majors:**
Una LEFT JOIN obtiene todas las filas de la tabla izquierda, pero solo las filas de la tabla derecha que están vinculadas desde la izquierda. Une las tablas students y majors con una LEFT JOIN. Usa primero la tabla students cuando sea aplicable.

  2. **Acción**:

     Escribe: `SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id;`
     
**psql students RIGHT JOIN majors:**

Una RIGHT JOIN devuelve todas las filas de la tabla de la derecha (la tabla después de JOIN), y las filas correspondientes de la tabla de la izquierda (la tabla antes de JOIN).

  3. **Acción**:

     Une las mismas dos tablas con una RIGHT JOIN esta vez.

     Escribe: `SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id;`
     
**psql students INNER JOIN majors:**

Una INNER JOIN devuelve solo las filas donde hay coincidencia en ambas tablas. Es decir, solo se incluyen en el resultado las filas que tienen correspondencias en ambas tablas basadas en la condición de JOIN.

  4. **Acción**:

     Une las tablas students y majors con una INNER JOIN. Usa primero la tabla students cuando sea aplicable.

     Escribe: `SELECT * FROM students INNER JOIN majors ON students.major_id = majors.major_id;`
     
### Paso 37 Ejercicios Prácticos de JOIN en SQL

Ahora deberías tener una idea sobre los cuatro tipos principales de JOIN. Intenta usar un `LEFT JOIN` para mostrar todas las especialidades, pero solo los estudiantes que tienen una especialidad

  1. **Acción**:

     Ingresa `SELECT * FROM majors LEFT JOIN students ON majors.major_id = students.major_id;`.
     
     Ahora, usa el `JOIN` apropiado para mostrar solo los estudiantes que están inscritos en una especialidad, y solo las especialidades que tienen un estudiante inscrito. Quieres unir las tablas `students` y `majors` de nuevo.
     
     Únelas con el `JOIN` que solo muestra filas si tienen un valor en la columna de clave foránea de la otra tabla.
     
  3. **Acción**:

     Ingresa `SELECT * FROM majors INNER JOIN students ON majors.major_id = students.major_id;`.
     
     Intenta usar un RIGHT JOIN para mostrar todos los estudiantes, pero solo las especialidades si un estudiante está inscrito en ellas.
     
     Une las tablas `students` y `majors` de nuevo
     
  4. **Acción**:

     Ingresa `SELECT * FROM majors RIGHT JOIN students ON majors.major_id = students.major_id;`.

     Usa el `JOIN` apropiado con las mismas dos tablas para mostrar todas las filas en ambas tablas, independientemente de si tienen un valor en la columna de clave foránea o no
     
  5. **Acción**:

     Ingresa `SELECT * FROM majors FULL JOIN students ON majors.major_id = students.major_id;`.
     
### Paso 38 PSQL Consultas

**psql SELECT * students INNER JOIN majors**

Usa el `JOIN` que muestre solo a los estudiantes que tienen una especialidad (majors) y solo a las especialidades que tienen un estudiante, sin agregar ninguna condición.

  1. **Acción**:

     Escribe: `SELECT * FROM students INNER JOIN majors ON students.major_id = majors.major_id;`.

     **psql SELECT major students INNER JOIN majors**

     Escribe el mismo comando, pero solo selecciona la columna que necesitas. Solo necesitas la columna `major`
     
  3. **Acción**:

     Escribe `SELECT major FROM students INNER JOIN majors ON students.major_id = majors.major_id;`.

     **psql SELECT DISTINCT(major) students INNER JOIN majors**

     Usa `DISTINCT` para devolver solo los valores únicos y ver la lista de especialidades que tienen estudiantes. Debes cambiar `major` de la consulta anterior a `DISTINCT(major)`

  4. **Acción**:

     Escribe `SELECT DISTINCT(major) FROM students INNER JOIN majors ON students.major_id = majors.major_id;`.

     **psql SELECT * students RIGHT JOIN majors**

     Supongamos que quieres una lista de las especialidades que los estudiantes no están cursando. Usa el JOIN más eficiente para unir las dos tablas que necesitas. Solo une las tablas por ahora, no utilices ninguna otra condición.

  5. **Acción**:

     Escribe `SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id; en el prompt de psql.`.

     **psql SELECT * students RIGHT JOIN majors WHERE student_id IS NULL**

     Ahora puedes ver las que no tienen estudiantes. Agrega una condición WHERE para ver solo las especialidades sin estudiantes, utilizando `student_id` en la condición.

  6. **Acción**:

     Escribe `SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id WHERE student_id IS NULL;`.

     **psql SELECT major students RIGHT JOIN majors WHERE student_id IS NULL**

     Selecciona solo las columnas necesarias para ver la lista de especialidades sin estudiantes. La columna que necesitas es `major`

  7. **Acción**:

     Escribe `SELECT major FROM students RIGHT JOIN majors ON students.major_id = majors.major_id WHERE student_id IS NULL;`.

     **psql SELECT * students LEFT JOIN majors**

     Usa el JOIN más eficiente para unir las tablas necesarias si se te pidiera obtener el nombre, apellido, especialidad y GPA de los estudiantes que están cursando Data Science o tienen un GPA de 3.8 o más. Solo une las tablas por ahora, no utilices ninguna otra condición
  
  8. **Acción**:

     Escribe `SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id;`.

     **psql SELECT students LEFT JOIN majors WHERE major = Data Science OR gpa >= 3.8**

     Usa `WHERE` para obtener solo los estudiantes que cumplen con los requisitos. Como recordatorio, el objetivo era encontrar estudiantes que estén cursando Data Science o que tengan un GPA de 3.8 o más. Debes agregar dos condiciones para verificar la columna `major` y otra para la columna `gpa`
     
  9. **Acción**:

     Escribe `SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id WHERE major='Data Science' OR gpa >= 3.8;`.

     **psql SELECT columns LEFT JOIN WHERE major = Data Science OR gpa >= 3.8**

     Escribe el mismo comando, pero selecciona solo las columnas que necesitas. Habían cuatro: el nombre del estudiante, apellido, su especialidad y GPA. Selecciónalos en ese orden.

  10. **Acción**:

      Escribe `SELECT first_name, last_name, major, gpa FROM students LEFT JOIN majors ON students.major_id = majors.major_id WHERE major='Data Science' OR gpa >= 3.8;`.

      **psql SELECT * students FULL JOIN majors**

      Usa el JOIN más eficiente para unir todas las tablas necesarias si quisieras obtener la lista de estudiantes y sus cursos, con un enfoque particular en los estudiantes que no tienen ningún curso asignado todavía y cursos que no tienen ningún estudiante inscrito. Solo une las tablas por ahora, no utilices ninguna otra condición.

  11. **Acción**:

      Escribe `SELECT * FROM students FULL JOIN courses ON students.course_id = courses.course_id;`.

      **psql SELECT * students FULL JOIN majors WHERE first_name || major LIKE ri**

      Agrega una cláusula `WHERE` a la consulta anterior para obtener solo las filas que necesitas. Las filas que querías eran aquellas con un nombre o especialidad que contuvieran "ri":

  12. **Acción**
      
      Escribe `SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE first_name LIKE '%ri%' OR major LIKE '%ri%';`.

      **psql SELECT major FROM students FULL JOIN majors WHERE first_name || major LIKE ri**

      Solo querías mostrar las columnas `first_name` y `major`. Ingresa la consulta anterior, pero solo obtén las columnas que necesitas

  13. **Acción**:

      Escribe `SELECT first_name, major FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE first_name LIKE '%ri%' OR major LIKE '%ri%';`.
      
### Paso 39 Agrega echo
Agrega el comando para imprimir lo que la instrucción está pidiendo.
1. **Acción**:
- Agrega:
```sh
echo "$($PSQL "SELECT major FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE major IS NOT NULL AND (student_id IS NULL OR first_name ILIKE '%ma%') ORDER BY major")"
```
2. **Acción**:
- Ejecuta el script `./student_info.sh` en la terminal.
### Paso 40  Agregar echo para cursos sin estudiantes o 'Obie Hilpert'
En el script, agrega un comando para imprimir esta frase como las demás: Lista de cursos únicos, en orden alfabético inverso, que ningún estudiante o 'Obie Hilpert' está tomando:
1. **Acción**:
- Al final del archivo `student_info.sh`, agrega:
```sh
echo -e "\nList of unique courses, in reverse alphabetical order, that no student or 'Obie Hilpert' is taking:"
```
### Paso 41 PSQL Consultas
**psql SELECT * FROM students FULL JOIN majors**
Comienza haciendo un FULL JOIN en tus tablas de `students` y `majors`:
1. **Acción**:
- Escribe `SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id;`.
**psql SELECT students.major_id students FULL JOIN majors**
Si observas los nombres de las columnas, verás dos columnas `major_id`: una de la tabla `students` y otra de la tabla `majors`. Si intentas consultarlas usando solo `major_id`, obtendrás un error. Necesitarás especificar de qué tabla quieres la columna, así: `<table>.<column>`. Ingresa el mismo JOIN pero obteniendo solo la columna `major_id` de la tabla `students`:
2. **Acción**:
- Escribe `SELECT students.major_id FROM students FULL JOIN majors ON students.major_id = majors.major_id;`.
**psql SELECT students.major_id FROM students FULL JOIN majors AS m**
Utilizaste 'AS' para renombrar columnas. También puedes usarlo para renombrar tablas o darles alias. Aquí tienes un ejemplo: `SELECT * FROM <table> AS <new_name>;`. Ingresa la misma consulta que acabas de hacer, pero renombra la tabla `majors` como 'm':
3. **Acción**:
- Escribe `SELECT students.major_id FROM students FULL JOIN majors AS m ON students.major_id = m.major_id;`.
**psql SELECT s.major_id FROM students AS s FULL JOIN majors AS m**
 Ingresa la misma consulta, pero renombra la tabla `students` como 's' también:
 4. **Acción**:
- Escribe `SELECT s.major_id FROM students AS s FULL JOIN majors AS m ON s.major_id = m.major_id;`.
**psql SELECT * FROM students FULL JOIN majors USING**
Hay una palabra clave de acceso directo, `USING`, para hacer JOIN entre tablas si la columna de clave foránea tiene el mismo nombre en ambas tablas. Aquí tienes un ejemplo: `SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>);`:
5. **Acción**:
- Escribe `SELECT * FROM students FULL JOIN majors USING(major_id);`.
**psql SELECT * FROM students FULL JOIN majors USING FULL JOIN major_courses USING**
Puedes agregar una tercera tabla a un JOIN así: `SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>) FULL JOIN <table_3> USING(<column>)`. Este ejemplo unirá las dos primeras tablas en una, convirtiéndola en la tabla izquierda para el segundo JOIN. Usa este método para unir las dos tablas de la consulta anterior con la tabla `majors_courses`:
6. **Acción**:
- Escribe `SELECT * FROM students FULL JOIN majors USING(major_id) FULL JOIN majors_courses USING(major_id);`.
**psql SELECT * students FULL JOIN majors USING JOIN major_courses USING JOIN courses USING**
Puedes unir tantas tablas como quieras. Une la última tabla a la consulta anterior para obtener los nombres de los cursos con toda esta información:
7. **Acción**:
- Escribe `SELECT * FROM students FULL JOIN majors USING(major_id) FULL JOIN majors_courses USING(major_id) FULL JOIN courses USING(course_id);`.
### Paso 42 Agregar echo result
En el script, agrega el comando para imprimir la información sugerida.
1. **Acción**:
- Agrega
```sh
echo "$($PSQL "SELECT DISTINCT(course) FROM students RIGHT JOIN majors USING(major_id) INNER JOIN majors_courses USING(major_id) INNER JOIN courses USING(course_id) WHERE (first_name = 'Obie' AND last_name = 'Hilpert') OR student_id IS NULL ORDER BY course DESC")"
```
2. **Acción**:
- Ejecuta el script `./student_info.sh` e la terminal.
### Paso 43 Agregar echo para cursos con solo un estudiante
Último paso. Añade un comando que imprima la frase: `List of courses, in alphabetical order, with only one student enrolled:`:
1. **Acción**:
- Agrega al  final del archivo `student_info.sh`:
```sh
echo -e "\nList of courses, in alphabetical order, with only one student enrolled:"
```
### Paso 44 Agregar resultado de consulta con echo
Añade un comando al final del script para imprimir la información sugerida:
1. **Acción**:
- Agrega al  final del archivo `student_info.sh`:
```sh
echo "$($PSQL "SELECT course FROM students INNER JOIN majors_courses USING(major_id) INNER JOIN courses USING(course_id) GROUP BY course HAVING COUNT(student_id) = 1 ORDER BY course")"
```
2. **Acción**:
- Ejecuta el script una última vez. :hola:.
19:13
### Archivo  `student_info.sh`
```sh
#!/bin/bash
# Info about my computer science students from students database
echo -e "\n~~ My Computer Science Students ~~\n"
PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
echo -e "\nFirst name, last name, and GPA of students with a 4.0 GPA:"
echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE gpa = 4.0")"
echo -e "\nAll course names whose first letter is before 'D' in the alphabet:"
echo "$($PSQL "SELECT course FROM courses WHERE course < 'D'")"
echo -e "\nFirst name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:"
echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE last_name >= 'R' AND (gpa > 3.8 OR gpa < 2.0)")"
echo -e "\nLast name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:"
echo "$($PSQL "SELECT last_name FROM students WHERE last_name ILIKE '%sa%' OR last_name ILIKE '%r_'")"
echo -e "\nFirst name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0:"
echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE major_id IS NULL AND (first_name LIKE 'D%' OR gpa > 3.0)")"
echo -e "\nCourse name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':"
echo "$($PSQL "SELECT course FROM courses WHERE course LIKE '_e%' OR course LIKE '%s' ORDER BY course DESC LIMIT 5")"
echo -e "\nAverage GPA of all students rounded to two decimal places:"
echo "$($PSQL "SELECT ROUND(AVG(gpa), 2) FROM students")"
echo -e "\nMajor ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:"
echo "$($PSQL "SELECT major_id, COUNT(*) AS number_of_students, ROUND(AVG(gpa), 2) AS average_gpa FROM students GROUP BY major_id HAVING COUNT(*) > 1")"
echo -e "\nList of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':"
echo "$($PSQL "SELECT major FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE major IS NOT NULL AND (student_id IS NULL OR first_name ILIKE '%ma%') ORDER BY major")"
echo -e "\nList of unique courses, in reverse alphabetical order, that no student or 'Obie Hilpert' is taking:"
echo "$($PSQL "SELECT DISTINCT(course) FROM students FULL JOIN majors USING(major_id) FULL JOIN majors_courses USING(major_id) FULL JOIN courses USING(course_id) WHERE student_id IS NULL OR (first_name = 'Obie' AND last_name = 'Hilpert') ORDER BY course DESC")"
echo -e "\nList of courses, in alphabetical order, with only one student enrolled:"
echo "$($PSQL "SELECT course FROM students INNER JOIN majors_courses USING(major_id) INNER JOIN courses USING(course_id) GROUP BY course HAVING COUNT(student_id) = 1 ORDER BY course")"
```









