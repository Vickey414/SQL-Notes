# 511. Game Play Analysis I

*Write an SQL query to report the device that is first logged in for each player. Return the result table in any order.*
Input: 
Activity table:
+-----------+-----------+------------+--------------+
| player_id | device_id | event_date | games_played |
+-----------+-----------+------------+--------------+
| 1         | 2         | 2016-03-01 | 5            |
| 1         | 2         | 2016-05-02 | 6            |
| 2         | 3         | 2017-06-25 | 1            |
| 3         | 1         | 2016-03-02 | 0            |
| 3         | 4         | 2018-07-03 | 5            |
+-----------+-----------+------------+--------------+
Output: 
+-----------+-------------+
| player_id | first_login |
+-----------+-------------+
| 1         | 2016-03-01  |
| 2         | 2017-06-25  |
| 3         | 2016-03-02  |
+-----------+-------------+

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


# 512. Game Play Analysis II
*Write an SQL query to report for each player and date, how many games played so far by the player. That is, the total number of games played by the player until that date. Check the example for clarity.*

## Solution
```
select a.player_id, a.event_date,sum(b.games_played) as games_played_so_far from Activity as a
left join Activity b
on a.player_id = b.player_id
and a.event_date >= b.event_date
group by a.player_id, a.event_date!
```



