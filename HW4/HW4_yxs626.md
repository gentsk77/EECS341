# Assignment 4

  EECS341 Spring 2019
  Yue Shu
  Due: Thursday, Feb 28, 2019

---

## 1. Find the name of users associated with only the area “Cleveland City”

### a. Relational algebra

$ \prod_{user.name} (\sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id ~\wedge~ role\_area.area\_id ~ = ~ area.id ~\wedge~ area.name~ = ~'Cleveland~City'} (user \times user\_role \times role\_area \times area)) $

### b. Tuple relational calculus

$ \{t~|~(\exist u)(u \in user (u[name] = t[name] \wedge (\exist ~ ur) (ur \in user\_role (ur[user\_id] = u[id] \wedge (\exist ra)(ra \in role\_area (ra[role\_id] = role[id] \wedge (\exist a)(a \in area (a[id] = ra[area\_id] \wedge a[name] = 'Cleveland City'))))))) \}   $

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

For this problem, in order to find the users associated with every area except "Cleveland City", we need to first figure out the total number of distinct areas in the database. 

### a. Relational algebra

What we do for this part is just to divide the list of all the areas except "Cleveland City" from a list of user names as well as the areas associated with them. 

$ \prod_{user.name, ~ role\_area.area\_id} (\sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id } (user \times user\_role \times role\_area )) / \prod_{area.id} (\sigma_{area.name <> 'Cleveland~City'} (area))  $


### b. Tuple relational calculus


### c. SQL

```sql

```
