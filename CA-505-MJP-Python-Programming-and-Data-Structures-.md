# slip 1

***

### Question 1: Write a Python Program to Calculate the Average of Numbers in a List

#### Approach

- Accept a list of numbers.
- Use `sum()` to add them and `len()` to count elements.
- Compute average: total sum divided by number of elements.
- Print the result.


#### Syntax Definitions

- **List Creation:** `numbers = [value1, value2, ...]`
- **Function Definition:** `def function_name(parameters):`
- **Sum \& Length:** `sum(numbers), len(numbers)`


#### Diagram (Text-based)

List Example:
`[10][20][30][40][50]`

#### Python Code

```python
# Functionality: Calculates the average of a list of numbers
def calculate_average(numbers):
    """
    Calculates the average of numbers in a list.
    :param numbers: List of numeric values
    :return: Float average value
    """
    if len(numbers) == 0:
        return 0.0
    total = sum(numbers)   # Add all numbers
    average = total / len(numbers)  # Divide by count
    return average

# Example usage
nums = [10, 20, 30, 40, 50]
print("Average:", calculate_average(nums))
```


#### Sample Input and Output

Input: `[10][20][30][40][50]`
Output: `Average: 30.0`

***

### Question 2 (Option 1): Write a Python Program to Perform BST Operations: Insert, Display

#### Approach

- Use a class for each tree node.
- BST class manages insertions.
- Inorder traversal for sorted display.


#### Syntax Definitions

- **Class:** `class ClassName:`
- **Constructor:** `def __init__(self, parameters):`
- **Recursion:** Functions calling themselves.


#### Diagram (Text-based)

BST for values `[40][20][60][10][30][50][70]`:

```
        40
       /  \
     20    60
    / \   / \
  10 30 50 70
```


#### Python Code

```python
# Functionality: Implements BST insert and inorder display
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

class BST:
    def __init__(self):
        self.root = None

    def insert(self, data):
        if self.root is None:
            self.root = Node(data)
        else:
            self._insert(self.root, data)
    
    def _insert(self, node, data):
        if data < node.data:
            if node.left is None:
                node.left = Node(data)
            else:
                self._insert(node.left, data)
        else:
            if node.right is None:
                node.right = Node(data)
            else:
                self._insert(node.right, data)

    def display(self):
        self._inorder(self.root)
    
    def _inorder(self, node):
        if node:
            self._inorder(node.left)
            print(node.data, end=' ')
            self._inorder(node.right)

# Example usage:
bst = BST()
elements = [40, 20, 60, 10, 30, 50, 70]
for elem in elements:
    bst.insert(elem)
print("BST inorder display:", end=' ')
bst.display()
```


#### Sample Input and Output

Input: `[40][20][60][10][30][50][70]`
Output: `BST inorder display: 10 20 30 40 50 60 70`


### Question 2 (Option 2): Python Program to Merge Two Sorted Linked Lists

#### Approach

- Use a class for each linked list node.
- Merge by comparing node values.
- Build new list node-by-node.


#### Syntax Definitions

- **Class:** `class Node:`
- **Node Creation:** `Node(value)`
- **Next Pointer:** `node.next`


#### Diagram (Text-based)

List 1: `1 → 3 → 5`
List 2: `2 → 4 → 6`
Merged: `1 → 2 → 3 → 4 → 5 → 6`

#### Python Code

```python
# Functionality: Merges two sorted linked lists
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

def merge_sorted_lists(head1, head2):
    dummy = Node(0)
    tail = dummy
    while head1 and head2:
        if head1.data < head2.data:
            tail.next = head1
            head1 = head1.next
        else:
            tail.next = head2
            head2 = head2.next
        tail = tail.next
    tail.next = head1 or head2
    return dummy.next

def print_list(head):
    while head:
        print(head.data, end=' ')
        head = head.next

# Example usage:
# Create first sorted list: 1->3->5
a1 = Node(1)
a2 = Node(3)
a3 = Node(5)
a1.next = a2
a2.next = a3

# Create second sorted list: 2->4->6
b1 = Node(2)
b2 = Node(4)
b3 = Node(6)
b1.next = b2
b2.next = b3

merged_head = merge_sorted_lists(a1, b1)
print("Merged linked list:", end=' ')
print_list(merged_head)
```


#### Sample Input and Output

Input Lists: `1 3 5` and `2 4 6`
Output: `Merged linked list: 1 2 3 4 5 6`

***

## SLIP 2
***
### Question 1: Write a program which accepts 6 integer values and prints DUPLICATES if any of the values entered are duplicates otherwise it prints ALL UNIQUE.

#### Approach:

- Input 6 integers and store them in a list
- Convert list to set to remove duplicates
- Compare the lengths: if set length < 6, duplicates exist
- Print appropriate message based on comparison


#### Syntax Definitions:

- **List Creation:** `numbers = [val1, val2, val3, val4, val5, val6]`
- **Set Creation:** `unique_set = set(numbers)`
- **Length Function:** `len(collection)`
- **Conditional Statement:** `if condition: ... else: ...`


#### Diagram (Text-based):

```
Input: [32, 10, 45, 90, 45, 6]
       ↓
Set:   {32, 10, 45, 90, 6}
       ↓
Length comparison: 5 < 6 → DUPLICATES
```


#### Python Code:

```python
# Functionality: Checks for duplicates among six entered integers
def check_duplicates():
    """
    Accepts 6 integers and checks for duplicates.
    Prints DUPLICATES if any duplicates exist, otherwise ALL UNIQUE.
    """
    numbers = []
    print("Enter 6 integers:")
    for i in range(6):
        num = int(input(f"Enter number {i+1}: "))
        numbers.append(num)
    
    unique_numbers = set(numbers)
    
    if len(unique_numbers) < 6:
        print("DUPLICATES")
    else:
        print("ALL UNIQUE")

# Alternative function for testing with predefined values
def check_duplicates_test(numbers):
    """Test version with predefined numbers"""
    unique_numbers = set(numbers)
    if len(unique_numbers) < 6:
        return "DUPLICATES"
    else:
        return "ALL UNIQUE"

# Example usage
test_nums = [32, 10, 45, 90, 45, 6]
print(check_duplicates_test(test_nums))
```


#### Sample Input and Output:

Input: `[32][10][45][90][45][6]`
Output: `DUPLICATES`



### Question 2 (Option 1): Write a python program to reverse the list and print both original and reversed lists using lists.

#### Approach:

- Accept a list of numbers from user
- Create reversed list using slicing method `[::-1]`
- Display both original and reversed lists with proper labels


#### Syntax Definitions:

- **List Slicing:** `reversed_list = original_list[::-1]`
- **List Input:** `list(map(int, input().split()))`
- **Print Function:** `print("Label:", list_name)`


#### Diagram (Text-based):

```
Original:  [1, 2, 3, 4, 5]
           ↓ (reverse)
Reversed:  [5, 4, 3, 2, 1]
```


#### Python Code:

```python
# Functionality: Reverses a list and displays both original and reversed versions
def reverse_and_display():
    """
    Accepts a list, reverses it, and prints both versions.
    """
    # Input list from user
    numbers = list(map(int, input("Enter numbers separated by spaces: ").split()))
    
    # Create reversed list
    reversed_numbers = numbers[::-1]
    
    # Display both lists
    print("Original list:", numbers)
    print("Reversed list:", reversed_numbers)

# Alternative function for testing
def reverse_list_test(lst):
    """Test version with predefined list"""
    print("Original list:", lst)
    reversed_lst = lst[::-1]
    print("Reversed list:", reversed_lst)
    return reversed_lst

# Example usage
test_numbers = [1, 2, 3, 4, 5]
reverse_list_test(test_numbers)
```


#### Sample Input and Output:

Input: `[1][2][3][4][5]`
Output:

```
Original list: [1, 2, 3, 4, 5]
Reversed list: [5, 4, 3, 2, 1]
```




### Question 2 (Option 2): Write a python program to count and display the total number of vowels, consonants, digits, and special characters in a string.

#### Approach:

- Input a string from user
- Iterate through each character in the string
- Use built-in methods to classify each character
- Maintain counters for each category
- Display the final counts


#### Syntax Definitions:

- **isalpha():** `char.isalpha()` - checks if character is alphabetic
- **isdigit():** `char.isdigit()` - checks if character is numeric
- **Membership Test:** `char in 'aeiouAEIOU'` - checks vowels
- **For Loop:** `for char in string:`


#### Diagram (Text-based):

```
String: "Hello@2021!"
H → Consonant    |    2 → Digit
e → Vowel        |    0 → Digit  
l → Consonant    |    2 → Digit
l → Consonant    |    1 → Digit
o → Vowel        |    ! → Special
@ → Special      |

Result: Vowels=2, Consonants=3, Digits=4, Special=2
```


#### Python Code:

```python
# Functionality: Counts vowels, consonants, digits, and special characters in a string
def count_character_types():
    """
    Accepts a string and counts different types of characters.
    Displays count of vowels, consonants, digits, and special characters.
    """
    # Input string from user
    input_string = input("Enter a string: ")
    
    # Define vowels
    vowels = "aeiouAEIOU"
    
    # Initialize counters
    vowel_count = 0
    consonant_count = 0
    digit_count = 0
    special_count = 0
    
    # Process each character
    for char in input_string:
        if char.isalpha():  # Check if alphabetic
            if char in vowels:
                vowel_count += 1
            else:
                consonant_count += 1
        elif char.isdigit():  # Check if digit
            digit_count += 1
        else:  # Special character (including spaces)
            special_count += 1
    
    # Display results
    print("Vowels:", vowel_count)
    print("Consonants:", consonant_count)
    print("Digits:", digit_count)
    print("Special Characters:", special_count)

# Alternative function for testing
def count_types_test(s):
    """Test version with predefined string"""
    vowels = "aeiouAEIOU"
    v_count = c_count = d_count = s_count = 0
    
    for char in s:
        if char.isalpha():
            if char in vowels:
                v_count += 1
            else:
                c_count += 1
        elif char.isdigit():
            d_count += 1
        else:
            s_count += 1
    
    print("Vowels:", v_count)
    print("Consonants:", c_count)
    print("Digits:", d_count)
    print("Special Characters:", s_count)

# Example usage
test_string = "Hello@2021!"
count_types_test(test_string)
```


#### Sample Input and Output:

Input: `"Hello@2021!"`
Output:

```
Vowels: 2
Consonants: 3
Digits: 4
Special Characters: 2
```

***

## SLIP 3
***
### Question 1: Write a Python program to add and remove operation on set.

#### Approach:

- Use a set to store elements.
- Use `add()` method to add an item and `remove()` (or `discard()`) method to remove.
- Display the set after each operation.


#### Syntax Definitions:

- **Set creation**: `s = set()`
- **Add element**: `s.add(value)`
- **Remove element**: `s.remove(value)` or `s.discard(value)`


#### Diagram (Text-based):

```
Start:      {}
add(3):     {3}
add(5):     {3, 5}
add(7):     {3, 5, 7}
remove(5):  {3, 7}
```


#### Python Code:

```python
# Functionality: Perform add and remove operations on a set
def set_add_remove_demo():
    """
    Demonstrate add and remove operations on a set.
    """
    s = set()
    print("Initial set:", s)
    s.add(3)
    print("After adding 3:", s)
    s.add(5)
    print("After adding 5:", s)
    s.add(7)
    print("After adding 7:", s)
    s.remove(5)
    print("After removing 5:", s)

# Example usage
set_add_remove_demo()
```


#### Sample Input and Output:

(No input required; uses sample values)
Output:

```
Initial set: set()
After adding 3: {3}
After adding 5: {3, 5}
After adding 7: {3, 5, 7}
After removing 5: {3, 7}
```



### Question 2 (Option 1): Write a python program to perform the following operations on Binary Search Tree:

- Create
- Count non-leaf nodes
- Traversal: Preorder, Inorder, Postorder


