# Assignment 3

  EECS341 Spring 2019
  Yue Shu  
  Due: Thursday, Feb 21, 2019

---

### 1. Find the ID and name for all users who are not associated with a role.

For this problem, what we need to do is to substract users who are associated with a role from all the users and project their name and id. 

```sql
SELECT DISTINCT t.name, t.id 
FROM user t 
WHERE t.id NOT IN (SELECT u.id 
                   FROM user u, user_role b 
                   WHERE u.id = b.user_id);
```

