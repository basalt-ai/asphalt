# Contributing to Asphalt

We're building the future of self-improving AI agents! Your contributions help create autonomous optimization that actually works in production.

## Quick Start

1. **Fork and clone**
   ```bash
   gh repo fork basalt-ai/asphalt --clone
   cd asphalt
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Run tests**
   ```bash
   npm test
   ```

4. **Make changes and verify**
   ```bash
   npm run build
   npm run lint
   npm test
   ```

## Development Setup

### Prerequisites

- **Node.js** 20+ and npm
- **TypeScript** 5.7+
- **Git** with GitHub CLI (`gh`) recommended
- **Docker** (for integration testing with databases/APIs)

### Project Structure

```
asphalt/
├── src/
│   ├── core/          # Core optimization engine and experiment framework
│   ├── signals/       # Business and behavioral signal connectors
│   ├── mutations/     # Safe agent mutation algorithms
│   ├── testing/       # A/B testing and statistical analysis
│   ├── memory/        # Compounding knowledge and learning systems
│   └── cli/           # Command-line interface
├── connectors/        # Data source integrations (databases, APIs, analytics)
├── examples/          # Example agents and optimization configurations
├── docs/              # Documentation
└── tests/             # Test files
```

### Running Locally

```bash
# Build and watch for changes
npm run dev

# Run CLI locally
./bin/asphalt.js --help

# Run specific tests
npm test -- --grep "mutation engine"

# Start test environment with Docker
docker-compose up -d
npm run test:integration
```

## What We're Looking For

### High Priority
- **Data source connectors** (Salesforce, HubSpot, Stripe, PostgreSQL, etc.)
- **Mutation algorithms** for different agent types (RAG, tool-using, conversational)
- **Statistical testing frameworks** for A/B experiments and significance testing
- **Production safety mechanisms** for rollback and circuit breaking

### Medium Priority
- **Agent framework integrations** (LangChain, Mastra, AutoGen, CrewAI)
- **Memory and learning algorithms** that generalize across domains
- **Behavioral signal extractors** from user interaction logs
- **Performance optimizations** for real-time optimization loops

### Lower Priority
- **Dashboard and visualization** components
- **Advanced analytics** and reporting features
- **Documentation improvements** and examples
- **Compliance and audit** features

## Contribution Guidelines

### Code Style

We use Biome for linting and formatting:

```bash
# Check formatting and lints
npm run lint

# Auto-fix issues
npm run lint:fix

# Format code
npm run format
```

**Key conventions:**
- Use TypeScript with strict settings
- Favor composition over inheritance
- Write self-documenting code with clear names
- Add comprehensive JSDoc for public APIs
- Ensure thread-safety for concurrent operations
- Handle failures gracefully with proper fallbacks

### Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add Salesforce connector for business signal integration
fix: prevent race condition in mutation testing framework
docs: add quickstart guide for autonomous optimization
test: add integration tests for A/B experiment lifecycle
perf: optimize signal aggregation for high-throughput workloads
```

### Pull Request Process

1. **Create a feature branch** from `main`
   ```bash
   git checkout -b feat/your-feature-name
   ```

2. **Make focused changes** - one feature/fix per PR

3. **Add comprehensive tests**
   ```bash
   # Unit tests
   npm test

   # Integration tests (requires Docker)
   npm run test:integration

   # Load tests for performance-critical changes
   npm run test:load
   ```

4. **Update documentation** for API changes or new features

5. **Ensure CI passes**
   - All tests pass
   - Linting and type checking pass
   - Performance benchmarks don't regress
   - Security scans pass

6. **Write a detailed PR description**
   - What problem does this solve?
   - What approach did you take?
   - How was it tested (especially safety mechanisms)?
   - Any production considerations?
   - Breaking changes?

### Testing

We use Jest and specialized testing frameworks:

```bash
# Run all tests
npm test

# Run tests in watch mode  
npm test -- --watch

# Run specific test categories
npm test -- --testPathPattern=mutations
npm test -- --testPathPattern=signals
npm test -- --testPathPattern=experiments

# Run integration tests
npm run test:integration

# Run load/performance tests
npm run test:load
```

