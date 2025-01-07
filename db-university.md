1. Selezionare tutti gli studenti nati nel 1990 (160)

```sql
SELECT COUNT(`date_of_birth`) AS `date_of_birth_count` FROM university.students
WHERE YEAR(`date_of_birth`) = "1990";
```

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

```sql
SELECT COUNT(`cfu`) AS `cfu_count` FROM university.courses
WHERE `cfu` > "10";
```

3. Selezionare tutti gli studenti che hanno più di 30 anni

```sql
SELECT
`id`,
`name`,
`surname`,
`date_of_birth`
FROM university.students
WHERE YEAR(`date_of_birth`) < "1995";
```

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
   laurea (286)

```sql
SELECT
`year`,
`period`,
COUNT(`id`) AS `count`
FROM university.courses
WHERE `year` = "1" AND `period` = "I semestre"
```

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
   20/06/2020 (21)

```sql
SELECT
`date`,
COUNT(`id`) AS `count_id`
FROM university.exams
WHERE HOUR(`hour`) >= 14 AND `date` = "2020-06-20"
GROUP BY `date`;
```

6. Selezionare tutti i corsi di laurea magistrale (38)

```sql
SELECT
`level`,
COUNT(`id`) AS `id_count`
FROM university.degrees
WHERE `level` LIKE "magistrale"
GROUP BY `level`;
```

7. Da quanti dipartimenti è composta l'università? (12)

```sql
SELECT COUNT(id) AS `departments_count` FROM university.departments;
```

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

```sql
SELECT COUNT(`id`) AS `id_count`
FROM university.teachers
WHERE `phone` IS NULL;
```

9. Inserire nella tabella degli studenti un nuovo record con i propri dati (per il campo
   degree_id, inserire un valore casuale)

```sql
INSERT INTO
`university`.`students`
VALUES (
    '66', 'Angelo', 'Gemelli', '2002-04-27', 'GMLNGL02D27Z368A', '2024-09-11', '666666', 'gemeangelo27@gmail.com'
    );
```

10. Cambiare il numero dell’ufficio del professor Pietro Rizzo in 126

```sql
UPDATE
`university`.`teachers`
SET `office_number` = '126'
WHERE (`id` = '58');
```

11. Eliminare dalla tabella studenti il record creato precedentemente al punto 9
