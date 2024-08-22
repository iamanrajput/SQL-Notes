## Practise Question
Create this sample table 
```
CREATE DATABASE college;
USE college;
CREATE TABLE student (
  rollno INT PRIMARY KEY,
  name VARCHAR(50),
  marks INT NOT NULL,
  grade VARCHAR(1),
  city VARCHAR(20)
);
```
Insert this data:
```
INSERT INTO student
(rollno, name, marks, grade, city)
VALUES
(101, "aman", 98, "A", "Delhi"), 
(102, "mayank", 93, "A", "Udaipur"),
(103, "devesh", 85, "B", "Sikar"),
(104, "akshita", 96, "A", "Delhi"),
(105, "shruti", 72, "C", "Delhi"),
(106, "kunal", 32, "F", "Bihar");
```
