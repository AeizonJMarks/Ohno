# The Ohno Protocol Specification
Version 1.0.0

## Chapter 3: Core Components

### Essential Protocol Structure

The Ohno Protocol is built on a foundation of trust, enabled by mandatory AI-generated analysis layered between human metadata and content. This three-layer approach ensures objective system understanding:

1. META Layer (Human-authored metadata)
2. SYNOPSIS Layer (AI-generated truth layer)
3. CONTENTS Layer (Human-authored content)

This structure is immutable and enforces the protocol's primary goal: enabling trustworthy human-AI collaboration through objective system analysis.

### File Structure

#### Pure Ohno Files (.ohno)
Every .ohno file MUST maintain this exact ordering to preserve the trust layer:

```
shebang
<blank-line>
meta-block     # Human context
<blank-line>
synopsis-block # AI analysis (mandatory)
<blank-line>
contents-block # Human content
```

Example of a complete .ohno file:
```
#!/usr/bin/env ohno

#### META: Title: Authentication System
#### META: Version: 1.0.0
#### META: Author: Development Team

#### SYNOPSIS: Authentication system implements OAuth2.0
#### SYNOPSIS: Critical security component with unpatched vulnerabilities
#### SYNOPSIS: Memory leak detected in token validation
#### SYNOPSIS: API endpoints lack proper rate limiting

#### CONTENTS:
### SECTION: initialization
Implementation details...
### END: SECTION: initialization
```

#### Integration with Source Files
Source files integrate Ohno using native comment syntax:

```python
#!/usr/bin/env python3
# #### META: Title: Auth Implementation
# #### META: Version: 2.0.0
# #### META: Author: Dev Team

# #### SYNOPSIS: Python OAuth implementation with security flaws
# #### SYNOPSIS: Token validation bypass possible
# #### SYNOPSIS: Rate limiting incorrectly implemented

# #### CONTENTS:
# ### SECTION: imports
from oauth import OAuth
# ### END: SECTION: imports
```

### Required Headers

#### META Block (Human Context)
Provides file metadata and human context:

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

#### SYNOPSIS Block (AI Truth Layer)
The SYNOPSIS block is the cornerstone of the Ohno Protocol. It MUST:
- Be generated exclusively by AI
- Never be written or modified by humans
- Provide objective system analysis
- Identify potential issues and implications
- Update automatically upon system changes

Example of AI-generated analysis:
```
#### SYNOPSIS: Authentication system implements OAuth2.0
#### SYNOPSIS: Critical security component with unpatched vulnerabilities
#### SYNOPSIS: Memory leak detected in token validation
#### SYNOPSIS: API endpoints lack proper rate limiting
#### SYNOPSIS: Dependencies require security updates
```

The SYNOPSIS block serves as:
1. Truth Layer - Unbiased system analysis
2. Security Barrier - Identifies potential issues
3. Context Builder - Maps system relationships
4. Change Detector - Tracks system evolution
5. Trust Enforcer - Prevents human manipulation

#### CONTENTS Section
The CONTENTS section organizes the main document content:

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
   - Follows reference format
   - Must reference valid targets

Example:
```
### LINK: src/auth.py:42
### LINK: config.ohno#initialization
### LINK: ../lib/utils.ohno
```

#### Task Management Tags

1. TODO/DONE
```
### TODO: Implement rate limiting
Implementation needed...
### DONE: 2024-12-17 14:30
```

2. FIXME
```
### FIXME: Memory leak in auth loop
Details of the issue...
### DONE: 2024-12-17 14:30
```

3. TRIAGE
```
### TRIAGE: Critical - Security vulnerability
### TRIAGE: Medium - Performance issue
### TRIAGE: Low - Documentation update
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

### Trust Verification

#### Synopsis Validation
Tools implementing the Ohno Protocol MUST:
1. Verify SYNOPSIS is AI-generated
2. Prevent human modification
3. Maintain synopsis integrity
4. Update analysis automatically
5. Track analysis changes

#### Integrity Checking
```python
def verify_synopsis(file):
    assert is_ai_generated(file.synopsis)
    assert not has_human_modifications(file.synopsis)
    assert matches_system_state(file.synopsis)
```

#### Component Validation

1. Structure Rules
   - Required headers present
   - Valid tag sequence
   - Matched section tags
   - Proper nesting

2. Content Rules
   - Valid field values
   - Complete references
   - Proper formats
   - Consistent style

3. Relationship Rules
   - Logical tag flow
   - Valid dependencies
   - Proper closure
   - Clear ownership

### Chapter Summary
This chapter defined the core components of the Ohno Protocol, emphasizing the crucial role of the AI-generated SYNOPSIS as a mandatory trust layer between human metadata and content. This structure ensures objective system analysis and maintains the integrity of human-AI collaboration throughout the development process. The chapter detailed the file structure, required headers, tag categories, extension system, and validation requirements that form the foundation of the protocol.
