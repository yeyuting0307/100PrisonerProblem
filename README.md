# 100 Prisoner Problem

## Question

100 prisoners are going to be executed, but there is a chance to survive.
The king asks them to count off, it means the first prisoner report 1, the second report 2, and keep going until the last report 100.
Once the prisoner reports an **odd number**, then sadly he would be executed immediately.

After a round of counting, the remaining prisoners still have to count off from 1 again,
and the execution won't stop until the last prisoner survived.

Assuming you are an extremely smart prisoner, which number would you chooce in the first round, 
and make sure you are the last lucky guy who successfully survived in 1/100 chance.



## Answer (By Code)

```python
arr = [x for x in range(1, 101)]

list_popped = arr[:] # copy arr
popped_sort = [] # record death order
while len(list_popped) > 1:
    del_ptr = []
    for j in range(len(list_popped[:])):
        if (j+1)%2!=0:
            del_ptr.append(j)
        else:
            pass
    
    # Get pop order
    pop_adjusts = []
    for i, pi in enumerate(del_ptr):
        adj = 0
        for j,pj in enumerate(del_ptr[:i+1]):
            if pi > pj:
                adj -= 1
            else:
                pass
        pop_adjusts.append(pi + adj)
    
    
    # Start pop with stop condition
    for p in pop_adjusts:
        popped_sort.append(list_popped[p])
        list_popped.pop(p)
        if len(list_popped) <= 1 :
            break
        
print('Death Order :', popped_sort)
print('Last Survival :', list_popped)
```

Death Order : [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29, 31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53, 55, 57, 59, 61, 63, 65, 67, 69, 71, 73, 75, 77, 79, 81, 83, 85, 87, 89, 91, 93, 95, 97, 99, 2, 6, 10, 14, 18, 22, 26, 30, 34, 38, 42, 46, 50, 54, 58, 62, 66, 70, 74, 78, 82, 86, 90, 94, 98, 4, 12, 20, 28, 36, 44, 52, 60, 68, 76, 84, 92, 100, 8, 24, 40, 56, 72, 88, 16, 48, 80, 32, 96]

Last Survival : [64]

