# Splunk Web Log Threat Hunting

## Project Overview

This project demonstrates my ability to use Splunk Enterprise to investigate web server logs, identify suspicious activity, analyze HTTP traffic, and visualize security events using SPL.

## Objectives

- Analyze Apache web server logs
- Identify the most active client IPs
- Investigate HTTP status codes
- Detect suspicious requests
- Investigate possible attack vectors
- Create visualizations using SPL

## Skills Demonstrated

- Splunk Enterprise
- Search Processing Language (SPL)
- Web Log Analysis
- Threat Hunting
- SOC Investigation
- HTTP Log Analysis
- Data Visualization

## Investigation Summary

During the investigation I performed:

- Traffic volume analysis
- Top client IP identification
- HTTP response code analysis
- URI popularity analysis
- Investigation of 500 Internal Server Errors
- Review of suspicious User-Agent strings
- Analysis of Referer headers
- Identification of automated scanners and crawlers
- Visualization of traffic trends

## Sample SPL Queries

```spl
index=main
| top limit=10 clientip
```

```spl
index=main
| top limit=10 uri_path
```

```spl
index=main
| stats count by status
```

```spl
index=main status=500
| table _time clientip method uri_path useragent referer
```

```spl
index=main
| timechart span=30m count
```

## Key Findings

- Googlebot generated a significant amount of legitimate web traffic.
- Several HTTP 500 errors were observed.
- Most requests returned HTTP 200 responses.
- HTTP 301 redirects were common.
- No evidence of SQL Injection attempts was identified.
- No successful Directory Traversal attempts were observed.
- No confirmed Remote Command Execution activity was detected.

## Tools Used

- Splunk Enterprise
- SPL
- Apache Access Logs
- Windows 11
