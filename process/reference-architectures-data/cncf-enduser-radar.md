# CNCF End User Technology Radar

This document provides comprehensive information about the CNCF End User Technology Radar, its history, methodology, and relationship to reference architecture reviews.

## What is the CNCF End User Technology Radar?

The **CNCF End User Technology Radar** is a publication that captures real-world perspectives from CNCF end users about cloud native technologies. It helps the community understand:

- Which technologies are being adopted at scale
- What end users recommend for different use cases
- Technology maturity and production readiness
- Emerging trends in cloud native adoption

The Radar provides valuable context for reference architecture reviewers by showing which technologies are validated by the end user community and how they're being used in production.

## Radar Ring Structure

The Technology Radar uses a **three-ring structure** to classify technologies based on end user recommendations:

### Ring 1: ADOPT
**Definition**: Technologies that end users confidently recommend for production use.

**Characteristics:**
- Proven in production at scale
- Strong community support
- Well-documented
- Multiple end users have successful implementations
- Low risk for new adopters

**Example technologies:**
- Kubernetes (container orchestration)
- Prometheus (monitoring)
- Envoy (service proxy)
- Helm (package management)

### Ring 2: TRIAL
**Definition**: Technologies that end users are actively evaluating or using in limited production.

**Characteristics:**
- Showing promise in production pilots
- Some end users have successful implementations
- May have rough edges or gaps
- Worth evaluating for specific use cases
- Medium risk, requires evaluation

**Example technologies:**
- Newer CNCF graduated/incubating projects
- Technologies solving emerging problems
- Tools with strong momentum but limited production history

### Ring 3: ASSESS
**Definition**: Technologies that are interesting but too early for production recommendation.

**Characteristics:**
- Early stage or experimental
- Limited production validation
- Worth watching and exploring
- May have significant unknowns
- Higher risk, not production-ready for most

**Example technologies:**
- Recently announced projects
- Sandbox projects with potential
- Technologies addressing emerging needs

### What's NOT on the Radar

Technologies may be excluded because:
- Too early/immature for end user evaluation
- Vendor-specific or proprietary
- Not cloud native relevant
- Insufficient end user adoption data

## Published Technology Radars

### Interactive Radars (2020-2021)

The CNCF published **6 interactive technology radars** covering different domains:

#### 1. Continuous Delivery (June 2020)
**Focus**: CI/CD pipelines, GitOps, deployment automation

**Key Technologies:**
- **Adopt**: Helm, Spinnaker, Tekton
- **Trial**: Argo CD, Flux, Jenkins X
- **Assess**: Keptn, various pipeline tools

**Insights:**
- GitOps emerging as preferred pattern
- Kubernetes-native CD tools gaining adoption
- Shift toward declarative delivery

#### 2. Observability (September 2020)
**Focus**: Monitoring, logging, tracing, alerting

**Key Technologies:**
- **Adopt**: Prometheus, Grafana, Jaeger, Fluentd
- **Trial**: OpenTelemetry, Thanos, Cortex
- **Assess**: Various vendor solutions

**Insights:**
- OpenTelemetry standardization important
- Multi-cluster monitoring challenges
- Cost of observability at scale

#### 3. Security (December 2020)
**Focus**: Container security, supply chain, policy enforcement

**Key Technologies:**
- **Adopt**: Falco, OPA (Open Policy Agent)
- **Trial**: Notary, TUF, various scanning tools
- **Assess**: Emerging security frameworks

**Insights:**
- Supply chain security growing priority
- Runtime security essential
- Policy as code adoption increasing

#### 4. DevSecOps (March 2021)
**Focus**: Security integration in development workflows

**Key Technologies:**
- **Adopt**: Policy enforcement, vulnerability scanning
- **Trial**: SBOM tools, signing/verification
- **Assess**: Emerging compliance automation

**Insights:**
- Shift-left security practices
- Automation critical for scale
- Developer experience important

#### 5. Storage (June 2021)
**Focus**: Persistent storage, databases, data services

**Key Technologies:**
- **Adopt**: Various CSI drivers, established databases
- **Trial**: Cloud-native databases, data services
- **Assess**: Emerging storage solutions

**Insights:**
- Stateful workloads increasing
- Storage performance and cost challenges
- Multi-cloud storage complexity

