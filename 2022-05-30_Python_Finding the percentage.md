# HackerRank_Python_Finding the percentage

## Problem
![image](https://user-images.githubusercontent.com/99947811/170924597-d2108d0b-f796-443b-a4e7-7541f7932106.png)
Link(https://www.hackerrank.com/challenges/finding-the-percentage/problem?isFullScreen=true)

## Solution
*     
    if __name__ == '__main__':
        n = int(input())
        student_marks = {}
        for _ in range(n):
            name, *line = input().split()
            scores = list(map(float, line))
            student_marks[name] = scores
        query_name = input()

        outputScore = student_marks[query_name]
        print("{:.2f}".format(sum(outputScore)/ len(outputScore)))
        
![image](https://user-images.githubusercontent.com/99947811/170924551-00dfeb94-c8cb-4df1-816e-1102ca0c3c58.png)
