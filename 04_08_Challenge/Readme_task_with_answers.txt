task 

Task - 1
-- What are the names of the students enrolled in the math class

select u.username from users as u
inner join enrollments as e on e.userid = u.userid
inner join classes as c on e.classcode = c.classcode
inner join roles as r on r.roleid=e.roleid
where c.classname = 'Math' and r.roletype= "Student";
________________________________________________
Task - 2
-- what classes in the person with username ehorstead2 enrolled in?

select c.className from classes as c
inner join enrollments as e on c.classcode = e.classcode
inner join users as u on u.userid = e.userid
where u.username = 'ehorstead2';
________________________________________________
Task - 3
-- Use a transaction to create a new class, enroll a teacher and two students in the class, and the check the names of the students who have name enrolled before
-- commmitting the transacton
begin transaction;

INSERT INTO classes
VALUES(6, "New Class")

INSERT INTO enrollments
VALUES (6,1,1), (6,1,2), (6,2,3);

commit;
select username from users as u
inner join enrollments as e on u.userid=e.userid
inner join classes as c on e.classcode=c.classcode
where c.classname = "New Class";
________________________________________________
Task - 4
-- Change the role of the teacher enrolled in the art class to be an administrator in that class

update enrollments set roleid = 3
where roleid =2 and classcode  = 2

select e.userid from enrollments as e
where e.roleId = 2 and e.classCode = 2;
