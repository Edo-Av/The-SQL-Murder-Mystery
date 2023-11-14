The SQL Murder Mystery

https://mystery.knightlab.com/

"A crime has taken place and the detective needs your help. The detective gave you the crime scene report, but you somehow lost it.
 You vaguely remember that the crime was a ​murder​ that occurred sometime on ​Jan.15, 2018​ and that it took place in ​SQL City​.
 Start by retrieving the corresponding crime scene report from the police department’s database."

//Start:

SELECT *
FROM crime_scene_report
WHERE city = "SQL City"
	AND type = "murder"
	AND date = 20180115
;

“Security footage shows that there were 2 witnesses. The first witness lives at the last house on "Northwestern Dr".
 The second witness, named Annabel, lives somewhere on "Franklin Ave".”

↓

//Witness 1:

SELECT *
FROM person p
	JOIN interview i ON p.id = i.person_id
WHERE address_street_name = "Northwestern Dr"
ORDER BY address_number DESC
;

"I heard a gunshot and then saw a man run out. He had a "Get Fit Now Gym" bag. The membership number on the bag started with "48Z".
 Only gold members have those bags. The man got into a car with a plate that included "H42W"."

↓

//Witness 2:

SELECT *
FROM person p
	JOIN interview i ON p.id = i.person_id
WHERE address_street_name = "Franklin Ave"
AND name LIKE '%Annabel%'
;

"I saw the murder happen, and I recognized the killer from my gym when I was working out last week on January the 9th."

↓

SELECT *
FROM person p
	JOIN get_fit_now_member gm ON p.id = gm.person_id
	JOIN get_fit_now_check_in gci ON gm.id = gci.membership_id
	JOIN drivers_license d ON p.license_id = d.id
WHERE membership_id LIKE '48Z%'
AND plate_number LIKE '%H42W%'
;

+++SPOILER+++ WARNING 1









+++SPOILER+++ WARNING 2









+++SPOILER+++ WARNING 3










"Jeremy Bowers"

↓

INSERT INTO solution VALUES (1, 'Jeremy Bowers')
;
        SELECT value FROM solution
;

“Congrats, you found the murderer! But wait, there's more... If you think you're up for a challenge, try querying the
 interview transcript of the murderer to find the real villain behind this crime. If you feel especially confident in
 your SQL skills, try to complete this final step with no more than 2 queries. Use this same INSERT statement with
 your new suspect to check your answer.”

↓

SELECT *
FROM interview
WHERE person_id = 67318
;

"I was hired by a woman with a lot of money. I don't know her name but I know she's around 5'5" (65") or 5'7" (67").
 She has red hair and she drives a Tesla Model S. I know that she attended the SQL Symphony Concert 3 times in December 2017."

↓

SELECT p.id
, p.name
, p.address_street_name
, d.*
, f.event_name
, f.date
FROM person p
	JOIN drivers_license d ON p.license_id = d.id
	JOIN facebook_event_checkin f ON p.id = f.person_id
WHERE (height >= 65 AND height <= 67)
AND d.gender = "female"
AND d.hair_color = "red"
AND d.car_make = "Tesla"
AND f.event_name = "SQL Symphony Concert"
;

+++SPOILER+++ WARNING 1









+++SPOILER+++ WARNING 2









+++SPOILER+++ WARNING 3










"Miranda Priestly"

↓

INSERT INTO solution VALUES (1, 'Miranda Priestly');
        SELECT value FROM solution;

"Congrats, you found the brains behind the murder! Everyone in SQL City hails you as the greatest SQL detective of all time. Time to break out the champagne!"




