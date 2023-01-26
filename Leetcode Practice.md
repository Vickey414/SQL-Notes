# 511. Game Play Analysis II

*Write an SQL query to report the device that is first logged in for each player. Return the result table in any order.*
<img width="509" alt="image" src="https://user-images.githubusercontent.com/29950267/214848609-1a4cbdb6-8025-447d-b273-8f198c507754.png">
## Solution
```sql
select a.player_id, b.device_id 
from 
(select 
    player_id, min(event_date) as first_login 
from Activity
group by player_id) as a 
left join 
    Activity b
    on a.player_id = b.player_id
    and a.event_date >= b.event_date
```


# 512. Game Play Analysis III
*Write an SQL query to report for each player and date, how many games played so far by the player. That is, the total number of games played by the player until that date. Check the example for clarity.*
<img width="666" alt="image" src="https://user-images.githubusercontent.com/29950267/214850129-3b2eb935-f6f1-4b18-b4d7-f3944cb174a9.png">
## Solution
```sql
select 
    a.player_id, 
    a.event_date,
    sum(b.games_played) as games_played_so_far 
from Activity as a
left join 
    Activity b
    on a.player_id = b.player_id
    and a.event_date >= b.event_date
group by 
    a.player_id, a.event_date!
```

# 534. Game Play Analysis IV
*Write an SQL query to report the fraction of players that logged in again on the day after the day they first logged in, rounded to 2 decimal places. In other words, you need to count the number of players that logged in for at least two consecutive days starting from their first login date, then divide that number by the total number of players.*
<img width="659" alt="image" src="https://user-images.githubusercontent.com/29950267/214850041-c0a6d5e7-c3ea-475c-92bb-fdf5196bfc2e.png">

## Solution
```sql
select round(sum(case when b.event_date is null then 0 else 1 end)/count(distinct(a.player_id)),2) as fraction
from 
(select 
    player_id, 
    min(event_date) as first_login 
from  Activity 
group by 
    player_id) as a
left join 
    Activity b
on a.player_id = b.player_id
and datediff(b.event_date,a.first_login) 
```

# 550. Game Play Analysis V
*The install date of a player is the first login day of that player.We define day one retention of some date x to be the number of players whose install date is x and they logged back in on the day right after x, divided by the number of players whose install date is x, rounded to 2 decimal places.
Write an SQL query to report for each install date, the number of players that installed the game on that day, and the day one retention. Return the result table in any order.*
<img width="654" alt="image" src="https://user-images.githubusercontent.com/29950267/214849970-b6bb07db-b082-4b52-aa8a-c0be0aca7fc0.png">
## Solution
```sql
select 
    n.install_dt, 
    count(n.install_dt) as installs,
    round(count(n.id_2)/count(n.install_dt),2) as Day1_retention
from
    (select 
        a.first_login as install_dt, 
        a.player_id as id_0, 
        b.player_id as id_2 
     from 
    (select 
        player_id, 
        min(event_date) as first_login 
    from Activity
    group by player_id) as a
    left join Activity as b
        on a.player_id = b.player_id
        and datediff(b.event_date,a.first_login) = 1) as n
    group by n.install_dt
```

# 571. Find Median Given Frequency of Numbers
*The median is the value separating the higher half from the lower half of a data sample.Write an SQL query to report the median of all the numbers in the database after decompressing the Numbers table. Round the median to one decimal point.*
<img width="651" alt="image" src="https://user-images.githubusercontent.com/29950267/214853100-b8141f35-2942-4d95-a612-6c642f1b15ce.png">
## Solution
```sql
select 
    round(sum(num)/2,1) as median 
from 
    (select 
        *,
        sum(frequency) over(order by num) as accumulated_sum,
        sum(frequency) over()/2 as median_num
     from Numbers) as m
     where accumulated_sum >= median_num 
     and accumulated_sum - frequency <= median_num
```

# 1082. Sales Analysis I
*Write an SQL query that reports the best seller by total sales price, If there is a tie, report them all.Return the result table in any order.*
<img width="649" alt="image" src="https://user-images.githubusercontent.com/29950267/214867270-e6b368ba-2ae4-4568-a290-dcc90ae175f8.png">

```sql
select 
    u.user_id as buyer_id,
    u.join_date as join_date,
    count(o.order_id) as orders_in_2019
from Users u
left join 
Orders o
on u.user_id = o.buyer_id
and year(o.order_date) = "2019"
group by u.user_id
```
