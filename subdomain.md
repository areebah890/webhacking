## Subdomain Enumeration Summary

In this part of the room, I focused on discovering subdomains associated with the target domain. Subdomains often expose additional functionality, test environments, or overlooked services that can be exploited.

### What I Learned:
- How to use tools like `subfinder`, `amass`, `assetfinder`, or online services like `crt.sh` to find subdomains.
- How to validate discovered subdomains by checking their HTTP response, DNS resolution, and open ports.
- How different subdomains may host admin panels, staging environments, or other sensitive areas.
- The importance of documenting subdomains for later testing in content discovery or vulnerability assessment.

### Example of Subdomain Enumeration Documentation

| Subdomain                | Status | Notes / Observations                          |
|---------------------------|--------|-----------------------------------------------|
| `admin.example.com`       | Up     | Admin login page, potential attack target    |
| `dev.example.com`         | Up     | Development environment, may contain sensitive data |
| `test.example.com`        | Down   | Not currently active                          |
| `old.example.com`         | Up     | Old version of the site, may have vulnerabilities |
| `api.example.com`         | Up     | API endpoint, check for exposed endpoints     |
| `mail.example.com`        | Up     | Mail server, could reveal info about users    |

### Tips for Subdomain Enumeration:
1. Start with passive discovery (`crt.sh`, `Sublist3r`, `Assetfinder`) to avoid detection.  
2. Use active scanning (`amass`, `subfinder`) to find hidden or unlisted subdomains.  
3. Check each discovered subdomain for HTTP response and open ports.  
4. Document each subdomain with status and notes for later content discovery and testing.