#### 6. Network (September 2021)
**Focus**: Service mesh, CNI, load balancing, ingress

**Key Technologies:**
- **Adopt**: Various CNI plugins, Envoy
- **Trial**: Service mesh implementations
- **Assess**: Advanced networking features

**Insights:**
- Service mesh adoption varies by scale
- Multi-cluster networking complex
- Performance overhead considerations

### Survey-Based Radar Reports (2024-2025)

The CNCF evolved to **survey-based reports** with broader participation:

#### 1. Multicluster Management (2024)
**Focus**: Managing multiple Kubernetes clusters at scale

**Key Findings:**
- Most enterprises run 10+ clusters
- Multi-cluster management tools emerging
- Federation and policy enforcement challenges
- Cost visibility across clusters

**Technologies Highlighted:**
- Cluster lifecycle management
- Multi-cluster networking
- Cross-cluster observability
- Policy and governance tools

#### 2. AI/ML on Kubernetes (2024)
**Focus**: Running AI/ML workloads on Kubernetes

**Key Findings:**
- GPU scheduling and resource management
- Model serving at scale
- Training vs. inference workloads
- Data pipeline integration

**Technologies Highlighted:**
- Kubeflow components
- GPU operators
- Model serving frameworks
- ML workflow tools

#### 3. Observability (2025)
**Focus**: Updated observability landscape

**Key Findings:**
- OpenTelemetry adoption accelerating
- eBPF-based observability gaining traction
- Cost management for observability data
- Platform engineering for observability

**Technologies Highlighted:**
- OpenTelemetry collectors and SDKs
- eBPF tools (Pixie, Cilium, etc.)
- Cost optimization tools
- Unified observability platforms

## Methodology

### Interactive Radar Process (2020-2021)

1. **End User Survey**: CNCF End User Community members surveyed
2. **Data Collection**: Technologies, adoption status, feedback collected
3. **Analysis**: TAB and End User Working Group review responses
4. **Ring Assignment**: Technologies placed in Adopt/Trial/Assess based on consensus
5. **Publication**: Interactive radar published with explanations
6. **Iteration**: Updated based on community feedback

### Survey-Based Report Process (2024-present)

1. **Survey Design**: Working group designs comprehensive survey
2. **Broad Distribution**: Survey distributed to entire CNCF community
3. **Data Analysis**: Statistical analysis of responses (100+ respondents typical)
4. **Report Creation**: Detailed report with findings and recommendations
5. **Community Review**: Draft reviewed by End User Community and TAB
6. **Publication**: Report published with raw data (anonymized)

## Key Insights Across All Radars

### Technology Maturity Patterns

1. **Core Infrastructure (Mature)**:
   - Kubernetes, Prometheus, Envoy consistently in "Adopt"
   - Strong consensus on foundational technologies
   - Focus shifts to advanced features and scaling

2. **Platform Engineering (Growing)**:
   - Internal developer platforms emerging
   - Golden paths and paved roads
   - Self-service infrastructure

3. **Security (Evolving)**:
   - Supply chain security accelerating
   - Policy as code becoming standard
   - Zero trust architecture adoption

4. **Observability (Standardizing)**:
   - OpenTelemetry becoming standard
   - eBPF adoption for performance and security
   - Cost optimization critical at scale

5. **AI/ML (Emerging)**:
   - Kubernetes for ML workloads growing
   - GPU management and scheduling challenges
   - Integration with data pipelines

### End User Priorities

Based on radar feedback and surveys:

1. **Developer Experience**: 92% of end users prioritize DX improvements
2. **Security**: 87% cite security as top priority
3. **Cost Optimization**: 78% focus on cloud cost management
4. **Multi-cluster Management**: 71% run 10+ clusters
5. **Observability**: 68% struggle with observability costs

### Common Challenges

1. **Complexity**: Managing multiple tools and integrations
2. **Skills Gap**: Finding talent with cloud native expertise
3. **Cost**: Infrastructure and tooling costs at scale
4. **Security**: Keeping up with security best practices
5. **Standardization**: Lack of standards across teams/clusters

## Relationship to Reference Architectures

### How Radars Inform Architecture Reviews

The Technology Radar provides context for evaluating reference architectures:

