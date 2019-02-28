# Assignment 4

  EECS341 Spring 2019
  Yue Shu
  Due: Thursday, Feb 28, 2019

---

## 1. Find the name of users associated with only the area “Cleveland City”

### a. Relational algebra

$ \prod_{user.name} (\sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id ~ \wedge ~ role\_area.area\_id = ~ area.id} (user \times user\_role \times role\_area \times area) - \sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id ~\wedge~ role\_area.area\_id ~ = ~ area.id ~\wedge~ area.name~ <> ~ 'Cleveland~City'} (user \times user\_role \times role\_area \times area)) $

### b. Tuple relational calculus

$ \{t| (\exists u)(u \in user \wedge t[name] = u[name] \wedge (\exists ur) (ur \in user\_role \wedge ur[user\_id] = u[id] \newline \wedge (\exists ra)(ra \in role\_area \wedge ra[role\_id] = ur[role\_id] \wedge (\forall a)(a \in area \wedge a[id] = ra[area\_id] \newline \Rightarrow a[name] = 'Cleveland~City')))))\} $

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

$ \prod_{user.name, ~ area.id} (\sigma_{user.id \, = \, user\_role.user\_id \, \wedge ~ user\_role.role\_id ~ = ~ role\_area.role\_id \wedge role\_area.area\_id = area.id \wedge area.name <> 'Cleveland City'} (user \times user\_role \times role\_area \times area)) / \prod_{area.id} (\sigma_{area.name <> 'Cleveland~City'} (area))  $

### b. Tuple relational calculus

$ \{t| (\exists u)(u \in user \wedge t[name] = u[name] \wedge (\forall a) (a \in area \wedge a[name] <> 'Cleveland ~ City' \Rightarrow \newline (\exists ur) (ur \in user\_role \wedge ur[user\_id] = u[id] \wedge (\exists ra)(ra \in role\_area \wedge ra[role\_id] = ur[role\_id] \newline \wedge a[id] = ra[area\_id] ))))\} $

### c. SQL

```sql
SELECT u.name 
FROM user u
WHERE NOT EXISTS (
  SELECT a.id
  FROM area a
  WHERE a.name <> 'Cleveland City' AND a.id NOT IN (
    SELECT area.id
    FROM user_role, role_area, area
    WHERE u.id = user_role.user_id
      AND user_role.role_id = role_area.role_id
      AND role_area.area_id = area.id));
```

