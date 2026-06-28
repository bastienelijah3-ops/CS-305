# CS-305

Briefly summarize your client, Artemis Financial, and its software requirements. Who was the client? What issue did the company want you to address?

Artemis Financial is a global financial consulting firm that handles highly sensitive client financial records, including retirement portfolios, savings metrics, and insurance policies. Their issue was their public facing RESTful web application was exposed to severe architectural and source code vulnerabilities. The primary issue was that the application used outdated open-source libraries (such as Spring Boot, Apache Tomcat, and Bouncy Castle) and lacked foundational security controls like transmission encryption, parameter sanitization, and data encapsulation, which made it highly vulnerable to Man in the Middle (MitM) attacks, timing flaws, and data leaks.

What did you do well when you found your client’s software security vulnerabilities? Why is it important to code securely? What value does software security add to a company’s overall well-being?

The vulnerability assessment successfully combined thorough manual source code inspection with automated static application security testing (SAST). This led to a precise diagnosis of both hidden internal programming bugs (e.g., plaintext passwords, lack of data encapsulation) and external dependency tracking (CVE mapping).

Coding securely ensures that security is built directly into the software development lifecycle (SDLC) rather than treated as an afterthought. It prevents malicious actors from exploiting logical code bugs to bypass authorization or gain arbitrary remote execution.

For financial institutions like Artemis, robust software security preserves the company's market reputation, protects customer trust, guards against devastating regulatory fines, and enforces compliance with global standards like GLBA, GDPR, and FIPS 140-3.

Which part of the vulnerability assessment was challenging or helpful to you?

I'd say the most helpful part of the vulnerability assessment was the CVE list which alsp provide descriptions and solutions of the problems that can/ are affecting Artemis.

How did you increase layers of security? In the future, what would you use to assess vulnerabilities and decide which mitigation techniques to use?

Defense in depth was achieved by first transitioning the web layer from plaintext HTTP to encrypted HTTPS/TLS. Seconnd, implementing SHA-256 cryptographic hashing to enforce data integrity. Third, upgrading underlying framework dependencies (Spring Boot, Apache Tomcat, Bouncy Castle) to eliminate known CVE threats. And lastly, enforcing data encapsulation by restricting variable visibilities to private.

How did you make certain the code and software application were functional and secure? After refactoring the code, how did you check to see whether you introduced new vulnerabilities?

Verification was achieved by creating integrated REST endpoint logic and then successfully recompiling and executing the application. This confirmed that the application could boot properly into an embedded HTTPS servlet environment (e.g., via port 8443) without active console exceptions.

After refactoring the code and upgrading the dependencies in the pom.xml, an additional automated dependency check script was re-run. Analyzing the subsequent post-mitigation report verified that the old CVE designations (such as CVE-2024-30171 and CVE-2026-43514) were cleared and that no regression or supply chain vulnerabilities were introduced.

What resources, tools, or coding practices did you use that might be helpful in future assignments or tasks?
Employers sometimes ask for examples of work that you have successfully completed to show your skills, knowledge, and experience. What might you show future employers from this assignment?

I'd say Javaa Keytool for building localized keystores and self signed certificates for testing environments. Also OWASP Dependency-Check Maven plugin for performing static analysis on open-source dependencies.