#### Approach:

- Use a class-based Node structure.
- Recursively insert nodes.
- Implement functions for preorder, inorder, postorder traversal.
- Recursively count non-leaf nodes (nodes with at least one child).


#### Syntax Definitions:

- **Class:** `class Node: ...`
- **Insert:** Recursively place new values left or right.
- **Traversal:** Recursively visit nodes.
- **Non-leaf node check:** Node with at least one child.


#### Diagram (Text-based):

Insert `[^14_40][^14_20][^14_60][^14_10][^14_30][^14_50][^14_70]`:

```
        40
       /  \
     20    60
    / \   /  \
  10 30 50  70
```

Non-leaf nodes: 40, 20, 60 (total 3)

#### Python Code:

```python
# Functionality: BST Creation, traversal, and non-leaf count
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

def insert(root, data):
    if root is None:
        return Node(data)
    elif data < root.data:
        root.left = insert(root.left, data)
    else:
        root.right = insert(root.right, data)
    return root

def preorder(root):
    if root:
        print(root.data, end=' ')
        preorder(root.left)
        preorder(root.right)

def inorder(root):
    if root:
        inorder(root.left)
        print(root.data, end=' ')
        inorder(root.right)

def postorder(root):
    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=' ')

def count_non_leaf_nodes(root):
    if root is None or (root.left is None and root.right is None):
        return 0
    return 1 + count_non_leaf_nodes(root.left) + count_non_leaf_nodes(root.right)

# Example usage
elements = [40, 20, 60, 10, 30, 50, 70]
root = None
for elem in elements:
    root = insert(root, elem)

print("Preorder traversal:", end=' ')
preorder(root)
print("\nInorder traversal:", end=' ')
inorder(root)
print("\nPostorder traversal:", end=' ')
postorder(root)
print("\nNon-leaf node count:", count_non_leaf_nodes(root))
```


#### Sample Input and Output:

Input: `[^14_40][^14_20][^14_60][^14_10][^14_30][^14_50][^14_70]`
Output:

```
Preorder traversal: 40 20 10 30 60 50 70 
Inorder traversal: 10 20 30 40 50 60 70 
Postorder traversal: 10 30 20 50 70 60 40 
Non-leaf node count: 3
```




### Question 2 (Option 2): Python program for dynamic implementation of Singly Linked List to perform Insert and Display operations.

#### Approach:

- Use a class to represent nodes and the linked list.
- Insert nodes at the end (`append` method).
- Display elements by traversing the list.


#### Syntax Definitions:

- **Class:** `class Node: ...`
- **Linked List:** Nodes pointing to next node, ends with `None`.


#### Diagram (Text-based):

Insert 10, 20, 30:

```
10 → 20 → 30 → None
```


#### Python Code:

```python
# Functionality: Dynamic Singly Linked List insert and display
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class SinglyLinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
        else:
            curr = self.head
            while curr.next:
                curr = curr.next
            curr.next = new_node

    def display(self):
        curr = self.head
        while curr:
            print(curr.data, end=' ')
            curr = curr.next

# Example usage
sll = SinglyLinkedList()
for value in [10, 20, 30]:
    sll.append(value)
print("Linked List:", end=' ')
sll.display()
```


#### Sample Input and Output:

Input: `10, 20, 30`
Output: `Linked List: 10 20 30`


---


## SLIP 4
***
### Question 1: Write a Python program to find maximum and the minimum value in a set.

#### Approach:

- Accept or define a set of numbers.
- Use Python’s built-in `max()` and `min()` functions to find the maximum and minimum values in the set.
- Print both values with labels.


#### Syntax Definitions:

- **Set Creation:** `s = {value1, value2, ...}`
- **Find Max:** `max(s)`
- **Find Min:** `min(s)`
- **Print:** `print("Max value:", max_value)`


#### Diagram (Text-based):

```
Set: {10, 22, 5, 33, 14}
        ↓
Max: 33
Min: 5
```


#### Python Code:

```python
# Functionality: Finds and displays the maximum and minimum values in a set
def find_max_min(s):
    """
    Prints the maximum and minimum values in a set.
    :param s: Input set of numbers
    """
    print("Set:", s)
    max_value = max(s)
    min_value = min(s)
    print("Max value:", max_value)
    print("Min value:", min_value)

# Example usage
sample_set = {10, 22, 5, 33, 14}
find_max_min(sample_set)
```


#### Sample Input and Output:

Input: `{10, 22, 5, 33, 14}`
Output:

```
Set: {33, 5, 10, 14, 22}
Max value: 33
Min value: 5
```




### Question 2 (Option 1): Write a python program to perform following operations on Binary Search Tree

- Create
- Count leaf nodes
- Traversal: Preorder, Inorder, Postorder


#### Approach:

- Create BST by inserting elements.
- Count leaf nodes using recursion: leaf nodes have no children.
- Display tree traversals: preorder, inorder, postorder.


#### Syntax Definitions:

- **Class for Node:** `class Node: ...`
- **Insert recursions:** For left/right children.
- **Leaf Check:** `if node.left is None and node.right is None`


#### Diagram (Text-based):

BST Example (Insert `[^15_50][^15_30][^15_70][^15_20][^15_40][^15_60][^15_80]`):

```
           50
         /    \
       30      70
      /  \    /  \
    20   40  60  80
Leaf nodes: 20, 40, 60, 80 (Total: 4)
```


#### Python Code:

```python
# Functionality: BST creation, leaf count & traversals
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

def insert(root, data):
    if root is None:
        return Node(data)
    if data < root.data:
        root.left = insert(root.left, data)
    else:
        root.right = insert(root.right, data)
    return root

def preorder(root):
    if root:
        print(root.data, end=' ')
        preorder(root.left)
        preorder(root.right)

def inorder(root):
    if root:
        inorder(root.left)
        print(root.data, end=' ')
        inorder(root.right)

def postorder(root):
    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=' ')

def count_leaf_nodes(root):
    if root is None:
        return 0
    if root.left is None and root.right is None:
        return 1
    return count_leaf_nodes(root.left) + count_leaf_nodes(root.right)

# Example usage
elements = [50, 30, 70, 20, 40, 60, 80]
root = None
for elem in elements:
    root = insert(root, elem)

print("Preorder traversal:", end=' ')
preorder(root)
print("\nInorder traversal:", end=' ')
inorder(root)
print("\nPostorder traversal:", end=' ')
postorder(root)
print("\nLeaf node count:", count_leaf_nodes(root))
```


#### Sample Input and Output:

Input: `[^15_50][^15_30][^15_70][^15_20][^15_40][^15_60][^15_80]`
Output:

```
Preorder traversal: 50 30 20 40 70 60 80 
Inorder traversal: 20 30 40 50 60 70 80 
Postorder traversal: 20 40 30 60 80 70 50 
Leaf node count: 4
```




### Question 2 (Option 2): Python program to create a linked list in the sorted order.

#### Approach:

- Accept or define elements to insert.
- For each new value, find correct sorted position in the linked list, and insert.
- Display list by traversing from head.


#### Syntax Definitions:

- **Class Node:** `class Node: ...`
- **Sorted Insert:** Find spot by comparing values.
- **Traversal:** Loop until `node.next` is None.


#### Diagram (Text-based):

Insert in order: 30, 10, 50, 40, 20
Sorted linked list: `10 → 20 → 30 → 40 → 50 → None`

#### Python Code:

```python
# Functionality: Sorted insertion & display of singly linked list
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class SortedLinkedList:
    def __init__(self):
        self.head = None
        
    def insert_sorted(self, value):
        new_node = Node(value)
        if self.head is None or value < self.head.data:
            new_node.next = self.head
            self.head = new_node
        else:
            curr = self.head
            while curr.next and curr.next.data < value:
                curr = curr.next
            new_node.next = curr.next
            curr.next = new_node
    
    def display(self):
        curr = self.head
        while curr:
            print(curr.data, end=' ')
            curr = curr.next
        print()

# Example usage
linked_list = SortedLinkedList()
for value in [30, 10, 50, 40, 20]:
    linked_list.insert_sorted(value)
print("Sorted Linked List:", end=' ')
linked_list.display()
```


#### Sample Input and Output:

Input: `30, 10, 50, 40, 20`
Output: `Sorted Linked List: 10 20 30 40 50`




---

## SLIP 5
***

### Question 1: Write a python program to create an array of n integers and display the array elements. Access individual elements through indexes.

#### Approach:

- Input the number of elements `n` and the elements.
- Store them in a Python list (used as an array).
- Print the whole array and then access individual elements using indexes.


#### Syntax Definitions:

- **List Creation:** `arr = [int(input('Enter element: ')) for _ in range(n)]`
- **Access via Index:** `arr[index]`
- **Print Statement:** `print(arr[index])`


#### Diagram (Text-based):

```
Array: [4, 7, 12, 9]
Indexes:  0  1  2  3
```


#### Python Code:

```python
# Functionality: Creates and displays array elements, accesses each by index
def array_demo():
    """
    Creates an array of n integers, displays the array, and accesses elements by index.
    """
    n = int(input("Enter number of elements: "))
    arr = [int(input(f"Element {i}: ")) for i in range(n)]
    
    print("Array:", arr)
    print("Accessing each element by index:")
    for i in range(n):
        print(f"arr[{i}] = {arr[i]}")

# Example usage (Test Version)
def array_demo_test():
    arr = [4, 7, 12, 9]
    print("Array:", arr)
    for i in range(len(arr)):
        print(f"arr[{i}] = {arr[i]}")

array_demo_test()
```


#### Sample Input and Output:

Input: `[^16_4][^16_7][^16_12][^16_9]`
Output:

```
Array: [4, 7, 12, 9]
arr[^16_0] = 4
arr[^16_1] = 7
arr[^16_2] = 12
arr[^16_3] = 9
```




### Question 2 (Option 1): Write a python program to perform following operations on BST

- Create
- Delete
- Traversal: Preorder, Inorder, Postorder


#### Approach:

- Create BST by inserting elements.
- Implement deletion: handle three cases (leaf, one child, two children).
- Display traversals.


#### Syntax Definitions:

- **BST Node Class:** `class Node: ...`
- **Insert/Delete/Traversal:** recursive functions.
- **BST Deletion:** Replace node with successor for two children.


#### Diagram (Text-based):

Insert:
Delete: 40
Resulting BST:

```
         60
       /    \
     20      80
       \    /  \
       50  70  90
```


#### Python Code:

```python
# BST with insert, delete and traversals
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

def insert(root, data):
    if root is None:
        return Node(data)
    if data < root.data:
        root.left = insert(root.left, data)
    else:
        root.right = insert(root.right, data)
    return root

def min_value_node(node):
    current = node
    while current.left is not None:
        current = current.left
    return current

def delete(root, data):
    if root is None:
        return root
    if data < root.data:
        root.left = delete(root.left, data)
    elif data > root.data:
        root.right = delete(root.right, data)
    else:
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left
        temp = min_value_node(root.right)
        root.data = temp.data
        root.right = delete(root.right, temp.data)
    return root

def preorder(root):
    if root:
        print(root.data, end=' ')
        preorder(root.left)
        preorder(root.right)

def inorder(root):
    if root:
        inorder(root.left)
        print(root.data, end=' ')
        inorder(root.right)

def postorder(root):
    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=' ')

# Example usage
elements = [60, 40, 80, 20, 50, 70, 90]
root = None
for elem in elements:
    root = insert(root, elem)

print("BST inorder before deletion:")
inorder(root)
print("\nDeleting 40...")
root = delete(root, 40)
print("Preorder traversal after deletion:")
preorder(root)
print("\nInorder traversal after deletion:")
inorder(root)
print("\nPostorder traversal after deletion:")
postorder(root)
```


#### Sample Input and Output:

Input:
Insert `[^16_60][^16_40][^16_80][^16_20][^16_50][^16_70][^16_90]`
Delete `40`
Output:

