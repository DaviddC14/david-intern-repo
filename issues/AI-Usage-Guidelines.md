# AI Usage Guidelines Reflection

**When should you use AI for assistance, and when should you rely on your own skills?**
I should use AI for generating boilerplate code, writing regular expressions, explaining unfamiliar error messages, or generating mock data for databases. I must rely on my own skills for designing core backend architecture, writing complex business logic, and reviewing security implementations to ensure they meet the project's specific standards.

**How can you avoid over-reliance on AI while still benefiting from it?**
To avoid over-reliance, I will enforce a personal rule: I will never copy and paste code that I do not fully understand. I will use AI as a pair programmer to get suggestions, but I will write the final implementation myself and ensure I can explain how every line of code works.

**What steps will you take to ensure data privacy when using AI tools?**
I will never input proprietary Focus Bear source code, database schemas, API keys, `.env` file contents, or any user PII (Personally Identifiable Information) into public AI models. 

**Task: Identify one task you can improve using an AI tool, and try it out.**
I used an AI tool to help generate unit tests for a standard API endpoint. 

**Review the AI-generated output critically—did it require editing or fact-checking?**
Yes, it required editing. The AI assumed a different testing framework than the one we typically use, and it generated a mock database connection that did not align with our actual environment setup. I had to manually refactor the setup and teardown blocks.

**Document one best practice you will follow when using AI tools at Focus Bear.**
I will always treat AI output as "untested code from a junior developer." It must be thoroughly reviewed, fact-checked against official documentation (like Node.js or Express.js docs), and validated through testing before being merged into any branch.