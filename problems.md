### Problem 1
You are given a string s consisting only of digits 0-9, commas ,, and dots.
Your task is to complete the regex_pattern defined below, which will be used to re.split() all of the , and . symbols in s.
It’s guaranteed that every comma and every dot in s is preceeded and followed by a digit.

    import re
    re.split(r"[,\.]","+91-011,2711.1111")
  
### Problem 2
Given an array of integers, calculate the fractions of its elements that are positive, negative, and are zeros. Print the decimal value of each fraction on a new line.
Note: This challenge introduces precision problems. The test cases are scaled to six decimal places, though answers.

    n = int(input())
    elements = input().split()
    elements = [int(i) for i in elements]
    
    positive = 0
    negative = 0
    zero = 0

    for i in elements:
        if i > 0:
            positive += 1
        elif i < 0:
            negative += 1
        elif i == 0:
            zero += 1

    ratios = [format(positive/n, '.6f'), format(negative/n, '.6f'), format(zero/n, '.6f')]

    print(*ratios, sep= '\n')   
    
### Problem 3
Given five positive integers, find the minimum and maximum values that can be calculated by summing exactly four of the five integers. Then print the respective minimum and maximum values as a single line of two space-separated long integers.

    n = input().split()
    n = [int(i) for i in n]
    n = sorted(n, key=int)

    minSum = sum(n[0:4])
    maxSum = sum(n[-4:])
    print(minSum, maxSum)
    
### Problem 4
You are in charge of the cake for your niece's birthday and have decided the cake will have one candle for each year of her total age. When she blows out the candles, she’ll only be able to blow out the tallest ones. Your task is to find out how many candles she can successfully blow out.

    n = int(input())
    candles = input().split()
    candles = [int(i) for i in candles]
    print(candles.count(max(candles)))
    
### Problem 5
Alice wrote a sequence of words in CamelCase as a string of letters, s, having the following properties:
- It is a concatenation of one or more words consisting of English letters.
- All letters in the first word are lowercase.
- For each of the subsequent words, the first letter is uppercase and rest of the letters are lowercase.

Given , print the number of words in s on a new line.

    import re
    print(len(re.findall('[A-Z][^A-Z]*', input())) + 1)    
    
### Problem 6
HackerLand University has the following grading policy:

Every student receives a  in the inclusive range from 0 to 100.
Any grade less than 40 is a failing grade.
Sam is a professor at the university and likes to round each student's  according to these rules:
- If the difference between the grade and the next multiple of 5 is less than 3, round  up to the grade next multiple of 5.
- If the value of grade is less than 38, no rounding occurs as the result will still be a failing grade.
For example, grade=84 will be rounded to 85 but grade = 29 will not be rounded because the rounding would result in a number that is less than 40.

Given the initial value of grade for each of Sam's n students, write code to automate the rounding process.

    grades = []
    for i in range(int(input())):
        grades.append(input())

    grades = list(map(int, grades))

    new = []
    for grade in grades:
        if grade < 38:
            new.append(grade)
        if grade%5>=3 and grade>=38:
            new.append(int(round(grade/5.0)*5.0))
        if grade%5<3 and grade>38:
            new.append(grade)


    print(*new, sep ='\n')
    
### Problem 7 
Sami's spaceship crashed on Mars! She sends a series of SOS messages to Earth for help.
Letters in some of the SOS messages are altered by cosmic radiation during transmission. Given the signal received by Earth as a string, s, determine how many letters of Sami's SOS have been changed by radiation.

For example, Earth receives SOSTOT. Sami's original message was SOSSOS. Two of the message characters were changed in transit.

Complete the marsExploration function in the editor below. It should return an integer representing the number of letters changed during transmission.

    string = input()
    n = 3
    SOS = [string[i:i+n] for i in range(0, len(string), n)]

    count = 0
    for sos in SOS:
        if sos!='SOS':
            if sos[0]!='S':
                count +=1
            if sos[1]!='O':
                count +=1
            if sos[2]!='S':
                count +=1
    print(count)
    
 ### Problem 8
You are given a string containing characters A and B only. Your task is to change it into a string such that there are no matching adjacent characters. To do this, you are allowed to delete zero or more characters in the string.

Your task is to find the minimum number of required deletions.

For example, given the string s=AABAAB, remove an A at positions 0 and 3 to make s=ABAB in 2 deletions.

    import itertools
    list = []
    for n in range(int(input())):
        word = input()
        list.append(word)

    new = []
    for i in list:
        new.append(''.join(c[0] for c in itertools.groupby(i)))

    for l, n in zip(list, new):
        print(len(l) - len(n)) 
        
 ### Problem 9
 Perform append, pop, popleft and appendleft methods on an empty deque d.
 
    from collections import deque
    d = deque()
    for i in range(int(input())):
        command = input()
        if command == 'pop':
            d.pop()
        if command == 'popleft':
            d.popleft()
        if command[0:7] == 'append ':
            d.append(int(command[7:]))
        if command[0:10] == 'appendleft':
            d.appendleft(int(command[11:]))

    print(*d, sep= ' ')
    