```
BST inorder before deletion:
20 40 50 60 70 80 90 
Deleting 40...
Preorder traversal after deletion:
60 20 50 80 70 90 
Inorder traversal after deletion:
20 50 60 70 80 90 
Postorder traversal after deletion:
50 20 70 90 80 60 
```




### Question 2 (Option 2): Write a python program for implementation of Doubly Linked List to perform Insert and Display operations.

#### Approach:

- Use a class for doubly linked list nodes (pointers `prev` and `next`).
- Insert at end.
- Display forwards by traversing from head and backwards from tail.


#### Syntax Definitions:

- **Class Node:** `class Node: ...`
- **Doubly Linked:** `node.prev`, `node.next`


#### Diagram (Text-based):

Insert: 10, 20, 30

```
None <- 10 <-> 20 <-> 30 -> None
```


#### Python Code:

```python
# Functionality: Doubly Linked List insert and display (forward/backward)
class DNode:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None

class DoublyLinkedList:
    def __init__(self):
        self.head = None
        self.tail = None
    
    def insert_end(self, value):
        new_node = DNode(value)
        if self.head is None:
            self.head = self.tail = new_node
        else:
            self.tail.next = new_node
            new_node.prev = self.tail
            self.tail = new_node

    def display_forward(self):
        curr = self.head
        print("Forward:", end=' ')
        while curr:
            print(curr.data, end=' ')
            curr = curr.next
        print()

    def display_backward(self):
        curr = self.tail
        print("Backward:", end=' ')
        while curr:
            print(curr.data, end=' ')
            curr = curr.prev
        print()

# Example usage
dll = DoublyLinkedList()
for val in [10, 20, 30]:
    dll.insert_end(val)
dll.display_forward()
dll.display_backward()
```


#### Sample Input and Output:

Input: `10, 20, 30`
Output:

```
Forward: 10 20 30 
Backward: 30 20 10 
```
***

## SLIP 6
***
### Question 1: Write a python program to get the number of occurrences of specified elements in an array.

#### Approach:

- Accept or define an array (list) of elements.
- Ask for the element to be counted.
- Use Python’s `count()` method to find occurrences.


#### Syntax Definitions:

- **List Creation:** `arr = [value1, value2, ...]`
- **Count Method:** `arr.count(element)`
- **Input:** `int(input("Enter number: "))`


#### Diagram (Text-based):

```
Array: [1, 2, 4, 2, 5, 2]
Count occurrences of 2 → 3
```


#### Python Code:

```python
# Functionality: Finds the number of occurrences of a specified element in an array
def count_occurrences():
    """
    Counts how many times a specified element appears in an array.
    """
    arr = [int(x) for x in input("Enter array elements separated by spaces: ").split()]
    element = int(input("Enter the element to count: "))
    occ = arr.count(element)
    print(f"Number of occurrences of {element}:", occ)

# Example usage (test version)
def count_occurrences_test():
    arr = [1, 2, 4, 2, 5, 2]
    element = 2
    print("Array:", arr)
    print(f"Number of occurrences of {element}:", arr.count(element))

count_occurrences_test()
```


#### Sample Input and Output:

Input:
Array: `[^17_1][^17_2][^17_4][^17_2][^17_5][^17_2]`
Element: `2`
Output:

```
Number of occurrences of 2: 3
```


### Question 2 (Option 1): Write a python program to perform following operations on Binary Search Tree

- Create
- Count total nodes
- Traversal: Preorder, Inorder, Postorder


#### Approach:

- Create BST by inserting values.
- Recursively count all nodes.
- Implement and print all tree traversals.


#### Syntax Definitions:

- **Class for Node:** `class Node: ...`
- **Insert, Traversal, Counting:** Recursive functions.


#### Diagram (Text-based):

Insert `[^17_40][^17_20][^17_60][^17_10][^17_30][^17_50][^17_70]`
Total nodes: 7

#### Python Code:

```python
# Functionality: BST creation, total node count, traversals
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

def insert(root, data):
    if root is None:
        return Node(data)
    if data < root.data:
        root.left = insert(root.left, data)
    else:
        root.right = insert(root.right, data)
    return root

def count_total_nodes(root):
    if root is None:
        return 0
    return 1 + count_total_nodes(root.left) + count_total_nodes(root.right)

def preorder(root):
    if root:
        print(root.data, end=' ')
        preorder(root.left)
        preorder(root.right)

def inorder(root):
    if root:
        inorder(root.left)
        print(root.data, end=' ')
        inorder(root.right)

def postorder(root):
    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=' ')

# Example usage
elements = [40, 20, 60, 10, 30, 50, 70]
root = None
for elem in elements:
    root = insert(root, elem)
print("Preorder traversal:", end=' ')
preorder(root)
print("\nInorder traversal:", end=' ')
inorder(root)
print("\nPostorder traversal:", end=' ')
postorder(root)
print("\nTotal number of nodes:", count_total_nodes(root))
```


#### Sample Input and Output:

Input: `[^17_40][^17_20][^17_60][^17_10][^17_30][^17_50][^17_70]`
Output:

```
Preorder traversal: 40 20 10 30 60 50 70 
Inorder traversal: 10 20 30 40 50 60 70 
Postorder traversal: 10 30 20 50 70 60 40 
Total number of nodes: 7
```




### Question 2 (Option 2): Python program to create doubly linked list and search the given node in the Linked list.

#### Approach:

- Use class for doubly linked list nodes with `prev` and `next` pointers.
- Insert nodes at end.
- Search by traversing the list and compare data.
- Output index or present/absent status.


#### Syntax Definitions:

- **Class Node:** `class Node`
- **Insert/Traversal/Searching:** Methods within DLL class.


#### Diagram (Text-based):

Insert: 10, 20, 30
Search: 20 found at index 1

#### Python Code:

```python
# Functionality: DLL insertion and node search
class DNode:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None

class DoublyLinkedList:
    def __init__(self):
        self.head = None
        self.tail = None
    
    def insert_end(self, value):
        new_node = DNode(value)
        if self.head is None:
            self.head = self.tail = new_node
        else:
            self.tail.next = new_node
            new_node.prev = self.tail
            self.tail = new_node

    def display(self):
        curr = self.head
        print("Linked List:", end=' ')
        while curr:
            print(curr.data, end=' ')
            curr = curr.next
        print()
    
    def search(self, value):
        curr = self.head
        position = 0
        found = False
        while curr:
            if curr.data == value:
                print(f"Node {value} found at position: {position}")
                found = True
                break
            curr = curr.next
            position += 1
        if not found:
            print(f"Node {value} not found in linked list.")

# Example usage
dll = DoublyLinkedList()
for val in [10, 20, 30]:
    dll.insert_end(val)
dll.display()
dll.search(20)
dll.search(40)
```


#### Sample Input and Output:

Input List: `10, 20, 30`
Search for: `20` and `40`
Output:

```
Linked List: 10 20 30 
Node 20 found at position: 1
Node 40 not found in linked list.
```


***

## SLIP 7
***
### Question 1: Write a python program to reverse the order of the items in the array.

#### Approach:

- Accept or define an array (list) of items.
- Use slicing (`[::-1]`) or the `reverse()` method to get the reversed order.
- Print both the original and reversed array for clarity.


#### Syntax Definitions:

- **List Creation:** `arr = [value1, value2, ...]`
- **List Slicing:** `reversed_arr = arr[::-1]`
- **Print Statement:** `print(list_name)`


#### Diagram (Text-based):

```
Original array: [1, 2, 3, 4, 5]
Reversed array: [5, 4, 3, 2, 1]
```


#### Python Code:

```python
# Functionality: Reverses the order of items in an array/list and displays both
def reverse_array(arr):
    """
    Reverses the array and prints both original and reversed arrays.
    :param arr: List/array of values
    """
    print("Original array:", arr)
    reversed_arr = arr[::-1]
    print("Reversed array:", reversed_arr)

# Example usage
sample_array = [1, 2, 3, 4, 5]
reverse_array(sample_array)
```


#### Sample Input and Output:

Input: `[^18_1][^18_2][^18_3][^18_4][^18_5]`
Output:

```
Original array: [1, 2, 3, 4, 5]
Reversed array: [5, 4, 3, 2, 1]
```


### Question 2 (Option 1): Write a python program to perform following operations on BST – Create, Display.

#### Approach:

- Use a class for the BST node.
- Insert data into BST with rules: left for less, right for greater.
- Display BST in sorted order (inorder traversal).


#### Syntax Definitions:

- **Class Node:** `class Node: ...`
- **BST Insert:** Recursively insert left or right.
- **Display Traversal:** Inorder traversal function.


#### Diagram (Text-based):

Insert: `[^18_50][^18_30][^18_70][^18_20][^18_40][^18_60][^18_80]`

```
           50
         /    \
       30      70
      /  \    /  \
    20   40  60  80
```

Display (inorder): `20 30 40 50 60 70 80`

#### Python Code:

```python
# Functionality: BST creation and display (inorder traversal)
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

def insert(root, data):
    if root is None:
        return Node(data)
    if data < root.data:
        root.left = insert(root.left, data)
    else:
        root.right = insert(root.right, data)
    return root

def inorder_display(root):
    if root:
        inorder_display(root.left)
        print(root.data, end=' ')
        inorder_display(root.right)

# Example usage
elements = [50, 30, 70, 20, 40, 60, 80]
root = None
for elem in elements:
    root = insert(root, elem)
print("BST Inorder display:", end=' ')
inorder_display(root)
print()
```


#### Sample Input and Output:

Input: `[^18_50][^18_30][^18_70][^18_20][^18_40][^18_60][^18_80]`
Output:

```
BST Inorder display: 20 30 40 50 60 70 80 
```


### Question 2 (Option 2): Write a python program to create singly linked list and search the given node in the Linked list.

#### Approach:

- Implement node and singly linked list classes.
- Insert values at end.
- Search for a value by traversing and comparing each node’s value.
- Give index if found, or state not found.


#### Syntax Definitions:

- **Class Node:** `class Node`
- **Linked List Insert:** At end: loop until `node.next` is None.
- **Traversal \& Search:** Loop, compare, and track position.


#### Diagram (Text-based):

Insert: `10, 20, 30`
Search for: `20`

```
10 → 20 → 30 → None
[search for 20 → found at index 1]
```


#### Python Code:

```python
# Functionality: Singly Linked List insert and search node
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class SinglyLinkedList:
    def __init__(self):
        self.head = None
    
    def insert_end(self, value):
        new_node = Node(value)
        if self.head is None:
            self.head = new_node
        else:
            curr = self.head
            while curr.next:
                curr = curr.next
            curr.next = new_node

    def display(self):
        curr = self.head
        print("Linked List:", end=' ')
        while curr:
            print(curr.data, end=' ')
            curr = curr.next
        print()
    
    def search(self, value):
        curr = self.head
        pos = 0
        found = False
        while curr:
            if curr.data == value:
                print(f"Node {value} found at position: {pos}")
                found = True
                break
            curr = curr.next
            pos += 1
        if not found:
            print(f"Node {value} not found in Linked List.")

# Example usage
sll = SinglyLinkedList()
for val in [10, 20, 30]:
    sll.insert_end(val)
sll.display()
sll.search(20)
sll.search(40)
```


#### Sample Input and Output:

Input: `10, 20, 30`
Search: `20` and `40`
Output:

```
Linked List: 10 20 30 
Node 20 found at position: 1
Node 40 not found in Linked List.
```

***

## SLIP 8
***
### Question 1: Write a python program to find the sum of all the elements in a list.

#### Approach:

- Input or define a list of numbers.
- Use a loop or Python’s built-in `sum()` to add all elements.
- Print the result.


#### Syntax Definitions:

- **List Creation:** `lst = [value1, value2, ...]`
- **Summation:** `total = sum(lst)`
- **For Loop Summing:** `for num in lst: total += num`


