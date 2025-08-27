## Content Discovery Summary

In the **Content Discovery** part of the room, I focused on finding hidden directories, files, and pages that aren’t directly linked from the website. This step helps reveal potential sensitive areas or forgotten files that could be exploited later.

### What I Learned:
- How to use automated tools like `gobuster` and `ffuf` to discover directories and files.
- How to manually check for common files like `backup.zip`, `config.php.bak`, or admin pages.
- How hidden or unlinked files can reveal sensitive information, credentials, or vulnerabilities.
- How to interpret HTTP response codes (200, 403, 404) to understand which paths exist and which are restricted.

### Example of Content Discovery Documentation

| URL / Path                  | Method | Status Code | Notes / Observations                       |
|------------------------------|--------|-------------|--------------------------------------------|
| `/admin`                     | GET    | 403         | Access denied, possible admin area         |
| `/backup.zip`                | GET    | 200         | Downloadable backup file, sensitive info  |
| `/uploads`                   | GET    | 200         | Directory listing enabled                  |
| `/config.php.bak`            | GET    | 200         | Exposed config backup                      |
| `/hidden-login`              | GET    | 200         | Login page not linked anywhere             |
| `/old/`                      | GET    | 301         | Redirect to old version of the site       |
| `/robots.txt`                | GET    | 200         | Contains disallowed paths                  |

### Tips for Content Discovery:
1. Start with automated tools using common wordlists (`gobuster dir -w /usr/share/wordlists/dirb/common.txt`).
2. Check for unusual file extensions like `.bak`, `.old`, `.zip`, `.sql`.
3. Use the browser to manually explore links that might be hidden in the source code.
4. Document everything with status codes to quickly see what’s accessible.
