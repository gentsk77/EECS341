# Assignment 2
EECS341 Spring 2019
Yue Shu
Due: Tuesday, Feb 12, 2019

---
  - [1. Find the name and email of users who have made at least one post](#1-find-the-name-and-email-of-users-who-have-made-at-least-one-post)
  - [2. Find the topic name, topic description, and subject of all posts and replies.](#2-find-the-topic-name-topic-description-and-subject-of-all-posts-and-replies)
  - [3. Find the name of users who have only posted in the topic “Computer Science”.](#3-find-the-name-of-users-who-have-only-posted-in-the-topic-computer-science)
  - [4. Translate from sql to relational algebra:](#4-translate-from-sql-to-relational-algebra)
  - [5. Translate from sql to relational algebra:](#5-translate-from-sql-to-relational-algebra)

---
## 1. Find the name and email of users who have made at least one post

$ \prod_{user.name,~user.email} (\sigma_{user.login~=~post.login}(user \times post)) $

## 2. Find the topic name, topic description, and subject of all posts and replies.

$ \prod_{topic.name,~topic.description,~post.subject} (\sigma_{topic.name~=~post.topic\_name}(topic \times post)) $

## 3. Find the name of users who have only posted in the topic “Computer Science”.

For this problem, what we want is simply the **difference** between **name of all of the users who have posted in topic "Computer Science"** and **name of users who have posted in topic other than "Computer Science"**. We obtain the set of name of users who have only posted in the topic "Computer Science" by taking the difference as below: 

$\prod_{user.name} (\sigma_{post.topic\_name~=~'Computer~Science'~\wedge~user.login~=~post.login}(user \times post))~-~$ 
$\prod_{user.name} (\sigma_{user.login~=~post.login}(user \times (post - \sigma_{post.topic\_name~=~'Computer~Science'}(post))))$

## 4. Translate from sql to relational algebra:

```sql
SELECT u.name, p.subject, p.content
FROM post p, user u
WHERE p.login = u.login
AND u.name = ‘Finnegas’
AND p.timestamp < ‘2019-01-01’
```

$\prod_{u.name,~p.subject,~p.content} (\sigma_{p.login~=~u.login~\wedge~u.name~=~'Finnegas'~\wedge~p.timestamp~<~'2019-01-01'}(\rho_{u}(user) \times \rho_{p}(post)))$

## 5. Translate from sql to relational algebra:

```sql
SELECT * FROM (SELECT * FROM topic) t
```

Basically the two `SELECT * FROM` syntax did not alter the set `topic`, so the outcome we finally get is simply renaming `topic` as `t` as below:
$$\rho_{t}(topic)$$