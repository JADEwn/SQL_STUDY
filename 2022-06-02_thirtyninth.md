# SQL_HackerRank_Contest Leaderboard

## Problem
![image](https://user-images.githubusercontent.com/99947811/171572587-d681ef11-842f-49ab-8847-b2d4b9e8fbec.png)
Link(https://www.hackerrank.com/challenges/contest-leaderboard/problem?isFullScreen=true)


## Solution
  <aside>
  * GROUP BY 를 활용해서 임시 테이블 만들기
    --> 해커id 별 > 챌린지 별 > 최고 점수
    --> select hacker_id, max(score) from submissions
        group by hacker_id, challenge)id
  * 토탈점수(즉, SUM(각 챌린지별 최고점수) = 0 인 사람들은 제외시키기
  </aside>


    SELECT h.hacker_id, h.name, SUM(max_each_challenge) AS total_score 
    FROM (SELECT hacker_id, MAX(score) as max_each_challenge FROM Submissions
    GROUP BY hacker_id, challenge_id
    HAVING NOT max(score) = 0 ) AS temp
    JOIN Hackers h
    ON h.hacker_id = temp.hacker_id
    Group by h.hacker_id, h.name
    Order by total_score DESC, h.hacker_id ASC
![image](https://user-images.githubusercontent.com/99947811/171586802-48e2833f-a661-4396-82a8-0ac01d3ddacb.png)
