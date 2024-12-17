# The Ohno Protocol Specification
Version 1.0.0

## Chapter 3: Core Components

### File Structure

#### Pure Ohno Files (.ohno)
Pure Ohno files MUST follow this exact structure:

```
shebang
<blank-line>
meta-block
<blank-line>
synopsis-block
<blank-line>
contents-section
```

Example:
```
#!/usr/bin/env ohno

#### META: Title: Authentication System
#### META: Version: 1.0.0
#### META: Author: Development Team

#### SYNOPSIS: Core authentication implementation
#### SYNOPSIS: Handles user verification
#### SYNOPSIS: Integrates with OAuth providers

#### CONTENTS:
### SECTION: initialization
Implementation details...
### END: SECTION: initialization
```

#### Integration with Source Files
Source files MAY include Ohno tags using native comment syntax:

```python
#!/usr/bin/env python3
# #### META: Title: Auth Implementation
# #### META: Version: 2.0.0
# #### META: Author: Dev Team

# #### SYNOPSIS: Python auth implementation
# #### SYNOPSIS: OAuth integration class

# #### CONTENTS:
# ### SECTION: imports
from oauth import OAuth
# ### END: SECTION: imports
```

### Required Headers

#### META Block
The META block provides essential file metadata.

Required Fields:
- Title: Document purpose/identity
- Version: Document version number
- Author: Content owner(s)
- Path: File location in project

Optional Fields:
- Dependencies
- License
- Status
- Custom fields

Example:
```
#### META: Title: Core Authentication
#### META: Version: 1.0.0
#### META: Author: Security Team
#### META: Path: src/auth/core.ohno
#### META: Dependencies: utils.ohno
#### META: Status: stable
```

#### SYNOPSIS Block
The SYNOPSIS block contains AI-optimized system analysis.

Characteristics:
- AI-generated content only
- System-wide context
- Multiple entries allowed
- Progressive refinement

Example:
```
#### SYNOPSIS: Implements core authentication
#### SYNOPSIS: Uses JWT for session management
#### SYNOPSIS: Includes rate limiting support
#### SYNOPSIS: Critical security component
```

#### CONTENTS Section
The CONTENTS section organizes the main document content.

Structure:
```
#### CONTENTS:
### SECTION: <identifier>
Content...
### END: SECTION: <identifier>

### SECTION: <identifier>
Content...
### END: SECTION: <identifier>
```

### Tag Categories

#### Structural Tags

1. SECTION
   - Defines content boundaries
   - Requires matching END tag
   - Can be nested
   - Identifies logical blocks

Example:
```
### SECTION: authentication
### SECTION: oauth
OAuth implementation...
### END: SECTION: oauth
### END: SECTION: authentication
```

2. LINK
   - Creates references
   - Can target files/lines/sections
   - Supports relative/absolute paths
   - Enables navigation

Example:
```
### LINK: src/auth.py:42
### LINK: config.ohno#initialization
### LINK: ../lib/utils.ohno
```

#### Task Management

1. TODO/DONE
```
### TODO: Implement rate limiting
Implementation needed...
### DONE: 2024-12-17
```

2. FIXME
```
### FIXME: Memory leak in auth loop
Details of the issue...
### DONE: 2024-12-17
```

3. TRIAGE
```
### TRIAGE: Critical - Security vulnerability
### TRIAGE: Medium - Performance issue
```

#### Documentation Tags

1. NOTE
```
### NOTE: Based on OAuth 2.0 spec
### NOTE: Requires secure connection
```

2. IDEA
```
### IDEA: Add cache layer
### IDEA: Implement retry mechanism
```

3. REVIEW
```
### REVIEW: Security implications
### REVIEW: Performance impact
```

#### Analysis Tags

1. METRICS
```
### METRICS: 100ms 50MB 99.9%
### METRICS: $50.00 24hrs 85%
```

2. FUNCTION
```
### FUNCTION: authenticate(user: str) -> bool
### PURE: yes
### EFFECTS: none
```

### Extension System

#### Custom Tags
Format: `@` prefix for custom tags
```
### @PERFORMANCE: Critical path
### @SECURITY: Encryption required
```

#### Namespace Tags
Format: namespace::tag
```
### TEAM::REVIEW: Architecture review
### SEC::CHECK: Passed verification
```

### Tag Relationships

#### Hierarchical Structure
```
### SECTION: authentication
### FUNCTION: verify_user()
### METRICS: 50ms 99.9%
### TODO: Add rate limiting
### END: SECTION: authentication
```

#### Task Flow
```
### TODO: Implement OAuth
### TRIAGE: High priority
### METRICS: 2days
### DONE: 2024-12-17
```

#### Documentation Chain
```
### IDEA: Add caching
### REVIEW: Performance impact
### METRICS: 500ms -> 50ms
### NOTE: Approved for implementation
```

### Component Validation

#### Structure Rules
1. Required headers present
2. Valid tag sequence
3. Matched section tags
4. Proper nesting

#### Content Rules
1. Valid field values
2. Complete references
3. Proper formats
4. Consistent style

#### Relationship Rules
1. Logical tag flow
2. Valid dependencies
3. Proper closure
4. Clear ownership

### Chapter Summary
This chapter detailed the core components of the Ohno Protocol, including file structure, required headers, tag categories, and their relationships. These components form the foundation for building maintainable, AI-friendly documentation and code organization systems.