#### Diagram (Text-based):

```
List: [2, 4, 5, 7]
Sum: 2 + 4 + 5 + 7 = 18
```


#### Python Code:

```python
# Functionality: Finds the sum of all elements in a list
def sum_of_list(lst):
    """
    Returns the sum of all elements in a list.
    """
    total = sum(lst)
    print("Sum of all elements:", total)

# Example usage
numbers = [2, 4, 5, 7]
sum_of_list(numbers)
```


#### Sample Input and Output:

Input: `[^19_2][^19_4][^19_5][^19_7]`
Output: `Sum of all elements: 18`


### Question 2 (Option 1): Write a python program to perform following operations on BST:

- Insert
- Delete
- Display Preorder, Inorder, Postorder


#### Approach:

- Use a class for the BST node.
- Insert values using standard BST rules.
- Delete a given value with logic for three deletion cases.
- Traverse and display the tree in preorder, inorder, and postorder.


#### Syntax Definitions:

- **Class Node:** `class Node: ...`
- **Insert:** Left for less, right for greater/equal.
- **Delete:** Leaf/one child/two children.
- **Traversal:** Recursive traversals.


#### Diagram (Text-based):

Insert: `[^19_40][^19_20][^19_60][^19_10][^19_30][^19_50][^19_70]`
Delete: `20`

```
         40
        /  \
      10    60
        \   / \
        30 50 70
```


#### Python Code:

```python
# Functionality: BST Insert, Delete, and Traversals
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

def insert(root, key):
    if root is None:
        return Node(key)
    if key < root.data:
        root.left = insert(root.left, key)
    else:
        root.right = insert(root.right, key)
    return root

def min_value_node(node):
    while node.left:
        node = node.left
    return node

def delete(root, key):
    if not root:
        return root
    if key < root.data:
        root.left = delete(root.left, key)
    elif key > root.data:
        root.right = delete(root.right, key)
    else:
        if not root.left:
            return root.right
        elif not root.right:
            return root.left
        temp = min_value_node(root.right)
        root.data = temp.data
        root.right = delete(root.right, temp.data)
    return root

def preorder(root):
    if root:
        print(root.data, end=' ')
        preorder(root.left)
        preorder(root.right)

def inorder(root):
    if root:
        inorder(root.left)
        print(root.data, end=' ')
        inorder(root.right)

def postorder(root):
    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=' ')

# Example usage
elements = [40, 20, 60, 10, 30, 50, 70]
root = None
for x in elements:
    root = insert(root, x)
root = delete(root, 20)
print("Preorder:", end=' ')
preorder(root)
print("\nInorder:", end=' ')
inorder(root)
print("\nPostorder:", end=' ')
postorder(root)
```


#### Sample Input and Output:

Insert: `[^19_40][^19_20][^19_60][^19_10][^19_30][^19_50][^19_70]`, Delete: `20`
Output:

```
Preorder: 40 10 30 60 50 70 
Inorder: 10 30 40 50 60 70 
Postorder: 30 10 50 70 60 40 
```

### Question 2 (Option 2): Write a python program to create a singly linked list and reverse the Linked list.

#### Approach:

- Implement a class for singly linked list nodes.
- Insert by appending at the end.
- Reverse list pointers in-place.
- Display the original and reversed lists.


#### Syntax Definitions:

- **Class Node:** `class Node`
- **Reversal Algorithm:** Loop, reverse pointers.


#### Diagram (Text-based):

Original: `10 → 20 → 30 → 40 → None`
Reversed: `40 → 30 → 20 → 10 → None`

#### Python Code:

```python
# Functionality: Creates and reverses a singly linked list
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class SinglyLinkedList:
    def __init__(self):
        self.head = None

    def append(self, value):
        new_node = Node(value)
        if not self.head:
            self.head = new_node
        else:
            curr = self.head
            while curr.next:
                curr = curr.next
            curr.next = new_node

    def display(self):
        curr = self.head
        while curr:
            print(curr.data, end=' ')
            curr = curr.next
        print()

    def reverse(self):
        prev = None
        curr = self.head
        while curr:
            next_node = curr.next
            curr.next = prev
            prev = curr
            curr = next_node
        self.head = prev

# Example usage
sll = SinglyLinkedList()
for v in [10, 20, 30, 40]:
    sll.append(v)
print("Original list:", end=' ')
sll.display()
sll.reverse()
print("Reversed list:", end=' ')
sll.display()
```


#### Sample Input and Output:

Insert: `10, 20, 30, 40`
Output:

```
Original list: 10 20 30 40 
Reversed list: 40 30 20 10 
```

***

## SLIP 9
***
### Question 1: Write a python function to calculate the factorial of a number. The function accepts the number as an argument.

#### Approach:

- Use a function that accepts an integer argument.
- Use a loop or recursion to multiply from 1 to n.
- Return the result.


#### Syntax Definitions:

- **Function definition:** `def factorial(n):`
- **Loop:** `for i in range(1, n+1):`
- **Recursion:** Function calling itself.


#### Diagram (Text-based):

```
factorial(5): 5 * 4 * 3 * 2 * 1 = 120
```


#### Python Code:

```python
# Functionality: Calculates factorial of a given number
def factorial(n):
    """
    Returns factorial of n using iterative method.
    :param n: integer
    :return: integer factorial
    """
    result = 1
    for i in range(1, n+1):
        result *= i
    return result

# Example usage
num = 5
print(f"Factorial of {num}:", factorial(num))
```


#### Sample Input and Output:

Input: `5`
Output: `Factorial of 5: 120`

### Question 2 (Option 1): Write a program to search an element using Linear Search.

#### Approach:

- Input or define a list of numbers and a target element.
- Scan each element from start to end.
- If found, report the index; if not, state not found.


#### Syntax Definitions:

- **For loop:** `for i in range(len(lst)):`
- **Input:** `input("Enter element: ")`


#### Diagram (Text-based):

List: `[^20_7][^20_12][^20_8][^20_5]`
Search for: `8` → found at index 2

#### Python Code:

```python
# Functionality: Searches for an element using linear search
def linear_search(lst, key):
    """
    Searches for key in lst using linear search.
    Returns index if found, else -1.
    """
    for i in range(len(lst)):
        if lst[i] == key:
            return i
    return -1

# Example usage
numbers = [7, 12, 8, 5]
search_for = 8
index = linear_search(numbers, search_for)
if index != -1:
    print(f"Element {search_for} found at index {index}")
else:
    print(f"Element {search_for} not found in list")
```


#### Sample Input and Output:

List: `[^20_7][^20_12][^20_8][^20_5]`
Search: `8`
Output: `Element 8 found at index 2`



### Question 2 (Option 2): Write a program to calculate indegree of a graph using adjacency matrix.

#### Approach:

- Input or define the adjacency matrix.
- For each node (column), sum the number of incoming edges (entries with 1).
- Print the indegree for all nodes.


#### Syntax Definitions:

- **Matrix:** `matrix[i][j]`
- **Sum column elements:** `sum(row[j] for row in matrix)`


#### Diagram (Text-based):

Adjacency Matrix:

```
    0 1 2
0 [0 1 0]
1 [1 0 1]
2 [0 1 0]
Indegree for each node:
Node 0 → 1 (incoming from 1)
Node 1 → 2 (incoming from 0 and 2)
Node 2 → 1 (incoming from 1)
```


#### Python Code:

```python
# Functionality: Calculates the indegree of each node using adjacency matrix
def calculate_indegree(matrix):
    """
    Prints indegree of each node in graph given adjacency matrix.
    :param matrix: 2D list (adjacency matrix)
    """
    n = len(matrix)
    for col in range(n):
        indegree = 0
        for row in range(n):
            if matrix[row][col]:
                indegree += 1
        print(f"Indegree of node {col}: {indegree}")

# Example usage
adj_matrix = [
    [0, 1, 0],
    [1, 0, 1],
    [0, 1, 0]
]
calculate_indegree(adj_matrix)
```


#### Sample Input and Output:

Input:

```
0 1 0
1 0 1
0 1 0
```

Output:

```
Indegree of node 0: 1
Indegree of node 1: 2
Indegree of node 2: 1
```

***

## SLIP 10
***
### Question 1: Write a Python script to generate and print a dictionary that contains a number between 1 and n in the form x: x*x.

#### Approach:

- Input integer n.
- Use a loop from 1 to n.
- Create dictionary where key = number, value = square of number.


#### Syntax Definitions:

- **Dictionary:** `d = {}`
- **For loop:** `for i in range(1, n+1):`
- **Assignment:** `d[i] = i*i`


#### Diagram (Text-based):

If `n = 5`:

```
1: 1
2: 4
3: 9
4: 16
5: 25
```


#### Python Code:

```python
# Functionality: Generates dictionary with number and its square from 1 to n
def generate_square_dict(n):
    """
    Returns a dictionary with number and its square from 1 to n.
    :param n: integer
    :return: dictionary
    """
    d = {}
    for i in range(1, n+1):
        d[i] = i*i
    print(d)
    return d

# Example usage
generate_square_dict(5)
```


#### Sample Input and Output:

Input: `n = 5`
Output: `{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}`



### Question 2 (Option 1): Write a program to search an element using Binary Search.

#### Approach:

- Input/define a sorted list and search target.
- Use binary search: set low and high, find mid, compare value, adjust bounds.
- Print index if found, else not found.


#### Syntax Definitions:

- **While Loop:** `while low <= high`
- **Mid Calculation:** `mid = (low + high) // 2`
- **Conditional:** if/elif/else


#### Diagram (Text-based):

List: `[^21_1][^21_3][^21_5][^21_7][^21_9]`
Search for: `5`
Check middle, adjust bounds, result: found at index 2.

#### Python Code:

```python
# Functionality: Binary search in sorted list
def binary_search(arr, key):
    """
    Returns index of key using binary search, else -1.
    :param arr: sorted list
    :param key: value to search
    """
    low, high = 0, len(arr)-1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == key:
            return mid
        elif arr[mid] < key:
            low = mid + 1
        else:
            high = mid - 1
    return -1

# Example usage
numbers = [1, 3, 5, 7, 9]
target = 5
idx = binary_search(numbers, target)
if idx != -1:
    print(f"Element {target} found at index {idx}")
else:
    print(f"Element {target} not found in list")
```


#### Sample Input and Output:

List: `[^21_1][^21_3][^21_5][^21_7][^21_9]`, Search: `5`
Output: `Element 5 found at index 2`


### Question 2 (Option 2): Write a Python program to calculate outdegree of a graph using adjacency matrix.

#### Approach:

- Use 2D list for adjacency matrix.
- Outdegree for node is sum of entries in its row.


#### Syntax Definitions:

- **Sum row in matrix:** `sum(matrix[row])`
- **For loop:** `for row in range(len(matrix))`


#### Diagram (Text-based):

Matrix:

```
0 1 0
1 0 1
0 1 0
Outdegree:
Node 0: 1
Node 1: 2
Node 2: 1
```


#### Python Code:

```python
# Functionality: Calculates outdegree of each node using adjacency matrix
def calculate_outdegrees(matrix):
    """
    Prints outdegree of each node.
    :param matrix: 2D list
    """
    n = len(matrix)
    for i in range(n):
        outdeg = sum(matrix[i])
        print(f"Outdegree of node {i}: {outdeg}")

# Example usage
adj_matrix = [
    [0, 1, 0],
    [1, 0, 1],
    [0, 1, 0]
]
calculate_outdegrees(adj_matrix)
```


#### Sample Input and Output:

Input:

```
0 1 0
1 0 1
0 1 0
```

Output:

```
Outdegree of node 0: 1
Outdegree of node 1: 2
Outdegree of node 2: 1
```

***

## SLIP 11
***
### Question 1: Write a program to generate Fibonacci numbers using a function.

#### Approach:

- Use a function that accepts n (count of numbers).
- Use a loop or recursion to generate Fibonacci sequence (0, 1, 1, 2, 3, ...).
- Print the sequence.


