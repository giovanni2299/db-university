## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    - SELECT * FROM `students` INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`name` = 'Corso di laurea in Economia'; (Mostra tutti: 68 altrimenti: 5000)


## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
    - SELECT * FROM `degrees` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze'; (1)


## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
    - SELECT * FROM `teachers` INNER JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` INNER JOIN `courses` ON `courses`.id = `course_teacher`.`course_id` WHERE `teachers`.`id` = 44; (11)


## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
    - SELECT * FROM `students` INNER JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id` ORDER BY `students`.`name` ASC, `students`.`surname` ASC; (5000)


## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
    -


## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
    -


## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.
    -