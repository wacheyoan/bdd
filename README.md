1) 
SELECT start_time as "Dates de début" 
from bookings b 
inner join members m on b.mem_id = m.mem_id
where m.first_name = 'David'
and m.surname = 'Farrell'

2) 
SELECT to_char(start_time,'HH:MI:SS') as "Heure de début",f.name
FROM bookings b 
INNER JOIN facilities f on b.fac_id = f.fac_id
WHERE f.name IN ('Tennis Court 1','Tennis Court 2')
AND to_char(start_time,'DD/MM/YYYY') = '21/09/2012'


3) 

select m1.*
from members m1 
inner join 
(
	select distinct(recommended_by) 
	from members
) m2 ON m1.mem_id = m2.recommended_by

4) 

Select m1.first_name,m1.surname,m2.first_name,m2.surname 
From members m1
left join members m2 on m1.recommended_by = m2.mem_id

5)

SELECT (m.first_name, m.surname) as "Nom et Prénom du membre", f.name 
from members m
inner join (
	select distinct(mem_id),fac_id
	from bookings
) b ON b.mem_id = m.mem_id
inner join (
	select distinct(fac_id),name
	from facilities
) f on f.fac_id = b.fac_id
where f.name IN ('Tennis Court 1','Tennis Court 2')

6)

SELECT (m.first_name,m.surname) as "Prénom et Nom du membre", f.name, member_cost 
from bookings b
inner join facilities f on b.fac_id = f.fac_id
inner join members m on m.mem_id = b.mem_id
where to_char(b.start_time,'DD/MM/YYYY') = '14/09/2012'
And (member_cost > 30 OR guest_cost > 30)
PAS FINI

