# 100 Prisoner Problem

## Question

100 prisoners are going to be executed, but there is a chance to survive.

The king asks them to count off, it means the first prisoner report 1, the second report 2, and keep going until the last report 100.
Once the prisoner reports an **odd number**, then sadly he would be executed immediately.

After a round of counting, the remaining prisoners still have to count off from 1 again,
and the execution won't stop until the last prisoner survived.

Assuming you are an extremely smart prisoner, which number would you chooce in the first round, 
and make sure you are the last lucky guy who successfully survived in 1/100 chance.





## Answer (By Decimal)

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




## Answer (By Binary)

```python

binary_num = ["%7s"%bin(i)[2:].zfill(7) for i in range(1, 101)]
death_note = []

for i in range(1, 8):
    temp_survived = []
    for b in binary_num:
        if b[-i] == '1':
            death_note.append(b)
        else:
            temp_survived.append(b) 
    binary_num = temp_survived
    
            
print('--------- Binary --------- ')
print('Death Order:', death_note[:-1])
print('Last Survived:', death_note[-1])



print('--------- Decimal --------- ')
death_note_copy = [int(b, 2) for b in death_note] # convert bin to dec
print('Death Order:', death_note_copy[:-1])
print('Last Survived:', death_note_copy[-1])
```

--------- Decimal --------- 
Death Order: [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29, 31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53, 55, 57, 59, 61, 63, 65, 67, 69, 71, 73, 75, 77, 79, 81, 83, 85, 87, 89, 91, 93, 95, 97, 99, 2, 6, 10, 14, 18, 22, 26, 30, 34, 38, 42, 46, 50, 54, 58, 62, 66, 70, 74, 78, 82, 86, 90, 94, 98, 4, 12, 20, 28, 36, 44, 52, 60, 68, 76, 84, 92, 100, 8, 24, 40, 56, 72, 88, 16, 48, 80, 32, 96]

Last Survived: 64



--------- Binary --------- 
Last Survived: 1000000

Death Order:
['0000001',
 '0000011',
 '0000101',
 '0000111',
 '0001001',
 '0001011',
 '0001101',
 '0001111',
 '0010001',
 '0010011',
 '0010101',
 '0010111',
 '0011001',
 '0011011',
 '0011101',
 '0011111',
 '0100001',
 '0100011',
 '0100101',
 '0100111',
 '0101001',
 '0101011',
 '0101101',
 '0101111',
 '0110001',
 '0110011',
 '0110101',
 '0110111',
 '0111001',
 '0111011',
 '0111101',
 '0111111',
 '1000001',
 '1000011',
 '1000101',
 '1000111',
 '1001001',
 '1001011',
 '1001101',
 '1001111',
 '1010001',
 '1010011',
 '1010101',
 '1010111',
 '1011001',
 '1011011',
 '1011101',
 '1011111',
 '1100001',
 '1100011',
 '0000010',
 '0000110',
 '0001010',
 '0001110',
 '0010010',
 '0010110',
 '0011010',
 '0011110',
 '0100010',
 '0100110',
 '0101010',
 '0101110',
 '0110010',
 '0110110',
 '0111010',
 '0111110',
 '1000010',
 '1000110',
 '1001010',
 '1001110',
 '1010010',
 '1010110',
 '1011010',
 '1011110',
 '1100010',
 '0000100',
 '0001100',
 '0010100',
 '0011100',
 '0100100',
 '0101100',
 '0110100',
 '0111100',
 '1000100',
 '1001100',
 '1010100',
 '1011100',
 '1100100',
 '0001000',
 '0011000',
 '0101000',
 '0111000',
 '1001000',
 '1011000',
 '0010000',
 '0110000',
 '1010000',
 '0100000',
 '1100000']

