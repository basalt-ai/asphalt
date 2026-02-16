<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo_white.png" />
  <source media="(prefers-color-scheme: light)" srcset="assets/logo.png" />
  <img src="assets/logo.png" alt="Asphalt" width="200" />
</picture>

<br>

**Self-improving engine for production AI agents** — Autonomous optimization that connects business metrics to agent improvements.

**[Documentation](docs/)** · **[Join Discord](https://discord.gg/yW2RyZKY)**

<br>

![Build Status](https://github.com/basalt-ai/asphalt/actions/workflows/test.yml/badge.svg)
[![npm version](https://img.shields.io/npm/v/@basalt-ai/asphalt.svg)](https://www.npmjs.com/package/@basalt-ai/asphalt)
[![License: Apache-2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-blue.svg)](https://www.typescriptlang.org/)
[![Node.js](https://img.shields.io/badge/Node.js-20%2B-green.svg)](https://nodejs.org/)
[![Discord](https://img.shields.io/discord/1471362791884455980?color=7289da&label=Discord&logo=discord&logoColor=white)](https://discord.gg/yW2RyZKY)

<br />

### Part of the Basalt Stack

<p>
  <strong>Cobalt</strong> (Testing) + <strong>Diamond</strong> (Datasets) + <strong>Limestone</strong> (Judges) + <strong>Asphalt</strong> (Optimization)
</p>

</div>

---

## Table of Contents

- [Why Asphalt](#why-asphalt)
- [Quickstart](#quickstart)
- [Core Concepts](#core-concepts)
- [Business Signal Integration](#business-signal-integration)
- [Safe Mutation Engine](#safe-mutation-engine)
- [Controlled Traffic Testing](#controlled-traffic-testing)
- [Compounding Memory](#compounding-memory)
- [CLI](#cli)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

## Why Asphalt

AI agents are static once deployed. You manually observe performance, run evals, tweak prompts, and hope for the best. The feedback loop is slow, disconnected from business metrics, and requires constant human intervention.

Asphalt changes this. It's an autonomous optimization engine that connects to your business and behavioral signals, learns from expert feedback, generates safe mutations of your agent, tests them on controlled traffic, and promotes only statistically significant improvements. With a compounding memory layer that accumulates learnings over time.

## Quickstart

```bash
npm install @basalt-ai/asphalt
npx asphalt init
npx asphalt connect --agent ./src/agents/support-bot.ts
```

Set up your first optimization loop:

```typescript
// asphalt.config.ts
import { defineOptimizer, signals, mutations } from '@basalt-ai/asphalt'

export default defineOptimizer({
  agent: {
    name: 'customer-support',
    endpoint: '/api/agents/support',
    type: 'conversational'
  },

  // Connect business metrics
  signals: {
    business: [
      signals.metric('customer_satisfaction', {
        source: 'zendesk',
        query: 'avg(satisfaction_score)',
        weight: 0.4
      }),
      signals.metric('resolution_time', {
        source: 'database', 
        query: 'avg(resolution_minutes)',
        target: 'minimize',
        weight: 0.3
      }),
      signals.metric('escalation_rate', {
        source: 'api',
        endpoint: '/metrics/escalations',
        target: 'minimize',
        weight: 0.2
      })
    ],
    
    behavioral: [
      signals.behavior('user_frustration', {
        indicators: ['repeat_queries', 'caps_usage', 'short_responses'],
        weight: 0.1
      })
    ],

    expert: [
      signals.feedback('support_manager', {
        reviews: 'daily',
        categories: ['accuracy', 'empathy', 'efficiency']
      })
    ]
  },

  // Define safe mutations
  mutations: {
    prompt: {
      techniques: ['instruction_variants', 'example_selection', 'tone_adjustment'],
      safety: { semantic_similarity: 0.85 }
    },
    
    reasoning: {
      techniques: ['chain_of_thought', 'step_back', 'self_reflection'],
      constraints: ['preserve_output_format']
    },

    tools: {
      techniques: ['tool_selection', 'parameter_tuning'],
      safety: { test_on_staging: true }
    }
  },

  // Controlled experimentation
  testing: {
    traffic_split: 0.05, // Test on 5% of traffic
    duration: '7d',
    significance: 0.95,
    early_stopping: true
  },

  // Memory and learning
  memory: {
    enabled: true,
    retain: ['successful_mutations', 'failure_patterns', 'user_preferences'],
    decay: '90d' // Gradually forget old learnings
  }
})
```

```bash
npx asphalt optimize --continuous
```

## Core Concepts

### Signal Integration

Asphalt connects to business metrics, behavioral indicators, and expert feedback to understand what "better" means for your specific agent and use case.

```typescript
// Business metrics from your data sources
const businessSignals = [
  signal.revenue('conversion_rate', {
    source: 'analytics',
    query: 'conversions / sessions',
    timeframe: '24h'
  }),
  
  signal.cost('api_usage', {
    source: 'billing',
    query: 'sum(api_costs)',
    target: 'minimize'
  })
]

// Behavioral patterns from user interactions  
const behaviorSignals = [
  signal.satisfaction('user_engagement', {
    indicators: ['session_duration', 'messages_per_session', 'return_rate'],
    aggregation: 'weighted_average'
  }),
  
  signal.frustration('negative_indicators', {
    patterns: ['repeated_questions', 'escalation_requests', 'session_abandonment'],
    threshold: 0.15
  })
]

// Expert feedback loops
const expertSignals = [
  signal.expert('domain_specialist', {
    schedule: 'weekly',
    sample_size: 50,
    focus: ['accuracy', 'domain_coverage', 'edge_cases']
  })
]
```

### Safe Mutation Engine

Generate variations of your agent that are semantically similar but potentially better performing. All mutations are safety-checked before deployment.

```typescript
const mutationEngine = mutations.create({
  techniques: [
    // Prompt engineering mutations
    mutations.prompt.instruction_variants({
      preserve_intent: true,
      max_deviation: 0.2,
      techniques: ['reframing', 'specificity_adjustment', 'tone_variation']
    }),
    
    // Reasoning pattern mutations
    mutations.reasoning.chain_variants({
      patterns: ['sequential', 'tree_search', 'reflection'],
      preserve_logic: true
    }),
    
    // Context and example mutations
    mutations.context.example_selection({
      strategy: 'dynamic_retrieval',
      similarity_threshold: 0.8,
      diversity_factor: 0.3
    }),
    
    // Tool usage mutations  
    mutations.tools.selection_optimization({
      consider: ['latency', 'accuracy', 'cost'],
      constraints: ['output_format', 'safety_checks']
    })
  ],
  
  safety: {
    semantic_similarity: 0.85, // Must be 85% similar to original
    output_validation: true,   // Validate outputs match schema
    fallback_enabled: true,    // Fall back to original on failure
    human_review: { threshold: 0.7 } // Human review if confidence < 70%
  }
})
```

### Controlled Experimentation

Test mutations on controlled traffic with statistical rigor. Only promote improvements that are statistically significant.

```typescript
const experiment = asphalt.experiment({
  name: 'prompt-optimization-v3',
  
  variants: {
    control: currentAgent,
    treatment: mutatedAgent
  },
  
  traffic: {
    allocation: { control: 0.95, treatment: 0.05 },
    targeting: { 
      users: 'returning_customers', // Test on familiar users first
      exclude: 'vip_customers' // Don't risk VIP experience
    }
  },
  
  success_metrics: [
    'customer_satisfaction > 4.2',
    'resolution_time < 300_seconds', 
    'escalation_rate < 0.08'
  ],
  
  guardrails: [
    'error_rate < 0.01',
    'response_time < 2_seconds',
    'cost_per_interaction < $0.05'
  ],
  
  statistical: {
    significance: 0.95,
    power: 0.80,
    minimum_sample_size: 1000,
    early_stopping: true // Stop early if clear winner
  }
})

await experiment.run()
```

## Business Signal Integration

Connect Asphalt to your business metrics for optimization that matters:

### Data Source Connectors

```typescript
// Database connections
signals.database({
  connection: process.env.DATABASE_URL,
  queries: {
    user_satisfaction: `
      SELECT AVG(rating) 
      FROM feedback 
      WHERE agent_id = $1 AND created_at > NOW() - INTERVAL '24h'
    `
  }
})

// API integrations
signals.api({
  base_url: 'https://api.zendesk.com',
  auth: { token: process.env.ZENDESK_TOKEN },
  endpoints: {
    csat_score: '/api/v2/satisfaction_ratings',
    resolution_time: '/api/v2/tickets/metrics'
  }
})

// Analytics platforms
signals.analytics({
  google_analytics: {
    property_id: 'GA_PROPERTY_ID',
    metrics: ['conversions', 'bounce_rate', 'session_duration']
  },
  
  mixpanel: {
    project_id: 'MIXPANEL_PROJECT',
    events: ['agent_interaction', 'goal_completion']
  }
})
```

### Custom Signal Processors

```typescript
// Complex business logic
const customSignal = signal.custom('net_promoter_score', {
  compute: async ({ timeframe, agent_id }) => {
    const responses = await db.query(`
      SELECT score FROM nps_surveys 
      WHERE agent_interaction = true 
      AND created_at > $1
    `, [timeframe])
    
    const promoters = responses.filter(r => r.score >= 9).length
    const detractors = responses.filter(r => r.score <= 6).length
    const total = responses.length
    
    return {
      value: ((promoters - detractors) / total) * 100,
      confidence: total > 30 ? 0.95 : 0.7,
      metadata: { sample_size: total }
    }
  }
})
```

## Safe Mutation Engine

Generate agent improvements while maintaining safety and reliability:

### Prompt Mutations

```typescript
const promptMutations = [
  // Instruction clarity improvements
  mutations.instruction.clarity({
    techniques: ['specificity', 'examples', 'constraints'],
    preserve: ['intent', 'tone', 'output_format']
  }),
  
  // Context optimization
  mutations.context.optimization({
    strategies: ['relevance_ranking', 'length_optimization', 'recency_weighting'],
    max_context_length: 4000
  }),
  
  // Few-shot example selection
  mutations.examples.dynamic({
    selection: 'similarity_based',
    diversity: 0.3,
    max_examples: 5
  })
]
```

### Reasoning Mutations

```typescript
const reasoningMutations = [
  // Chain of thought variations
  mutations.reasoning.cot_variants({
    styles: ['step_by_step', 'question_decomposition', 'assumption_checking'],
    complexity: 'adaptive' // Adjust based on query complexity
  }),
  
  // Self-reflection mechanisms
  mutations.reasoning.reflection({
    triggers: ['uncertainty', 'conflicting_information'],
    depth: 2 // Maximum reflection rounds
  })
]
```

## Controlled Traffic Testing

Safe, statistically rigorous testing in production:

### Progressive Rollouts

```typescript
const rollout = asphalt.rollout({
  stages: [
    { traffic: 0.01, duration: '6h', gate: 'no_regressions' },
    { traffic: 0.05, duration: '24h', gate: 'positive_signals' }, 
    { traffic: 0.20, duration: '72h', gate: 'significance_achieved' },
    { traffic: 1.00, gate: 'manual_approval' }
  ],
  
  rollback: {
    triggers: ['error_rate > 0.02', 'satisfaction < baseline'],
    speed: 'immediate'
  }
})
```

### A/B Testing Framework

```typescript
const abTest = asphalt.test({
  hypothesis: 'Improved context retrieval increases resolution rate',
  
  variants: {
    control: { context_method: 'keyword_search' },
    treatment: { context_method: 'semantic_search' }
  },
  
  success_criteria: [
    'resolution_rate_improvement > 0.05',
    'user_satisfaction >= baseline',
    'response_time <= baseline * 1.1'
  ],
  
  statistical: {
    significance: 0.95,
    minimum_effect_size: 0.03,
    sequential_testing: true
  }
})
```

## Compounding Memory

Learn and accumulate knowledge over time:

### Mutation History

```typescript
// Track what works
const memorySystem = asphalt.memory({
  successful_mutations: {
    retention: 'permanent',
    indexing: ['domain', 'user_type', 'query_category'],
    learning: 'pattern_extraction'
  },
  
  failed_experiments: {
    retention: '90d',
    learning: 'failure_analysis',
    prevention: 'similarity_blocking'
  },
  
  user_preferences: {
    retention: '180d',
    personalization: true,
    privacy: 'anonymized'
  }
})
```

### Knowledge Transfer

```typescript
// Apply learnings to new scenarios
const knowledge = await asphalt.knowledge.extract({
  from: 'customer_support_improvements',
  patterns: ['prompt_structures', 'context_strategies', 'reasoning_approaches'],
  generalization: 'domain_agnostic'
})

await asphalt.knowledge.apply({
  to: 'sales_agent',
  knowledge: knowledge,
  adaptation: 'domain_specific_tuning'
})
```

## CLI

```bash
asphalt init                                # Initialize Asphalt project
asphalt connect --agent <path>             # Connect to your agent
asphalt signals add --type business        # Add business metric signals  
asphalt optimize --continuous              # Start continuous optimization
asphalt experiment create --name <name>    # Create A/B test experiment
asphalt rollout --variant <id>            # Progressive rollout of improvements
asphalt memory export --format json       # Export learned knowledge
asphalt dashboard                          # Launch optimization dashboard
asphalt alerts setup                       # Configure performance alerts
```

## Roadmap

Asphalt is open source and community-driven. [Tell us what matters to you](https://github.com/basalt-ai/asphalt/discussions/1).

| Status | Feature |
|--------|---------|
| :construction: | **Signal integration framework** - Connect business and behavioral metrics |
| :construction: | **Safe mutation engine** - Generate and validate agent improvements |
| :crystal_ball: | **Controlled experimentation** - A/B testing with statistical rigor |
| :crystal_ball: | **Compounding memory** - Learn and accumulate knowledge over time |
| :crystal_ball: | **Auto-optimization** - Fully autonomous improvement loops |
| :crystal_ball: | **Multi-agent orchestration** - Optimize agent teams and workflows |
| :crystal_ball: | **Enterprise features** - Advanced analytics, compliance, audit trails |
| :crystal_ball: | **Integration ecosystem** - Connect with popular agent frameworks |

⭐ **Star this repo to follow progress**

## Contributing

We welcome contributions! See our **[Contributing Guide](CONTRIBUTING.md)** for development setup, code standards, and PR process.

- **Report bugs**: [Open an issue](https://github.com/basalt-ai/asphalt/issues)
- **Request features**: [GitHub Discussions](https://github.com/basalt-ai/asphalt/discussions)
- **Join Discord**: [Basalt Community](https://discord.gg/yW2RyZKY)

Built and maintained by [Basalt](https://getbasalt.ai). Open source forever under Apache 2.0.

## License

Apache 2.0 — see [LICENSE](LICENSE) for details.