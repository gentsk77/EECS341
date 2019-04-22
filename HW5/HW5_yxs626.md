# Assignment 5

  EECS341 Spring 2019
  Yue Shu
  Due: Tuesday, April 22, 2019

---

### 1. Write a naive (straightforward) expression of this query in relational algebra using only cross joins, and applying predicate selections after the joins.

$$
\prod_{p.name, f.departure\_datetime, departure.name, arrival.name}( \newline \sigma_{p.id = t.passenger\_id ~ \wedge ~ p.id = :PASS\_ID ~ \wedge ~ t.flight\_id = f.id ~ \wedge ~ f.route\_id = r.id ~ \wedge ~ f.departure\_datetime > now() ~ \wedge ~ arrival.name = r.arrival\_airport ~ \wedge ~ departure.name = r.departure\_airport} (\newline \rho_p(passenger) \times \rho_t(ticket) \times \rho_f(flight) \times \rho_r(route) \times \rho_{departure}(airport) \times \rho_{arrival}(airport)))
$$

### 2. Convert the expression from (1) into a parse tree.