#### Syntax Definitions:

- **Function Definition:** `def fibonacci(n):`
- **Loop:** `for i in range(n):`
- **List for sequence:** `fib_nums = []`


#### Diagram (Text-based):

```
For n = 7: 0, 1, 1, 2, 3, 5, 8
```


#### Python Code:

```python
# Functionality: Generates n Fibonacci numbers
def fibonacci(n):
    """
    Prints the first n Fibonacci numbers.
    """
    fib_nums = []
    a, b = 0, 1
    for i in range(n):
        fib_nums.append(a)
        a, b = b, a + b
    print("Fibonacci sequence:", fib_nums)

# Example usage
fibonacci(7)
```


#### Sample Input and Output:

Input: `n = 7`
Output: `Fibonacci sequence: [^22_0][^22_1][^22_1][^22_2][^22_3][^22_5][^22_8]`


### Question 2 (Option 1): Write a Python program to sort given numbers using Bubble Sort algorithm.

#### Approach:

- Use Bubble Sort: compare adjacent elements, swap if needed, repeat for all iterations.
- Print sorted list.


#### Syntax Definitions:

- **For loops:** Nested
- **List:** `lst = [...]`
- **Swap statement:** `lst[j], lst[j+1] = lst[j+1], lst[j]`


#### Diagram (Text-based):

Unsorted: `[^22_5][^22_2][^22_8][^22_4]`
After sort: `[^22_2][^22_4][^22_5][^22_8]`

#### Python Code:

```python
# Functionality: Sorts a list using Bubble Sort
def bubble_sort(lst):
    """
    Sorts the list using Bubble Sort and prints the sorted list.
    """
    n = len(lst)
    for i in range(n):
        for j in range(0, n-i-1):
            if lst[j] > lst[j+1]:
                lst[j], lst[j+1] = lst[j+1], lst[j]
    print("Sorted list:", lst)

# Example usage
numbers = [5, 2, 8, 4]
bubble_sort(numbers)
```


#### Sample Input and Output:

Input: `[^22_5][^22_2][^22_8][^22_4]`
Output: `Sorted list: [^22_2][^22_4][^22_5][^22_8]`



### Question 2 (Option 2): Write a Python class named Circle constructed by a radius and two methods which will compute the area and the perimeter of a circle.

#### Approach:

- Create a `Circle` class with attribute `radius`.
- Method `area()` returns $\pi r^2$, method `perimeter()` returns $2\pi r$.
- Use `math.pi` for accuracy.


#### Syntax Definitions:

- **Class:** `class Circle:`
- **Constructor:** `def __init__(self, radius):`
- **Methods:** `def area(self):` `def perimeter(self):`


#### Diagram (Text-based):

Circle with radius `r`
Area = $\pi r^2$
Perimeter = $2 \pi r$

#### Python Code:

```python
import math

# Functionality: Circle class with area and perimeter methods
class Circle:
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return math.pi * self.radius * self.radius

    def perimeter(self):
        return 2 * math.pi * self.radius

# Example usage
c = Circle(5)
print("Area:", c.area())
print("Perimeter:", c.perimeter())
```


#### Sample Input and Output:

Input: `radius = 5`
Output:

```
Area: 78.53981633974483
Perimeter: 31.41592653589793
```


***

## SLIP 12
***
### Question 1: Write a Python script to generate and print a dictionary that contains a number between 1 and n in the form x: x*x.

_Sample: For n = 5, Expected Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}_

#### Approach:

- Accept an integer n.
- Use a loop from 1 to n.
- For each value, key is the number, value is its square.


#### Syntax Definitions:

- **Dictionary Creation:** `d = {}`
- **For Loop:** `for i in range(1, n+1): d[i] = i*i`
- **Print Dict:** `print(dict_name)`


#### Diagram (Text-based):

```
If n = 5:
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```


#### Python Code:

```python
# Functionality: Generates dictionary of numbers and their squares
def generate_square_dict(n):
    """
    Generates dictionary x: x*x for 1 to n
    """
    d = {i: i * i for i in range(1, n + 1)}
    print(d)
    return d

# Example usage
generate_square_dict(5)
```


#### Sample Input and Output:

Input: `n = 5`
Output: `{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}`


### Question 2 (Option 1): Write a Python program to implement sorting Merge Sort algorithm.

#### Approach:

- Implement merge sort recursively:
    - Divide list into halves, recursively sort each half.
    - Merge sorted halves into one sorted list.
- Print the sorted array.


#### Syntax Definitions:

- **Recursion:** Function calls itself on halves of array.
- **Merging:** Combine two sorted lists.


#### Diagram (Text-based):

Unsorted: `[^23_8][^23_6][^23_2][^23_4][^23_1]`
Sorted: `[^23_1][^23_2][^23_4][^23_6][^23_8]`

#### Python Code:

```python
# Functionality: Sorts a list using Merge Sort
def merge_sort(arr):
    """
    Recursively sorts arr using merge sort.
    """
    if len(arr) > 1:
        mid = len(arr) // 2
        left = arr[:mid]
        right = arr[mid:]

        merge_sort(left)
        merge_sort(right)

        i = j = k = 0
        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                arr[k] = left[i]
                i += 1
            else:
                arr[k] = right[j]
                j += 1
            k += 1
        while i < len(left):
            arr[k] = left[i]
            i += 1
            k += 1
        while j < len(right):
            arr[k] = right[j]
            j += 1
            k += 1

# Example usage
numbers = [8, 6, 2, 4, 1]
merge_sort(numbers)
print("Sorted array:", numbers)
```


#### Sample Input and Output:

Input: `[^23_8][^23_6][^23_2][^23_4][^23_1]`
Output: `Sorted array: [^23_1][^23_2][^23_4][^23_6][^23_8]`



### Question 2 (Option 2): Write a Python program to create a class representing a shopping cart.

_Include methods for adding and removing items, and calculating the total price._

#### Approach:

- Class with methods to add, remove items (name, price), calculate total.
- Store items in a dictionary or list.


#### Syntax Definitions:

- **Class, Methods:** `class ShoppingCart:`
- **Dict/List for items:** `self.items = {}`


#### Diagram (Text-based):

Add: Apple ₹10, Milk ₹30
Remove: Apple
Total: ₹30

#### Python Code:

```python
# Functionality: ShoppingCart class with add/remove/total
class ShoppingCart:
    def __init__(self):
        self.items = {}
    
    def add_item(self, name, price):
        self.items[name] = price
    
    def remove_item(self, name):
        if name in self.items:
            del self.items[name]
    
    def total_price(self):
        return sum(self.items.values())

# Example usage
cart = ShoppingCart()
cart.add_item("Apple", 10)
cart.add_item("Milk", 30)
print("Items:", cart.items)
cart.remove_item("Apple")
print("Items after removal:", cart.items)
print("Total price:", cart.total_price())
```


#### Sample Input and Output:

```
Items: {'Apple': 10, 'Milk': 30}
Items after removal: {'Milk': 30}
Total price: 30
```

***

## SLIP 13
***
### Question 1: Write a Python script to sort ascending and descending a dictionary by value.

#### Approach:

- Given a dictionary of key-value pairs.
- Use `sorted()` to order by value, ascending and descending.
- Print both results.


#### Syntax Definitions:

- **Dictionary:** `d = {'a': 4, 'b': 1, 'c': 3}`
- **sorted() with lambda:** `sorted(d.items(), key=lambda x: x[^24_1])`


#### Diagram (Text-based):

Example:
`{'a': 4, 'b': 1, 'c': 3}`
Ascending → `b:1, c:3, a:4`
Descending → `a:4, c:3, b:1`

#### Python Code:

```python
# Functionality: Sorts a dictionary by value in ascending and descending order
def sort_dict_by_value(d):
    """
    Sorts dictionary by value ascending and descending.
    Prints results as lists of tuples.
    """
    asc = sorted(d.items(), key=lambda x: x[^24_1])
    desc = sorted(d.items(), key=lambda x: x[^24_1], reverse=True)
    print("Ascending:", asc)
    print("Descending:", desc)

# Example usage
sample_dict = {'a': 4, 'b': 1, 'c': 3}
sort_dict_by_value(sample_dict)
```


#### Sample Input and Output:

Input: `{'a': 4, 'b': 1, 'c': 3}`
Output:

```
Ascending: [('b', 1), ('c', 3), ('a', 4)]
Descending: [('a', 4), ('c', 3), ('b', 1)]
```


### Question 2 (Option 1): Write a Python program to search an element in an integer array using Binary Search.

#### Approach:

- Binary search on sorted array: low, high, mid approach.
- Print index or not found.


#### Syntax Definitions:

- **Array:** `arr = [..]`
- **While loop:** `while low <= high`


#### Diagram (Text-based):

Array: `[^24_2][^24_5][^24_8][^24_11][^24_15]`
Search for: `8` → Found at index 2

#### Python Code:

```python
# Functionality: Binary search in array
def binary_search(arr, key):
    low, high = 0, len(arr)-1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == key:
            return mid
        elif arr[mid] < key:
            low = mid + 1
        else:
            high = mid - 1
    return -1

# Example usage
nums = [2, 5, 8, 11, 15]
target = 8
idx = binary_search(nums, target)
if idx != -1:
    print(f"Element {target} found at index {idx}")
else:
    print(f"Element {target} not found in array")
```


#### Sample Input and Output:

Array: `[^24_2][^24_5][^24_8][^24_11][^24_15]`; Search: `8`
Output: `Element 8 found at index 2`



### Question 2 (Option 2): Write a Python program to implement sorting Quick Sort algorithm.

#### Approach:

- Recursive quick sort logic: partition, then sort halves.
- Print sorted array.


#### Syntax Definitions:

- **Recursion:** Function calls itself for slices.
- **Partition:** Choose pivot, move elements.


#### Diagram (Text-based):

Unsorted: `[^24_14][^24_8][^24_2][^24_7]`
Sorted: `[^24_2][^24_7][^24_8][^24_14]`

#### Python Code:

```python
# Functionality: Quick sort
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[^24_0]
        less = [x for x in arr[1:] if x < pivot]
        greater = [x for x in arr[1:] if x >= pivot]
        return quick_sort(less) + [pivot] + quick_sort(greater)

# Example usage
numbers = [14, 8, 2, 7]
sorted_nums = quick_sort(numbers)
print("Sorted array:", sorted_nums)
```


#### Sample Input and Output:

Input: `[^24_14][^24_8][^24_2][^24_7]`
Output: `Sorted array: [^24_2][^24_7][^24_8][^24_14]`


***

## SLIP 14
***
### Question 1: Write a Python script to generate and print a dictionary that contains a number between 1 and n in the form x: x*x.

#### Approach:

- Accept an integer n.
- For each number from 1 to n, key = number, value = square.
- Store and print dictionary.


#### Syntax Definitions:

- **Dictionary Creation:** `d = {}`
- **Loop:** `for i in range(1, n+1): d[i] = i*i`
- **Print:** `print(d)`


#### Diagram:

For n=4:

```
{1: 1, 2: 4, 3: 9, 4: 16}
```


#### Python Code:

```python
# Generate dictionary with number and its square from 1 to n
def generate_square_dict(n):
    d = {i: i*i for i in range(1, n+1)}
    print(d)
    return d

# Example usage
generate_square_dict(4)
```


#### Sample Input and Output:

Input: `n = 4`
Output: `{1: 1, 2: 4, 3: 9, 4: 16}`


### Question 2 (Option 1): Write a Python program to implement sorting Insertion Sort algorithm.

#### Approach:

- Insertion sort: Traverse from second item, insert left for each, moving greater ones right.
- Print sorted array.


#### Syntax Definitions:

- **Loop:** For i in range(1, len(arr))
- **Insert:** While arr[j] > key


#### Diagram:

