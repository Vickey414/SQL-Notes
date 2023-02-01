## 511. Game Play Analysis II

*Write an SQL query to report the device that is first logged in for each player. Return the result table in any order.*
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/214848609-1a4cbdb6-8025-447d-b273-8f198c507754.png">
#### Solution
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


## 512. Game Play Analysis III
*Write an SQL query to report for each player and date, how many games played so far by the player. That is, the total number of games played by the player until that date. Check the example for clarity.*
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/214850129-3b2eb935-f6f1-4b18-b4d7-f3944cb174a9.png">
#### Solution
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
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/214850041-c0a6d5e7-c3ea-475c-92bb-fdf5196bfc2e.png">

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

## 550. Game Play Analysis V
*The install date of a player is the first login day of that player.We define day one retention of some date x to be the number of players whose install date is x and they logged back in on the day right after x, divided by the number of players whose install date is x, rounded to 2 decimal places.
Write an SQL query to report for each install date, the number of players that installed the game on that day, and the day one retention. Return the result table in any order.*
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/214849970-b6bb07db-b082-4b52-aa8a-c0be0aca7fc0.png">
#### Solution
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

## 571. Find Median Given Frequency of Numbers
*The median is the value separating the higher half from the lower half of a data sample.Write an SQL query to report the median of all the numbers in the database after decompressing the Numbers table. Round the median to one decimal point.*
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/214853100-b8141f35-2942-4d95-a612-6c642f1b15ce.png">
#### Solution
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

## 1158. Market Analysis I
*Write an SQL query that reports the best seller by total sales price, If there is a tie, report them all.Return the result table in any order.*
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/214867270-e6b368ba-2ae4-4568-a290-dcc90ae175f8.png">

#### Solution
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

## 1159. Market Analysis II
*Write an SQL query to find for each user whether the brand of the second item (by date) they sold is their favorite brand. If a user sold less than two items, report the answer for that user as no. It is guaranteed that no seller sold more than one item on a day.*
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215742952-2c8841ca-c14f-47a4-bc9f-0c7f3a6aebf3.png">
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215743101-dc637834-2441-4046-8bfa-15e414510631.png">

```sql
    select user_id as seller_id, 
    (case when 
        # 这个favorite_brand是users表中的favorite_brand,判断的条件就是favorite_brand与select出来的item_brand是否相等
        u.favorite_brand = (
            select i.item_brand
            from Orders o
            left join Items i
            on o.item_id = i.item_id # 到这一步之前，先是把orders这个表新增加一列item_brand
            where o.seller_id = u.user_id 
            # 然后结合外层，加了item_brand之后的orders表和u的表进行join，其中用o.seller_id和u.user_id匹配，
            # 这道题的初衷是看商户sell的第二个商品是否是他们最喜欢的brand
            # 所以orders表中的seller_id和users表中的user_id是同一个，均表示商户的id。
            # 然后这里会得到这样的表，users表中有1，orders中没有1，还是会显示1，只不过item_brand为空
            # users表中有1个2，orders中有两个2，则生成的表会有两行对应2，对应的item_brand就是商户sell的两个item，同理3和4也是
            order by order_date 
            # 这里会根据user_id进行group之后再order
            limit 1 offset 1) then "yes" else "no" end) as 2nd_item_fav_brand
            # offset跳过第一个，limit限制取1个，也就是取了第二个
from 
Users u
```

## 1082. Sales Analysis I
* 在这里考察的是先创建临时表，用with，然后进行select，注意最后一句where不能直接用total_sales = max(total_sales)因为会有group报错.
*Write an SQL query that reports the best seller by total sales price, If there is a tie, report them all*.  
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215746512-b3324e13-4972-48ec-b625-fd2c3ae94fa4.png">

```sql
with tmp as
        (
            select seller_id, sum(price) as total_sales
            from 
            Sales
            group by seller_id
        )
select
    seller_id
from tmp
where total_sales = (select max(total_sales) from tmp)
```

## 1083. Sales Analysis II
* Write an SQL query that reports the buyers who have bought S8 but not iPhone. Note that S8 and iPhone are products present in the Product table.*.  
<img width="645" alt="image" src="https://user-images.githubusercontent.com/29950267/214878268-85ddbc4e-67a9-4cad-8962-935fda8fa749.png">

#### Solution
```sql
with table1 as
(select buyer_id, product_name
from Sales s
left join Product p
on s.product_id = p.product_id)
select distinct buyer_id 
from table1
    where buyer_id in (select buyer_id from table1 where product_name = "S8")
    and buyer_id not in (select buyer_id from table1 where product_name ="iPhone")
```
## 1084. Sales Analysis III
Write an SQL query that reports the products that were only sold in the first quarter of 2019. That is, between 2019-01-01 and 2019-03-31 inclusive.
* We only find out product sold only in the first quarter
<img width="676" alt="image" src="https://user-images.githubusercontent.com/29950267/216078796-75b1a787-bbb0-4621-aadf-1b9547da9c6c.png">
```sql
select product_id,product_name
from 
Product
where product_id in
    (
        select product_id
        from Sales s
        group by product_id
        having 
          sum(sale_date < date('2019-01-01 ')) = 0
          and sum(sale_date > date('2019-03-31')) = 0
    )
```


## 京东SQL面试题
#### 1. 考察日期函数
![image](https://user-images.githubusercontent.com/29950267/215034371-f29632b6-65ac-4e82-b88e-9ba679c10354.png)


```sql
select earlydate, count(user_id) as new_customer_num
(select user_id,min(orderdate) as earlyday
from order
group by user_id)tmp
where datediff(curdate(),earlyday))<30
group by earlyday
```


#### 2. 考察case when函数
![image](https://user-images.githubusercontent.com/29950267/215260284-2e495f07-eb58-482d-9f43-b343bd9d9379.png)

```sql
select 
    gender,
    sum(case when age < 20 then 1 else 0 end) "under 20",
    sum(case when age > 40 then 1 else 0 end) "above 40"
    sum(case when age >20 and age < 40 then 1 else 0 end) "between 20 and 40"
from user  
group by gender
```

#### 3. 考察窗口函数
![image](https://user-images.githubusercontent.com/29950267/215260758-ac9a2ec1-c4d0-4e76-961a-5fa31eeef4c9.png)
```sql
select category, product, total_sale
from
    (
    select 
        *, rank() over (partition by category order by total_sale desc) as rank
    from(
            select 
                category, product, sum(sale_num) as total_sale
            from ord
            group by category, product
        ) tmp1
    )tmp2
where rank = 1
```

#### 4. 考察窗口函数和日期函数
![image](https://user-images.githubusercontent.com/29950267/215327932-1170dbed-2fea-4588-989a-2edf3f57e27a.png)

```sql
select user_id, sub_date, count(*) as log_time
    (select
        user_id, DATA_SUB(log_date, INTERVAL rank DAY) as sub_date
    from 
        (
        select
            user_id, log_date, ROW_NUMBER()over(partition by user_id) as rank
        from 
            (
            select user_id, DATE_FORMAT(request_tm, "%Y-%m-%D") as log_date
            from userlog
            ) tmp1
        ) tmp2
    ) tmp3
group by user_id, sub_date
having log_times = 2

    ```
    
