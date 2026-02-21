# Step 2: Upgrade Vulnerable Dependencies

Once you've identified a vulnerability, the next step is to mitigate it by upgrading to a version that includes a fix.

## Instructions

### 1. Upgrade the package
Based on the `govulncheck` report, we need at least version `v0.3.7`. We'll upgrade to `v0.3.8` to be safe:

```bash
go get golang.org/x/text@v0.3.8
```

### 2. Verify the fix
Run `govulncheck` again to confirm the project is now secure:

```bash
govulncheck ./...
```

The output should now state:
`No vulnerabilities found.`

---

## Best Practices
- **Regular Scans**: Run `govulncheck` as part of your CI/CD pipeline.
- **Selective Upgrades**: Only upgrade what is necessary if you're concerned about breaking changes, but always aim for the latest stable versions.
- **Security Awareness**: Always check the "More info" links in the reports to understand the nature of the risks.
