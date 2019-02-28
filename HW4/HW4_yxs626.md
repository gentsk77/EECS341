# Assignment 4

  EECS341 Spring 2019
  Yue Shu
  Due: Thursday, Feb 28, 2019

---

## 1. Find the name of users associated with only the area “Cleveland City”

### a. Relational algebra

For this problem, we are simply substracting users who are associated with area other than Cleveland City from users who are associated with at least one area. The only thing we should notice is that we cannot take the substraction of names directly, since in the case when there are repeated names, and if one was associated with "Cleveland City" only while others are not, the name will not be retrieved by doing the substraction directly. 

$ \prod_{user.name} (\sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id } (user \times user\_role \times role\_area \times area) - \sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id ~\wedge~ role\_area.area\_id ~ = ~ area.id ~\wedge~ area.name~ <> ~'Cleveland~City'} (user \times user\_role \times role\_area \times area)) $

### b. Tuple relational calculus

For this part we can simply use the $\Rightarrow$ operator to apply an universal qualification.

$ \{t| (\exists u)(u \in user \wedge t[name] = u[name] \wedge (\exists ur) (ur \in user\_role \wedge ur[user\_id] = u[id] \newline \wedge (\exists ra)(ra \in role\_area \wedge ra[role\_id] = ur[role\_id] \wedge (\forall a)(a \in area \wedge a[id] = ra[area\_id] \Rightarrow a[name] = "Cleveland ~ City")))))\}  $

### c. SQL

```sql
SELECT DISTINCT u.name
FROM user u, user_role ur, role_area ra, area a 
WHERE u.id = ur.user_id  
  AND ur.role_id = ra.role_id 
  AND ra.area_id = a.id 
  AND u.id NOT IN (
    SELECT user.id 
    FROM user, user_role, role_area, area
    WHERE user.id = user_role.user_id
      AND user_role.role_id = role_area.role_id
      AND role_area.area_id = area.id
      AND area.name <> 'Cleveland City');
```

--- 

## 2. Find the name of users associated with every area except “Cleveland City”

### a. Relational algebra

What we do for this part is just to divide the list of all the areas except "Cleveland City" from a list of user names as well as the areas associated with them. 

$ \prod_{user.name, ~ role\_area.area\_id} (\sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id } (user \times user\_role \times role\_area )) / \prod_{area.id} (\sigma_{area.name <> 'Cleveland~City'} (area))  $


### b. Tuple relational calculus


### c. SQL

```sql

```
