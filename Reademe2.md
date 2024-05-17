# JOIN

## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    - SELECT * FROM `students` INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`name` = 'Corso di laurea in Economia'; (Mostra tutti: 68 altrimenti: 5000)


## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
    - SELECT * FROM `degrees` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze'; (1)


## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
    - SELECT * FROM `teachers` INNER JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` INNER JOIN `courses` ON `courses`.id = `course_teacher`.`course_id` WHERE `teachers`.`id` = 44; (11)


## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
    - SELECT * FROM `students` INNER JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id` ORDER BY `students`.`name` ASC, `students`.`surname` ASC; (5000)


## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
    - SELECT * FROM `degrees` INNER JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id` INNER JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id` INNER JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`; (75)


## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
    - SELECT DISTINCT `teachers`.`name`, `teachers`.`surname` FROM `teachers` INNER JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` INNER JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id` INNER JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `departments`.`name` = 'Dipartimento di Matematica';  (54)


# GRUOP BY

## Contare quanti iscritti ci sono stati ogni anno
    - SELECT COUNT(id), YEAR(`enrolment_date`) FROM `students` GROUP BY YEAR (`enrolment_date`); 


## Contare gli insegnanti che hanno l'ufficio nello stesso edificio
    - SELECT COUNT(`id`), `office_address` FROM `teachers` WHERE `office_address` = `office_address` GROUP BY `office_address`; 


## Calcolare la media dei voti di ogni appello d'esame
    - SELECT `date`, AVG (`vote`) FROM `exams` INNER JOIN `exam_student` ON `exams`.`id` = `exam_student`. `exam_id` GROUP BY `date` ORDER BY `exams`.`date` ASC 


## Contare quanti corsi di laurea ci sono per ogni dipartimento
    - SELECT `departments`.`name`, COUNT(`degrees`.`id`) FROM `departments` INNER JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id` GROUP BY `departments`.`name`; 

