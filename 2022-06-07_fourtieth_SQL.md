# SQL_HackerRank_Placement

## Problem
![image](https://user-images.githubusercontent.com/99947811/172304742-aa74589f-99bc-4941-9604-b27ad8936c7d.png)
Link(https://www.hackerrank.com/challenges/placements/problem?isFullScreen=true)


## Solution
* Inner Join을 사용하여 --> friend's id 별 salary를 대응시킨 테이블(friends_tbl)을 생성했다
* (이 문제에서는 Null 값이 없기에, 사실 left join, inner join 뭘 활용하든 결과값이 같다. 그냥 join을 써도 된다)


      select s.name
      from friends f

      join students s
      on s.id = f.id

      join packages p
      on p.id = f.id

      inner join packages as friends_tbl
      on friends_tbl.id = f.friend_id

      where friends_tbl.salary > p.salary
      order by friends_tbl.salary


![image](https://user-images.githubusercontent.com/99947811/172304848-d547c42c-b4b4-4dd5-b22e-20c55efe5e9d.png)


### 다른 풀이

      select s.name
      from friends f

      join students s
      on s.id = f.id

      join packages p
      on p.id = f.id

      join packages as friends_tbl
      on (friends_tbl.id = f.friend_id 
      and friends_tbl.salary > p.salary)
      
      order by friends_tbl.salary
