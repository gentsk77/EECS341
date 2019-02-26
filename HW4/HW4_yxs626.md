# Assignment 4

  EECS341 Spring 2019
  Yue Shu
  Due: Thursday, Feb 28, 2019

---

## 1. Find the name of users associated with only the area “Cleveland City”

### a. Relational algebra

$ \prod_{user.name} (\sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id ~\wedge~ role\_area.area\_id ~ = ~ area.id ~\wedge~ area.name~ = ~'Cleveland~City'} (user \times user\_role \times role\_area \times area)) $

### b. Tuple relational calculus


### c. SQL

```sql
SELECT DISTINCT u.name 
FROM user u, user_role ur, role_area ra, area a 
WHERE u.id = ur.user_id  
  AND ur.role_id = ra.role_id 
  AND ra.area_id = a.id 
  AND a.name = 'Cleveland City';
```

--- 

## 2. Find the name of users associated with every area except “Cleveland City”

We are substracting prob1 from all of the users who is related to an area. 

### a. Relational algebra

$ \prod_{user.name} (\sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id ~\wedge~ role\_area.area\_id ~ = ~ area.id} (user \times user\_role \times role\_area \times area)) - \prod_{user.name} (\sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id ~\wedge~ role\_area.area\_id ~ = ~ area.id ~\wedge~ area.name~ = ~'Cleveland~City'} (user \times user\_role \times role\_area \times area)) $

### b. Tuple relational calculus


### c. SQL

```sql
SELECT DISTINCT user.name 
FROM user, user_role, role_area, area 
WHERE user.id = user_role.user_id  
  AND user_role.role_id = role_area.role_id 
  AND role_area.area_id = area.id 
  AND user.id NOT IN (SELECT ur.user_id
                      FROM user_role ur, role_area ra, area a
                      WHERE ur.role_id = ra.role_id 
                        AND ra.area_id = a.id 
                        AND a.name = 'Cleveland City');
```