### Problem 10
You are given a two lists A and B. Your task is to compute their cartesian product AxB.

    from itertools import product
    a = list(map(str, input().split()))
    print(a)
    b = list(map(int, input().split()))
    ab = list(product(a, b))
    print(*ab, sep= " ")
    
### Problem 11
You are given a string S. 
Your task is to print all possible permutations of size k of the string in lexicographic sorted order.

    from itertools import permutations
    letters, number = input().split()
    for i in list(permutations(sorted(letters), int(number))):
        print(*i, sep = '')
        
### Problem 12
You are given a string S. 

Your task is to print all possible combinations, up to size k, of the string in lexicographic sorted order.

    from itertools import combinations
    s, k = input().split()

    for j in range(1, int(k) + 1):
        for i in list(combinations(sorted(s), j)):
            print(*i, sep = '')
            
### Problem 13
You are given a string S. 

Your task is to print all possible size K replacement combinations of the string in lexicographic sorted order.

    from itertools import combinations_with_replacement
    s, k = input().split()
    for i in list(combinations_with_replacement(sorted(s), int(k))):
        print(*i, sep='')
        
### Problem 14
You are given a space separated list of nine integers. Your task is to convert this list into a 3 X 3 NumPy array.

    import numpy
    array = numpy.array(list(map(int, input().split())))
    print(numpy.reshape(array,(3, 3)))

### Problem 15
You are given a N X M integer array matrix with space separated elements (N = rows and  M= columns). 

Your task is to print the transpose and flatten results.

    n, m = input().split()
    n = int(n)

    d = []
    for i in range(n):
        d.append(list(map(int, input().split())))

    d = numpy.array(d)
    print(numpy.transpose(d))
    print(d.flatten())

### Problem 16
You are given two integer arrays of size N X P and M X P (N & M are rows, and P is the column). Your task is to concatenate the arrays along axis 0.

    first = list(map(int, input().split()))
    n = first[0]
    m = first[1]
    p = first[2]

    a = []
    for i in range(n):
        a.append(list(map(int, input().split())))

    b = []
    for i in range(m):
        b.append(list(map(int, input().split())))

    a = numpy.array(a)
    b = numpy.array(b)
    print(numpy.concatenate((a,b), axis = 0))
   
### Problem 17
You are given a 2-D array with dimensions N X M. 

Your task is to perform the min function over axis  and then find the max of that.

    import numpy
    n,m = input().split()
    a = []
    for i in range(int(n)):
        a.append(list(map(int, input().split())))
    a= numpy.array(a)

    print(numpy.max(numpy.min(a, axis = 1)))

### Problem 18
You are given two arrays A and B. Both have dimensions of N x N. 
Your task is to compute their matrix product.

    import numpy
    n = int(input())
    a =[]
    for i in range(n):
        a+= map(int, input().split())
    a = numpy.array(a)
    a = numpy.reshape(a, (n,n))

    b =[]
    for i in range(n):
        b+= map(int, input().split())
    b = numpy.array(b)
    b = numpy.reshape(b, (n,n))

    print(numpy.dot(a,b))
    
### Problem 19
You are given two arrays: A and B. Your task is to compute their inner and outer product.

    import numpy
    a = numpy.array(list(map(int, input().split())))
    b = numpy.array(list(map(int, input().split())))

    print(numpy.inner(a,b))
    print(numpy.outer(a, b))

### Problem 20
You are given the coefficients of a polynomial P. Your task is to find the value of P at point x.

    import numpy
    P = list(map(float, input().split()))
    print (numpy.polyval(P, int(input())))
    
### Problem 21
You are given a square matrix A with dimensions N x N. Your task is to find the determinant.

    import numpy
    n = int(input())
    a = []
    for i in range(n):
        a.append(list(map(float, input().split())))

    a = numpy.array(a)

    b =numpy.linalg.det(a)

    print(round(b, 2))
    
### Problem 22
John works at a clothing store. He has a large pile of socks that he must pair by color for sale. Given an array of integers representing the color of each sock, determine how many pairs of socks with matching colors there are.

    from collections import Counter
    import math

    def socks(n, array):
        array = dict(Counter(array))
        pairs = []
        for i, j in array.items():
            pairs.append(math.floor(j/2))
        print(sum(pairs))

    n = int(input())
    array = list(map(str, input().split()))
    socks(n, array)
    
### Problem 23
You have been asked to help study the population of birds migrating across the continent. Each type of bird you are interested in will be identified by an integer value. Each time a particular kind of bird is spotted, its id number will be added to your array of sightings. You would like to be able to find out which type of bird is most common given a list of sightings. Your task is to print the type number of that bird and if two or more types of birds are equally common, choose the type with the smallest ID number.

    import operator
    from collections import Counter

    def MigratoryBirds(n, array):
        array = dict(Counter(array))
        print(max(array, key=array.get))


    n = int(input())
    array = list(map(int, input().split()))
    MigratoryBirds(n, array)
    
