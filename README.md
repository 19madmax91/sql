# sql
sql solutions

select city from station where city REGEXP "^[aeiou].*"



select name from employee where salary > 2000 AND months < 10 order by employee_id ASC

select city.name from city inner join country
on countrycode = code
where continent = 'Africa'

select country.continent, round(avg(city.population)-0.5) from city
inner join country
on city.countrycode = code
group by country.continent

select sum(city.population) from city inner join country
on countrycode = code 
where continent = 'Asia' 

SELECT NAME FROM STUDENTS WHERE MARKS > 75 ORDER BY RIGHT(NAME, 3), ID ASC;

select round(sum(lat_n),2), round(sum(long_w,2) from station

select truncate(sum(lat_n),4) from station where lat_n > 38.7880 AND lat_n < 137.2345

select truncate(max(lat_n),4) from station where lat_n < 137.2345

select round(long_w,4) from station where lat_n = (select max(lat_n)from station where lat_n < 137.2345)

select round(min(lat_n),4) from station where lat_n > 38.7780

select round(long_w,4) from station where lat_n = (select min(lat_n) from station where lat_n > 38.7780)

select c.company_code, f.founder, count(l.lead_manager_code), count(s.senior_manager_code), count(m.manager_code), count (e.employee_code)
from founder f, lead_manager l, senior_manager s, manager m, employee e
where  c.company_code = l.company_code
and l.lead_manager_code = s.lead_manager_code
and s.senior_manager_code = m.senior_manager_code
and m.manager_code = e.manager_code
group by c.company_code order by c.company_code
