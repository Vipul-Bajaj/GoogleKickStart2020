<h1>High Buildings</h1>

<p>
<h2>Problem</h2>
In an unspecified country, Google has an office campus consisting of N office buildings in a line, numbered from 1 to N from left to right. When represented in meters, the height of each building is an integer between 1 to N, inclusive.

Andre and Sule are two Google employees working in this campus. On their lunch break, they wanted to see the skyline of the campus they are working in. Therefore, Andre went to the leftmost point of the campus (to the left of building 1), looking towards the rightmost point of the campus (to the right of building N). Similarly, Sule went to the rightmost point of the campus, looking towards the leftmost point of the campus.

To Andre, a building x is visible if and only if there is no building to the left of building x that is strictly higher than building x. Similarly, to Sule, a building x is visible if and only if there is no building to the right of building x that is strictly higher than building x.

Andre learned that there are A buildings that are visible to him, while Sule learned that there are B buildings that are visible to him. After they regrouped and exchanged information, they also learned that there are C buildings that are visible to both of them.

They are wondering about the height of each building. They are giving you the value of N, A, B, and C for your information. As their friend, you would like to construct a possible height for each building such that the information learned on the previous paragraph is correct, or indicate that there is no possible height construction that matches the information learned (thus at least one of them must have been mistaken).

<b>Input</b><br>
The first line of the input gives the number of test cases, T. T test cases follow. Each consists of a single line with four integers N, A, B, and C: the information given by Andre and Sule.

<b>Output</b><br>
For each test case, output one line containing Case #x: y, where x is the test case number (starting from 1) and y is IMPOSSIBLE if there is no possible height for each building according to the above information, or N space-separated integers otherwise. The i-th integer in y must be the height of the i-th building (in meters) between 1 to N.

<b>Limits</b><br>
Time limit: 20 seconds per test set.<br>
Memory limit: 1GB.<br>
1 ≤ T ≤ 100.<br>
1 ≤ C ≤ N.<br>
C ≤ A ≤ N.<br>
C ≤ B ≤ N.<br>

<b>Test set 1 (Visible Verdict)</b><br>
1 ≤ N ≤ 5.

<b>Test set 2 (Visible Verdict)</b><br>
1 ≤ N ≤ 100.

<b>Sample</b>

    Input
        3
        4 1 3 1
        4 4 4 3
        5 3 3 2

    Output
        Case #1: 4 1 3 2
        Case #2: IMPOSSIBLE
        Case #3: 2 1 5 5 3
        
In Sample Case #1, the sample output sets the height of each building such that only the first building is visible to Andre, while the first, third, and fourth buildings are visible to Sule. Therefore, only the first building is visible to both Andre and Sule. Note that there exist other correct solutions, such as 4 3 1 2.

In Sample Case #2, all N = 4 buildings are visible to Andre and Sule. Therefore, it is impossible to have C ≠ N in this case.

In Sample Case #3, the sample output sets the height of each building such that the first, third, and fourth buildings are visible to Andre, while the third, fourth, and fifth buildings are visible to Sule. Therefore, the third and fourth buildings are visible to both Andre and Sule. Note that there exist other correct solutions.
</p>

<h2>Solution</h2>

***

```python
t =  int(input())
test=1
while t>0:
    n,a,b,c  = list(map(int,input().split()))
    
    if (a==b==n and c!=n) or (c>a or c>b ):
        print("Case #{0}: {1}".format(test,"IMPOSSIBLE"))
    else:
        buildings = ["1"]*n

        highest_building = n

        n_a = a-c
        
        i = 0
        while i<n_a:
            buildings[i] = str(i+1)
            i+=1
        
        for j in range(0,c):
            buildings[i] = str(highest_building)
            i+=1
        
        n_b = b-c
        i = n-1
        h = 2
        for j in range(0,n_b):
            buildings[i] = str(h)
            h+=1
            i-=1
        
        print("Case #{0}: {1}".format(test,buildings))
    test+=1
    t-=1
```
