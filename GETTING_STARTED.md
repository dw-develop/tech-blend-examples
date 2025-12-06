# Getting Started - For Maintainers

Quick guide for adding new examples to this repository.

## Adding a New Example

### 1. Choose the Right Directory

```
architectures/     → Full reference architectures with diagrams
terraform/         → Reusable Terraform modules
kubernetes/        → K8s manifests and configs
ci-cd/            → Pipeline templates
security/         → Security configs and baselines
templates/        → Complete project templates
```

### 2. Create Example Directory

```bash
# Example: Adding AWS VPC Terraform module
mkdir -p terraform/aws/vpc
cd terraform/aws/vpc
```

### 3. Use the Template

```bash
# Copy the example template
cp ../../../EXAMPLE_TEMPLATE.md README.md
```

### 4. Add Your Code

Create your example files:
- `main.tf` (for Terraform)
- `values.yaml` (for Helm)
- `manifest.yaml` (for K8s)
- etc.

### 5. Write Documentation

Edit `README.md` following the template:
- Clear overview
- Prerequisites
- Quick start
- Configuration options
- Troubleshooting
- **Include CTAs to consulting services!**

### 6. Test Everything

- Run through the quick start yourself
- Verify all commands work
- Check links
- Ensure no secrets/credentials

### 7. Commit and Push

```bash
git add .
git commit -m "feat: add AWS VPC Terraform module"
git push origin main
```

## Documentation Standards

### README Structure
Every example must have:
1. **Title** - Clear, descriptive
2. **Overview** - What and why
3. **Architecture** - Diagram or description
4. **Prerequisites** - Everything needed
5. **Quick Start** - Step-by-step
6. **Configuration** - Options and customization
7. **Production Considerations** - Security, HA, cost
8. **Troubleshooting** - Common issues
9. **Related Resources** - Links to blog posts
10. **CTAs** - Consulting services at the end

### Code Quality
- Production-ready
- Well-commented
- No hardcoded secrets
- Follow best practices
- Include examples/

## Linking to Blog Posts

When you publish a blog post about an example:

1. Add link in example README:
```markdown
## Related Resources
- [Blog: Title](https://techblendconsult.io/blog/slug)
```

2. Add link in blog post:
```markdown
See the complete code example on GitHub:
👉 [tech-blend-examples/path/to/example](https://github.com/...)
```

## Announcing New Examples

### Discord
Post in `#code-examples`:
```
🆕 New Example: [Name]

Just added [brief description]

Check it out: [GitHub link]

Questions? Ask here!
```

### LinkedIn
```
🎁 Just open-sourced: [Example Name]

[What it does]
[Why it's useful]
[Link]

Free to use, MIT licensed.

#DevOps #Kubernetes #Terraform
```

### Website
Add to `/examples` page (if it exists)

## Maintenance

### Updating Examples
- Keep dependencies up to date
- Update for new tool versions
- Address issues promptly
- Improve based on feedback

### Responding to Issues
- Acknowledge within 24-48 hours
- Provide helpful guidance
- Convert good questions to FAQ
- Close with resolution

## Monetization Reminders

Every example should:
1. ✅ Have consulting CTAs at the end
2. ✅ Link to blog posts
3. ✅ Be excellent quality (builds trust)
4. ✅ Solve real problems (attracts right audience)

Remember: Free examples → Trust → Consulting leads → Revenue

## Questions?

Check main [README.md](README.md) or [CONTRIBUTING.md](CONTRIBUTING.md)
