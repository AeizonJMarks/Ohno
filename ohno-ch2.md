# The Ohno Protocol Specification
Version 1.0.0

## Chapter 2: Tag Architecture

### Tag Anatomy

#### Core Structure
Every Ohno tag follows this precise structure:
```
<comment-syntax>[whitespace|newline]<tag-scope><space><tag><space><element><newline>
```

Where:
- `<comment-syntax>`: Language-specific comment markers
- `[whitespace|newline]`: Required separator after comment syntax
- `<tag-scope>`: Tag hierarchy indicator (#### or ###)
- `<space>`: Single space character
- `<tag>`: Uppercase tag identifier
- `<element>`: Tag content
- `<newline>`: Line terminator

#### Component Details

1. Comment Syntax
   - Single-line: `#`, `//`, `;`
   - Block-style: `/* */`, `<!-- -->`, `{- -}`
   - Must be valid in target language
   - Must be consistent within blocks

2. Whitespace Rules
   - Block comments require newline after opening
   - Single-line comments require space after marker
   - One space required after tag scope
   - One space required after tag
   - No trailing whitespace allowed

3. Tag Scope
   - `####`: Header-level scope (meta-information)
   - `###`: Standard scope (content and tasks)
   - Must be consistent within blocks
   - No mixed scopes in single block

4. Tag Format
   - Uppercase ASCII letters only
   - No numbers or special characters
   - No spaces within tag name
   - Maximum length: 16 characters

5. Element Content
   - Format depends on tag type
   - May contain spaces
   - No newlines within element
   - UTF-8 encoded text

### Comment Integration

#### Single-Line Comments

```python
# ### SECTION: Authentication
# Code implementation...
# ### END: SECTION: Authentication
```

```javascript
// ### TODO: Implement rate limiting
// ### METRICS: 100ms 50MB
```

```lisp
;; ### LINK: src/auth.lisp#init
;; ### NOTE: Critical section
```

#### Block Comments

```c
/* 
#### META: System Configuration
#### SYNOPSIS: Core initialization
*/
```

```html
<!-- 
#### META: Authentication Module
#### SYNOPSIS: Handles user verification
-->
```

```haskell
{- 
### SECTION: Data Processing
Implementation details...
### END: SECTION: Data Processing
-}
```

### Scope Levels

#### Header Level (####)
Reserved for file-level metadata and system information:
- META: File metadata
- SYNOPSIS: Content overview
- CONTENTS: Section marker

Example:
```python
# #### META: Title: Authentication System
# #### META: Version: 1.0.0
# #### SYNOPSIS: Core authentication handlers
```

#### Standard Level (###)
Used for all content and task-related tags:
- SECTION: Content blocks
- TODO/DONE: Task management
- METRICS: Measurements
- Other standard tags

Example:
```python
# ### SECTION: initialization
# ### METRICS: 24hrs $50.00
# ### TODO: Add error handling
```

### Language-Specific Implementation

#### Compiled Languages

1. C/C++
```c
// Single-line style
// ### SECTION: Memory Management

/* Block style
#### META: Memory Handler
#### SYNOPSIS: Core allocator
*/
```

2. Java/Kotlin
```java
// Javadoc integration
/**
 * #### META: Data Processor
 * #### SYNOPSIS: Handles streaming
 */
```

#### Interpreted Languages

1. Python
```python
# Standard single-line
# ### SECTION: Data Processing

'''
#### META: Processing Module
#### SYNOPSIS: Data handling
'''
```

2. JavaScript
```javascript
// Single-line format
// ### TODO: Implement caching

/* Block format for headers
#### META: Cache Handler
#### SYNOPSIS: Memory cache
*/
```

#### Markup Languages

1. HTML
```html
<!-- 
#### META: Page Template
#### SYNOPSIS: Base layout
-->
```

2. XML
```xml
<!-- 
#### META: Configuration
#### SYNOPSIS: System settings
-->
```

### Validation Rules

#### Structural Validation

1. Comment Syntax
   - Must be valid for language
   - Must be consistently applied
   - Must not break language parser

2. Tag Format
   - Correct scope level
   - Valid tag name
   - Proper spacing
   - Complete structure

3. Content Rules
   - No nested tags
   - No broken references
   - Valid element format
   - Proper encoding

#### Error Handling

1. Parser Requirements
   - Clear error messages
   - Line number references
   - Context information
   - Recovery suggestions

2. Common Errors
   - Invalid comment syntax
   - Incorrect scope level
   - Missing whitespace
   - Malformed elements

### Best Practices

#### Consistency Rules
1. Use consistent comment style within blocks
2. Maintain proper indentation
3. Group related tags together
4. Follow language conventions

#### Organization
1. Place headers at file start
2. Group related sections
3. Maintain clear hierarchy
4. Use meaningful identifiers

#### Documentation
1. Keep elements concise
2. Use clear descriptions
3. Maintain references
4. Update regularly

### Chapter Summary
This chapter defined the precise technical requirements for Ohno Protocol tag implementation, including structure, formatting, language integration, and validation rules. The architecture ensures consistency and parseability while maintaining flexibility across different programming languages and paradigms.
