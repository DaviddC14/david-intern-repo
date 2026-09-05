# Data Privacy & Confidentiality Reflection

**What steps can you take to ensure you handle data securely in your daily tasks?**
As a Backend Developer, I will ensure that all API endpoints I develop properly sanitize inputs. I will also make sure that I never expose Personally Identifiable Information (PII) or authentication tokens in server logs or error messages returned to the client.

**How should you store, share, and dispose of sensitive information safely?**
Sensitive configurations, such as database credentials and API keys, must only be stored in secure `.env` files that are strictly added to `.gitignore`. They should never be hardcoded into the source code or shared unencrypted over Slack. 

**What are some common mistakes that lead to data privacy issues, and how can they be avoided?**
A common mistake is accidentally pushing API keys, `.env` files, or production database dumps to GitHub repositories. This can be avoided by rigorously reviewing the `git diff` before every commit, setting up pre-commit hooks, and using automated secret-scanning tools.

**Task: Habit or practice to improve data security**
I will strictly use mock data (fake data generated for testing) rather than real production user data when developing and testing backend features locally. 

**Task: Key learning or security measure to implement**
I will ensure that strict Role-Based Access Control (RBAC) and authorization checks are implemented on every single API route so that users can only ever query and access their own specific data, completely aligning with Focus Bear's privacy policy.