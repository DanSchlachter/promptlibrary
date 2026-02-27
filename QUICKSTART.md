# Quick Start Guide

Get started with SAP CAP agents in under 5 minutes!

## Installation

### For All Projects (Recommended)

```bash
# Clone the repository
git clone <repository-url>
cd promptlibrary

# Copy agents to OpenCode global config
mkdir -p ~/.config/opencode/agents
cp agents/*.md ~/.config/opencode/agents/

# Restart OpenCode or start it in your CAP project
cd /path/to/your/cap/project
opencode
```

### For Single Project

```bash
# In your CAP project root
mkdir -p .opencode/agents

# Copy from repository
cp /path/to/promptlibrary/project-template/.opencode/agents/*.md .opencode/agents/
```

## First Steps

### 1. Validate Your Environment

```bash
# In OpenCode
@cap-setup-validator check if my environment is ready
```

### 2. Switch to CAP Expert Mode

Press `Tab` key in OpenCode to cycle through primary agents until you see **cap-expert**.

### 3. Start Building

Ask the orchestrator for help:

```
I want to create a bookshop service with books and authors
```

Or invoke specific agents:

```bash
# Design data model
@cap-domain-modeler create entities for a bookshop

# Implement service logic
@cap-service-developer add custom validation

# Add security
@cap-security implement authorization

# Create tests
@cap-test-developer write integration tests
```

## Available Agents

| Agent | Type | Purpose | Invoke With |
|-------|------|---------|-------------|
| cap-expert | Primary | Central orchestrator | Tab key |
| cap-setup-validator | Subagent | Environment validation | @cap-setup-validator |
| cap-domain-modeler | Subagent | CDS schema design | @cap-domain-modeler |
| cap-service-developer | Subagent | Business logic | @cap-service-developer |
| cap-test-developer | Subagent | Testing | @cap-test-developer |
| cap-cf-deployer | Subagent | Deployment | @cap-cf-deployer |
| cap-upgrader | Subagent | Version upgrades | @cap-upgrader |
| cap-security | Subagent | Authorization | @cap-security |

## Common Tasks

### Create a New Feature
```
<Tab to cap-expert>
I need to add order management functionality with:
- Orders entity
- Order items
- Stock validation
- Authorization
```

### Deploy to Cloud Foundry
```
@cap-cf-deployer create mta.yaml for my project and help me deploy
```

### Add Security
```
@cap-security implement role-based access:
- Admins can do everything
- Users can read and create orders
- Public can view products
```

### Upgrade CAP Version
```
@cap-upgrader help me upgrade from CDS 8 to CDS 9
```

## Tips

1. **Start with cap-expert** for complex workflows
2. **Use @ mentions** for specific tasks
3. **Provide context** - the more details, the better
4. **Ask questions** - agents can explain their recommendations
5. **Iterate** - refine and improve based on agent suggestions

## Next Steps

- Read the full [README.md](README.md) for detailed documentation
- Check [USAGE_EXAMPLES.md](examples/USAGE_EXAMPLES.md) for real-world scenarios
- Customize with [team-conventions.md.template](prompts/team-conventions.md.template)

## Need Help?

- Review the examples in `examples/USAGE_EXAMPLES.md`
- Check agent descriptions in the `agents/` directory
- Read the comprehensive README.md

Happy coding! 🚀
