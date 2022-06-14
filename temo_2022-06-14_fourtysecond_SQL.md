# SQL_HackerRank_Interviews

## Problem
Samantha interviews many candidates from different colleges using coding challenges and contests. 
Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are 0 .
Link()

## 오답

 the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views 를 하라는데,
 SELECT (ss.total_submissions + ss.total_accepted_submissions +vs.total_views +vs.total_unique_views) 로 잘못이해함



    select
    ct.contest_id, ct.hacker_id, ct.name,
    SUM(ss.total_submissions), SUM(ss.total_accepted_submissions), SUM(vs.total_views), SUM(vs.total_unique_views)

    from contests ct

    join Colleges cg
    on ct.contest_id = cg.contest_id

    join Challenges ch
    on cg.college_id  = ch.college_id 

    join View_Stats vs
    on vs.challenge_id  = ch.challenge_id 

    join Submission_Stats ss
    on ss.challenge_id  = vs.challenge_id 


    group by ct.contest_id, ct.hacker_id, ct.name
    having SUM(ss.total_submissions) + SUM(ss.total_accepted_submissions) + SUM(vs.total_views) + SUM(vs.total_unique_views) >0
    order by ct.contest_id
![image](https://user-images.githubusercontent.com/99947811/173465738-f5ced871-107b-4324-9588-881872c2e6ff.png)


![image](https://user-images.githubusercontent.com/99947811/173466104-bc69eae1-8a24-44fa-9c5b-2cef90c63262.png)

##Solution

    select ct.contest_id, ct.hacker_id, ct.name, SUM(ss.total_submissions), SUM(ss.total_accepted_submissions), SUM(vs.total_views), SUM(vs.total_unique_views) from contests ct

    join Colleges cg
    on ct.contest_id = cg.contest_id

    join Challenges ch
    on cg.college_id  = ch.college_id 

    join (select challenge_id, SUM(total_submissions), SUM(total_accepted_submissions) from Submission_Stats group by challenge_id) as ss on ss.challenge_id  = ch.challenge_id 

    join (select challenge_id, SUM(total_views), SUM(total_unique_views) from View_Stats group by challenge_id) as vs on vs.challenge_id = ch.challenge_id

    group by ct.contest_id, ct.hacker_id, ct.name
    having SUM(ss.total_submissions) + SUM(ss.total_accepted_submissions) + SUM(vs.total_views) + SUM(vs.total_unique_views) >0 

    order by ct.contest_id
