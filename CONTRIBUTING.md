# Contributing to Tech Blend Examples

Thank you for your interest in contributing! We welcome contributions from the community.

## How to Contribute

### Reporting Issues

If you find a bug or have a suggestion:

1. **Check existing issues** to avoid duplicates
2. **Create a new issue** with:
   - Clear, descriptive title
   - Detailed description
   - Steps to reproduce (for bugs)
   - Expected vs actual behavior
   - Your environment (OS, tool versions, etc.)

### Contributing Code

#### 1. Fork & Clone

```bash
# Fork the repo on GitHub, then clone your fork
git clone https://github.com/YOUR_USERNAME/tech-blend-examples.git
cd tech-blend-examples
```

#### 2. Create a Branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/your-bug-fix
```

#### 3. Make Your Changes

**For new examples:**
- Create a new directory under the appropriate category
- Include a comprehensive README.md
- Add architecture diagrams (if applicable)
- Ensure code is production-ready and tested
- Follow the example template (see below)

**For existing examples:**
- Test your changes thoroughly
- Update documentation if needed
- Maintain backward compatibility when possible

#### 4. Example Template

Each example should include:

```
example-name/
├── README.md           # Detailed documentation
├── diagram.png         # Architecture diagram (optional)
├── main.tf            # Code files (or equivalent)
├── variables.tf       # Configuration
└── examples/          # Usage examples
    └── basic/
```

**README.md Template:**

```markdown
# Example Name

Brief description of what this example does.

## Architecture

[Include or link to diagram]

## Prerequisites

- Tool 1 (version)
- Tool 2 (version)
- Access requirements

## Quick Start

\`\`\`bash
# Step-by-step instructions
\`\`\`

## Configuration

Explain key configuration options

## Customization

How to adapt for different use cases

## Production Considerations

Security, cost, scalability notes

## Troubleshooting

Common issues and solutions

## References

- [Related blog post](https://techblendconsult.io/blog/...)
- [Documentation](...)
```

#### 5. Test Your Changes

- Test all code examples
- Verify documentation accuracy
- Run linters (if applicable)
- Ensure no secrets or credentials are committed

#### 6. Commit Your Changes

```bash
git add .
git commit -m "feat: add AWS production VPC example"
```

**Commit message format:**
- `feat:` - New feature/example
- `fix:` - Bug fix
- `docs:` - Documentation only
- `refactor:` - Code refactoring
- `test:` - Adding tests
- `chore:` - Maintenance tasks

#### 7. Push & Create PR

```bash
git push origin feature/your-feature-name
```

Then create a Pull Request on GitHub with:
- Clear description of changes
- Link to related issues
- Screenshots/diagrams (if applicable)

## Code Standards

### General Guidelines

- **Production-ready**: All code should be suitable for production use
- **Well-documented**: Include clear comments and documentation
- **Secure**: No hardcoded secrets, follow security best practices
- **Tested**: Verify everything works as documented
- **Maintainable**: Use clear naming, consistent formatting

### Terraform

- Use Terraform >= 1.5.0
- Follow [HashiCorp style guide](https://www.terraform.io/docs/language/syntax/style.html)
- Use modules for reusable components
- Include `variables.tf`, `outputs.tf`, `main.tf`
- Add `.terraform.lock.hcl` to gitignore

### Kubernetes

- Use latest stable K8s APIs
- Follow [K8s best practices](https://kubernetes.io/docs/concepts/configuration/overview/)
- Include resource limits and requests
- Use namespaces appropriately
- Add RBAC configurations

### Documentation

- Use clear, concise language
- Include code examples
- Add troubleshooting sections
- Link to related resources
- Explain "why" not just "what"

## What We're Looking For

### High Priority

- Production-ready AWS/GCP/Azure infrastructure examples
- Kubernetes configurations (monitoring, security, GitOps)
- CI/CD pipeline templates
- Security hardening configurations
- Complete reference architectures

### Nice to Have

- Additional cloud providers
- Alternative tools/approaches
- Performance optimizations
- Cost optimization examples
- Disaster recovery patterns

## Review Process

1. **Automated checks** run on PR submission
2. **Maintainer review** within 3-5 days
3. **Feedback/changes** may be requested
4. **Merge** once approved

## Questions?

- **Discord**: [Join Tech Blend Community](https://discord.gg/hk4ny22R)
- **Email**: sales@techblendconsult.io
- **Issues**: Open an issue for discussion

## Recognition

Contributors will be:
- Listed in release notes
- Credited in example READMEs
- Mentioned in our Discord community

Thank you for helping make infrastructure more accessible! 🚀
