
# Regular Expressions

### 1. Delimiters

Characters used to mark the beginning and end of a pattern.

**Example:**

```javascript
const regex = /hello/;
const result = "hello world".match(regex); // Matches "hello"

```

----------

### 2. Literal Characters

Characters without special meaning. Example: a to z, 0 to 9

**Example:**

```javascript
const regex = /cat/;
const result = "The cat sat on the mat.".match(regex); // Matches "cat"

```

----------

### 3. Meta-Characters

Characters with special meaning. Example: . ^ $ * + ? {} [] \ | ()

**Example:**

```javascript
const regex = /\d+/;
const result = "There are 123 apples.".match(regex); // Matches "123"

```

----------

### 4. Dot Metacharacter (`.`)

Matches any single character except newline characters (\n, \r).

**Example:**

```javascript
const regex = /c.t/;
const result = "cat cut cot".match(regex); // Matches "cat", "cut", "cot"

```

----------

### 5. Escape Character (`\`)

Used to escape special characters or introduce special sequences (\n, \t, etc.)

**Example:**

```javascript
const regex = /\./;
const result = "This is a sentence.".match(regex); // Matches "."

```

----------

### 6. Flags/Modifiers

-   **`g`** (global): Searches for all occurrences of the pattern within the text, rather than just the first one.
-   **`i`** (case-insensitive): Ignores case differences when matching letters.
-   **`m`** (multi-line): Changes the behavior of ^ and $ anchors to match the beginning and end of each line within the text, rather than just the beginning and end of the entire text.
-   **`s`** (dotAll): Allows the dot (.) to match newline characters (\n), which it doesn't do by default.
-   **`u`** (unicode): Enables full Unicode support for the regex pattern.
-   **`y`** (sticky): Matches only from the last index where a previous match ended.

**Example:**

```javascript
const regex = /hello/gi;
const result = "Hello hello HELLO".match(regex); // Matches all occurrences, ignoring case

```

----------

### 7. Defining Sets of Characters

-   Match specific characters: `[abc]`
-   Match ranges within character classes: `[a-z]` or `[0-9]`
-   Combine ranges: `[a-z0-9]`
-   Negate character classes: `[^abc]`

**Example:**

```javascript
const regex = /[aeiou]/g;
const result = "hello world".match(regex); // Matches "e", "o", "o"

```

----------

### 8. Types of Quantifiers

-   `*` Matches 0 or more occurrences.
-   `+` Matches 1 or more occurrences.
-   `?` Matches 0 or 1 occurrence.
-   `{n}` Matches exactly `n` occurrences.
-   `{n,}` Matches `n` or more occurrences.
-   `{n,m}` Matches between `n` and `m` occurrences.

**Example:**

```javascript
const regex = /\d{2,4}/;
const result = "12345".match(regex); // Matches "1234"

```

----------

### 9. Anchors

-   `^` Asserts the position at the start of the string.
-   `$` Asserts the position at the end of the string.
-   `m` (multi-line flag, not an anchor): Changes the behavior of ^ and $ anchors to match the beginning and end of each line within the text, rather than just the beginning and end of the entire text.

**Example:**

```javascript
const regex = /^hello/;
const result = "hello world".match(regex); // Matches "hello" at the start

```

----------

### 10. Types of Shorthand Classes

-   `\d` Matches any digit (equivalent to `[0-9]`).
-   `\D` Matches any non-digit.
-   `\w` Matches any word character (equivalent to `[A-Za-z0-9_]`).
-   `\W` Matches any non-word character.
-   `\s` Matches any whitespace character (spaces, tabs, line breaks).
-   `\S` Matches any non-whitespace character.

**Example:**

```javascript
const regex = /\w+/g;
const result = "Hello world!".match(regex); // Matches "Hello", "world"

```

----------

### 11. Alternation

-   Use the vertical bar `|` to specify alternatives (e.g., `cat|dog`).

**Example:**

```javascript
const regex = /cat|dog/;
const result = "I have a dog.".match(regex); // Matches "dog"

```

----------

### 12. Types of Groups

-   **Grouping:** Parentheses `()`.
-   **Capturing groups and backreferences:** `\(\1\2)`.
-   **Non-capturing groups:** `(?:...)`.
-   **Named capture groups:** `(?<name>...)`.
-   **Backreferences using names:** `\k<name>`.

**Example:**

```javascript
const regex = /(?<word>\w+)/;
const result = "hello".match(regex); // Matches "hello" and captures as "word"

```

----------

### 13. Boundaries

-   **Word boundaries:** `\b`
-   **Non-word boundaries:** `\B`

**Example:**

```javascript
const regex = /\bcat\b/;
const result = "cat scat".match(regex); // Matches "cat"

```

----------

### 14. Lookaheads and Lookbehinds

-   **Positive lookahead:** `pattern1(?=pattern2)`
-   **Negative lookahead:** `pattern1(?!pattern2)`
-   **Positive lookbehind:** `(?<=pattern1)pattern2`
-   **Negative lookbehind:** `(?<!pattern1)pattern2`

**Example:**

```javascript
const regex = /(?<=\$)\d+/;
const result = "$100".match(regex); // Matches "100"

```

----------

### 15. Debugging

-   Track the current input position.
-   Use lookahead for conditions before the main pattern: `(?=pattern2)pattern1`.
-   Use lookbehind for conditions after the main pattern: `pattern1(?<=pattern2)`.

**Example:**

```javascript
const regex = /(?=\d{2})\d{1}/;
const result = "123".match(regex); // Matches "1"

```

----------

### 16. Substitution Syntax

-   `$&` Inserts the matched substring.
-   `$\` Inserts the portion of the string that precedes the matched substring.
-   `$'` Inserts the portion of the string that follows the matched substring.
-   `$n` Inserts the nth (1-indexed) capturing group where n is a positive integer less than 100.
-   `$<name>` Inserts the named capturing group where Name is the group name.
-   `$$` Inserts a `$`.

**Example:**

```javascript
const regex = /(cat)/;
const result = "cat".replace(regex, "$& is an animal"); // Replaces with "cat is an animal"

```

----------

### 17. How to Create Regex in JavaScript

-   Regex can be created using forward slashes to enclose the pattern.
    
    ```javascript
    const regex = /pattern/;
    const result = regex.test("pattern in text"); // Returns true
    
    ```
    

-   Regex can also be created using the `RegExp` constructor.
    
    ```javascript
    const regex = new RegExp('pattern');
    const result = regex.test("pattern in text"); // Returns true
    
    ```
    

----------

### RegExp Methods and Properties

1.  `exec()`
2.  `test()`
3.  `lastIndex`

**Example:**

```javascript
const regex = /hello/;
const result = regex.exec("hello world"); // Matches "hello" with details

```

----------

### String Methods Supporting Regex

1.  `match()`
2.  `matchAll()`
3.  `replace()`
4.  `replaceAll()`
5.  `search()`
6.  `split()`

**Example:**

```javascript
const regex = /\s+/;
const result = "split this string".split(regex); // Splits into ["split", "this", "string"]

```
