# Best Practice for Backing up Files to GitHub
## A Guide for NHS Wales Staff

### Table of Contents
1. [Introduction](#introduction)
2. [Why Shared Drives Are Problematic](#why-shared-drives-are-problematic)
3. [Benefits of Using GitHub](#benefits-of-using-github)
4. [Best Practices for GitHub Usage](#best-practices-for-github-usage)
5. [Security Considerations for NHS Wales](#security-considerations-for-nhs-wales)
6. [Implementation Guide](#implementation-guide)
7. [Common Scenarios and Solutions](#common-scenarios-and-solutions)
8. [Getting Started Checklist](#getting-started-checklist)

---

## Introduction

This guide is specifically designed for NHS Wales staff who currently use shared drives to back up code, database scripts, system configurations, and analysis files. It explains why this practice is problematic and provides comprehensive best practices for using GitHub as a superior alternative for version control and file management.

**Target Audience:** NHS Wales IT staff, developers, data analysts, and anyone managing code or configuration files within the organisation.

---

## Why Shared Drives Are Problematic

### 🚨 Critical Issues with Shared Drive Backups

#### 1. **No Version Control**
- **Problem:** Multiple versions of files with names like `script_v1.sql`, `script_v2_final.sql`, `script_v2_FINAL_ACTUALLY.sql`
- **Impact:** Confusion about which version is current, risk of using outdated code
- **Real Scenario:** A database migration script gets modified by multiple team members, leading to conflicting versions and potential data loss

#### 2. **Lack of Change Tracking**
- **Problem:** No record of who made what changes and when
- **Impact:** Impossible to trace the source of bugs or understand the evolution of code
- **Compliance Risk:** NHS Wales requires audit trails for changes to systems handling patient data

#### 3. **No Collaboration Management**
- **Problem:** Multiple people editing the same file simultaneously
- **Impact:** Lost work, conflicts, and inconsistent implementations
- **Example:** Two developers unknowingly modify the same stored procedure, overwriting each other's work

#### 4. **Security Vulnerabilities**
- **Problem:** Shared drives often have overly broad access permissions
- **Impact:** Sensitive code and configurations accessible to unauthorized staff
- **Risk:** Potential exposure of database connection strings, API keys, or patient data access methods

#### 5. **No Backup Strategy**
- **Problem:** Shared drives can fail, and backups may not be comprehensive
- **Impact:** Complete loss of work and institutional knowledge
- **Reality:** Network outages or hardware failures can make critical systems inaccessible

#### 6. **Lack of Integration**
- **Problem:** No connection to deployment pipelines or automated testing
- **Impact:** Manual, error-prone deployment processes
- **Inefficiency:** Increased time to market and higher risk of human error

---

## Benefits of Using GitHub

### ✅ Why GitHub is Superior for NHS Wales

#### 1. **Complete Version History**
- Every change is tracked with timestamps, author information, and detailed comments
- Ability to revert to any previous version instantly
- Comprehensive audit trail for compliance requirements

#### 2. **Secure Collaboration**
- Multiple developers can work on the same codebase without conflicts
- Pull request system ensures code review before changes are merged
- Clear ownership and responsibility for changes

#### 3. **Enhanced Security**
- Granular access controls at repository and branch level
- Integration with NHS Wales Active Directory for authentication
- Encrypted storage and transmission of all data

#### 4. **Automated Workflows**
- GitHub Actions can automate testing, deployment, and compliance checks
- Integration with NHS Wales CI/CD pipelines
- Automatic notifications for changes and issues

#### 5. **Documentation Integration**
- Code and documentation live together
- Markdown support for rich documentation
- Wikis for larger documentation projects

#### 6. **Disaster Recovery**
- Multiple redundant backups across geographically distributed data centers
- 99.95% uptime SLA
- Point-in-time recovery capabilities

---

## Best Practices for GitHub Usage

### 🏥 NHS Wales Specific Guidelines

#### 1. **Repository Structure**
```
nhs-wales-project/
├── README.md                 # Project overview and setup instructions
├── docs/                     # Detailed documentation
├── src/                      # Source code
├── scripts/                  # Database and deployment scripts
├── config/                   # Configuration files (no secrets!)
├── tests/                    # Test files
└── .gitignore               # Files to exclude from version control
```

#### 2. **Naming Conventions**
- **Repositories:** `nhs-wales-[project-name]` (e.g., `nhs-wales-patient-portal`)
- **Branches:** `feature/[description]`, `bugfix/[description]`, `hotfix/[description]`
- **Commits:** Clear, descriptive messages explaining what and why

#### 3. **Branching Strategy**
- **main:** Production-ready code only
- **develop:** Integration branch for features
- **feature branches:** Individual features or fixes
- **Always use pull requests** for merging to main or develop

#### 4. **Security Best Practices**
- **Never commit secrets:** Use environment variables or Azure Key Vault
- **Use .gitignore:** Exclude sensitive files, logs, and build artifacts
- **Regular access reviews:** Quarterly review of repository permissions
- **Enable branch protection:** Require reviews and status checks

#### 5. **Documentation Standards**
- **README.md:** Must include setup instructions, dependencies, and contact information
- **Code comments:** Explain complex business logic and NHS-specific requirements
- **Change logs:** Document significant changes and their impact on NHS systems

---

## Security Considerations for NHS Wales

### 🔒 Protecting Patient Data and NHS Systems

#### 1. **Data Classification**
- **Public:** Open source libraries, general documentation
- **Internal:** NHS Wales-specific configurations (non-sensitive)
- **Confidential:** Database schemas, API specifications
- **Restricted:** Never store patient data or credentials in GitHub

#### 2. **Access Control**
- Use NHS Wales GitHub Enterprise with SSO integration
- Implement least-privilege access principles
- Regular access audits and automated deprovisioning

#### 3. **Compliance Requirements**
- All repositories must comply with NHS Digital standards
- Enable audit logging and retention policies
- Regular security scanning of code and dependencies

#### 4. **Incident Response**
- Immediate revocation procedures for compromised accounts
- Clear escalation paths for security incidents
- Regular backup verification and recovery testing

---

## Implementation Guide

### 📋 Step-by-Step Migration from Shared Drives

#### Phase 1: Assessment (Week 1)
1. **Inventory existing shared drive content**
   - Catalog all code, scripts, and configuration files
   - Identify file owners and current users
   - Assess sensitivity levels and access requirements

2. **Plan repository structure**
   - Group related files into logical repositories
   - Define naming conventions and standards
   - Create migration timeline and responsibilities

#### Phase 2: Setup (Week 2)
1. **Create GitHub repositories**
   ```bash
   # Example commands for NHS Wales admin
   gh repo create nhs-wales-database-scripts --private
   gh repo create nhs-wales-web-portal --private
   ```

2. **Configure security settings**
   - Enable branch protection rules
   - Set up required reviewers
   - Configure automated security scanning

#### Phase 3: Migration (Weeks 3-4)
1. **Initial upload**
   ```bash
   # Example migration process
   git init
   git add .
   git commit -m "Initial migration from shared drive"
   git remote add origin https://github.com/nhs-wales/project-name.git
   git push -u origin main
   ```

2. **Team onboarding**
   - Training sessions on Git and GitHub
   - Establish code review processes
   - Create team documentation and workflows

#### Phase 4: Transition (Week 5)
1. **Update development processes**
   - Modify deployment scripts to use GitHub
   - Update documentation and procedures
   - Establish monitoring and backup verification

2. **Decommission shared drive access**
   - Archive old shared drive content
   - Remove write access to shared drives
   - Redirect teams to GitHub repositories

---

## Common Scenarios and Solutions

### 💡 Real-World NHS Wales Use Cases

#### Scenario 1: Database Migration Scripts
**Previous:** Scripts scattered across shared drives, no version control
**Solution:**
```
nhs-wales-database-migrations/
├── README.md
├── migrations/
│   ├── 2024-01-15-patient-table-update.sql
│   ├── 2024-01-20-new-appointment-system.sql
│   └── rollback/
├── procedures/
└── functions/
```

#### Scenario 2: Web Application Configuration
**Previous:** Config files with hardcoded credentials on shared drives
**Solution:**
```
nhs-wales-patient-portal/
├── config/
│   ├── app.config.template    # Template with placeholders
│   └── environments/
│       ├── dev.config.template
│       └── prod.config.template
└── deploy/
    └── setup-config.ps1       # Script to populate from Key Vault
```

#### Scenario 3: Data Analysis Scripts
**Previous:** R/Python scripts with no documentation or version control
**Solution:**
```
nhs-wales-health-analytics/
├── README.md                  # Analysis overview
├── data-sources/              # Documentation of data sources
├── scripts/
│   ├── patient-outcome-analysis.R
│   └── cost-effectiveness-study.py
├── results/                   # Generated reports (anonymized)
└── documentation/
    └── methodology.md
```

---

## Getting Started Checklist

### ✅ Your First Steps

#### Before You Begin
- [ ] Complete NHS Wales GitHub training course
- [ ] Obtain necessary approvals from IT Security
- [ ] Identify team members who need access

#### Repository Setup
- [ ] Create repository with appropriate naming convention
- [ ] Configure repository settings and permissions
- [ ] Create initial README.md with project description
- [ ] Set up .gitignore file for your technology stack
- [ ] Enable branch protection rules

#### Security Configuration
- [ ] Review and configure access permissions
- [ ] Enable security scanning and alerts
- [ ] Set up integration with NHS Wales monitoring
- [ ] Document security considerations in README

#### Team Onboarding
- [ ] Provide Git/GitHub training to team members
- [ ] Establish code review processes
- [ ] Create team coding standards document
- [ ] Set up notification preferences

#### Migration Execution
- [ ] Back up current shared drive content
- [ ] Upload initial codebase to GitHub
- [ ] Update deployment processes
- [ ] Test new workflow with small changes
- [ ] Archive shared drive content
- [ ] Update team documentation

---

## Support and Resources

### 🆘 Getting Help

- **NHS Wales IT Helpdesk:** For technical issues and access requests
- **GitHub Enterprise Support:** For platform-specific questions
- **Internal Training:** Regular workshops on Git and GitHub best practices
- **Documentation:** Comprehensive guides available on NHS Wales intranet

### Additional Resources
- [NHS Digital Technology Standards](https://digital.nhs.uk/about-nhs-digital/our-work/nhs-digital-data-and-technology-standards)
- [GitHub Enterprise Security](https://docs.github.com/en/enterprise-server/admin/user-management/managing-users-in-your-enterprise)
- [Git Best Practices](https://git-scm.com/book/en/v2)

---

**Remember:** The transition from shared drives to GitHub is not just about technology—it's about adopting modern software development practices that improve quality, security, and collaboration across NHS Wales.