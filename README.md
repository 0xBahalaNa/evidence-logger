# evidence_logger.py

A Python tool that generates timestamped audit evidence files from a AWS policy compliance check.

## Purpose

During GRC audits, you need to prove:
- When a check was performed
- What was checked
- What issues were found

This script automates evidence generation so you have audit-ready documentation.

This repository contains `test_policy.json` for testing purposes. 

## Features

- Timestamped filenames (never overwrites previous evidence)
- Checks for overly permissive policy statements
- Flags `Action: "*"` (all actions allowed)
- Flags `Resource: "*"` (all resources affected)
- Formatted, human-readable output

## Requirements

- Python 3.6 or higher
- No external dependencies (uses standard library only)

## Usage

1. Place your AWS policy JSON file in the same directory as the script
2. Update `policy_file` variable if your file has a different name
3. Run the script:

```bash
python evidence_logger.py
```

4. Check the generated evidence file:

```
evidence_2025-12-09_17-27-15_policy_check.txt
```

## Example Output

```
================================================================================
COMPLIANCE EVIDENCE LOG
================================================================================
Timestamp: 2025-12-09_17-27-15

Checking: test_policy.json

[FAIL] Statement "DangerousAdmin": Action is "*"
[FAIL] Statement "DangerousAdmin": Resource is "*"

Result: 2 issues found

================================================================================
END OF LOG
================================================================================
```

## Future Improvements
- Accept policy filename as command-line argument
- Scan multiple policies in a directory
- Add more compliance checks (e.g., Effect: Allow without conditions)
- Output JSON format for machine processing
- Save evidence files to dedicated `evidence/` folder

## License
- MIT License