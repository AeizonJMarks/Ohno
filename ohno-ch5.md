# The Ohno Protocol Specification
Version 1.0.0

## Chapter 5: Tag Dictionary

### Built-in Tags

#### Header Tags (####)

1. META
Purpose: File metadata and properties
```
#### META: Title: Authentication System
#### META: Version: 1.0.0
#### META: Author: Development Team
#### META: Path: src/auth/core.ohno
```
Required Fields:
- Title: Document purpose
- Version: Semantic version
- Author: Owner/maintainer
- Path: File location

2. SYNOPSIS
Purpose: AI-oriented system analysis
```
#### SYNOPSIS: Core authentication handler
#### SYNOPSIS: Implements OAuth2 protocol
#### SYNOPSIS: Critical security component
```
Characteristics:
- AI-generated content
- System-wide context
- Multiple entries allowed
- Progressive refinement

3. CONTENTS
Purpose: Main content marker
```
#### CONTENTS:
### SECTION: implementation
Code or content here...
### END: SECTION: implementation
```
Rules:
- Single occurrence per file
- Follows synopsis block
- Contains all sections
- Required in .ohno files

#### Structural Tags (###)

1. SECTION
Purpose: Content organization
```
### SECTION: initialization
Content here...
### END: SECTION: initialization
```
Rules:
- Requires matching END tag
- Can be nested
- Must have unique identifier
- May contain other tags

2. LINK
Purpose: Cross-references
```
### LINK: src/auth.py:42
### LINK: config.ohno#initialization
### LINK: ../lib/utils.ohno
```
Formats:
- File references
- Line numbers
- Section references
- External URLs

#### Task Management Tags

1. TODO
Purpose: Future task marking
```
### TODO: Implement rate limiting
Implementation needed...
### DONE: 2024-12-17 14:30
```
Attributes:
- Task description
- Optional priority
- Optional deadline
- Optional assignee

2. DONE
Purpose: Task completion
```
### DONE: 2024-12-17 14:30
### DONE: @username 2024-12-17
```
Requirements:
- Valid timestamp
- Optional assignee
- Links to TODO/FIXME
- No content required

3. FIXME
Purpose: Issue marking
```
### FIXME: Memory leak in auth loop
Critical memory issue...
### DONE: 2024-12-17 14:30
```
Attributes:
- Issue description
- Optional severity
- Optional impact
- Optional timeline

4. TRIAGE
Purpose: Issue prioritization
```
### TRIAGE: Critical - Security vulnerability
### TRIAGE: Medium - Performance issue
### TRIAGE: Low - Documentation update
```
Format:
- Priority level
- Issue description
- Optional category
- Optional impact

#### Documentation Tags

1. IDEA
Purpose: Improvement suggestions
```
### IDEA: Implement caching layer
### IDEA: Add retry mechanism
### IDEA: Optimize query performance
```
Components:
- Suggestion description
- Optional benefits
- Optional complexity
- Optional priority

2. REVIEW
Purpose: Review requirements
```
### REVIEW: Security implications
### REVIEW: Performance impact
### REVIEW: API compatibility
```
Attributes:
- Review focus
- Optional reviewer
- Optional deadline
- Optional status

3. NOTE
Purpose: General annotations
```
### NOTE: Based on RFC 6749
### NOTE: Requires secure connection
### NOTE: Implementation details
```
Characteristics:
- Contextual information
- No specific format
- Optional references
- Optional categories

#### Analysis Tags

1. METRICS
Purpose: Measurement recording
```
### METRICS: 100ms 50MB 99.9%
### METRICS: $50.00 24hrs 85%
```
Format:
- Space-delimited values
- Valid measurements
- Optional context
- Optional baseline

2. FUNCTION
Purpose: Function documentation
```
### FUNCTION: authenticate(user: str) -> bool
### PURE: yes
### EFFECTS: none
```
Components:
- Function signature
- Purity indicator
- Side effects
- Optional complexity

### Extension Tags

#### Custom Tag Format
```
### @NAMESPACE::TAG: content
```

1. Performance Tags
```
### @PERF::LATENCY: 100ms p99
### @PERF::MEMORY: 50MB peak
### @PERF::CPU: 85% utilization
```

2. Security Tags
```
### @SEC::AUDIT: 2024-12-17 passed
### @SEC::LEVEL: HIGH
### @SEC::REVIEW: required
```

3. Team Tags
```
### @TEAM::OWNER: backend
### @TEAM::REVIEW: required
### @TEAM::STATUS: in-progress
```

#### Namespacing Rules

1. Namespace Format
- Uppercase letters
- No special characters
- Maximum 8 characters
- Must be unique

2. Tag Format
- Uppercase letters
- No special characters
- Maximum 16 characters
- Must be unique in namespace

3. Content Format
- Free-form text
- Optional structured data
- Optional references
- Optional metrics

### Validation Rules

#### Built-in Tags
1. Format Requirements
- Correct scope level
- Valid tag name
- Proper spacing
- Complete structure

2. Content Requirements
- Valid elements
- Proper references
- Correct measurements
- Logical relationships

#### Extension Tags
1. Namespace Rules
- Valid format
- Registered namespace
- Proper documentation
- Clear purpose

2. Content Rules
- Format compliance
- Data validation
- Reference checking
- Context verification

### Chapter Summary
This chapter provided a comprehensive reference for all tags in the Ohno Protocol, including built-in tags and extension patterns. Each tag's purpose, format, and usage requirements were detailed, along with validation rules and best practices.
