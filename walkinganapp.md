## Walking an Application Room Summary

In the **Walking an Application** room, I learned how to systematically explore a web application to understand its structure, functionality, and potential vulnerabilities. The room focused on **reconnaissance, enumeration, and analysis** rather than immediately exploiting vulnerabilities. 

### What I Learned in Each Part:

1. **Reconnaissance**
   - I explored the main pages and functionality of the application.
   - I learned to identify interesting URLs, parameters, and input points.
   - I understood the importance of observing application behavior and error messages.

2. **Directory and File Enumeration**
   - I used tools like `gobuster` to find hidden directories, admin pages, and backup files.
   - I learned how exposed or forgotten files can reveal sensitive information.

3. **Parameter & Input Analysis**
   - I examined GET and POST parameters to see how inputs were handled.
   - I identified places where user input could potentially be manipulated.
   - This taught me the foundation for future vulnerability testing like SQLi or LFI.

4. **Authentication & Session Exploration**
   - I analyzed login forms and authentication flows.
   - I learned to check for weak credentials, logic flaws, and session management issues.

5. **Documentation & Observations**
   - I documented all endpoints, inputs, and behaviors for future testing.
   - This emphasized the importance of planning and structured reconnaissance before exploitation.

### Key Takeaways
- Systematically exploring an application helps map its attack surface.
- Careful observation can reveal subtle vulnerabilities.
- Reconnaissance is as critical as exploitation in web penetration testing.

## Application Endpoint Documentation

| Endpoint / URL           | Method | Input / Parameters            | Observed Behavior / Response                         | Notes / Potential Issues                  |
|---------------------------|--------|-------------------------------|-----------------------------------------------------|------------------------------------------|
| `/`                       | GET    | None                          | Loads homepage                                     | Main landing page                         |
| `/login`                  | POST   | username, password            | Returns success or error message                   | Check for default creds or SQLi          |
| `/register`               | POST   | username, password, email     | Creates new user                                   | Input validation?                         |
| `/profile`                | GET    | user_id (query param)         | Shows user profile                                 | Possible IDOR (Insecure Direct Object Ref) |
| `/upload`                 | POST   | file                          | Accepts file upload, saves to /uploads/           | Test file upload restrictions             |
| `/admin`                  | GET    | None                          | Redirects to login if not authenticated           | Check for hidden pages or bypass          |
| `/about`                  | GET    | None                          | Loads about page                                   | No issues                                 |
| `/search`                 | GET    | query                         | Displays search results                             | Potential injection point                 |
| `/config.bak`             | GET    | None                          | Downloads backup file                               | Sensitive information exposure            |
