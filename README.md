# Tech Blend Examples

> Production-ready code examples, reference architectures, and templates for modern cloud infrastructure

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

## 🎯 What's Inside

This repository contains battle-tested infrastructure code and architecture patterns used in production environments across Fortune 500 companies and innovative startups.

- **📐 Architecture Designs** - Reference architectures with diagrams and documentation
- **🏗️ Terraform Modules** - Reusable infrastructure-as-code components
- **☸️ Kubernetes Configs** - Production-grade manifests and Helm charts
- **🚀 CI/CD Pipelines** - GitHub Actions, GitLab CI, and Jenkins templates
- **🔒 Security Baselines** - CIS benchmarks, policies, and hardening configs
- **📦 Project Templates** - Full-stack application templates ready to deploy

## 🚀 Quick Start

Browse the directories above or jump directly to popular examples:

### Featured Examples

Coming soon! We're adding production-ready examples including:

- **AWS Production Infrastructure** - Multi-region VPC, EKS, RDS with monitoring
- **Kubernetes Multi-Region Setup** - HA clusters with service mesh
- **Complete CI/CD Pipeline** - From commit to production with security scanning
- **Zero Trust Service Mesh** - Istio configuration with mTLS and policies
- **Secrets Management with Vault** - HashiCorp Vault cluster with K8s integration

## 📚 Directory Structure

```
tech-blend-examples/
├── architectures/          # Reference architectures
│   ├── aws-production/     # AWS production setup
│   ├── k8s-multi-region/   # Kubernetes multi-region
│   └── zero-trust-mesh/    # Service mesh security
├── terraform/              # Terraform modules
│   ├── aws/                # AWS modules
│   ├── gcp/                # GCP modules
│   └── azure/              # Azure modules
├── kubernetes/             # Kubernetes manifests
│   ├── monitoring/         # Prometheus, Grafana, Loki
│   ├── security/           # Network policies, RBAC
│   └── gitops/             # ArgoCD, Flux configs
├── ci-cd/                  # CI/CD pipelines
│   ├── github-actions/     # GitHub Actions workflows
│   ├── gitlab-ci/          # GitLab CI configs
│   └── jenkins/            # Jenkins pipelines
├── security/               # Security configurations
│   ├── cis-benchmarks/     # CIS compliance configs
│   ├── network-policies/   # K8s network policies
│   └── vault/              # HashiCorp Vault configs
└── templates/              # Full project templates
    ├── nextjs-aws/         # Next.js on AWS
    ├── microservices-k8s/  # Microservices on K8s
    └── api-gateway/        # API Gateway setup
```

## 💡 How to Use

Each example includes:
- **README.md** - Overview, architecture, and usage instructions
- **Code** - Production-ready configurations
- **Diagrams** - Architecture visualizations (where applicable)
- **Documentation** - Detailed setup and customization guides

### Prerequisites

Depending on the example, you may need:
- AWS/GCP/Azure CLI tools
- Terraform >= 1.5.0
- kubectl >= 1.28
- Helm >= 3.0
- Docker

### Installation

1. Clone this repository:
```bash
git clone https://github.com/YOUR_USERNAME/tech-blend-examples.git
cd tech-blend-examples
```

2. Navigate to the example you want to use:
```bash
cd architectures/aws-production/
```

3. Follow the README in that directory for setup instructions

## 📖 Blog Posts

Many examples have accompanying detailed blog posts:

- [Kubernetes Gateway API: The Modern Replacement for Nginx Ingress](https://techblendconsult.io/blog/kubernetes-gateway-api-nginx-ingress)
- [Service Mesh: The Missing Infrastructure Layer for Microservices](https://techblendconsult.io/blog/service-mesh-microservices-architecture)
- [GitOps: Using Git as Single Source of Truth](https://techblendconsult.io/blog/gitops-continuous-deployment)

Visit our [blog](https://techblendconsult.io/blog) for more technical deep-dives.

## 💬 Community

Join our community to discuss these examples, get help, and share your implementations:

- **Discord**: [Join Tech Blend Community](https://discord.gg/hk4ny22R)
- **LinkedIn**: [Tech Blend Consulting](https://www.linkedin.com/company/tech-blend-consult)
- **Website**: [techblendconsult.io](https://techblendconsult.io)

## 🤝 Contributing

We welcome contributions! Whether it's:
- 🐛 Bug fixes
- 📝 Documentation improvements
- ✨ New examples
- 💡 Suggestions

Please see our [Contributing Guide](CONTRIBUTING.md) for details.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

This means you can:
- ✅ Use commercially
- ✅ Modify and distribute
- ✅ Use privately
- ✅ Include in proprietary software

## 🆘 Need Help?

### Free Resources
- Browse examples in this repo
- Join our [Discord community](https://discord.gg/hk4ny22R)
- Read our [blog posts](https://techblendconsult.io/blog)

### Professional Services

Need custom implementation or have specific requirements?

**Tech Blend Consulting offers:**
- 💼 **Architecture Review** - 2-hour deep-dive with recommendations ($997)
- 🛠️ **Custom Implementation** - We deploy and configure for you ($5k-15k)
- 👥 **Team Training** - Hands-on workshops for your team ($2k/day)
- 🔄 **Ongoing Support** - Retainer-based consulting ($10k+/month)

**Schedule a free 30-min consultation:**
📅 [Book a Call](https://calendly.com/dennis-weston-techblendconsult/intro)

📧 Email: [sales@techblendconsult.io](mailto:sales@techblendconsult.io)

---

**Built with ❤️ by [Tech Blend Consulting](https://techblendconsult.io)**

*Empowering enterprises with expert security, automation, and infrastructure solutions*
