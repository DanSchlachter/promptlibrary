# SAP CAP Development Agents for OpenCode

A comprehensive collection of specialized AI agents for SAP Cloud Application Programming Model (CAP) development with CDS 9.x support.

## Overview

This repository provides a complete set of OpenCode agents designed to accelerate SAP CAP development by offering expert guidance across all phases of the development lifecycle. The agents are provider-agnostic and work with Claude, OpenAI, and other LLM providers.

## Agent Collection

### Central Orchestrator
- **`cap-expert`**: Central orchestration agent that coordinates between specialized agents for typical SAP CAP workflows

### Specialized Agents
1. **`cap-setup-validator`**: Validates local development environment (Node.js, CDS CLI, CF CLI, etc.)
2. **`cap-domain-modeler`**: Expert in CDS schema design, entity relationships, and domain modeling
3. **`cap-service-developer`**: Implements custom handlers and business logic in Node.js
4. **`cap-test-developer`**: Creates unit tests, integration tests, and test data
5. **`cap-cf-deployer`**: Manages Cloud Foundry deployments and MTA configuration
6. **`cap-upgrader`**: Handles CAP version upgrades and migration scripts
7. **`cap-security`**: Implements authorization (@requires, @restrict) and security best practices

## Installation

### Option 1: Global Installation (All Projects)

Copy agents to your global OpenCode configuration:

```bash
# Clone this repository
git clone <repository-url>
cd promptlibrary

# Copy agents to global config
mkdir -p ~/.config/opencode/agents
cp agents/*.md ~/.config/opencode/agents/
```

### Option 2: Project-Specific Installation

Copy agents to your SAP CAP project:

```bash
# In your CAP project root
mkdir -p .opencode/agents

# Copy from this repository
cp /path/to/promptlibrary/project-template/.opencode/agents/*.md .opencode/agents/
```

## Usage

### Using the Central Orchestrator

The `cap-expert` agent is your main entry point. It's a **primary agent** that you can switch to using the Tab key in OpenCode.

```bash
# Switch to CAP Expert mode
<Tab>  # Cycle through primary agents until you see "cap-expert"

# Then ask for help
I want to create a new service for managing employees
```

The orchestrator will automatically delegate to appropriate specialized agents based on your needs.

### Invoking Specialized Agents Directly

You can invoke specialized agents directly using @ mentions:

```bash
# Check environment setup
@cap-setup-validator check if my environment is ready for CAP development

# Design a domain model
@cap-domain-modeler create entities for a book shop with authors, books, and orders

# Implement service logic
@cap-service-developer add validation logic to prevent negative quantities

# Create tests
@cap-test-developer write integration tests for the OrdersService

# Deploy to Cloud Foundry
@cap-cf-deployer prepare deployment configuration for production

# Upgrade CAP version
@cap-upgrader help me upgrade from CAP 7 to CDS 9

# Add security
@cap-security implement role-based access control for admin operations
```

## Typical Workflows

### 1. New Project Setup
```bash
# Switch to cap-expert
<Tab>

# Ask for project setup
I'm starting a new CAP project for an order management system

# The orchestrator will:
# 1. Validate environment (@cap-setup-validator)
# 2. Help with initial project structure
# 3. Guide domain modeling (@cap-domain-modeler)
```

### 2. Feature Development
```bash
# Design data model
@cap-domain-modeler I need to add customer loyalty points to my e-commerce app

# Implement service logic
@cap-service-developer calculate loyalty points when orders are completed

# Add authorization
@cap-security only admins should be able to adjust loyalty points manually

# Create tests
@cap-test-developer write tests for the loyalty points calculation
```

### 3. Deployment
```bash
# Prepare deployment
@cap-cf-deployer create mta.yaml for deploying to Cloud Foundry with HANA

# Validate security before deploying
@cap-security review my authorization annotations for production readiness
```

### 4. Upgrade & Maintenance
```bash
# Upgrade CAP version
@cap-upgrader I want to upgrade from CDS 8 to CDS 9

# Validate environment after upgrade
@cap-setup-validator verify my environment is correctly configured
```

## Technology Stack

The agents are optimized for:
- **CAP Version**: CDS 9.x (latest)
- **Runtime**: Node.js (primary focus)
- **Database**: SQLite (development), SAP HANA (production)
- **Deployment**: Cloud Foundry with MTA
- **Testing**: Jest, Chai, Mocha
- **Security**: XSUAA, OAuth2, JWT

## Team Customization

### Adding Team-Specific Conventions

Create a `prompts/team-conventions.md` file to add your team's coding standards:

