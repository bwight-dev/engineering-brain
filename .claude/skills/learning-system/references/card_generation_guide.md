# Anki Card Generation Guide

## File Format

Every generated card file MUST follow this exact structure:

```
#separator:tab
#html:true
#notetype:Cloze
#deck:[Topic Name]::[Subtopic Name]
#tags:[space-separated default tags]

"card text"<TAB>"extra/back text"<TAB>per-card-tags
```

## Rules

### 1. File Structure
- **Header lines** start with `#` — they configure the Anki import
- **Blank line** separates header from card data
- **One card per line** — three fields separated by literal TAB characters
- **File encoding**: UTF-8
- **Filename pattern**: `YYYY-MM-DD_subtopic-id_cloze.txt`

### 2. Three Fields Per Card

| Field | Content | Required |
|-------|---------|----------|
| Field 1 | Card front text (with cloze deletions) | Yes |
| Field 2 | Extra info shown on back | Optional (use `""` if empty) |
| Field 3 | Per-card tags (space-separated, no `#`) | Yes |

### 3. Card Type Mix (per session of 15-20 cards)
- **~60% Concept Cloze** — definitions, principles, comparisons
- **~25% Code Cloze** — code blocks with blanked-out key parts (Python + TypeScript)
- **~15% Q&A** — question on front, answer on back (still using Cloze notetype)

### 4. Cloze Deletion Rules
- Syntax: `{{c1::answer}}` or `{{c1::answer::hint}}`
- **Maximum 3 cloze deletions per card** (`c1`, `c2`, `c3`)
- Place cloze on **key concepts**, NOT trivial words
- Multiple `{{c1::...}}` references create a single card (all revealed together)
- Different numbers (`c1`, `c2`, `c3`) create separate review cards from one note

### 5. Code Block Formatting
- Wrap code in `<pre><code class='language-python'>` or `<pre><code class='language-typescript'>`
- Close with `</code></pre>`
- **HTML-encode** special characters inside code:
  - `<` → `&lt;`
  - `>` → `&gt;`
  - `&` → `&amp;`
- Add comments in code to explain what's happening
- Use `#` comments for Python, `//` comments for TypeScript

### 6. Dual Language Rule
- Every code concept MUST have BOTH a Python AND TypeScript version
- These are separate cards (two lines in the file)
- Tag Python cards with `python` and TypeScript cards with `typescript`

### 7. Quote Escaping
- All three fields are wrapped in double quotes
- Escape quotes inside fields by doubling them: `""` → literal `"`
- Example: `"He said ""hello"""`

### 8. Deck Naming
- Use `::` for hierarchy: `CS Fundamentals::Big O Notation`
- Match the topic/subtopic names from curriculum.json

### 9. Tags
- Header `#tags:` sets default tags for all cards in the file
- Per-card tags (field 3) are additional tags specific to that card
- Use lowercase, hyphenated: `big-o`, `design-patterns`, `interview-prep`
- Always include the topic category tag

## Example Cards

### Concept Cloze Card
```
"Big O notation describes the {{c1::upper bound}} of an algorithm's growth rate, focusing on the {{c2::worst case}} scenario."	"Used to compare algorithm efficiency as input size grows."	cs-fundamentals big-o
```

### Code Cloze Card (Python)
```
"<pre><code class='language-python'># Binary Search - returns index or -1
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left &lt;= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] &lt; target:
            {{c1::left = mid + 1}}
        else:
            {{c2::right = mid - 1}}
    return -1</code></pre>"	"Time: O(log n), Space: O(1). Array must be sorted."	python binary-search algorithms
```

### Code Cloze Card (TypeScript)
```
"<pre><code class='language-typescript'>// Binary Search - returns index or -1
function binarySearch(arr: number[], target: number): number {
    let left = 0, right = arr.length - 1;
    while (left &lt;= right) {
        const mid = Math.floor((left + right) / 2);
        if (arr[mid] === target) return mid;
        else if (arr[mid] &lt; target) {{c1::left = mid + 1}};
        else {{c2::right = mid - 1}};
    }
    return -1;
}</code></pre>"	"Time: O(log n), Space: O(1). Array must be sorted."	typescript binary-search algorithms
```

### Q&A Card (using Cloze notetype)
```
"Why is a <b>Heap</b> preferred over a <b>Sorted Array</b> for a Priority Queue?"	"<b>Heaps</b> are faster for insertions (O(log n) vs O(n)). Arrays require shifting all elements on every insert."	heaps interview-prep data-structures
```

### Multi-Cloze Concept Card
```
"The three pillars of observability are:
1. {{c1::Logs}} - discrete event records
2. {{c2::Metrics}} - numeric measurements over time
3. {{c3::Traces}} - request flow across services"	"Together they provide full visibility into system behavior."	distributed observability
```

## Quality Checklist

Before saving a card file, verify:
- [ ] Header has all 5 lines (#separator, #html, #notetype, #deck, #tags)
- [ ] Blank line between header and cards
- [ ] Each card has exactly 3 tab-separated fields
- [ ] Cloze deletions are on KEY concepts (not filler words)
- [ ] Max 3 cloze per card
- [ ] Code blocks are properly HTML-encoded
- [ ] Code cards exist in BOTH Python and TypeScript
- [ ] 15-20 cards total per file
- [ ] Tags are lowercase and hyphenated
- [ ] No broken HTML tags