Unsorted: `[^25_8][^25_4][^25_1]` → Sorted: `[^25_1][^25_4][^25_8]`

#### Python Code:

```python
# Sort list using Insertion Sort algorithm
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i-1
        while j >= 0 and arr[j] > key:
            arr[j+1] = arr[j]
            j -= 1
        arr[j+1] = key
    print("Sorted array:", arr)

# Example usage
numbers = [8, 4, 1]
insertion_sort(numbers)
```


#### Sample Input and Output:

Input: `[^25_8][^25_4][^25_1]`
Output: `Sorted array: [^25_1][^25_4][^25_8]`


### Question 2 (Option 2): Write a program to calculate indegree of a graph.

#### Approach:

- Adjacency matrix: rows=source, columns=destination.
- Indegree for node: count of 1s in column.


#### Syntax:

- Sum column elements: `sum(row[j] for row in matrix)`


#### Diagram:

Adjacency matrix:

```
0 1 0
1 0 1
0 1 0
Indegrees: Node 0: 1, Node 1: 2, Node 2: 1
```


#### Python Code:

```python
# Calculate indegree of each node in adjacency matrix
def calculate_indegree(matrix):
    n = len(matrix)
    for col in range(n):
        indegree = sum(matrix[row][col] for row in range(n))
        print(f"Indegree of node {col}: {indegree}")

# Example usage
adj_matrix = [
    [0,1,0],
    [1,0,1],
    [0,1,0]
]
calculate_indegree(adj_matrix)
```


#### Sample Input and Output:

Input:

```
0 1 0
1 0 1
0 1 0
```

Output:

```
Indegree of node 0: 1
Indegree of node 1: 2
Indegree of node 2: 1
```

***

## SLIP 15
***
### Question 1: Write a Python program to combine two dictionaries adding values for common keys.

_Sample: d1 = {'a': 100, 'b': 200, 'c': 300}; d2 = {'a': 300, 'b': 200, 'd': 400}_
_Expected output: Counter({'a': 400, 'b': 400, 'd': 400, 'c': 300})_

#### Approach:

- Use `collections.Counter` (or manual loop) to add values of common keys.
- For non-intersecting keys, retain original value.


#### Syntax Definitions:

- **Counter addition:** `Counter(d1) + Counter(d2)`
- **Dictionary:** `d = {key: value, ...}`


#### Diagram:

```
d1: a:100, b:200, c:300
d2: a:300, b:200, d:400
Result: a:400, b:400, c:300, d:400
```


#### Python Code:

```python
from collections import Counter

# Functionality: Combines two dictionaries by adding values for common keys
def combine_dictionaries(d1, d2):
    result = Counter(d1) + Counter(d2)
    print("Combined dictionary:", result)
    return result

# Example usage
d1 = {'a': 100, 'b': 200, 'c': 300}
d2 = {'a': 300, 'b': 200, 'd': 400}
combine_dictionaries(d1, d2)
```


#### Sample Input and Output:

Input:

```
d1 = {'a': 100, 'b': 200, 'c': 300}
d2 = {'a': 300, 'b': 200, 'd': 400}
```

Output: `Counter({'a': 400, 'b': 400, 'd': 400, 'c': 300})`



### Question 2 (Option 1): Write a program to calculate outdegree of a graph using adjacency matrix.

#### Approach:

- Outdegree = number of outgoing edges from a node (sum of row).
- For each row in the matrix, sum its elements.


#### Syntax Definitions:

- **Matrix sum:** `sum(matrix[i])`
- **For loop over rows:** `for i in range(len(matrix))`


#### Diagram:

Adjacency matrix example:

```
0 1 1
0 0 0
1 1 0
Row sums → Outdegrees: 2, 0, 2
```


#### Python Code:

```python
# Functionality: Calculates outdegree for each node using adjacency matrix
def calculate_outdegree(matrix):
    for i, row in enumerate(matrix):
        print(f"Outdegree of node {i}: {sum(row)}")

# Example usage
adj_matrix = [
    [0, 1, 1],
    [0, 0, 0],
    [1, 1, 0]
]
calculate_outdegree(adj_matrix)
```


#### Sample Input and Output:

Input:

```
0 1 1
0 0 0
1 1 0
```

Output:

```
Outdegree of node 0: 2
Outdegree of node 1: 0
Outdegree of node 2: 2
```


### Question 2 (Option 2): Write a Python class named Rectangle constructed by a length and width and two methods which will compute the area and perimeter.

#### Approach:

- Define class Rectangle with constructor for length and width.
- Method for area: \$ length \times width \$.
- Method for perimeter: \$ 2 \times (length + width) \$.


#### Syntax Definitions:

- **Class:** `class Rectangle:`
- **Constructor:** `def __init__(self, length, width):`


#### Diagram:

```
Length 4, Width 5:
Area = 20
Perimeter = 18
```


#### Python Code:

```python
# Functionality: Rectangle class with area and perimeter methods
class Rectangle:
    def __init__(self, length, width):
        self.length = length
        self.width = width

    def area(self):
        return self.length * self.width

    def perimeter(self):
        return 2 * (self.length + self.width)

# Example usage
rect = Rectangle(4, 5)
print("Area:", rect.area())
print("Perimeter:", rect.perimeter())
```


#### Sample Input and Output:

Input: `length = 4, width = 5`
Output:

```
Area: 20
Perimeter: 18
```
***

## SLIP 16
***
### Question 1: Write a Python program to create a list of tuples with the first element as the number and second element as the square of the number, also display original list in reverse. (10 marks)

#### Approach:

- Use a list comprehension to create tuples: `(num, num*num)` for numbers in range.
- Print the list.
- Print the list in reverse order using slicing (`[::-1]`).


#### Syntax Definitions:

- **List comprehension:** `[(i, i*i) for i in range(1, n+1)]`
- **Reverse list:** `lst[::-1]`
- **Tuple:** `(number, square)`


#### Diagram:

For n = 5,
List: `[(1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]`
Reversed: `[(5, 25), (4, 16), (3, 9), (2, 4), (1, 1)]`

#### Python Code:

```python
# List of tuples with number and its square, then reversed
def tuple_square_list(n):
    lst = [(i, i*i) for i in range(1, n+1)]
    print("List:", lst)
    print("Reversed list:", lst[::-1])

# Example usage
tuple_square_list(5)
```


#### Sample Input and Output:

Input: n = 5
Output:

```
List: [(1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
Reversed list: [(5, 25), (4, 16), (3, 9), (2, 4), (1, 1)]
```


### Question 2 (Option 1): Write a python code for static implementation of stack. (20 marks)

#### Approach:

- Implement stack operations using a list with fixed size.
- Include push, pop, isEmpty, isFull, display methods.
- Prevent overflow/underflow.


#### Syntax Definitions:

- **Stack list:** `stack = [None]*size`
- **Top pointer:** `top = -1` (initially)
- **Methods:** push, pop, isEmpty, isFull


#### Diagram:

Stack size = 5:
Push: 10, 20
Stack: `[10, 20, None, None, None]`, top=1
Pop:
Stack: `[10, None, None, None, None]`, top=0

#### Python Code:

```python
# Static stack implementation
class StaticStack:
    def __init__(self, size):
        self.size = size
        self.stack = [None]*size
        self.top = -1

    def is_empty(self):
        return self.top == -1

    def is_full(self):
        return self.top == self.size - 1

    def push(self, item):
        if self.is_full():
            print("Stack Overflow")
        else:
            self.top += 1
            self.stack[self.top] = item
            print(f"Pushed {item}")

    def pop(self):
        if self.is_empty():
            print("Stack Underflow")
            return None
        else:
            item = self.stack[self.top]
            self.stack[self.top] = None
            self.top -= 1
            print(f"Popped {item}")
            return item

    def display(self):
        print("Stack:", self.stack[:self.top+1])

# Example usage
s = StaticStack(5)
s.push(10)
s.push(20)
s.display()
s.pop()
s.display()
```


#### Sample Input and Output:

Push: 10, 20
Output:

```
Pushed 10
Pushed 20
Stack: [10, 20]
Popped 20
Stack: [^27_10]
```


### Question 2 (Option 2): Write a Python program for Evaluation of postfix expression. (20 marks)

#### Approach:

- Tokenize the expression.
- Use a stack: if number push, if operator pop two, evaluate, push result.
- Print result of evaluation.


#### Syntax Definitions:

- **Split string:** `expr.split()`
- **Stack:** List `.append()` and `.pop()`


#### Diagram:

Expression: `2 3 1 * + 9 -`
Step:
Push 2, Push 3, Push 1, Pop 1\&3, Push 3\*1=3, Pop 3\&2, Push 2+3=5, Push 9, Pop 9\&5, Push 5-9=-4
Result: -4

#### Python Code:

```python
# Postfix expression evaluation
def eval_postfix(expr):
    stack = []
    tokens = expr.split()
    for token in tokens:
        if token.isdigit():
            stack.append(int(token))
        else:
            b = stack.pop()
            a = stack.pop()
            if token == '+':
                stack.append(a+b)
            elif token == '-':
                stack.append(a-b)
            elif token == '*':
                stack.append(a*b)
            elif token == '/':
                stack.append(a/b)
    result = stack.pop()
    print("Result:", result)
    return result

# Example usage
eval_postfix("2 3 1 * + 9 -")
```


#### Sample Input and Output:

Input: `"2 3 1 * + 9 -"`
Output: `Result: -4`

***

## SLIP 17
***
### Question 1: Write a Python Program to Calculate the Average of Numbers in a Given List.

#### Approach:

- Accept a list of numbers.
- Use `sum()` to add all and divide by `len()` for average.
- Print the result, labeled.


#### Syntax Definitions:

- **List:** `lst = [num1, num2, ...]`
- **Sum \& Avg:** `average = sum(lst) / len(lst)`


#### Diagram:

List: `[^28_10][^28_20][^28_30][^28_40][^28_50]`
Average: `(10 + 20 + 30 + 40 + 50) / 5 = 30.0`

#### Python Code:

```python
def calculate_average(lst):
    average = sum(lst) / len(lst)
    print("Average:", average)
    return average

# Example usage
numbers = [10, 20, 30, 40, 50]
calculate_average(numbers)
```


#### Sample Input and Output:

Input: `[^28_10][^28_20][^28_30][^28_40][^28_50]`
Output: `Average: 30.0`

### Question 2 (Option 1): Write a python code for static implementation of queue.

#### Approach:

- Use a list of fixed size for queue.
- Implement `enqueue`, `dequeue`, `isEmpty`, `isFull`, `display`.
- Maintain `front` and `rear` pointers.


#### Syntax Definitions:

- **List:** `queue = [None]*size`
- **Pointers:** `front`, `rear`


#### Diagram:

Queue size 5; Enqueue: 10, 20
Queue: `[10, 20, None, None, None]` (front=0, rear=1).

#### Python Code:

```python
class StaticQueue:
    def __init__(self, size):
        self.size = size
        self.queue = [None]*size
        self.front = 0
        self.rear = -1

    def is_empty(self):
        return self.front > self.rear

    def is_full(self):
        return self.rear == self.size - 1

    def enqueue(self, item):
        if self.is_full():
            print("Queue Overflow")
        else:
            self.rear += 1
            self.queue[self.rear] = item
            print(f"Enqueued {item}")

    def dequeue(self):
        if self.is_empty():
            print("Queue Underflow")
        else:
            item = self.queue[self.front]
            self.queue[self.front] = None
            self.front += 1
            print(f"Dequeued {item}")
            return item

    def display(self):
        print("Queue:", self.queue[self.front:self.rear+1])

# Example usage
q = StaticQueue(5)
q.enqueue(10)
q.enqueue(20)
q.display()
q.dequeue()
q.display()
```


#### Sample Input and Output:

Enqueue: 10, 20
Output:

```
Enqueued 10
Enqueued 20
Queue: [10, 20]
Dequeued 10
Queue: [^28_20]
```


