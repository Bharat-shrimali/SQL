# SQL
#1 Which country has the most people? 
%%sql
SELECT * FROM facts
WHERE population == (SELECT MAX(population) 
                    FROM facts 
                    WHERE name != "World");
OUTPUT           
* sqlite:///factbook.db
Done.
id	code	name	area	area_land	area_water	population	population_growth	birth_rate	death_rate	migration_rate
37	ch	China	9596960	9326410	270550	1367485388	0.45	12.49	7.53	0.44
______________________________________________________________________________________________________________________

#2 Which country has the highest growth rate?
%%sql
SELECT * FROM facts
WHERE population_growth == (SELECT MAX(population_growth) 
                    FROM facts 
                    WHERE name != "World");
OUTPUT
* sqlite:///factbook.db
Done.
id	code	name	area	area_land	area_water	population	population_growth	birth_rate	death_rate	migration_rate
162	od	South Sudan	644329	None	None	12042910	4.02	36.91	8.18	11.47
________________________________________________________________________________________________________________________

#3 Which countries have the highest ratios of water to land?
%%sql
SELECT * FROM facts
WHERE name != "World"
ORDER BY (area_water/area_land) DESC;
OUTPUT : too long
_________________________________________________________________________________________________________________________

#4 Which countries have more water than land?
%%sql
SELECT * FROM facts
WHERE area_water > area_land;

OUTPUT
 * sqlite:///factbook.db
Done.
id	code	name	area	area_land	area_water	population	population_growth	birth_rate	death_rate	migration_rate
228	io	British Indian Ocean Territory	54400	60	54340	None	None	None	None	None
247	vq	Virgin Islands	1910	346	1564	103574	0.59	10.31	8.54	7.67
___________________________________________________________________________________________________________________________

#5 Which countries will add the most people to their populations next year?
%%sql
SELECT * FROM facts
WHERE ((population*population_growth/100) - (population*migration_rate/100)) == (SELECT MAX((population*population_growth/100) - (population*migration_rate/100)) 
                    FROM facts 
                    WHERE name != "World");
                    
                    
 OUTPUT
 * sqlite:///factbook.db
Done.
id	code	name	area	area_land	area_water	population	population_growth	birth_rate	death_rate	migration_rate
77	in	India	3287263	2973193	314070	1251695584	1.22	19.55	7.32	0.04
_____________________________________________________________________________________________________________________________

#6 Which countries have a higher death rate than the birth rate?
%%sql
SELECT * FROM facts
WHERE death_rate > birth_rate;
________________________________________________________________________________________________________________________________

#7 Which countries have the highest population/area ratio
%%sql
SELECT * FROM facts
WHERE name != "World"
ORDER BY (population/area) DESC;
