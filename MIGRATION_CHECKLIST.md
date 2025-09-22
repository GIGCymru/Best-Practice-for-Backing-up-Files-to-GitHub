# Migration Checklist for NHS Wales Teams

## Pre-Migration Assessment

### Inventory Your Current Setup
- [ ] List all shared drive locations containing code/scripts
- [ ] Identify file types and their purposes:
  - [ ] Database scripts (.sql files)
  - [ ] Application code (.cs, .js, .py, .r files)
  - [ ] Configuration files
  - [ ] Documentation files
  - [ ] Other: ________________

### Assess Security Requirements
- [ ] Classify data sensitivity levels
- [ ] Identify any files containing patient information (should NOT be migrated)
- [ ] Review access requirements for each file/folder
- [ ] Document compliance requirements

### Team Preparation
- [ ] Identify team members who need GitHub access
- [ ] Schedule GitHub training sessions
- [ ] Establish code review team
- [ ] Define repository ownership

## Migration Execution

### Repository Setup
- [ ] Create GitHub repository with appropriate name
- [ ] Configure repository settings:
  - [ ] Set to private
  - [ ] Enable vulnerability alerts
  - [ ] Configure branch protection rules
  - [ ] Set up required reviewers

### Initial Upload
- [ ] Clean up files before migration:
  - [ ] Remove temporary files
  - [ ] Remove files with sensitive data
  - [ ] Remove duplicate/obsolete versions
- [ ] Create proper folder structure
- [ ] Upload files to GitHub
- [ ] Create initial documentation

### Security Configuration
- [ ] Review and configure access permissions
- [ ] Enable automated security scanning
- [ ] Set up integration with NHS Wales monitoring systems
- [ ] Test access controls

### Team Onboarding
- [ ] Provide access to team members
- [ ] Conduct hands-on training session
- [ ] Establish workflow and processes
- [ ] Create team documentation

## Post-Migration

### Process Updates
- [ ] Update deployment procedures
- [ ] Modify backup processes
- [ ] Update documentation and SOPs
- [ ] Notify stakeholders of changes

### Validation
- [ ] Test new workflow with small changes
- [ ] Verify security configurations
- [ ] Confirm backup and recovery procedures
- [ ] Validate compliance requirements

### Cleanup
- [ ] Archive shared drive content
- [ ] Remove write access to old locations
- [ ] Update shortcuts and bookmarks
- [ ] Document new processes

## Success Criteria

By the end of migration, you should have:
- [ ] All code under version control
- [ ] Clear audit trail of changes
- [ ] Secure collaboration environment
- [ ] Documented processes and procedures
- [ ] Trained team members
- [ ] Improved deployment capabilities

## Common Issues and Solutions

### Issue: "We have too many files to migrate"
**Solution:** Start with the most critical files first, migrate in phases

### Issue: "Our files contain sensitive information"
**Solution:** Clean data before migration, use environment variables for secrets

### Issue: "Team doesn't know Git/GitHub"
**Solution:** Start with basic training, use GitHub Desktop for non-technical users

### Issue: "Integration with existing systems"
**Solution:** Plan integration points, use GitHub APIs and webhooks

## Support Resources

- NHS Wales IT Helpdesk: [Contact Information]
- GitHub Training Materials: [Internal Links]
- Best Practices Documentation: [Internal Links]
- Emergency Contacts: [Contact Information]