### Question 2 (Option 2): Write a python code for dynamic implementation of Stack to perform following operations Init, Push, Pop, IsEmpty, IsFull.

#### Approach:

- Use Python list for a dynamic stack; set max size for `is_full`.
- Implement methods for initialization, push, pop, is_empty, is_full.


#### Syntax Definitions:

- **List stack:** `stack = []`
- **Methods:** push, pop, isEmpty, isFull


#### Diagram:

Max size=3; Push: 5, 10; Pop: 10

#### Python Code:

```python
class DynamicStack:
    def __init__(self, max_size):
        self.stack = []
        self.max_size = max_size

    def is_empty(self):
        return len(self.stack) == 0

    def is_full(self):
        return len(self.stack) == self.max_size

    def push(self, item):
        if self.is_full():
            print("Stack Overflow")
        else:
            self.stack.append(item)
            print(f"Pushed {item}")

    def pop(self):
        if self.is_empty():
            print("Stack Underflow")
            return None
        else:
            item = self.stack.pop()
            print(f"Popped {item}")
            return item

    def display(self):
        print("Stack:", self.stack)

# Example usage
s = DynamicStack(3)
s.push(5)
s.push(10)
s.display()
s.pop()
s.display()
```


#### Sample Input and Output:

Push: 5, 10
Output:

```
Pushed 5
Pushed 10
Stack: [5, 10]
Popped 10
Stack: [^28_5]
```


***

## SLIP 19
***
### Question 1: Write a Python program to get the 5th element from front and 5th element from last of a tuple. (10 marks)

#### Approach:

- Use tuple indexing: 5th from front is index 4, 5th from last is index -5.
- Use checks for tuple length to avoid errors.


#### Syntax Definitions:

- **Tuple:** `tup = (value1, ..., valueN)`
- **Indexing:** `tup[^29_4]` and `tup[-5]`


#### Diagram:

Example: `(11, 22, 33, 44, 55, 66, 77, 88)`

```
5th from front: 55
5th from last: 44
```


#### Python Code:

```python
def fifth_elements(tup):
    if len(tup) >= 5:
        print("5th element from front:", tup[^29_4])
        print("5th element from last:", tup[-5])
    else:
        print("Tuple does not have enough elements.")

# Example usage
tuple1 = (11, 22, 33, 44, 55, 66, 77, 88)
fifth_elements(tuple1)
```


#### Sample Input and Output:

Input: `(11, 22, 33, 44, 55, 66, 77, 88)`
Output:

```
5th element from front: 55
5th element from last: 44
```


### Question 2 (Option 1): Write a python code for simple implementation of priority queue. (20 marks)

#### Approach:

- Use list of tuples `(priority, value)` or dictionary.
- Insert elements such that highest priority is served first (lowest int).
- Use sorting or `heapq`.


#### Syntax Definitions:

- **List of tuples:** `pq = []`
- **Insert:** `pq.append((priority, value))`
- **Sort:** `pq.sort()`
- **Pop/serve:** `pq.pop(0)`


#### Diagram:

Queue: `[(2, 'apple'), (1, 'banana'), (3, 'cherry')]`
Sorted: `[(1, 'banana'), (2, 'apple'), (3, 'cherry')]`

#### Python Code:

```python
# Simple priority queue implementation using list
class PriorityQueue:
    def __init__(self):
        self.pq = []
    
    def insert(self, priority, value):
        self.pq.append((priority, value))
        self.pq.sort()  # keeps lowest priority first

    def serve(self):
        if self.pq:
            print("Serving:", self.pq.pop(0))
        else:
            print("Queue is empty.")

    def display(self):
        print("Priority Queue:", self.pq)

# Example usage
pq = PriorityQueue()
pq.insert(2, 'apple')
pq.insert(1, 'banana')
pq.insert(3, 'cherry')
pq.display()
pq.serve()
pq.display()
```


#### Sample Input and Output:

Input: Insert `(2, 'apple'), (1, 'banana'), (3, 'cherry')`
Output:

```
Priority Queue: [(1, 'banana'), (2, 'apple'), (3, 'cherry')]
Serving: (1, 'banana')
Priority Queue: [(2, 'apple'), (3, 'cherry')]
```


### Question 2 (Option 2): Write a python code for dynamic implementation of Stack to perform following operations Init, Push, Pop, IsEmpty, IsFull. (20 marks)

#### Approach:

- Use Python list, set max_size.
- Implement methods for initialization, push, pop, is_empty, is_full.


#### Syntax Definitions:

- **List stack:** `self.stack = []`
- **Size:** `self.max_size`


#### Diagram:

Max size 3; Push: 11, 22, 33; Pop: 33

#### Python Code:

```python
class DynamicStack:
    def __init__(self, max_size):
        self.stack = []
        self.max_size = max_size

    def is_empty(self):
        return len(self.stack) == 0

    def is_full(self):
        return len(self.stack) == self.max_size

    def push(self, val):
        if self.is_full():
            print("Stack Overflow")
        else:
            self.stack.append(val)
            print(f"Pushed {val}")

    def pop(self):
        if self.is_empty():
            print("Stack Underflow")
        else:
            val = self.stack.pop()
            print(f"Popped {val}")
            return val

    def display(self):
        print("Stack:", self.stack)

# Example usage
s = DynamicStack(3)
s.push(11)
s.push(22)
s.push(33)
s.display()
s.pop()
s.display()
```


#### Sample Input and Output:

Push 11, 22, 33; Pop 33
Output:

```
Pushed 11
Pushed 22
Pushed 33
Stack: [11, 22, 33]
Popped 33
Stack: [11, 22]
```
***

## SLIP 20
***
### Question 1: Write a program to display the following pattern.

_1 2 3 4 5 6 7 8 9 10_

#### Approach:

- Use a for loop to print numbers from 1 to 10, space-separated.


#### Syntax Definitions:

- **For loop:** `for i in range(1, 11):`
- **Print with end:** `print(i, end=' ')`


#### Diagram (Text-based):

Pattern:
`1 2 3 4 5 6 7 8 9 10`

#### Python Code:

```python
def print_pattern():
    for i in range(1, 11):
        print(i, end=' ')
    print()  # for newline

# Example usage
print_pattern()
```


#### Sample Input and Output:

Output: `1 2 3 4 5 6 7 8 9 10`


### Question 2 (Option 1): Write a code for static stack implementation in Python.

#### Approach:

- Fixed-size list as stack, with top pointer.
- Implement `push`, `pop`, `isEmpty`, `isFull`, `display`.


#### Syntax Definitions:

- **List:** `stack = [None]*size`
- **Top:** `top = -1`


#### Diagram:

Stack size 5; Push: 2, 4, 6
Stack: `[^30_2][^30_4][^30_6]`, top=2

#### Python Code:

```python
class StaticStack:
    def __init__(self, size):
        self.size = size
        self.stack = [None]*size
        self.top = -1

    def is_empty(self):
        return self.top == -1

    def is_full(self):
        return self.top == self.size - 1

    def push(self, item):
        if self.is_full():
            print("Stack Overflow")
        else:
            self.top += 1
            self.stack[self.top] = item
            print(f"Pushed {item}")

    def pop(self):
        if self.is_empty():
            print("Stack Underflow")
        else:
            item = self.stack[self.top]
            self.stack[self.top] = None
            self.top -= 1
            print(f"Popped {item}")

    def display(self):
        print("Stack:", self.stack[:self.top+1])

# Example usage
s = StaticStack(5)
s.push(2)
s.push(4)
s.push(6)
s.display()
s.pop()
s.display()
```


#### Sample Input and Output:

Push: 2, 4, 6
Output:

```
Pushed 2
Pushed 4
Pushed 6
Stack: [2, 4, 6]
Popped 6
Stack: [2, 4]
```



### Question 2 (Option 2): Write a python code for dynamic implementation of linear Queue to perform following operations init, enqueue, dequeue, isEmpty, isFull.

#### Approach:

- Use a Python list with max_size.
- Methods: initialization, enqueue, dequeue, isEmpty, isFull.


#### Syntax Definitions:

- **List Queue:** `self.queue = []`
- **Methods:** enqueue, dequeue, isEmpty, isFull


#### Diagram:

Max size 3; Enqueue: 11, 22, 33; Dequeue: 11

#### Python Code:

```python
class DynamicQueue:
    def __init__(self, max_size):
        self.queue = []
        self.max_size = max_size

    def is_empty(self):
        return len(self.queue) == 0

    def is_full(self):
        return len(self.queue) == self.max_size

    def enqueue(self, item):
        if self.is_full():
            print("Queue Overflow")
        else:
            self.queue.append(item)
            print(f"Enqueued {item}")

    def dequeue(self):
        if self.is_empty():
            print("Queue Underflow")
        else:
            item = self.queue.pop(0)
            print(f"Dequeued {item}")
            return item

    def display(self):
        print("Queue:", self.queue)

# Example usage
q = DynamicQueue(3)
q.enqueue(11)
q.enqueue(22)
q.enqueue(33)
q.display()
q.dequeue()
q.display()
```


#### Sample Input and Output:

Enqueue: 11, 22, 33; Dequeue: 11
Output:

```
Enqueued 11
Enqueued 22
Enqueued 33
Queue: [11, 22, 33]
Dequeued 11
Queue: [22, 33]
```
***

## SLIP 21
***
### Question 1: Write a python program which accepts 6 integer values and prints DUPLICATES if any of the values entered are duplicates otherwise it prints ALL UNIQUE.

_Example: Let 6 integers are 32, 10, 45, 90, 45, 6 then output DUPLICATES to be printed._

#### Approach:

- Accept 6 integers as a list.
- Use set to find unique elements.
- If set length < 6, duplicates exist.


#### Syntax:

- **List:** `lst = [int(input(...)) for _ in range(6)]`
- **Set:** `set(lst)`


#### Python Code:

```python
def check_duplicates():
    nums = [int(input(f"Enter integer {i+1}: ")) for i in range(6)]
    if len(set(nums)) < 6:
        print("DUPLICATES")
    else:
        print("ALL UNIQUE")

# Test version
nums = [32, 10, 45, 90, 45, 6]
print("DUPLICATES" if len(set(nums)) < 6 else "ALL UNIQUE")
```


#### Sample Input and Output:

Input: `32, 10, 45, 90, 45, 6`
Output: `DUPLICATES`

***

### Question 2 (Option 1): Show the static implementation of queue using Python.

#### Approach:

- Fixed size list, front/rear pointers.
- Implement enqueue, dequeue, is_empty, is_full, display.


#### Syntax:

- **List:** `queue = [None]*size`
- **Pointers:** `front=0`, `rear=-1`


#### Python Code:

```python
class StaticQueue:
    def __init__(self, size):
        self.size = size
        self.queue = [None]*size
        self.front = 0
        self.rear = -1

    def is_empty(self):
        return self.front > self.rear

    def is_full(self):
        return self.rear == self.size-1

    def enqueue(self, val):
        if self.is_full():
            print("Queue Overflow")
        else:
            self.rear += 1
            self.queue[self.rear] = val
            print(f"Enqueued {val}")

    def dequeue(self):
        if self.is_empty():
            print("Queue Underflow")
        else:
            val = self.queue[self.front]
            self.queue[self.front] = None
            self.front += 1
            print(f"Dequeued {val}")

    def display(self):
        print("Queue:", self.queue[self.front:self.rear+1])

# Example usage
q = StaticQueue(5)
q.enqueue(11)
q.enqueue(22)
q.display()
q.dequeue()
q.display()
```


#### Sample Input and Output:

Enqueue: 11, 22
Output:

```
Enqueued 11
Enqueued 22
Queue: [11, 22]
Dequeued 11
Queue: [^31_22]
```


***

### Question 2 (Option 2): Write a python code for Implementation of an algorithm that reverses string of characters using stack and checks whether a string is a palindrome or not.

#### Approach:

