###Create Our Students Table
```
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    name TEXT,
    teacher_id INTEGER);
```

###Insert Students
```
INSERT INTO students (name, teacher_id)
    VALUES ("Dave", 1);
INSERT INTO students (name, teacher_id)
    VALUES ("Jessie", 1);
INSERT INTO students (name, teacher_id)
    VALUES ("Bob", 1);
INSERT INTO students (name, teacher_id)
    VALUES ("Sara", 2);
INSERT INTO students (name, teacher_id)
    VALUES ("George",  2);
INSERT INTO students (name, teacher_id)
    VALUES ("Alexis",  NULL);
```

###Students Schema
```
id               name        teacher_id            
---------------  ----------  ----------  
1                Dave           1           
2                Jess           2              
3                Bob            1          
4                Sara           2  
5                Rob            2
6                Alexis        Null             
```

###Create Our Teachers Table
```
CREATE TABLE teachers (
    id INTEGER PRIMARY KEY,
    name TEXT);
```

###Insert Into Teachers

```
INSERT INTO teachers (name)
    VALUES ("Steven");
INSERT INTO teachers (name)
    VALUES ("Joe");
INSERT INTO teachers (name)
    VALUES ("Jeff");
```

###Teachers Schema

```
id               name                         
---------------  ---------
1                Joe                    
2                Steven  
3                Jeff                                  
```


###Left Outer Join

```
SELECT * from teachers
   LEFT OUTER JOIN students on teachers.id = students.teacher_id;
```

This query will return all of the records in the left table (teachers) regardless if any of those records have a match in the right table (students). It will also return any matching records from the right table. So for our example, it first returns all of the teachers followed by any student that has a `teacher_id`. You can see that Alexis was not returned because her `teacher_id` column is `NULL`.

###Results

```
id  teacher_name   id      name     teacher_id               
--- ------------  ----    ------    -----------
1	   Steven		     2       Bob          1
1	   Steven	  	   1       Dave         1	 
1	   Steven	  	   3       Jess         1
2	   Joe	     	   5       Rob          1
2	   Joe	     	   4       Sara         1
3	   Jeff	    	   NULL    NULL         NULL		              
```


##Right Join

```
SELECT * from teachers
   RIGHT OUTER JOIN students on teachers.id = students.teacher_id;
```
This query will return all of the records in the right table (students) regardless if any of those records have a match in the left table (teachers). It will also return any matching records from the left table. You can see that all of the students were returned, but this time Jeff was left out.

###Results

```
id    teacher_name   id      name     teacher_id               
---   ------------  ----    ------    -----------
1	     Steven		     2       Bob          1
1	     Steven	  	   1       Dave         1	 
1	     Steven	  	   3       Jess         1
2	     Joe	     	   5       Rob          1
2	     Joe	     	   4       Sara         1
NULL   NULL	    	   6       Alexis       NULL		              
```

##Full Join
