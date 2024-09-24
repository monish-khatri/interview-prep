### **1. Reverse a String**

**Problem**: Write a PHP function to reverse a given string.

**Solution**:
```php
function reverseString($str) {
    return strrev($str);
}

echo reverseString("hello"); // Output: "olleh"
```

---

### **2. Check if a String is a Palindrome**

**Problem**: Write a PHP function to check if a given string is a palindrome (reads the same forward and backward).

**Solution**:
```php
function isPalindrome($str) {
    $str = strtolower(preg_replace('/[^a-z0-9]+/', '', $str)); // Remove non-alphanumeric characters
    return $str === strrev($str);
}

echo isPalindrome("A man, a plan, a canal: Panama"); // Output: true
```

---

### **3. Find the Maximum Element in an Array**

**Problem**: Write a function to find the maximum element in a given array.

**Solution**:
```php
function findMax($arr) {
    return max($arr);
}

$arr = [3, 1, 5, 2, 7, 4];
echo findMax($arr); // Output: 7
```

---

### **4. Find the First Non-Repeated Character in a String**

**Problem**: Write a function to find the first non-repeated character in a given string.

**Solution**:
```php
function firstNonRepeatedCharacter($str) {
    $charCount = array_count_values(str_split($str));
    foreach (str_split($str) as $char) {
        if ($charCount[$char] == 1) {
            return $char;
        }
    }
    return null;
}

echo firstNonRepeatedCharacter("swiss"); // Output: "w"
```

---

### **5. Implement Binary Search**

**Problem**: Implement binary search for a sorted array in PHP.

**Solution**:
```php
function binarySearch($arr, $target) {
    $low = 0;
    $high = count($arr) - 1;
    
    while ($low <= $high) {
        $mid = intdiv($low + $high, 2);
        
        if ($arr[$mid] == $target) {
            return $mid;
        } elseif ($arr[$mid] < $target) {
            $low = $mid + 1;
        } else {
            $high = $mid - 1;
        }
    }
    
    return -1; // Target not found
}

$arr = [1, 3, 5, 7, 9, 11];
echo binarySearch($arr, 7); // Output: 3
```

---

### **6. Merge Two Sorted Arrays**

**Problem**: Write a PHP function to merge two sorted arrays into one sorted array.

**Solution**:
```php
function mergeSortedArrays($arr1, $arr2) {
    return array_merge(array_merge($arr1, $arr2), []);
}

$arr1 = [1, 3, 5];
$arr2 = [2, 4, 6];
$result = mergeSortedArrays($arr1, $arr2);
print_r($result); // Output: [1, 2, 3, 4, 5, 6]
```

---

### **7. Implement a Queue using Two Stacks**

**Problem**: Implement a queue using two stacks (LIFO behavior). 

**Solution**:
```php
class QueueUsingStacks {
    private $stack1 = [];
    private $stack2 = [];
    
    public function enqueue($item) {
        array_push($this->stack1, $item);
    }
    
    public function dequeue() {
        if (empty($this->stack2)) {
            while (!empty($this->stack1)) {
                array_push($this->stack2, array_pop($this->stack1));
            }
        }
        return array_pop($this->stack2);
    }
}

$queue = new QueueUsingStacks();
$queue->enqueue(1);
$queue->enqueue(2);
$queue->enqueue(3);
echo $queue->dequeue(); // Output: 1
```

---

### **8. Find the Intersection of Two Arrays**

**Problem**: Write a PHP function to find the intersection of two arrays.

**Solution**:
```php
function findIntersection($arr1, $arr2) {
    return array_values(array_intersect($arr1, $arr2));
}

$arr1 = [1, 2, 3, 4];
$arr2 = [3, 4, 5, 6];
$result = findIntersection($arr1, $arr2);
print_r($result); // Output: [3, 4]
```

---

### **9. Implement a Stack with `push()`, `pop()`, and `min()`**

**Problem**: Implement a stack that supports `push()`, `pop()`, and retrieving the minimum element in constant time.

**Solution**:
```php
class MinStack {
    private $stack = [];
    private $minStack = [];
    
    public function push($item) {
        array_push($this->stack, $item);
        if (empty($this->minStack) || $item <= end($this->minStack)) {
            array_push($this->minStack, $item);
        }
    }
    
    public function pop() {
        $item = array_pop($this->stack);
        if ($item == end($this->minStack)) {
            array_pop($this->minStack);
        }
        return $item;
    }
    
    public function getMin() {
        return end($this->minStack);
    }
}

$stack = new MinStack();
$stack->push(3);
$stack->push(5);
$stack->push(2);
$stack->push(1);
echo $stack->getMin(); // Output: 1
```

---

### **10. Find the Middle Element of a Linked List**

**Problem**: Write a PHP function to find the middle element of a singly linked list.

**Solution**:
```php
class ListNode {
    public $val;
    public $next;
    
    public function __construct($val) {
        $this->val = $val;
        $this->next = null;
    }
}

function findMiddle($head) {
    $slow = $head;
    $fast = $head;
    
    while ($fast !== null && $fast->next !== null) {
        $slow = $slow->next;
        $fast = $fast->next->next;
    }
    
    return $slow->val;
}

// Example
$head = new ListNode(1);
$head->next = new ListNode(2);
$head->next->next = new ListNode(3);
$head->next->next->next = new ListNode(4);
$head->next->next->next->next = new ListNode(5);

echo findMiddle($head); // Output: 3
```

---

### **11. Remove Duplicates from a Sorted Array**

**Problem**: Write a function to remove duplicates from a sorted array and return the new length of the array.

**Solution**:
```php
function removeDuplicates(&$arr) {
    $count = count($arr);
    if ($count == 0) return 0;
    
    $j = 0;
    for ($i = 1; $i < $count; $i++) {
        if ($arr[$i] != $arr[$j]) {
            $j++;
            $arr[$j] = $arr[$i];
        }
    }
    
    return $j + 1;
}

$arr = [1, 1, 2, 2, 3, 3, 4];
$newLength = removeDuplicates($arr);
echo $newLength; // Output: 4
```

---

### **12. Two Sum Problem**

**Problem**: Given an array of integers, return indices of the two numbers such that they add up to a specific target.

**Solution**:
```php
function twoSum($nums, $target) {
    $map = [];
    
    foreach ($nums as $i => $num) {
        $diff = $target - $num;
        if (isset($map[$diff])) {
            return [$map[$diff], $i];
        }
        $map[$num] = $i;
    }
    
    return [];
}

$nums = [2, 7, 11, 15];
$target = 9;
$result = twoSum($nums, $target);
print_r($result); // Output: [0, 1]
```

---

These problems and solutions cover a broad range of data structures and algorithmic concepts that are commonly asked in interviews, along with implementation in PHP.
