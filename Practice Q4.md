## Practice Qs 🚀

Q: In the student table :

a. Change the name of column" name" to "full_ name".

b. Delete all the students who scored marks less than 80.

c. Delete the column for grades.

```
SELECT * FROM student
ALTER TABLE student
CHANGE name full_name VARCHAR(50);
DELETE FROM student
WHERE marks < 80;
DROP COLUMN grade
```
