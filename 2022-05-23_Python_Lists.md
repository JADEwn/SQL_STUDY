#HackerRank_Python_Lists

## Problem
![image](https://user-images.githubusercontent.com/99947811/169935418-1051ad32-ee5c-4007-9414-d8a512e53ad1.png)
Link(https://www.hackerrank.com/challenges/python-lists/problem?isFullScreen=true)



## Solution

##### cmd = input().split() --> 값을 입력받아 만들어진 '문자열 리스트'
##### e.g. 입력값이 append 3 인 경우 --> cmd[0] = 'append', cmd[1] = '3'

    ip = int(input())  #input
    op = []            #output
    for i in range(ip):
        cmd = input().split()  #command
        if cmd[0] == 'append':
            op.append(int(cmd[1]))
        elif cmd[0] == 'insert':
            op.insert(int(cmd[1]), int(cmd[2]))
        elif cmd[0] == 'remove':
            op.remove(int(cmd[1]))
        elif cmd[0] == 'print':
            print(op)
        elif cmd[0] == 'sort':
            op.sort()
        elif cmd[0] == 'pop':
            op.pop()
        elif cmd[0] == 'reverse':
            op.reverse()
            
            


# 오답    
    if __name__ == '__main__':
        N = int(input())
        array = [] 
        for j in range(N):
            cmd = input().split()
            cmd = list(map(int,cmd)) #'insert'..command까지도 int가 되어버림....
            if cmd[0] == 'insert':
                array.append(cmd[1],cmd[2])
            elif cmd[0] == 'remove':
                array.remove(cmd[1])
            elif cmd[0] == 'append':
                array.append(cmd[1])
            elif cmd[0] == 'sort':
                array.sort()
            elif cmd[0] == 'pop':
                array.pop()
            elif cmd[0] == 'reverse':
                array.reverse()
            elif cmd[0] == 'print':
                print(array)
