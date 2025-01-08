1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT
`students`.`degree_id`,
`degrees`.`name` `degree_name`,
`students`.`name`,
`students`.`surname`
 FROM `students`
 INNER JOIN `degrees`
 ON `students`.`degree_id`=`degrees`.`id`
WHERE `students`.`degree_id`= 53;
```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
   Neuroscienze

```sql
SELECT
`departments`.`name` `department_name`,
`degrees`.`department_id`,
`degrees`.`name` `degree_name`,
`degrees`.`level` `degree_level`
FROM `departments`
INNER JOIN `degrees`
ON `departments`.`id`= `degrees`.`department_id`
WHERE `degrees`.`department_id`= 7 AND
`degrees`.`level`= "magistrale";
```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT
`course_teacher`.*,
`teachers`.`name` `teacher_name`,
`teachers`.`surname` `teacher_surname`
FROM `course_teacher`
INNER JOIN `courses`
ON `courses`.`id`=`course_teacher`.`course_id`
INNER JOIN `teachers`
ON `teachers`.`id`= `course_teacher`.`teacher_id`
WHERE `course_teacher`.`teacher_id`= 44;
```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
   sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
   nome

```sql
SELECT
`students`.`id` `student_id`,
`students`.`degree_id`,
`students`.`surname`,
`students`.`name`,
`degrees`.`name` `degree_name`,
`degrees`.`level`,
`departments`.`name` `department_name`
 FROM `students`
INNER JOIN `degrees`
ON `degrees`.`id`=`students`.`degree_id`
INNER JOIN `departments`
ON `departments`.`id`=`degrees`.`department_id`
ORDER BY `students`.`surname`, `students`.`name`;
```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT
`degrees`.`id` `degree_id`,
`degrees`.`name` `degree_name`,
`degrees`.`level`,
`teachers`.`id` `teacher_id`,
`teachers`.`name` `teacher_name`,
`teachers`.`surname` `teacher_surname`,
`courses`.`id` `course_id`,
`courses`.`name` `course_name`
FROM `degrees`
JOIN `teachers`
JOIN `courses`
ON `courses`.`degree_id`=`degrees`.`id`
JOIN `course_teacher`
ON `course_teacher`.`teacher_id`=`teachers`.`id`
ORDER BY `degrees`.`id`;
```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18
