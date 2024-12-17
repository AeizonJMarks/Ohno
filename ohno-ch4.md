# The Ohno Protocol Specification
Version 1.0.0

## Chapter 4: Data Elements

### Number Format

#### Basic Structure
Numbers in Ohno follow this format:
```
[currency-symbol]integer[.mantissa][unit]
```

Components:
- Currency symbol (optional)
- Integer portion (required)
- Decimal point and mantissa (optional)
- Unit suffix (optional)
- No spaces between components

#### Currency Notation

Supported Formats:
1. Symbol Prefix
   - $: USD
   - £: GBP
   - €: EUR
   - ¥: JPY

2. Code Prefix
   - USD: US Dollar
   - EUR: Euro
   - GBP: British Pound
   - JPY: Japanese Yen

Examples:
```
$42.50      # USD with decimal
£100        # GBP without decimal
EUR50.00    # Euro using code
```

#### Units

Standard Units:
1. Time
   - ms (milliseconds)
   - s (seconds)
   - mins (minutes)
   - hrs (hours)
   - days

2. Size
   - B (bytes)
   - KB (kilobytes)
   - MB (megabytes)
   - GB (gigabytes)
   - TB (terabytes)

3. Percentage
   - % (percent)
   - ‰ (per mille)
   - ppm (parts per million)

4. Custom
   - Project-specific units
   - Must be alphanumeric
   - No spaces allowed

Examples:
```
100ms       # Time in milliseconds
2.5GB       # Size in gigabytes
99.9%       # Percentage
42units     # Custom unit
```

### Reference System

#### Path Format
Basic structure:
```
[prefix]path[#section][::line-number]
```

Components:
- Prefix: Directory notation
- Path: File location
- Section: Internal reference
- Line: Specific line number

#### Path Types

1. Relative Paths
```
./utils/auth.ohno      # Current directory
../lib/common.ohno     # Parent directory
config/settings.ohno   # Subdirectory
```

2. Absolute Paths
```
/project/src/main.ohno    # From project root
C:/dev/project/main.ohno  # Windows format
~/project/docs/spec.ohno  # Home directory
```

3. URL References
```
https://github.com/org/repo#section
git://repository.git
file:///absolute/path
```

#### Reference Components

1. Section References
```
file.ohno#initialization   # Section reference
main.py#setup::42         # Section with line
#global-config            # Internal section
```

2. Line References
```
auth.py::100          # Specific line
config.ohno::50-60    # Line range
test.js::42,44,46     # Multiple lines
```

3. Combined References
```
src/auth.py#login::100    # Section and line
../config.ohno#db::30     # Relative with section and line
```

### Metrics Format

#### Basic Structure
```
### METRICS: <measurement> [<measurement>...]
```

Rules:
- Space-delimited values
- No commas between metrics
- Each metric follows number format
- Order not significant

#### Measurement Types

1. Time Metrics
```
### METRICS: 100ms 24hrs 7days
### METRICS: 500ms 1.5hrs
```

2. Size Metrics
```
### METRICS: 2.5GB 500MB 100KB
### METRICS: 1TB 50GB
```

3. Performance Metrics
```
### METRICS: 99.9% 100ms 50MB/s
### METRICS: 1000rps 50ms
```

4. Cost Metrics
```
### METRICS: $50.00 24hrs
### METRICS: EUR100.00 7days
```

#### Combined Metrics
```
### METRICS: 100ms 50MB 99.9% $10.00
### METRICS: 24hrs 2.5GB 85% EUR50.00
```

### Custom Data Types

#### Tag Extensions
Format:
```
### @<namespace>::<type>: <value>
```

Examples:
```
### @PERF::LATENCY: 100ms 99th
### @SEC::LEVEL: HIGH
```

#### Structured Data

1. Key-Value Pairs
```
### DATA: key=value key2=value2
### CONFIG: port=8080 host=localhost
```

2. JSON Format
```
### JSON: {"status": "active", "priority": 1}
### CONFIG: {"db": {"host": "localhost"}}
```

3. Custom Formats
```
### @FORMAT::CSV: value1,value2,value3
### @FORMAT::XML: <data><value>1</value></data>
```

### Validation Requirements

#### Number Validation
1. Format Rules
   - Valid numeric format
   - Recognized currency symbols
   - Valid unit formats
   - No internal spaces

2. Range Rules
   - Non-negative values
   - Reasonable magnitude
   - Appropriate precision
   - Unit consistency

#### Reference Validation
1. Path Rules
   - Valid file paths
   - Existing targets
   - Proper formatting
   - Access permissions

2. Section Rules
   - Valid section names
   - Existing sections
   - Proper nesting
   - Clear boundaries

#### Metrics Validation
1. Format Rules
   - Valid measurements
   - Proper spacing
   - Recognized units
   - Consistent style

2. Combination Rules
   - Compatible units
   - Logical groupings
   - Clear purpose
   - Meaningful context

### Chapter Summary
This chapter defined the data elements of the Ohno Protocol, including number formats, reference systems, metrics formats, and custom data types. These elements provide the foundation for consistent data representation and manipulation within the protocol.
