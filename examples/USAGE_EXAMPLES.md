# Usage Examples

This document provides practical examples of using the SAP CAP agents in real-world scenarios.

## Example 1: Creating a New CAP Project from Scratch

### Scenario
You're starting a new e-commerce project and need to set up everything from scratch.

### Steps

#### 1. Validate Environment
```bash
@cap-setup-validator check if my environment is ready for CAP development
```

**Expected Output:**
```
Environment Status: ✅ READY

Core Tools:
  Node.js: ✅ v20.11.0
  npm: ✅ v10.2.4
  @sap/cds-dk: ✅ v8.1.0
  SQLite: ✅ v3.43.2

You're ready to start CAP development!
```

#### 2. Design Domain Model
```bash
@cap-domain-modeler I need to create a domain model for an e-commerce platform with:
- Products with categories
- Customers
- Orders with multiple order items
- Inventory tracking
```

**Agent Response:**
The agent will create CDS schema with proper entities, associations, and compositions.

#### 3. Implement Business Logic
```bash
@cap-service-developer implement order processing logic that:
- Validates stock availability
- Reduces inventory when order is placed
- Calculates order total
- Creates order items
```

#### 4. Add Security
```bash
@cap-security implement authorization where:
- All users can view products
- Authenticated users can create orders
- Admins can manage products and view all orders
```

#### 5. Create Tests
```bash
@cap-test-developer create comprehensive tests for:
- Order creation flow
- Stock validation
- Authorization rules
```

---

## Example 2: Adding a New Feature to Existing Project

### Scenario
Adding customer loyalty points feature to an existing e-commerce app.

### Steps

#### 1. Extend Domain Model
```bash
@cap-domain-modeler add loyalty points functionality:
- Customers have loyalty points balance
- Points are earned on purchases (1 point per $10)
- Points can be redeemed for discounts
- Track points transactions
```

#### 2. Implement Points Logic
```bash
@cap-service-developer implement loyalty points logic:
- Calculate points earned on order completion
- Apply points discount when redeeming
- Prevent negative points balance
- Create audit trail for points transactions
```

#### 3. Add Authorization
```bash
@cap-security ensure:
- Users can view their own points
- Users can redeem their own points
- Admins can adjust points manually
- Audit all points adjustments
```

#### 4. Test the Feature
```bash
@cap-test-developer create tests for:
- Points calculation on purchase
- Points redemption flow
- Negative balance prevention
- Admin adjustment capabilities
```

---

## Example 3: Deploying to Cloud Foundry

### Scenario
You've developed a CAP application locally and need to deploy it to Cloud Foundry.

### Steps

#### 1. Review Current Setup
```bash
@cap-setup-validator check if I have all deployment tools installed
```

#### 2. Create Deployment Configuration
```bash
@cap-cf-deployer create mta.yaml for:
- Node.js service module
- HANA HDI container
- XSUAA authentication
- Destination service for external APIs
- Approuter for UI
```

#### 3. Configure Security
```bash
@cap-security review my xs-security.json and ensure:
- Proper scopes defined
- Role templates configured
- Role collections for Admin and User roles
```

#### 4. Build and Deploy
```bash
@cap-cf-deployer help me build and deploy:
1. Build MTA archive
2. Deploy to dev space
3. Test the deployment
4. Create production extension descriptor
```

---

## Example 4: Upgrading CAP Version

### Scenario
Your project is on CDS 7, and you want to upgrade to CDS 9.

### Steps

#### 1. Assess Current Version
```bash
@cap-upgrader analyze my current setup and create an upgrade plan from CDS 7 to CDS 9
```

#### 2. Review Breaking Changes
```bash
@cap-upgrader what are the breaking changes I need to handle?
```

#### 3. Execute Upgrade
```bash
@cap-upgrader guide me through:
1. Updating package.json dependencies
2. Running migration tool
3. Updating code patterns
4. Fixing breaking changes
```

#### 4. Validate After Upgrade
```bash
@cap-setup-validator verify my environment after the upgrade

@cap-test-developer run all tests and report any failures
```

---

## Example 5: Implementing Complex Authorization

### Scenario
You need to implement multi-level authorization with regional access control.

### Steps

#### 1. Design Authorization Model
```bash
@cap-security I need to implement:
- Regional managers can only see data for their region
- Sales reps see only their own customers
- Executives see everything
- Country managers see their country's data

The user's region is stored in XSUAA attributes.
```

#### 2. Implement Instance-Based Authorization
```bash
@cap-security implement instance-based authorization using:
- @restrict annotations with where clauses
- $user.attr.region for regional filtering
- Programmatic checks in handlers
```

#### 3. Test Authorization
```bash
@cap-test-developer create tests that verify:
- Regional managers see only their region's data
- Sales reps see only their customers
- Unauthorized access is blocked
- Admins have full access
```

---

## Example 6: Performance Optimization

### Scenario
Your service is slow, and you need to optimize queries and performance.

### Steps

#### 1. Review Data Model
```bash
@cap-domain-modeler review my entity definitions and suggest:
- Proper indexing strategies
- Association vs composition choices
- Potential N+1 query issues
```

#### 2. Optimize Service Handlers
```bash
@cap-service-developer optimize my handlers:
- Eliminate N+1 queries
- Use batch operations
- Implement caching where appropriate
- Add pagination
```

#### 3. Add Performance Tests
```bash
@cap-test-developer create performance tests that:
- Measure response times
- Test with large datasets
- Identify slow queries
```

---

## Example 7: Troubleshooting Deployment Issues