**Test categories:**
- **Unit tests**: Individual functions and classes
- **Integration tests**: End-to-end optimization workflows
- **Load tests**: Performance under production-like loads
- **Safety tests**: Rollback mechanisms and failure modes
- **Statistical tests**: A/B testing framework validation

### Safety and Production Readiness

Asphalt runs in production environments with real user traffic. Safety is paramount:

#### Required for Production Features
- **Comprehensive error handling** with graceful degradation
- **Rollback mechanisms** that trigger automatically on regressions
- **Rate limiting** and circuit breakers for external API calls
- **Data privacy compliance** (anonymization, retention policies)
- **Audit logging** for all optimization decisions
- **Load testing** results showing performance under stress

#### Safety Checklist
- [ ] Mutations preserve semantic meaning within configurable thresholds
- [ ] Experiments can be instantly rolled back without data loss
- [ ] Signal collection respects user privacy and data policies
- [ ] Memory systems handle edge cases (empty data, corrupted state)
- [ ] All external integrations have proper timeouts and retries
- [ ] Statistical tests properly handle multiple comparisons and early stopping

### Documentation

Update docs when you:
- Add new connectors or mutation types
- Change APIs or configuration formats
- Add production deployment considerations
- Create new examples or integration guides

```bash
# Build docs locally
npm run docs:build

# Serve docs for development  
npm run docs:dev

# Generate API documentation
npm run docs:api
```

## Domain Expertise Contributions

Asphalt benefits from domain knowledge in several areas:

### Production AI Systems
- **MLOps** - Model versioning, deployment, monitoring
- **Agent architectures** - RAG systems, tool-using agents, multi-agent workflows
- **Production optimization** - A/B testing, feature flags, gradual rollouts

### Statistics and Experimentation
- **Causal inference** - Identifying causal relationships in optimization
- **Sequential testing** - Early stopping and adaptive experiments
- **Bayesian optimization** - Efficient search through agent parameter spaces

### Business Intelligence
- **Metrics design** - Choosing the right business signals to optimize for
- **Data warehousing** - Efficient signal collection and aggregation
- **Real-time analytics** - Low-latency optimization feedback loops

## Getting Help

- **Questions?** Open a [GitHub Discussion](https://github.com/basalt-ai/asphalt/discussions)
- **Found a bug?** [File an issue](https://github.com/basalt-ai/asphalt/issues)
- **Need real-time help?** Join our [Discord](https://discord.gg/yW2RyZKY)
- **Production deployment?** Check our enterprise support options

## Areas Needing Expertise

We especially welcome contributions in:

### Data Engineering
- **Real-time pipelines** - Stream processing for live optimization
- **Data quality** - Validation and cleansing of business signals  
- **Privacy engineering** - Anonymization and compliance frameworks

### Machine Learning
- **Online learning** - Algorithms that improve with each interaction
- **Transfer learning** - Applying optimizations across different agents
- **Reinforcement learning** - Agent improvement through environment feedback

### Production Systems
- **Distributed systems** - Scaling optimization across multiple agents
- **Monitoring** - Observability for autonomous optimization systems
- **Security** - Protecting optimization systems from adversarial attacks

## Code of Conduct

Be professional, collaborative, and safety-conscious. We're building systems that make autonomous decisions in production.

Key principles:
- **Safety first** - Always consider production impact and failure modes
- **Data responsibility** - Respect user privacy and business data sensitivity
- **Transparency** - Make optimization decisions explainable and auditable
- **Collaboration** - Different perspectives improve robustness

## Recognition

Contributors are recognized through:
- **README.md** - Major contributors listed
- **Release notes** - Contributors credited for their changes
- **Conference opportunities** - Present contributions at AI/ML conferences
- **Beta access** - Early access to new features and enterprise tools

## Production Deployment Support

If you're using Asphalt in production, we provide:
- **Architecture reviews** - Help with deployment planning
- **Performance optimization** - Assistance with scale challenges
- **Custom connectors** - Help building integrations for your stack
- **Priority support** - Faster response times for production issues

## Questions?

Don't hesitate to reach out! Open a discussion, join Discord, or tag @basalt-ai in your PR.

Thanks for helping build the future of autonomous AI agent optimization! 🚀