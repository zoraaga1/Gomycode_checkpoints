# Sentence Analyzer Algorithm

A simple algorithm that analyzes sentences character-by-character to calculate:
- Total length (including the terminating period)
- Word count (space-separated)
- Vowel count (case-insensitive)

## How It Works

### Input Requirements
- Must be a valid sentence ending with '.' 
- Example: `"The quick brown fox."`

### Processing Logic
1. **Character Analysis**:
   - Processes each character sequentially
   - Includes all characters in length count (including spaces and final '.')

2. **Word Counting**:
   - Words are separated by one or more spaces
   - Handles multiple spaces between words
   - Example: `"Hello   world."` → 2 words

3. **Vowel Detection**:
   - Counts both uppercase and lowercase vowels (A/a, E/e, I/i, O/o, U/u)
   - Example: `"Algorithm."` → 3 vowels

### Output
Three precise metrics:
1. `Sentence length`: [character count]
2. `Word count`: [number of words]
3. `Vowel count`: [number of vowels]

## Algorithm Pseudocode

```pseudocode
ALGORITHM SentenceAnalyzer
VAR
    input: STRING
    length, words, vowels: INTEGER ← 0
    vowel_set: ARRAY ← ['a','e','i','o','u','A','E','I','O','U']
    in_word: BOOLEAN ← FALSE

BEGIN
    READ input
    
    FOR i FROM 0 TO input.length - 1 DO
        IF input[i] = '.' THEN BREAK
        
        length := length + 1
        
        // Vowel check
        IF input[i] IN vowel_set THEN
            vowels := vowels + 1
        END IF
        
        // Word detection
        IF input[i] = ' ' THEN
            IF in_word THEN
                words := words + 1
                in_word ← FALSE
            END IF
        ELSE
            in_word ← TRUE
        END IF
    END FOR
    
    // Count final word
    IF in_word THEN words := words + 1
    
    // Include terminating period
    length := length + 1
    
    WRITE "Length:", length
    WRITE "Words:", words
    WRITE "Vowels:", vowels
END