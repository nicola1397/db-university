# TRACCIA 1

SELECT
`degrees`.`name`,
`students`.\*
FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

# TRACCIA 2

SELECT
`departments`.`name`,
`degrees`.\*
FROM `degrees`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Neuroscienze';

# TRACCIA 3

SELECT \*
FROM `course_teacher`
INNER JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`
WHERE `course_teacher`.`teacher_id` = 44;

# TRACCIA 4

SELECT
`students`.`name` AS 'student_name',
`students`.`surname` AS 'student_surname',
`degrees`.`name` AS 'degrees_name',
`degrees`.`level` AS 'degrees_level',
`degrees`.`address` AS 'degrees_address',
`degrees`.`website` AS 'website',
`degrees`.`email` AS 'email',
`departments`.`name` AS 'departments_name',
`departments`.`address` AS 'departments_address',
`departments`.`phone` AS 'departments_phone',
`departments`.`head_of_department` AS 'head_of_department'
FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`
ORDER BY `student_name`, `student_surname` ASC;

# TRACCIA 5

SELECT
`degrees`.`name` AS 'degrees_name',
`courses`.`name` AS 'course_name',
`teachers`.`name` AS 'teacher_name',
`teachers`.`surname` AS 'teacher_surname'

FROM `degrees`

INNER JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`

INNER JOIN `course_teacher`
ON `course_teacher`.`course_id` = `courses`.`id`

INNER JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`;

# TRACCIA 6

SELECT DISTINCT `teachers`.\*
FROM `departments`
INNER JOIN `degrees`
ON `departments`.`id` = `degrees`.`department_id`
INNER JOIN `courses`
ON `courses`.`degree_id` = `degrees`.`id`
INNER JOIN `course_teacher`
ON `course_teacher`.`course_id` = `courses`.`id`
INNER JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
WHERE `departments`.`name` = 'Dipartimento di Matematica';

# TRACCIA 7

SELECT
CONCAT(`students`.`name`, " ", `students`.`surname`) AS 'student',
`exams`.`course_id`,
`courses`.`name` AS 'course_name',
COUNT(\*) AS 'number_of_try',
MAX(`exam_student`.`vote`) AS 'max_vote'
FROM `exam_student`
INNER JOIN `students`ON `students`.`id` = `exam_student`.`student_id`
INNER JOIN `exams`ON `exam_student`.`exam_id` = `exams`.`id`
INNER JOIN `courses`ON `courses`.`id` = `exams`.`course_id`
GROUP BY `exam_student`.`student_id`, `exams`.`course_id`
HAVING `max_vote` >= 18;
