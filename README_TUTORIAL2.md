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

### Paso 22: Agrega echo

En el script de información del estudiante, agrega una declaración `echo` en la parte inferior como la otra para imprimir los resultados de la consulta sugerida.

  1. **Acción**:

     Agregue al final del archivo `student_info.sh`
     
     ```sh
     echo "$($PSQL "SELECT last_name FROM students WHERE last_name ILIKE '%sa%' OR last_name LIKE '%r_'")"
     ```

1700. ./student_info.sh
1700.1
Ejecute la secuencia de comandos para ver los resultados.

SUGERENCIAS
Ejecute el script student_info.sh
Escriba ./student_info.sh en la terminal y presione enter
Asegúrese de estar en la carpeta del proyecto primero
1710. Agregue echo students without major begin with D or gpa > 3.0
1710.1
Parece que cinco estudiantes cumplen con esas condiciones. Agregue otro comando echo en la parte inferior, como los demás. Haga que este diga: Nombre, apellido y GPA de los estudiantes que no han seleccionado una especialidad y su nombre comienza con 'D' o tienen un GPA mayor que 3.0:

SUGERENCIAS
En la parte inferior del archivo, use echo con el indicador -e y un carácter de nueva línea nuevamente para imprimir la oración sugerida
El carácter de nueva línea es \n
A continuación, se incluye un ejemplo del comando: echo -e "\n<text_here>"
En la parte inferior del archivo student_info.sh, agregue lo siguiente:
echo -e "\nNombre, apellido y GPA de los estudiantes que no han seleccionado una especialidad y su nombre comienza con 'D' o tienen un GPA mayor que 3.0:"
1715. psql SELECT * FROM students
1715.1
Comience por ver todos los datos en la tabla students.

SUGERENCIAS
Use las palabras clave SELECT y FROM con * para ver todos los datos
Ingrese SELECT * FROM students; en el indicador de psql
Ingrese psql --username=freecodecamp --dbname=students en la terminal para iniciar sesión en el indicador de psql si aún no lo ha hecho
