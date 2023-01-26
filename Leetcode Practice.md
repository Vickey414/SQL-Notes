#511. Game Play Analysis I
##Solution
```
select a.player_id, b.device_id 
from 
(select player_id, min(event_date) as first_login from Activity
group by player_id) as a 
left join Activity b
on a.player_id = b.player_id
and a.event_date >= b.event_date
```


#
##Solution
