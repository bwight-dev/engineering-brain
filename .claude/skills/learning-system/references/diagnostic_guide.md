# Diagnostic Assessment Guide

## Purpose

Identify Brad's current knowledge level across all 13 curriculum topics to create a personalized learning path. The diagnostic should take approximately 30-45 minutes.

## How to Administer

1. Go topic by topic in curriculum order
2. Start with the **Easy** question for each topic
3. Score Brad's answer 1-5:
   - **5**: Perfect, could teach this
   - **4**: Solid understanding, minor gaps
   - **3**: Knows the basics, needs depth
   - **2**: Vaguely familiar, significant gaps
   - **1**: No knowledge or completely wrong
4. **Adaptive difficulty**:
   - Score 4-5 on Easy → ask Medium and Hard
   - Score 3 on Easy → ask Medium only
   - Score 1-2 on Easy → skip to next topic (score it low)
5. After all topics, calculate results and write diagnostic_results.json

## Scoring Summary

| Score | Level | Action |
|-------|-------|--------|
| 4-5 | Strong | Skip or review only, move to advanced subtopics |
| 3 | Moderate | Generate cards, light practice |
| 1-2 | Weak | Full card generation + deliberate practice |

## Question Bank

### 1. CS Fundamentals

**Easy**: What does O(n log n) mean? Give an example of an algorithm with this complexity.

**Medium**: Explain the difference between time complexity and space complexity. Can you optimize one at the expense of the other? Give an example.

**Hard**: What is amortized time complexity? Explain why appending to a dynamic array (Python list / JS array) is O(1) amortized even though individual operations can be O(n).

### 2. JavaScript / TypeScript

**Easy**: What is the difference between `let`, `const`, and `var`? When would you use each?

**Medium**: Explain what a closure is. Write a function that uses a closure to create a private counter.

**Hard**: Describe the JavaScript event loop. In what order do these execute and why?
```
console.log('1');
setTimeout(() => console.log('2'), 0);
Promise.resolve().then(() => console.log('3'));
queueMicrotask(() => console.log('4'));
console.log('5');
```

**TypeScript Bonus**: What is a discriminated union in TypeScript? Write one for handling API responses (loading, success, error).

### 3. Python Fundamentals

**Easy**: What is the difference between a list and a tuple in Python? When would you use each?

**Medium**: Explain what a decorator is. Write a simple timing decorator that measures how long a function takes.

**Hard**: Explain Python's GIL (Global Interpreter Lock). Why does it exist, what problems does it cause, and how do you work around it for CPU-bound vs I/O-bound tasks?

### 4. Data Structures

**Easy**: What is the difference between a stack and a queue? Give a real-world use case for each.

**Medium**: Explain how a hash map works internally. What happens during a collision, and what is the worst-case time complexity for lookup?

**Hard**: When would you use a Trie instead of a hash map? Describe the trade-offs in time complexity, space usage, and operations supported.

### 5. Algorithm Patterns

**Easy**: Explain the Two Pointers technique. When would you use it?

**Medium**: Solve this in your head or pseudocode: Given a sorted array, find two numbers that sum to a target. What pattern would you use and what is the complexity?

**Hard**: Explain the difference between memoization (top-down) and tabulation (bottom-up) in dynamic programming. When would you prefer one over the other?

### 6. SOLID and Design Patterns

**Easy**: What does the Single Responsibility Principle mean? Give an example of a class that violates it.

**Medium**: Explain the Strategy pattern. When would you use it instead of a chain of if/else statements?

**Hard**: Explain the Dependency Inversion Principle. How does it relate to dependency injection? Write a brief example showing a class that follows DIP vs one that violates it.

### 7. Clean Architecture and DDD

**Easy**: What is a "bounded context" in Domain-Driven Design?

**Medium**: Explain the Dependency Rule in Clean Architecture. Why should inner layers not know about outer layers?

**Hard**: What is an Aggregate in DDD? Why should external code only reference the Aggregate Root? What problems does this solve?

### 8. System Design

**Easy**: What is a CDN and why would you use one?

**Medium**: How would you design a URL shortening service? Walk through the high-level components.

**Hard**: You're designing a system that needs to handle 10 million writes per second. What strategies would you use for data storage, and how would you handle consistency vs availability trade-offs?

### 9. React / Next.js / Vercel

**Easy**: What is the difference between state and props in React?

**Medium**: Explain the useEffect hook. What is the cleanup function for? What are common mistakes developers make with useEffect?

**Hard**: Explain the difference between Server Components and Client Components in Next.js App Router. When would you choose one over the other? How does data flow between them?

### 10. SQL Mastery

**Easy**: What is the difference between INNER JOIN and LEFT JOIN?

**Medium**: Write a query using a window function to rank employees by salary within each department.

**Hard**: Explain database normalization up to 3NF. When and why would you intentionally denormalize?

### 11. Distributed Systems

**Easy**: What is the CAP theorem? Can you have all three?

**Medium**: Explain the difference between synchronous and asynchronous communication between microservices. What are the trade-offs?

**Hard**: Explain the Saga pattern for distributed transactions. How does it differ from traditional two-phase commit, and what are its failure modes?

### 12. Cryptography and Networking

**Easy**: What is the difference between symmetric and asymmetric encryption? Give an example of each.

**Medium**: Describe what happens during a TLS handshake. Why is it necessary?

**Hard**: Explain how OAuth 2.0 works. What are the different grant types, and when would you use Authorization Code flow vs Client Credentials?

### 13. Math for AI

**Easy**: What is a vector? What does the dot product of two vectors represent?

**Medium**: Explain gradient descent in simple terms. What is a learning rate and what happens if it's too high or too low?

**Hard**: Explain backpropagation. How does the chain rule from calculus enable training neural networks?

## After the Diagnostic

1. Write results to `data/diagnostic_results.json`:
```json
{
  "assessment_date": "ISO timestamp",
  "total_score_pct": 42,
  "results_by_topic": {
    "topic-id": {
      "score": 3,
      "max_score": 5,
      "pct": 60,
      "confidence": "medium",
      "strengths": ["..."],
      "gaps": ["..."],
      "priority": "high|medium|low",
      "recommended_subtopics": ["subtopic-ids"]
    }
  },
  "overall_strengths": ["..."],
  "overall_gaps": ["..."],
  "recommended_learning_path": ["topic-ids in order"]
}
```

2. Update `data/progress.json`:
   - Set `diagnostic_completed: true`
   - Set `current_focus` to the first topic in the recommended path
   - Set `started_at` timestamp

3. Present to Brad:
   - Visual summary of scores by topic
   - Top 3 strengths
   - Top 3 priority gaps
   - Recommended learning order
   - Estimated total cards and sessions