- Use stack (list).
- For reversal: push chars, then pop.
- Check if original equals reversed for palindrome.


#### Syntax:

- **Push/pop:** `.append(char)`/`.pop()`


#### Python Code:

```python
def reverse_string_stack(s):
    stack = []
    for char in s:
        stack.append(char)
    rev = ''.join(stack.pop() for _ in range(len(stack)))
    print("Reversed string:", rev)
    if s == rev:
        print("Palindrome!")
    else:
        print("Not a palindrome.")

# Example usage
reverse_string_stack("madam")
reverse_string_stack("python")
```


#### Sample Input and Output:

Input: `madam`
Output:

```
Reversed string: madam
Palindrome!
```

Input: `python`
Output:

```
Reversed string: nohtyp
Not a palindrome.
```

***

## SLIP 22
***
### Question 1: Write a Python program to find repeated items in a tuple. (10 marks)

#### Approach:

- Iterate through tuple, use set or dictionary to count item frequencies.
- Collect items that occur more than once.


#### Syntax:

- **Tuple:** `tup = (value1, ..., valueN)`
- **Set/dict:** `seen`, `repeats`


#### Python Code:

```python
def find_repeated(tup):
    seen = set()
    repeats = set()
    for item in tup:
        if item in seen:
            repeats.add(item)
        else:
            seen.add(item)
    print("Repeated items:", tuple(repeats))

# Example usage
tuple1 = (1, 2, 3, 2, 4, 1, 5)
find_repeated(tuple1)
```


#### Sample Input and Output:

Input: `(1, 2, 3, 2, 4, 1, 5)`
Output: `Repeated items: (1, 2)`

***

### Question 2 (Option 1): Show the static implementation of stack using python. (20 marks)

#### Approach:

- Fixed-size list, top pointer, implement push/pop/isEmpty/isFull/display.


#### Syntax:

- **List:** `stack = [None]*size`
- **Top:** `top = -1`


#### Python Code:

```python
class StaticStack:
    def __init__(self, size):
        self.size = size
        self.stack = [None]*size
        self.top = -1

    def is_empty(self):
        return self.top == -1

    def is_full(self):
        return self.top == self.size - 1

    def push(self, item):
        if self.is_full():
            print("Stack Overflow")
        else:
            self.top += 1
            self.stack[self.top] = item
            print(f"Pushed {item}")

    def pop(self):
        if self.is_empty():
            print("Stack Underflow")
        else:
            item = self.stack[self.top]
            self.stack[self.top] = None
            self.top -= 1
            print(f"Popped {item}")

    def display(self):
        print("Stack:", self.stack[:self.top+1])

# Example usage
s = StaticStack(3)
s.push(10)
s.push(20)
s.display()
s.pop()
s.display()
```


#### Sample Input and Output:

Push: 10, 20
Output:

```
Pushed 10
Pushed 20
Stack: [10, 20]
Popped 20
Stack: [^32_10]
```


***

### Question 2 (Option 2): Write a python code for implementation of circular queue. (20 marks)

#### Approach:

- Fixed-size list, front/rear pointers, wrap-around logic (modulo size).
- Implement enqueue, dequeue, isEmpty, isFull, display.


#### Syntax:

- **List:** `queue = [None]*size`
- **Modulo:** `(pointer + 1) % size`


#### Python Code:

```python
class CircularQueue:
    def __init__(self, size):
        self.size = size
        self.queue = [None]*size
        self.front = -1
        self.rear = -1

    def is_empty(self):
        return self.front == -1

    def is_full(self):
        return (self.rear + 1) % self.size == self.front

    def enqueue(self, item):
        if self.is_full():
            print("Queue Overflow")
        else:
            if self.front == -1:
                self.front = self.rear = 0
            else:
                self.rear = (self.rear + 1) % self.size
            self.queue[self.rear] = item
            print(f"Enqueued {item}")

    def dequeue(self):
        if self.is_empty():
            print("Queue Underflow")
        else:
            item = self.queue[self.front]
            self.queue[self.front] = None
            if self.front == self.rear:
                self.front = self.rear = -1
            else:
                self.front = (self.front + 1) % self.size
            print(f"Dequeued {item}")

    def display(self):
        print("Queue:", self.queue)

# Example usage
cq = CircularQueue(3)
cq.enqueue(10)
cq.enqueue(20)
cq.enqueue(30)
cq.display()
cq.dequeue()
cq.display()
```


#### Sample Input and Output:

Enqueue: 10, 20, 30; Dequeue: 10
Output:

```
Enqueued 10
Enqueued 20
Enqueued 30
Queue: [10, 20, 30]
Dequeued 10
Queue: [None, 20, 30]
```


***

## SLIP 24
***
### Question 1: Write a Python Program to Calculate the Sum of Numbers in a List. (10 Marks)

#### Approach:

- Input/define list of numbers.
- Use `sum()` function or a loop to add all numbers.
- Print the result.


#### Syntax:

- **List:** `lst = [num1, num2, ...]`
- **sum:** `sum(lst)`


#### Python Code:

```python
def list_sum(lst):
    total = sum(lst)
    print("Sum of numbers:", total)
    return total

# Example usage
numbers = [3, 5, 7, 2]
list_sum(numbers)
```


#### Sample Output:

```
Sum of numbers: 17
```


***

### Question 2 (Option 1): Write a program to search an element using Binary Search. (20 Marks)

#### Approach:

- List must be sorted.
- Use binary search logic: low/high/mid, repeat until found/not found.


#### Syntax:

- **List:** `lst = [..]`
- **While loop:** `while low <= high`


#### Python Code:

```python
def binary_search(lst, key):
    low, high = 0, len(lst)-1
    while low <= high:
        mid = (low + high)//2
        if lst[mid] == key:
            return mid
        elif lst[mid] < key:
            low = mid+1
        else:
            high = mid-1
    return -1

# Example usage
numbers = [2, 5, 9, 12, 15]
key = 9
idx = binary_search(numbers, key)
if idx != -1:
    print(f"Element {key} found at index {idx}")
else:
    print(f"Element {key} not found in list")
```


#### Sample Output:

```
Element 9 found at index 2
```


***

### Question 2 (Option 2): Write a Python program to calculate outdegree of a graph using adjacency matrix. (20 Marks)

#### Approach:

- Each row of adjacency matrix represents outgoing edges.
- Sum each row to compute outdegree of each node.


#### Syntax:

- **Matrix:** `matrix[row]`
- **Sum:** `sum(matrix[row])`


#### Python Code:

```python
def calculate_outdegree(matrix):
    n = len(matrix)
    for row in range(n):
        outdeg = sum(matrix[row])
        print(f"Outdegree of node {row}: {outdeg}")

# Example usage
adj_matrix = [
    [0, 1, 0],
    [1, 0, 1],
    [0, 0, 0]
]
calculate_outdegree(adj_matrix)
```


#### Sample Output:

```
Outdegree of node 0: 1
Outdegree of node 1: 2
Outdegree of node 2: 0
```


***

## SLIP 23
***
### Question 1: Write a Python Program to Calculate the Average of Numbers in a Given List. (10 marks)

#### Approach:

- Input or define a list of numbers.
- Use `sum()` and `len()` to calculate the average.
- Print labeled result.


#### Syntax:

- **List:** `lst = [num1, num2, ...]`
- **Average:** `avg = sum(lst)/len(lst)`


#### Python Code:

```python
def calculate_average(lst):
    avg = sum(lst) / len(lst)
    print("Average:", avg)
    return avg

# Example usage
numbers = [10, 20, 30, 40, 50]
calculate_average(numbers)
```


#### Sample Output:

```
Average: 30.0
```


***

### Question 2 (Option 1): Write the code for static queue implementation in Python. (20 marks)

#### Approach:

- Use fixed-size list, front and rear pointers.
- Implement enqueue, dequeue, is_empty, is_full, display.


#### Syntax:

- **List:** `queue = [None]*size`
- **Pointers:** `front=0`, `rear=-1`


#### Python Code:

```python
class StaticQueue:
    def __init__(self, size):
        self.size = size
        self.queue = [None]*size
        self.front = 0
        self.rear = -1

    def is_empty(self):
        return self.front > self.rear

    def is_full(self):
        return self.rear == self.size - 1

    def enqueue(self, val):
        if self.is_full():
            print("Queue Overflow")
        else:
            self.rear += 1
            self.queue[self.rear] = val
            print(f"Enqueued {val}")

    def dequeue(self):
        if self.is_empty():
            print("Queue Underflow")
        else:
            val = self.queue[self.front]
            self.queue[self.front] = None
            self.front += 1
            print(f"Dequeued {val}")

    def display(self):
        print("Queue:", self.queue[self.front:self.rear+1])

# Example usage
q = StaticQueue(5)
q.enqueue(11)
q.enqueue(22)
q.display()
q.dequeue()
q.display()
```


#### Sample Output:

```
Enqueued 11
Enqueued 22
Queue: [11, 22]
Dequeued 11
Queue: [^34_22]
```


***

### Question 2 (Option 2): Write a python code for Implementation of an algorithm that reverses string of characters using stack and checks whether a string is a palindrome or not. (20 marks)

#### Approach:

- Push characters on stack, pop and form reversed string.
- Compare with original to check palindrome.


#### Syntax:

- **List as stack:** `stack = []`
- **Push:** `stack.append(char)`
- **Pop:** `stack.pop()`


#### Python Code:

```python
def reverse_and_check_palindrome(s):
    stack = []
    for char in s:
        stack.append(char)
    rev = ''.join(stack.pop() for _ in range(len(stack)))
    print("Reversed string:", rev)
    if rev == s:
        print("Palindrome!")
    else:
        print("Not a palindrome.")

# Example usage
reverse_and_check_palindrome("level")
reverse_and_check_palindrome("python")
```


#### Sample Output:

For `"level"`:

```
Reversed string: level
Palindrome!
```

For `"python"`:

```
Reversed string: nohtyp
Not a palindrome.
```


***

## SLIP 25
***
### Question 1: Write a python program to get the number of occurrences of specified elements in an array. (10 Marks)

#### Approach:

- Accept/define an array/list.
- Accept the target element to count.
- Use `count()` method to find occurrences.


#### Syntax:

- **List:** `arr = [num1, num2, ...]`
- **Count:** `arr.count(x)`


#### Python Code:

```python
def count_occurrences(arr, x):
    count = arr.count(x)
    print(f"Number of occurrences of {x}:", count)
    return count

# Example usage
numbers = [2, 4, 2, 5, 2, 8]
count_occurrences(numbers, 2)
```


#### Sample Output:

```
Number of occurrences of 2: 3
```


***

### Question 2 (Option 1): Write a Python program to sort given numbers using Bubble Sort algorithms. (20 Marks)

#### Approach:

- Use bubble sort: repeatedly check pairs and swap if needed.


#### Syntax:

- **List:** `arr`
- **Bubble sort:** Nested loops


#### Python Code:

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    print("Sorted array:", arr)
    return arr

# Example usage
numbers = [7, 4, 9, 2, 6]
bubble_sort(numbers)
```


#### Sample Output:

```
Sorted array: [2, 4, 6, 7, 9]
```


***

### Question 2 (Option 2): Write a Python class named Circle constructed by a radius and two methods which will compute the area and the perimeter of a circle. (20 Marks)

#### Approach:

- Create Circle class with radius.
- Method for area: \$ \pi r^2 \$
- Method for perimeter: \$ 2\pi r \$


#### Syntax:

- **Class:** `class Circle:`
- **Math import:** `import math`


#### Python Code:

```python
import math

class Circle:
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        return math.pi * self.radius ** 2
    
    def perimeter(self):
        return 2 * math.pi * self.radius

# Example usage
c = Circle(7)
print("Area:", c.area())
print("Perimeter:", c.perimeter())
```


#### Sample Output:

```
Area: 153.93804002589985
Perimeter: 43.982297150257104
```


***


