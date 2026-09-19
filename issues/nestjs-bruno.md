# API Debugging with Bruno Reflection

**How does Bruno help with API testing compared to Postman or cURL?**
Bruno stores API collections as plain text `.bru` files directly in the project repository. This makes version control and collaboration via Git seamless compared to Postman's cloud-synced approach, while offering a much richer, more user-friendly interface than raw cURL commands in the terminal.

**How do you send an authenticated request in Bruno?**
Inside a specific request, I can navigate to the "Auth" tab, select the appropriate authentication method (such as "Bearer Token"), and input the token. Bruno then automatically handles injecting the correct `Authorization` header into the outgoing HTTP request.

**What are the advantages of organizing API requests in collections?**
Organizing requests into collections allows developers to group related endpoints logically, share the entire setup with the team via version control, and utilize environment variables (like switching between `http://localhost:3000` and a production URL) across multiple requests simultaneously.

**How would you structure a Bruno collection for a NestJS backend project?**
I would create a dedicated folder like `bruno-collection` at the root of the NestJS repository. Within the collection, I would create sub-folders that directly mirror the NestJS controller structure (e.g., `Auth/`, `Users/`, `Notifications/`) to keep the API tests organized and intuitive to navigate alongside the source code.