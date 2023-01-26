# 511. Game Play Analysis II

*Write an SQL query to report the device that is first logged in for each player. Return the result table in any order.*
<img width="562" alt="image" src="https://user-images.githubusercontent.com/29950267/214850283-9635476f-5fb7-4edc-b7b5-0d1fc428f431.png">

<img width="509" alt="image" src="https://user-images.githubusercontent.com/29950267/214848609-1a4cbdb6-8025-447d-b273-8f198c507754.png">
## Solution
```
select a.player_id, b.device_id 
from 
(select player_id, min(event_date) as first_login from Activity
group by player_id) as a 
left join Activity b
on a.player_id = b.player_id
and a.event_date >= b.event_date
```


# 512. Game Play Analysis III
*Write an SQL query to report for each player and date, how many games played so far by the player. That is, the total number of games played by the player until that date. Check the example for clarity.*
<img width="666" alt="image" src="https://user-images.githubusercontent.com/29950267/214850129-3b2eb935-f6f1-4b18-b4d7-f3944cb174a9.png">
## Solution
```
select a.player_id, a.event_date,sum(b.games_played) as games_played_so_far from Activity as a
left join Activity b
on a.player_id = b.player_id
and a.event_date >= b.event_date
group by a.player_id, a.event_date!
```

# 534. Game Play Analysis IV
*Write an SQL query to report the fraction of players that logged in again on the day after the day they first logged in, rounded to 2 decimal places. In other words, you need to count the number of players that logged in for at least two consecutive days starting from their first login date, then divide that number by the total number of players.*
<img width="659" alt="image" src="https://user-images.githubusercontent.com/29950267/214850041-c0a6d5e7-c3ea-475c-92bb-fdf5196bfc2e.png">

## Solution
```
select round(sum(case when b.event_date is null then 0 else 1 end)/count(distinct(a.player_id)),2) as fraction
from 
(select player_id, min(event_date) as first_login 
from  Activity 
group by player_id) as a
left join Activity b
on a.player_id = b.player_id
and datediff(b.event_date,a.first_login) 
```

# 550. Game Play Analysis V
*The install date of a player is the first login day of that player.We define day one retention of some date x to be the number of players whose install date is x and they logged back in on the day right after x, divided by the number of players whose install date is x, rounded to 2 decimal places.
Write an SQL query to report for each install date, the number of players that installed the game on that day, and the day one retention. Return the result table in any order.*
<img width="654" alt="image" src="https://user-images.githubusercontent.com/29950267/214849970-b6bb07db-b082-4b52-aa8a-c0be0aca7fc0.png">
## Solution



