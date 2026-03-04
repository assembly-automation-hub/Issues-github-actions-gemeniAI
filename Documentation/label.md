# Label and Tag Documentation

This document explains how to route the AI analysis to specialized personas using specific tags in your commit messages or labels on your Pull Requests. By categorizing your changes, the script focuses on specific aspects of the code to generate highly relevant issues. To track and manage these generated issues effectively, you need to work with tables in GitHub Projects.

## Supported Labels and Tags

### 1. Strict Security Auditor
* **Trigger Labels/Tags:** `security`, `sec`, `audit`
* **Focus:** Deep security audit based on the OWASP Top 10.
* **Output:** Scans the code for injection flaws, XSS, hardcoded secrets, and insecure data handling. Generates a critical vulnerability report detailing the exact lines of code and providing specific patching instructions.

### 2. Strict Code Reviewer
* **Trigger Labels/Tags:** `review`, `refactor`, `code-review`
* **Focus:** Code quality, SOLID principles, DRY, and overall architecture.
* **Output:** Identifies code smells, bad naming conventions, and redundant logic. Generates an issue with concrete refactoring improvements and code snippets demonstrating a cleaner approach.

### 3. QA Engineer
* **Trigger Labels/Tags:** `qa`, `test`, `testing`
* **Focus:** Edge cases, points of failure, and test coverage.
* **Output:** Generates ready-to-use unit test code blocks and a bulleted checklist for manual testing to ensure the new changes do not break existing functionality.

### 4. Performance Expert
* **Trigger Labels/Tags:** `perf`, `optimize`, `performance`
* **Focus:** Performance bottlenecks, time/space complexity, and resource management.
* **Output:** Identifies slow loops, redundant database calls, or high memory usage. Suggests algorithmic optimizations to improve execution speed.

### 5. Product Manager
* **Trigger Labels/Tags:** `pm`, `release`, `product`
* **Focus:** Business value and user-facing benefits.
* **Output:** Translates technical code changes into clear user benefits. Formats the output as a public changelog or release notes suitable for end-users.

## Default Behavior

If no specific label or tag is detected, the script defaults to generating standard technical documentation. It will create a clear description of what was changed and will only add a "Security Warning" section if an obvious security flaw is spotted.

## Usage Guide

You can trigger these specific AI personas in two ways, depending on your workflow:

### Method 1: Using Commits (Push)
Include the desired tag in square brackets anywhere in your commit message. The script will parse the message and apply the corresponding persona.
* **Example:** `git commit -m "Update authentication flow [sec]"`
* **Example:** `git commit -m "Refactor sorting algorithm [perf]"`

### Method 2: Using Pull Requests
Assign the corresponding label directly to the Pull Request using the GitHub interface before the script executes. 
* **Example:** Add the `qa` label to a Pull Request to generate testing instructions based on the accumulated diff.
