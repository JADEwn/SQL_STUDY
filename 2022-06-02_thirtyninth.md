# SQL_HackerRank_Contest Leaderboard

## Problem
You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!
The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of 0 from your result.

![image](https://user-images.githubusercontent.com/99947811/171572587-d681ef11-842f-49ab-8847-b2d4b9e8fbec.png)
Link(https://www.hackerrank.com/challenges/contest-leaderboard/problem?isFullScreen=true)

<aside>
- 아이디, 이름, 토탈점수를 내림차순으로 반환해라
- group by를 활용해서 임시 테이블 만들기
  --> 해커id 별 > 챌린지 별 > 최고 점수
  --> select hacker_id, max(score) from submissions
  ````group by hacker_id, challenge)id
- 토탈점수가 같은 사람이 있으면, 아이디를 오름차순 정렬
- 토탈점수 0 인 사람들은 제외시키기
</aside>

## Solution
    SELECT h.hacker_id, h.name, SUM(max_each_challenge) AS total_score 
    FROM (SELECT hacker_id, MAX(score) as max_each_challenge FROM Submissions
    GROUP BY hacker_id, challenge_id
    HAVING NOT max(score) = 0 ) AS temp
    JOIN Hackers h
    ON h.hacker_id = temp.hacker_id
    Group by h.hacker_id, h.name
    Order by total_score DESC, h.hacker_id ASC
![image](https://user-images.githubusercontent.com/99947811/171586802-48e2833f-a661-4396-82a8-0ac01d3ddacb.png)
