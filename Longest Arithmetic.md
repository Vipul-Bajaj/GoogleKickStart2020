<h1>Longest Airthmetic</h1>

<p>
<h2>Problem</h2>
An arithmetic array is an array that contains at least two integers and the differences between consecutive integers are equal. For example, [9, 10], [3, 3, 3], and [9, 7, 5, 3] are arithmetic arrays, while [1, 3, 3, 7], [2, 1, 2], and [1, 2, 4] are not arithmetic arrays.

Sarasvati has an array of N non-negative integers. The i-th integer of the array is Ai. She wants to choose a contiguous arithmetic subarray from her array that has the maximum length. Please help her to determine the length of the longest contiguous arithmetic subarray.

<b>Input</b><br>
The first line of the input gives the number of test cases, T. T test cases follow. Each test case begins with a line containing the integer N. The second line contains N integers. The i-th integer is Ai.

<b>Output</b><br>
For each test case, output one line containing Case #x: y, where x is the test case number (starting from 1) and y is the length of the longest contiguous arithmetic subarray.

<b>Limits</b><br>
Time limit: 20 seconds per test set.<br>
Memory limit: 1GB.<br>
1 ≤ T ≤ 100.<br>
0 ≤ Ai ≤ 10^9.<br>
1 ≤ length of S ≤ 100.<br>

<b>Test set 1 (Visible Verdict)</b><br>
2 ≤ N ≤ 2000.

<b>Test set 2 (Visible Verdict)</b><br>
2 ≤ N ≤ 2 × 105 for at most 10 test cases.
For the remaining cases, 2 ≤ N ≤ 2000.

<b>Sample</b>

    Input
        4
        7
        10 7 4 6 8 10 11
        4
        9 7 5 3
        9
        5 5 4 5 5 5 4 5 6
        10
        5 4 3 2 1 2 3 4 5 6

    Output
        Case #1: 4
        Case #2: 4
        Case #3: 3
        Case #4: 6
        
In Sample Case #1, the integers inside the bracket in the following represent the longest contiguous arithmetic subarray: 10 7 [4 6 8 10] 11

In Sample Case #2, the whole array is an arithmetic array, thus the longest contiguous arithmetic subarray is the whole array.

In Sample Case #3, the longest contiguous arithmetic subarray is either [5, 5, 5] (a subarray from the fourth integer to the sixth integer) or [4, 5, 6] (a subarray from the seventh integer to the ninth integer).

In Sample Case #4, the longest contiguous arithmetic subarray is the last six integers.
</p>

<h2>Solution</h2>

***

```python
t = int(input())
test = 1
while t>0:
    n  = int(input())
    A = list(map(int,input().split()))
    max_till = 0
    i = 0
    j = 1
    c = 1
    d = A[j]-A[i]
    
    while i<n-1 and j<n:
        if A[j]-A[i] == d:
            c+=1
            i+=1
            j+=1
        else:
            if c>max_till:
                max_till  = c
            c = 1
            d =  A[j]-A[i]
    if c>max_till:
        max_till = c
        
    print("Case #{0}: {1}".format(test,max_till))
    t-=1
    test+=1
```
