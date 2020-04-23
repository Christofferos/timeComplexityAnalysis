# timeComplexityAnalysis

Analysis of the time complexity for different classical data structures. The main take away is when to use which structure in order to reach highest efficiency.

<br>

<h3> Task 2 - Time Complexities for Data Structures

| Operation | Unsorted Array | Sorted Array | Unsorted SLL | Sorted SLL | Hash table (Average) | Hash table (Worst) |
| --------- | -------------- | ------------ | ------------ | ---------- | -------------------- | ------------------ |
| Find      | O(n)           | O(log n)     | O(n)         | O(n)       | O(1)                 | O(n)               |
| Insert    | O(n)           | O(n)         | O(1)         | O(1)       | O(1)                 | O(n)               |
| Remove    | O(n)           | O(n)         | O(1)         | O(1)       | O(1)                 | O(n)               |

<br/>
<h5> Motivation:

**Unsorted Array** - Find, we do not know where element is and worst case we will go through the whole array. For insertion to work it needs to find where it can be inserted in the array, which requires iteration through the array to find it - that is O(n) timecomplexity. Remove, we need to find which element to remove from which "bucket" therefore we can in worst case find ourselves going through the whole list before finding the correct element.
<br/>
**Sorted Array** - Find, if we know that elements are sorted in increasing or decreasing order we can simply divide the array into two and search for it in the half that has a value closer to the requested element (Binary Search). Insert in worst-case is just as motivated above.
Remove in worst-case is just as motivated above.
<br/>
**Unsorted SLL** - Find, we need to go from "first" element in unstorted LinkedList to "last" element to find the "last" element which would be the worst-case element to find. To insert an element we need to reach the end of the LinkedList which is of linear size (n). To remove the worst-case element we need to reach the "last" element that is n-steps from the "start" element.
<br/>
**Sorted SLL** - Same motivation goes for these three operations in "Sorted SLL" as in "Unsorted SLL". _OBS. Binary Search is not possible in this case as with Arrays!_
<br/>
**Hash table (Average)** - The find operation is of constant time complexity since we have a key value connected to each search which leads to the correct "bucket" in the array right away with the requested element. We can Insert an element in any "bucket" if it is already filled just put it on the end of the LinkedList connected to that "bucket". Remove, works in the same fashion as "find" just that it removes the element in the LinkedList connected to the "bucket" and takes the same time.
<br/>
**Hash table (Worst)** - In worst case scenario all elements hash to the same location and are part of aone long chain of Links of size n, which we know from earlier excercies takes O(n) time to go through to reach the desired element. Find, Insert and Remove work in similar fashion to each other and will go through one single LinkedList of particular "bucket" in the array containing all the space for the hashMap.

<h3>Task 3 - Dynamic Tables

    What is the initial capacity of an ArrayList's internal array?
    At what size does the internal array grow, and by how much?
    Explain what really happens by the term "grow" in this context?
    What is the capacity of the internal array once 20 elements have been added?
    If objects were removed, would the size of the internal array change also?
    What is the worst, average, and best-case time complexity of the add(E e) method of Arraylist?

**1.** The initial zero-sized array has a capacity of 10.

**2.** ACORDING to how it is in reality: when we try to add an element to an already filled array, the arrays' elemets will be copied and moved to a larger array of size 1.5 times the last array.

(ACORDING TO THE SOURCE CODE we were given: In the add method (that adds one Object to array) a method call is done to another add-method but with 3 parameters. This is where the size and capacity of the arrays is increased by one IF the index of the added element is equal to the Array.length! (and calls the grow() method).)

**3.** The "grow" term can be misleading because according to the source code, the array is recreaten not enlarged. So, a new array of greater size is made and the old array is thrown away to the garbage collector.

**4.** The internal capacity is at 22 when 20 elemts have been added. Process: 10 capacity initially, then 15, then 22 as the elemts are added into the array.

((The internal capacity increases along the size of the array after we pass 10 elements added. It is only if we call ensureCapacity and increase it with a greater number that we will see an internal array with greater capacity at 20 inserted/added elements.))

**5.** The object removed from an given index position in the array will make that position null, but the capacity of the internal array will stay the same as before removal. The size is amount of elements in the array, so this will decrease by one.

**6.**

- Best case: amortized O(1).
- Average case: O(1) in most situations of a call on add() we only need to add on an element to the ArrayList which is done in constant time. In some situations we will need to increase the ArrayList size, but by using the accounting method for calculation of time complexity it is possible to take the cost for expansion into account when adding any element, which will mean that the adding of an element can be expressed in constant time complexity, O(1).
- Worst Case: O(n) since the array has to be resized and copied.
