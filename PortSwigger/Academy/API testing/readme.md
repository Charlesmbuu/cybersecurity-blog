# API Testing
---
:star: This learning path taught me how to test APIs that aren't fully used by the website front-end.

:star: Learnt key API recon skills to help me discover more attack surface. 

:star: In addition, I learnt how to identify server-side parameter pollution vulnerabilities that may impact internal APIs.

---

## API Vulnerabilities Mitigation

- When designing  APIs, make sure that security is a consideration from the beginning.
- Ensure that you:
```
⭐ Secure your documentation if you don't intend your API to be publicly accessible.
⭐ Ensure your documentation is kept up to date so that legitimate testers have fully visibility of the API's attack surface.
⭐ Apply an allowlist of permitted HTTP methods.
⭐ Validate that the content type is expected for each request or response.
⭐ Use generic error messages to avoid giving away information that may be useful for an attacker.
⭐ Use protective measures on all versions of your API, not just  the current production version.
```

- To prevent mass assignment vulnerabilties, allowlist the properties that can be updated by the user, and blocklist sensitive properties that shouldn't be updated by the user.