### Scenario
Your Cloud Foundry deployment is failing.

### Steps

#### 1. Analyze Deployment Error
```bash
@cap-cf-deployer my deployment failed with this error:
[paste error message]

Help me troubleshoot.
```

#### 2. Check Configuration
```bash
@cap-cf-deployer review my mta.yaml for:
- Correct service bindings
- Proper memory allocations
- Valid resource configurations
```

#### 3. Validate Services
```bash
@cap-cf-deployer help me verify:
- HANA HDI container is created correctly
- XSUAA service is bound
- Service credentials are accessible
```

---

## Example 8: Multi-Tenant Application Setup

### Scenario
Converting a single-tenant app to multi-tenant.

### Steps

#### 1. Update Data Model
```bash
@cap-domain-modeler add multi-tenancy support:
- Enable @cds.persistence annotations
- Plan tenant isolation strategy
```

#### 2. Configure XSUAA for Multi-Tenancy
```bash
@cap-security update xs-security.json for:
- tenant-mode: shared
- Multi-tenant OAuth configuration
```

#### 3. Update Deployment Configuration
```bash
@cap-cf-deployer update mta.yaml for multi-tenancy:
- Add SaaS registry service
- Configure subscription callbacks
- Update service bindings
```

#### 4. Test Multi-Tenant Isolation
```bash
@cap-test-developer create tests that verify:
- Tenant data isolation
- Subscription/unsubscription flows
- Cross-tenant access prevention
```

---

## Example 9: Integrating External APIs

### Scenario
You need to integrate a third-party shipping API into your order management system.

### Steps

#### 1. Plan Integration
```bash
@cap-service-developer I need to integrate a shipping API that:
- Calculates shipping costs
- Creates shipping labels
- Tracks shipments

Show me the best pattern for external API calls.
```

#### 2. Add Destination Configuration
```bash
@cap-cf-deployer configure destination service for:
- External shipping API
- Authentication (API key)
- Proxy settings if needed
```

#### 3. Implement Error Handling
```bash
@cap-service-developer implement robust error handling for:
- API timeouts
- Network failures
- Invalid responses
- Retry logic
```

#### 4. Test Integration
```bash
@cap-test-developer create tests with:
- Mocked external API responses
- Error scenario testing
- Timeout handling
```

---

## Example 10: Creating Custom Actions and Functions

### Scenario
You need to implement custom business operations beyond CRUD.

### Steps

#### 1. Define Custom Actions
```bash
@cap-domain-modeler add custom actions to my service:
- submitOrder (action) - processes an order
- calculateDiscount (function) - calculates discount
- cancelOrder (action) - cancels an order
- getRecommendations (function) - gets product recommendations
```

#### 2. Implement Action Logic
```bash
@cap-service-developer implement the submitOrder action that:
- Validates order data
- Checks inventory
- Creates order record
- Sends confirmation email
- Returns order ID
```

#### 3. Add Authorization
```bash
@cap-security secure custom actions:
- submitOrder requires 'User' role
- cancelOrder requires ownership or 'Admin' role
- calculateDiscount is public
- getRecommendations requires authentication
```

#### 4. Test Actions
```bash
@cap-test-developer test custom actions:
- Happy path for submitOrder
- Error cases (insufficient stock, invalid data)
- Authorization checks
- cancelOrder permissions
```

---

## Tips for Effective Agent Usage

### 1. Start with Context
Provide clear context about your project, existing code, and goals.

**Good:**
```
@cap-domain-modeler I have an existing book shop with Books and Authors.
I need to add a review system where customers can rate and review books.
Reviews should be associated with both the book and the customer.
```

**Less Effective:**
```
Add reviews to my app
```

### 2. Be Specific About Requirements
The more specific you are, the better the agent can help.

**Good:**
```
@cap-security implement authorization where:
- Authenticated users can create reviews
- Users can edit/delete only their own reviews
- Admins can moderate (delete) any review
- Reviews are read-only after 7 days (except for admins)
```

### 3. Ask for Explanations
Don't hesitate to ask agents to explain their recommendations.

```
@cap-domain-modeler why did you use Composition instead of Association for OrderItems?
```

### 4. Iterate and Refine
Work iteratively with the agents.

```
@cap-service-developer the validation logic you provided is good, but I also need to:
- Check if the product is discontinued
- Validate minimum order quantity
- Apply bulk order discounts
```

### 5. Combine Agents for Complex Tasks
Let the orchestrator coordinate, or invoke multiple agents manually.

```
# Using orchestrator
<Tab to cap-expert>
I need to add a wishlist feature with full testing and security

# Or manual coordination
@cap-domain-modeler add wishlist entities
@cap-service-developer implement wishlist operations
@cap-security protect wishlist (users see only their own)
@cap-test-developer test wishlist functionality
```

---

## Common Workflows Cheat Sheet

| Task | Agent to Use | Example Prompt |
|------|-------------|----------------|
| Check environment | `@cap-setup-validator` | Check if I'm ready for CAP development |
| Design entities | `@cap-domain-modeler` | Create entities for [domain] |
| Write handlers | `@cap-service-developer` | Implement logic for [operation] |
| Add security | `@cap-security` | Implement authorization for [entity] |
| Create tests | `@cap-test-developer` | Test [feature] |
| Deploy app | `@cap-cf-deployer` | Deploy to Cloud Foundry |
| Upgrade CAP | `@cap-upgrader` | Upgrade from CDS X to CDS 9 |
| Complex workflow | `cap-expert` (Tab key) | [Describe full workflow] |

---

For more examples and detailed documentation, see the README.md file.
