# TRACCIA 1

SELECT YEAR(`enrolment_date`) AS 'enrolment_year',
COUNT(\*)

FROM `students`
GROUP BY `enrolment_year`;

# TRACCIA 2

SELECT `office_address`,
COUNT(\*) AS 'number_of_teachers'
FROM `teachers`
GROUP BY `office_address`;

# TRACCIA 3

SELECT `exam_id`,
AVG(`vote`) AS 'vote_average'
FROM `exam_student`
GROUP BY `exam_id`;

# TRACCIA 4

SELECT `department_id`,
COUNT(\*) AS 'degrees_number'
FROM `degrees`
GROUP BY `department_id`;
