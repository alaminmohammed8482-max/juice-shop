## Project Overview

OWASP Juice Shop was used as a practice project to apply Secure SDLC and DevSecOps principles. The goal was to identify, fix, and validate security vulnerabilities across the development lifecycle using automated security tools.

## Static Application Security Testing (SAST)

Static Application Security Testing (SAST) was performed using CodeQL to analyze the source code. Several critical and high-risk issues such as code injection, server-side request forgery, and unsafe input handling were identified. Many of these issues were reduced by improving validation and applying secure coding practices.

## Software Composition Analysis (SCA)

Software Composition Analysis (SCA) was carried out using `npm audit` and Snyk. The initial scan showed a high number of vulnerable dependencies. After updating packages and pinning dependency versions, the number of vulnerabilities was significantly reduced. Some issues remained due to missing patches or breaking changes, and these were documented and monitored.

## Dynamic Application Security Testing (DAST)

Dynamic Application Security Testing (DAST) was performed using OWASP ZAP against the running application. The first scan identified runtime security weaknesses. After applying configuration hardening and input validation fixes, a second scan confirmed that high-risk runtime issues were reduced.

## Docker Security Hardening

Docker security hardening was applied to reduce container-level risks. A lightweight base image was used, the application was run as a non-root user, unnecessary files were removed, and multi-stage builds were implemented. Container images were scanned using security tools to validate security improvements.

## Lessons Learned

This project showed that not all vulnerabilities can be fully fixed, but risk can be reduced. Integrating security tools into the CI/CD pipeline made security testing continuous and automated. The biggest lesson learned was that security works best when it is part of the development process, not added at the end.