```markdown
# Team Coding Conventions

## Naming Conventions
- Entity names: PascalCase (e.g., `OrderItems`)
- Field names: camelCase (e.g., `orderDate`)
- Service names: PascalCase with "Service" suffix (e.g., `CatalogService`)

## Code Organization
- Keep handlers in `srv/` directory
- Domain models in `db/` directory
- Tests in `test/` directory

## Testing Standards
- Minimum 80% code coverage
- Use Jest for all tests
- Follow AAA pattern (Arrange, Act, Assert)

## Security Guidelines
- Always use @requires for authenticated endpoints
- Implement instance-based authorization for sensitive data
- Audit log all administrative actions
```

The agents will automatically reference this file when providing guidance.

## Features

- **Provider-Agnostic**: Works with Claude, OpenAI, and other LLM providers
- **CDS 9 Optimized**: Targets the latest SAP CAP version
- **Comprehensive Coverage**: All aspects of CAP development
- **Best Practices Built-In**: Follows official SAP CAP guidelines
- **Safety Controls**: Permission-based for destructive operations
- **Team Customizable**: Support for team-specific conventions

## Project Structure

```
promptlibrary/
├── agents/                      # Global agents
│   ├── cap-expert.md           # Central orchestrator (primary agent)
│   ├── cap-setup-validator.md  # Environment validation (subagent)
│   ├── cap-domain-modeler.md   # Domain modeling (subagent)
│   ├── cap-service-developer.md# Service implementation (subagent)
│   ├── cap-test-developer.md   # Testing (subagent)
│   ├── cap-cf-deployer.md      # Cloud Foundry deployment (subagent)
│   ├── cap-upgrader.md         # Version upgrades (subagent)
│   └── cap-security.md         # Security & authorization (subagent)
├── project-template/            # Template for project use
│   └── .opencode/
│       └── agents/             # Same agents for project-specific use
├── prompts/                     # Shared prompt templates
│   └── team-conventions.md.template
├── examples/                    # Example usage scenarios
└── README.md                   # This file
```

## Agent Modes

### Primary Agent (cap-expert)
- Accessible via Tab key cycling
- Coordinates other agents
- Handles complex workflows
- Provides high-level guidance

### Subagents (Specialized)
- Accessible via @ mentions
- Deep expertise in specific areas
- Automatically invoked by cap-expert when needed
- Can be used independently

## Requirements

- **OpenCode**: Latest version
- **Node.js**: 18.x or 20.x (LTS)
- **@sap/cds-dk**: Version 8.x or higher
- **Optional**: CF CLI (for deployment), MBT (for MTA builds)

## Best Practices

1. **Start with the Orchestrator**: Use `cap-expert` for complex tasks and let it delegate
2. **Direct Access for Specific Tasks**: Use @ mentions for focused, single-domain tasks
3. **Environment First**: Always validate your setup with `@cap-setup-validator` before starting
4. **Test as You Go**: Invoke `@cap-test-developer` after implementing features
5. **Security by Default**: Consult `@cap-security` early in the development process

## Examples

See the `examples/` directory for complete usage scenarios:
- Creating a new CAP project from scratch
- Adding a new service to an existing project
- Implementing complex authorization rules
- Deploying to Cloud Foundry
- Upgrading from CDS 7 to CDS 9

## Troubleshooting

### Agents Not Appearing
- Ensure agents are in `~/.config/opencode/agents/` (global) or `.opencode/agents/` (project)
- Restart OpenCode after adding new agents

### Agent Not Responding as Expected
- Check agent description matches your use case
- Try the central `cap-expert` orchestrator instead
- Provide more context in your prompt

### Permission Errors
- Some agents require approval for destructive operations (e.g., deployment)
- Review the permission settings in each agent's frontmatter

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Add or improve agents
4. Submit a pull request

## Resources

- [SAP CAP Documentation](https://cap.cloud.sap/docs/)
- [CDS 9 Release Notes](https://cap.cloud.sap/docs/releases/)
- [OpenCode Documentation](https://opencode.ai/docs/)
- [OpenCode Agents Guide](https://opencode.ai/docs/agents/)

## License

MIT License - See LICENSE file for details

## Support

- Issues: Open an issue in this repository
- Questions: Discussion forum or team chat
- SAP CAP Issues: [SAP Community](https://answers.sap.com/tags/9f13aee1-834c-4105-8e43-ee442775e5ce)

## Changelog

### Version 1.0.0 (Initial Release)
- 8 specialized agents for SAP CAP development
- Central orchestrator (cap-expert)
- CDS 9.x support
- Provider-agnostic design
- Comprehensive documentation

---

**Happy CAP Development!** 🚀

For questions or feedback, please open an issue or contact the maintainers.
