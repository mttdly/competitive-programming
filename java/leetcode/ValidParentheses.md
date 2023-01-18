# **20. Valid Parentheses**
## **Description**:

**Difficulty**: _Easy_</br>
**Platform**: _Leetcode_</br>

>Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

-   Open brackets must be closed by the same type of brackets.
-   Open brackets must be closed in the correct order.
-   Every close bracket has a corresponding open bracket of the same type.

### **Example 1**:
```java
Input: s = "()"
Output: true
```

### **Example 2**:
```java
Input: s = "()[]{}"
Output: true
```

### **Example 3**:
```java
Input: s = "(]"
Output: false
```

### **Constraints**:
>1 <= s.length <= 104
>s consists of parentheses only '()[]{}'.

## **Solution - Iteration 1**:
```java
class Solution {
    public boolean isValid(String s)
    {
        int stringLength = s.length();
        
        Deque<Character> stack = new ArrayDeque<>(stringLength);
        
        for (int i = 0; i < stringLength; i++){
            if (s.charAt(i) == '(' || s.charAt(i) == '[' || s.charAt(i) == '{') {
                stack.push(s.charAt(i));
            } else {
                if (stack.isEmpty()) {
                    return false;
                }
                switch (s.charAt(i)) {
 
                    case ')':
                        if (stack.pop() != '(') {
                            return false;
                        }
                        break;
                    case ']':
                        if (stack.pop() != '[') {
                            return false;
                        }
                        break;

                    case '}':
                        if (stack.pop() != '{') {
                            return false;
                        }
                        break;
                }
            }    
        }
        return stack.isEmpty();
    }
}
```
