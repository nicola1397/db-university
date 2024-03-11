# TRACCIA 1

SELECT \*
FROM `students`
WHERE YEAR(`date_of_birth`) = 1990

# TRACCIA 2

SELECT \*
FROM `courses`
WHERE `cfu` >= 10;

# TRACCIA 3

SELECT \*
FROM `students`
WHERE YEAR(NOW()) - YEAR(date_of_birth) >= 30

# TRACCIA 4

SELECT \*
FROM `courses`
WHERE `period`="I semestre" AND `year`=1;

# TRACCIA 5

SELECT \*
FROM `exams`
WHERE `date`="2020-06-20" AND `hour` >= "14:00:00";

# TRACCIA 6

SELECT \*
FROM `degrees`
WHERE `level`="magistrale";

# TRACCIA 7

SELECT COUNT(`id`)
FROM `departments`;

# TRACCIA 8

SELECT COUNT(`id`)
FROM `teachers`
WHERE phone IS NULL;
