# NHS Wales GitHub Security Guidelines

## Overview

This document provides security guidelines specific to NHS Wales for using GitHub to store and manage code, scripts, and configuration files. These guidelines ensure compliance with NHS Digital standards and protect patient data.

## Data Classification and Handling

### ✅ SAFE to store in GitHub:
- Application source code (without credentials)
- Database schema definitions
- Configuration templates (with placeholders)
- Documentation and procedures
- Test data (anonymized/synthetic)
- Open source contributions

### ⚠️ REQUIRES SPECIAL HANDLING:
- Production configuration files (use templates + secrets management)
- API specifications (review for sensitive endpoints)
- Infrastructure as Code (ensure no embedded secrets)
- Third-party integration code (review for credentials)

### ❌ NEVER store in GitHub:
- Patient data or personal information
- Database connection strings with credentials
- API keys or authentication tokens
- Certificates and private keys
- Production passwords or secrets
- NHS network topology information
- Unencrypted backup files

## Repository Security Configuration

### Required Settings for All NHS Wales Repositories

```yaml
Repository Settings:
  visibility: private
  vulnerability_alerts: enabled
  automated_security_fixes: enabled
  dependency_graph: enabled
  
Branch Protection Rules (main/master):
  require_status_checks: true
  require_branches_up_to_date: true
  require_pull_request_reviews: true
  required_reviewers: 2
  dismiss_stale_reviews: true
  require_code_owner_reviews: true
  restrict_pushes: true
  
Security Settings:
  secret_scanning: enabled
  push_protection: enabled
  dependency_review: enabled
```

### Access Control

#### Repository Access Levels
- **Admin:** IT Security team, Project leads
- **Write:** Development team members
- **Read:** Stakeholders, documentation reviewers
- **No Access:** Default for all other NHS Wales staff

#### Team Structure Example
```
NHS Wales GitHub Organization
├── nhs-wales-admins (Admin access)
├── nhs-wales-developers (Write access)
├── nhs-wales-reviewers (Read access)
└── project-specific-teams
    ├── patient-portal-team
    ├── analytics-team
    └── infrastructure-team
```

## Secrets Management

### Using Azure Key Vault Integration

```bash
# Example: Secure configuration loading
# Instead of storing secrets in GitHub:

# ❌ Bad - secrets in code
$connectionString = "Server=prod-sql;Database=PatientDB;User=admin;Password=secret123"

# ✅ Good - using Key Vault
$connectionString = Get-AzKeyVaultSecret -VaultName "nhs-wales-keyvault" -Name "PatientDB-ConnectionString"
```

### Environment Variables Pattern

```yaml
# config.template.yml
database:
  host: ${DB_HOST}
  port: ${DB_PORT}
  username: ${DB_USERNAME}
  password: ${DB_PASSWORD}
  
api:
  key: ${API_KEY}
  endpoint: ${API_ENDPOINT}
```

## Code Review Security Requirements

### Mandatory Security Reviews

All pull requests must be reviewed for:

1. **Credential Exposure**
   - Search for hardcoded passwords, keys, tokens
   - Check configuration files for sensitive data
   - Verify environment variable usage

2. **Data Privacy**
   - Ensure no patient data in code or comments
   - Check for NHS ID numbers or personal information
   - Verify anonymization of test data

3. **Access Control**
   - Review authentication and authorization code
   - Check for proper role-based access controls
   - Verify session management implementation

4. **Vulnerability Assessment**
   - Review dependencies for known vulnerabilities
   - Check for secure coding practices
   - Validate input sanitization

### Security Review Checklist

```markdown
## Security Review Checklist

- [ ] No hardcoded credentials or secrets
- [ ] No patient data or personal information
- [ ] Proper input validation and sanitization
- [ ] Secure authentication mechanisms
- [ ] Appropriate error handling (no information disclosure)
- [ ] Dependencies scanned for vulnerabilities
- [ ] Configuration follows security templates
- [ ] Documentation updated for security considerations
```

## Incident Response

### Security Incident Types

1. **Credential Exposure**
   - Immediate action: Revoke compromised credentials
   - Remove from git history using BFG Repo-Cleaner
   - Notify IT Security team within 1 hour

2. **Unauthorized Access**
   - Disable affected accounts immediately
   - Review access logs and audit trail
   - Conduct impact assessment

3. **Data Breach**
   - Follow NHS Wales data breach procedures
   - Notify Information Governance team immediately
   - Document incident for compliance reporting

### Emergency Contacts

- **IT Security:** [Emergency Contact]
- **GitHub Admin:** [Emergency Contact]
- **Information Governance:** [Emergency Contact]
- **Incident Response Team:** [Emergency Contact]

## Compliance Requirements

### NHS Digital Standards Alignment

- **DCB0129:** Clinical Risk Management
- **DCB0160:** Business Continuity Planning
- **SCCI0090:** Information Risk Management

### Audit Requirements

- All repository access must be logged
- Regular access reviews (quarterly)
- Security scanning reports maintained
- Incident documentation required

### Data Protection

- GDPR compliance for any personal data
- Data minimization principles
- Right to erasure considerations
- Privacy by design implementation

## Monitoring and Alerting

### Automated Security Monitoring

```yaml
Security Alerts:
  - Secret detection in commits
  - Vulnerable dependency notifications
  - Unusual access patterns
  - Large file uploads
  - Failed authentication attempts

Notification Channels:
  - Email to security team
  - Slack alerts for urgent issues
  - ServiceNow tickets for incidents
  - Dashboard monitoring
```

### Regular Security Tasks

#### Weekly
- [ ] Review security alerts and warnings
- [ ] Check for new vulnerable dependencies
- [ ] Monitor access patterns

#### Monthly
- [ ] Conduct access review
- [ ] Update security documentation
- [ ] Review and test incident procedures

#### Quarterly
- [ ] Complete access audit
- [ ] Security training refresh
- [ ] Policy review and updates

## Training and Awareness

### Required Training

All NHS Wales staff using GitHub must complete:

1. **Git and GitHub Fundamentals** (4 hours)
2. **NHS Wales Security Guidelines** (2 hours)
3. **Data Protection and Privacy** (1 hour)
4. **Incident Response Procedures** (1 hour)

### Ongoing Education

- Monthly security newsletters
- Quarterly brown bag sessions
- Annual security awareness training
- Just-in-time training for new features

## Tools and Resources

### Security Tools
- **GitHub Advanced Security** - Secret scanning, dependency review
- **Azure Key Vault** - Secrets management
- **SonarCloud** - Code quality and security analysis
- **OWASP ZAP** - Application security testing

### Documentation Templates
- Security requirements template
- Threat model template
- Incident response runbook
- Security review checklist

## Contact Information

- **GitHub Security Team:** github-security@wales.nhs.uk
- **IT Security Office:** itsecurity@wales.nhs.uk
- **Data Protection Officer:** dpo@wales.nhs.uk
- **Emergency Hotline:** [24/7 Contact Number]