### Problem 24
Two cats and a mouse are at various positions on a line. You will be given their starting positions. Your task is to determine which cat will reach the mouse first, assuming the mouse doesn't move and the cats travel at equal speed. If the cats arrive at the same time, the mouse will be allowed to move and it will escape while they fight.

    queries = []
    for i in range(int(input())):
        queries = list(map(int, input().split()))
        a = queries[0]
        b = queries[1]
        c = queries[2]
        if abs(a-c) < abs(b-c):
            print('Cat A')
        if abs(b-c) < abs(a-c):
            print('Cat B')
        if abs(a-c) == abs(b-c):
            print('Mouse C')
 
### Problem 25
Dan is playing a video game in which his character competes in a hurdle race. Hurdles are of varying heights, and Dan has a maximum height he can jump. There is a magic potion he can take that will increase his maximum height by 1 unit for each dose. How many doses of the potion must he take to be able to jump all of the hurdles.

    def HurtleRace(n, k, height):
        Min = []
        for i in height:
            if k<i:
                Min.append(i-k)
        if len(Min)>0:
            print(max(Min))
        else:
            print(0)

    n, k = list(map(int, input().split()))
    height = list(map(int, input().split()))
    HurtleRace(n, k, height)
    
### Problem 26
Complete the designerPdfViewer function in the editor below. It should return an integer representing the size of the highlighted area.

designerPdfViewer has the following parameter(s):
- h: an array of integers representing the heights of each letter
- word: a string

        def DesignerPDF(values, word):
            keys = []
            letters = 'abcdefghijklmnopqrstuvwxyz'
            for i in letters:
                keys.append(i)

            keys = tuple(keys)
            dictt = dict(zip(keys, values))

            maxx = []
            for i in word:
                maxx.append(dictt.get(i))
            print(max(maxx)*len(maxx))

        values = tuple(map(int, input().split()))
        word = input()
        DesignerPDF(values, word)
        
### Problem 27
Monica wants to buy a keyboard and a USB drive from her favorite electronics store. The store has several models of each. Monica wants to spend as much as possible for the 2 items, given her budget.

Given the price lists for the store's keyboards and USB drives, and Monica's budget, find and print the amount of money Monica will spend. If she doesn't have enough money to both a keyboard and a USB drive, print -1 instead. She will buy only the two required items.

    b,n,m = list(map(int, input().split()))
    keyboards = list(map(int, input().split()))
    usb = list(map(int, input().split()))

    def electronicsShop(keyboards, usb, b):
        budget =[]
        for i in keyboards:
            for j in usb:
                if (j+i)<=b:
                    budget.append(j+i)
                else:
                    budget.append(-1)
        if len(budget)>1:
            print(max(budget))
        else:
            print(*budget, sep = '')

    electronicsShop(keyboards, usb, b)
        
### Problem 28
A Discrete Mathematics professor has a class of students. Frustrated with their lack of discipline, he decides to cancel class if fewer than some number of students are present when class starts. Arrival times go from on time () to arrived late ().

Given the arrival time of each student and a threshhold number of attendees, determine if the class is canceled.

    for i in range(int(input())):
        students, cases = list(map(int, input().split()))
        attendance = list(map(int, input().split()))
        cancel = []
        for i in attendance:
            if i<=0:
                cancel.append(i)

        if len(cancel)>= cases:
            print('NO')
        else:
            print('YES')
            
### Problem 29
Karl has an array of integers. He wants to reduce the array until all remaining elements are equal. Determine the minimum number of elements to delete to reach his goal.

    from collections import Counter
    import operator

    n = int(input())
    a = list(map(int, input().split()))
    s = dict(Counter(a))
    greater = max(s, key = s.get)

    new = []
    for i in a:
        if i==greater:
            new.append(i)

    print(len(a)-len(new))
    
### Problem 30
You will be given an array of integers. All of the integers except one occur twice. That one is unique in the array.

Given an array of integers, find and print the unique element.

    from collections import Counter
    n= int(input())
    s = list(map(int, input().split()))
    s = dict(Counter(s))
    print(min(s, key=s.get))
    
### Problem 31
An array is a type of data structure that stores elements of the same type in a contiguous block of memory. In an array, A, of size N, each memory location has some unique index, i (where 0<i<N), that can be referenced as A[i] (you may also see it written as Ai).

Given an array, A, of N integers, print each element in reverse order as a single line of space-separated integers.

    def Array(n, s):
        s = s[::-1]
        print(*[int(i) for i in s], sep= ' ')

    n = int(input())
    s = list(map(str, input().split()))
    Array(n, s)
    
### Problem 32
Lily has a chocolate bar that she wants to share it with Ron for his birthday. Each of the squares has an integer on it. She decides to share a contiguous segment of the bar selected such that the length of the segment matches Ron's birth month and the sum of the integers on the squares is equal to his birth day. You must determine how many ways she can divide the chocolate.

    n = int(input())
    a = list(map(int, input().split()))
    d, m = list(map(int, input().split()))
    count = 0

    for i in range(0, len(a)):
        if sum(a[i:i+m])==d:
            count +=1
        else:
            count
    print(count)
    
