# Deliberate Practice Session Guide

## Philosophy

Deliberate practice means focused, structured coding with immediate feedback. It is NOT:
- Watching someone else code
- Copy-pasting solutions
- Solving problems you already know how to solve

It IS:
- Working at the edge of your ability
- Getting specific feedback on mistakes
- Repeating patterns until they're automatic
- Building from simple to complex

## Session Structure

### 1. Warm-Up (2 min)
- State the concept being practiced
- Quick verbal review: "In your own words, what is [concept]?"
- If Brad can't explain it, review the Anki cards first

### 2. Guided Problem (10-15 min)
- Present a problem that requires the concept
- Let Brad attempt it
- Provide hints if stuck (never full solutions)
- Hints should be questions: "What data structure would help here?" not "Use a hash map"

### 3. Review (5 min)
- Walk through Brad's solution
- Discuss: correctness, edge cases, complexity
- Show the optimal solution if Brad's differs
- Ask Brad to explain WHY the optimal approach works

### 4. Variation (5-10 min)
- Modify the problem slightly (add constraint, change input)
- Brad solves the variation independently
- This cements the pattern

### 5. Wrap-Up (2 min)
- Brad states what he learned in one sentence
- Rate mastery 1-5
- Note any concepts that need more practice

## Exercise Templates by Topic

### Data Structures

**Arrays/Strings**:
- Reverse a string in place
- Find duplicates in an array
- Rotate an array by k positions
- Implement run-length encoding

**Linked Lists**:
- Reverse a linked list (iterative and recursive)
- Detect a cycle (Floyd's algorithm)
- Merge two sorted linked lists
- Find the middle node

**Trees**:
- Implement BFS (level-order traversal)
- Implement DFS (inorder, preorder, postorder)
- Find the height of a binary tree
- Validate a BST
- Find the lowest common ancestor

**Graphs**:
- Implement BFS with a queue
- Implement DFS with recursion and iteratively
- Detect a cycle in a directed graph
- Find connected components

### Algorithm Patterns

**Two Pointers**:
- Two Sum (sorted array)
- Container with most water
- Remove duplicates from sorted array
- Valid palindrome

**Sliding Window**:
- Maximum sum subarray of size k
- Longest substring without repeating characters
- Minimum window substring

**Binary Search**:
- Standard binary search
- Find first/last occurrence
- Search in rotated sorted array
- Find peak element

**Dynamic Programming**:
- Fibonacci (memo vs tabulation)
- Climbing stairs
- Coin change
- Longest common subsequence
- 0/1 Knapsack

### Design Patterns (Implement in Both Python + TypeScript)

**Singleton**: Database connection pool
**Factory**: Shape creator (Circle, Square, Triangle)
**Observer**: Event emitter / pub-sub system
**Strategy**: Payment processor (Credit Card, PayPal, Crypto)
**Builder**: HTTP request builder
**Decorator**: Logging decorator for functions

### React Patterns

**Custom Hooks**: useLocalStorage, useFetch, useDebounce
**Composition**: Modal with configurable header/body/footer
**Performance**: Memoized list with virtualization

## Difficulty Progression

For each subtopic, follow this progression:

1. **Recall**: Implement the basic concept from memory
2. **Apply**: Use it to solve a standard problem
3. **Adapt**: Solve a problem that requires modifying the pattern
4. **Combine**: Solve a problem requiring multiple concepts together
5. **Explain**: Teach the concept back (Feynman technique)

## Mastery Rating Scale

| Rating | Meaning | Next Step |
|--------|---------|-----------|
| 1 | Cannot start without help | Review cards, retry practice |
| 2 | Needs significant hints | Practice again with similar problems |
| 3 | Can solve with minor hints | Practice variations independently |
| 4 | Solves independently, minor issues | Move to harder variations |
| 5 | Solves cleanly, can explain why | Topic mastered, move on |