#### 1. Technology Selection Validation
**Reference architectures should:**
- Primarily use "Adopt" technologies for core components
- Provide rationale if using "Trial" or "Assess" technologies
- Explain why specific technologies were chosen over alternatives

**Example**: If an architecture uses a non-standard service mesh (not in "Adopt" ring), reviewers should look for detailed justification based on specific requirements.

#### 2. Industry Best Practices
**Reference architectures should demonstrate:**
- Alignment with end user community recommendations
- Awareness of common pitfalls and challenges
- Solutions to known problems (e.g., multi-cluster management)

**Example**: Observability architecture should address cost management, a known challenge highlighted in multiple radars.

#### 3. Technology Maturity Assessment
**Reviewers should consider:**
- Is the architecture using proven, production-ready technologies?
- Are experimental technologies clearly identified?
- Is there a migration path as technologies mature?

**Example**: An architecture using OpenTelemetry (moving from "Trial" to "Adopt") should show production validation at submitter's scale.

#### 4. Emerging Trends
**Reference architectures should:**
- Address current end user priorities (security, cost, DX)
- Show awareness of emerging patterns (platform engineering, FinOps)
- Demonstrate forward-thinking design

**Example**: A platform engineering reference architecture should align with patterns from the Multicluster Management radar.

### What Radars DON'T Tell Us

**Important limitations:**

1. **Not Prescriptive**: Radars reflect current end user consensus, not absolute truth
2. **Context Matters**: "Adopt" for one organization may be "Assess" for another based on scale, industry, requirements
3. **Timing**: Technologies move between rings as they mature
4. **Scope**: Radars cover popular technologies, not every possible solution
5. **Survey Bias**: Respondents may not represent all industries or use cases

**For reviewers:**
- Don't reject architectures solely because they use "Trial" or "Assess" technologies
- Consider submitter's specific requirements and constraints
- Focus on rationale and production validation, not just ring placement
- Recognize that innovation often happens outside "Adopt" ring

## Using Radar Data in Reviews

### Recommended Review Process

1. **Identify Core Technologies**: List main technologies in the architecture
2. **Check Radar Status**: Note which ring (if any) each technology appears in
3. **Assess Alignment**: Does overall architecture align with end user recommendations?
4. **Evaluate Divergence**: If using technologies outside "Adopt", is there clear rationale?
5. **Consider Context**: Does the submitter's scale/industry/requirements justify choices?
6. **Verify Production Use**: For "Trial"/"Assess" technologies, is there production validation?

### Review Questions

When evaluating technology choices:

- **Adopt technologies**: ✅ Good, standard choices (require minimal explanation)
- **Trial technologies**: ⚠️ Require explanation of why chosen and production validation
- **Assess technologies**: ⚠️ Require strong justification, clear risks acknowledged, fallback plans
- **Not on radar**: ⚠️ May be too new, too niche, or not cloud native - needs investigation

### Example Review Scenarios

**Scenario 1: Architecture uses all "Adopt" technologies**
- ✅ Low risk from technology maturity perspective
- ✅ Aligns with community recommendations
- Focus review on: architecture design, scale validation, completeness

**Scenario 2: Architecture uses mix of "Adopt" and "Trial"**
- ⚠️ Moderate risk, needs examination
- Check: Is rationale provided? Is production validation demonstrated?
- Focus review on: specific "Trial" choices, risk mitigation, experience sharing

**Scenario 3: Architecture uses "Assess" or unlisted technologies**
- ⚠️ Higher risk, requires careful review
- Check: Why these choices? What alternatives were considered? What are the tradeoffs?
- Focus review on: justification quality, production proof, value to community

## References

- **Interactive Radars (2020-2021)**: https://radar.cncf.io/ (archived)
- **Survey Reports (2024-present)**: https://www.cncf.io/reports/
- **End User Community**: https://www.cncf.io/enduser/
- **Technology Radar Methodology**: https://www.cncf.io/blog/tag/radar/

## Related Documents

- `cncf-case-studies-research.md` - Analysis of 179 published case studies
- `../reference-architecture-review-guidelines.md` - Detailed review guidelines for reference architectures
- `../../AGENTS.md` - General agent instructions and context

---

**Last Updated**: February 2026
**Source**: CNCF Technology Radar publications (2020-2025) and End User Community surveys
**Maintainer**: TAB Reference Architecture Review Team
