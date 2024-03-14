<p align="left">SQL Murder Mystery Solution</p>

###

<div align="center">
  <img height="200" src="https://mystery.knightlab.com/174092-clue-illustration.png"  />
</div>

###

<p align="left">Here are my notes and code while working through the sql murder mystery:</p>

###

<p align="left">-- Find out who the 2 witnesses are: <br>SELECT *<br>FROM crime_scene_report<br>WHERE type = 'murder'<br>AND city = 'SQL City'<br>AND date = 20180115;<br><br>-- Write a query that identifies the first witness:<br>Select * from person where address_street_name = 'Northwestern Dr' <br>ORDER BY address_number DESC<br>LIMIT 1;<br><br>--Write a query that identifies the second witness:<br>Select * from person where name like 'Annabel%' and<br>address_street_name = 'Franklin Ave'<br><br>--Write a query that shows the interview transcripts for our two subjects:<br>select name, transcript<br>from interview i<br>join person p<br>on i.person_id = p.id<br>where name = 'Morty Schapiro' or name = 'Annabel Miller';<br><br>-- membership starts with "48Z" / gold member / License plate H42W <br>-- was at the gym jan 9th <br>-- Find the murderer: <br>select * <br>from get_fit_now_check_in gc<br>join get_fit_now_member gm<br>on gc.membership_id = gm.id<br>join person p<br>on gm.person_id = p.id<br>join drivers_license dl<br>on p.license_id = dl.id<br>where gm.id like '%48z%' and <br>check_in_date = '20180109' and plate_number like '%H42W%'<br><br>--Read transcript find real murderer: <br>select name, transcript<br>from interview i<br>join person p<br>on i.person_id = p.id<br>where name = 'Jeremy Bowers'<br><br>-- woman / height = 67 or 65 / red hair / drives tesla <br>-- went to sql symphony concert 3 times in december 2017 <br>select *<br>from facebook_event_checkin fb<br>join person p<br>on fb.person_id = p.id<br>join drivers_license dl<br>on p.license_id = dl.id<br>where dl.hair_color = 'red' and <br>dl.car_make = 'Tesla' and dl.gender = 'female'</p>

###
