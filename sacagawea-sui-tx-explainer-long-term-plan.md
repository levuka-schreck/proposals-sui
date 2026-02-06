# Sui Transaction Explainer (Project Sacagawea)

## Long-Term Sustainability & Maintenance Plan

> Prepared by **Levuka Venture Labs FZCO** | February 2026

---

## Executive Summary

This document outlines our comprehensive strategy for ensuring the Sui Transaction Explainer remains a valuable, reliable, and up-to-date resource for the Sui ecosystem over the long term. Sustainability for a developer tool of this nature requires attention to three core pillars: **protocol compatibility** (keeping pace with Sui's evolution), **community adoption** (building a user base that validates ongoing investment), and **operational efficiency** (minimizing maintenance burden while maximizing reliability).

Our approach combines proactive monitoring, community engagement, and a tiered maintenance model that scales effort with actual usage and ecosystem importance.

---

## 1. Sustainability Model

### 1.1 Open-Source Foundation

The Transaction Explainer will be released as an **open-source project** under the MIT or Apache 2.0 license, ensuring:

- **Community Contributions:** External developers can submit package registry updates, bug fixes, and feature enhancements
- **Forkability:** Teams can self-host or customize without vendor dependency
- **Transparency:** All parsing logic is auditable, building trust in the tool's accuracy
- **Ecosystem Alignment:** Matches the open-source ethos of the Sui ecosystem

### 1.2 Governance Model

For long-term sustainability, we recommend transitioning to a lightweight community governance model after Year 1:

- **Phase 1 (Months 1-12):** Levuka Venture Labs FZCO maintains full ownership and maintenance responsibility
- **Phase 2 (Months 13-24):** Establish a maintainer committee (2-3 active contributors) with commit access
- **Phase 3 (Month 24+):** Consider transfer to a Sui ecosystem working group or foundation stewardship if adoption warrants

---

## 2. Maintenance Approach

### 2.1 Maintenance Tiers

We define three tiers of maintenance activity, each with distinct triggers and response times:

#### Tier 1: Critical Maintenance (Response: <24 hours)

| Trigger | Action | Frequency |
|---------|--------|-----------|
| Sui protocol breaking changes | Update parsing logic to restore functionality | As needed (estimate: 2-4x/year) |
| Security vulnerability discovered | Patch and deploy immediately | Rare |
| Complete service outage | Diagnose and restore | Rare |

#### Tier 2: Routine Maintenance (Response: <1 week)

| Trigger | Action | Frequency |
|---------|--------|-----------|
| New transaction types added to Sui | Add parsing support and plain-language templates | Quarterly |
| Popular new protocols launch | Add to package registry with friendly names | Monthly |
| Dependency updates (security patches) | Update packages, test, deploy | Monthly |
| Minor UI/UX improvements | Implement based on user feedback | Quarterly |

#### Tier 3: Enhancement Maintenance (Response: Planned releases)

| Trigger | Action | Frequency |
|---------|--------|-----------|
| Feature requests from community | Evaluate, prioritize, implement | Quarterly releases |
| Performance optimizations | Profile and optimize based on usage data | Semi-annually |
| Documentation updates | Refresh guides, add new examples | Quarterly |
| Analytics and reporting improvements | Enhance observability based on operational learnings | Semi-annually |

### 2.2 Estimated Maintenance Effort

| Activity | Hours/Month | Annual Hours | Annual Cost (at $75/hr) |
|----------|-------------|--------------|--------------------------|
| Protocol compatibility updates | 4-8 | 48-96 | $3.6K-7.2K |
| Package registry curation | 2-4 | 24-48 | $1.8K-3.6K |
| Dependency updates & security | 2-3 | 24-36 | $1.8K-2.7K |
| Bug fixes & user support | 2-4 | 24-48 | $1.8K-3.6K |
| Documentation maintenance | 1-2 | 12-24 | $900-1.8K |
| **Total Routine Maintenance** | **11-21** | **132-252** | **$9.9K-18.9K/year** |

> **Note:** Year 1 maintenance is typically higher (closer to upper bound) as edge cases are discovered. Years 2+ trend toward lower bound as the system stabilizes.

### 2.3 Maintenance Schedule

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     ANNUAL MAINTENANCE CALENDAR                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  WEEKLY                                                                 │
│  ├── Monitor Sui release notes and Discord announcements                │
│  ├── Review error logs and user-reported issues                         │
│  └── Triage GitHub issues and PRs                                       │
│                                                                         │
│  MONTHLY                                                                │
│  ├── Dependency security audit and updates                              │
│  ├── Package registry additions (new protocols)                         │
│  ├── Performance metrics review                                         │
│  └── Community feedback synthesis                                       │
│                                                                         │
│  QUARTERLY                                                              │
│  ├── Q1: Post-launch stabilization, initial feedback incorporation      │
│  ├── Q2: Feature release (stretch goals, community requests)            │
│  ├── Q3: Performance optimization, documentation refresh                │
│  └── Q4: Annual review, roadmap planning, dependency major upgrades     │
│                                                                         │
│  ANNUALLY                                                               │
│  ├── Comprehensive security review                                      │
│  ├── Sustainability assessment and funding renewal                      │
│  └── Governance model evaluation                                        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Protocol Compatibility Strategy

### 3.1 Sui Protocol Monitoring

Staying compatible with Sui's evolving protocol is the primary maintenance challenge. Our monitoring approach:

| Channel | What We Monitor | Action Trigger |
|---------|-----------------|----------------|
| **Testnet/Devnet** | Pre-mainnet changes for advance preparation | Test against devnet before mainnet upgrades |
| **Automated Tests** | CI runs against live RPC with sample transactions | Alerts on test failures |

### 3.2 Compatibility Testing Matrix

We maintain a suite of test transactions covering all supported transaction types:

| Transaction Type | Test Coverage | Update Frequency |
|------------------|---------------|------------------|
| Simple SUI transfer | ✅ Covered | Stable |
| Multi-recipient transfer | ✅ Covered | Stable |
| NFT transfer | ✅ Covered | Stable |
| DEX swap (Cetus, Turbos, etc.) | ✅ Covered | Update with new DEXs |
| Staking operations | ✅ Covered | Stable |
| Sponsored transactions | ✅ Covered | Monitor for changes |
| Programmable Transaction Blocks (complex) | ✅ Covered | Monitor for new commands |
| Failed transactions | ✅ Covered | Stable |

### 3.3 Deprecation & Migration Policy

When Sui deprecates APIs or changes transaction structures:

1. **Detection:** Automated tests fail or monitoring alerts trigger
2. **Assessment:** Evaluate scope of change (minor adjustment vs. major refactor)
3. **Communication:** Post GitHub issue detailing the change and timeline
4. **Implementation:** Update parsing logic with backward compatibility where possible
5. **Deployment:** Ship fix with release notes explaining what changed
6. **Documentation:** Update user guides if behavior changes

---

## 4. Community Engagement & Support

### 4.1 Support Channels

| Channel | Purpose | Response Target |
|---------|---------|-----------------|
| **GitHub Issues** | Bug reports, feature requests, package submissions | <48 hours acknowledgment |
| **GitHub Discussions** | Usage questions, community ideas | <72 hours |
| **Email (for sponsors)** | Direct support for ecosystem partners | <24 hours |

### 4.2 Community Contribution Guidelines

We actively encourage community contributions with clear guidelines:

**Easy Contributions (No code review required):**
- Package registry additions via PR template
- Documentation typo fixes
- Translation contributions

**Standard Contributions (Code review required):**
- Bug fixes with test coverage
- New transaction type templates
- UI/UX improvements

**Major Contributions (Design review required):**
- New features or significant refactors
- Architecture changes
- External integrations

### 4.3 Recognition Program

To incentivize community maintenance:
- **Contributors List:** Maintained in README with links to profiles

---

## 5. Infrastructure & Operations

### 5.1 Hosting Strategy

| Component | Provider | Cost | Redundancy |
|-----------|----------|------|------------|
| **Frontend Hosting** | Vercel (Pro) | ~$20/month | Global edge, auto-failover |
| **Domain & DNS** | Cloudflare | ~$15/year | DDoS protection, caching |
| **Monitoring** | Vercel Analytics + Sentry | ~$30/month | Error tracking, performance |
| **RPC Endpoint** | Public RPC → Dedicated if needed | $0-100/month | Fallback to public |

**Annual Infrastructure Cost:** ~$600-1,800/year (scales with traffic)

### 5.2 Uptime & Reliability Targets

| Metric | Target | Monitoring |
|--------|--------|------------|
| **Availability** | 99.5% uptime | Vercel status + UptimeRobot |
| **Response Time** | <4s for transaction explanation | Vercel Analytics |
| **Error Rate** | <1% of requests | Sentry error tracking |

### 5.3 Incident Response

```
┌─────────────────────────────────────────────────────────────────┐
│                    INCIDENT RESPONSE FLOW                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. DETECTION                                                   │
│     └── Automated alert OR user report                          │
│                                                                 │
│  2. TRIAGE (< 1 hour)                                           │
│     ├── Severity assessment (Critical/High/Medium/Low)          │
│     └── Assign owner                                            │
│                                                                 │
│  3. MITIGATION                                                  │
│     ├── Critical: Immediate fix or rollback (< 4 hours)         │
│     ├── High: Fix within 24 hours                               │
│     └── Medium/Low: Scheduled for next release                  │
│                                                                 │
│  4. COMMUNICATION                                               │
│     ├── GitHub issue with status updates                        │
│                                                                 │
│  5. POST-MORTEM (Critical/High only)                            │
│     ├── Root cause analysis                                     │
│     └── Prevention measures documented                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 6. Success Metrics & Sustainability Indicators

### 6.1 Key Performance Indicators

We track these metrics to assess project health and justify continued investment:

| Metric | Year 1 Target | Measurement |
|--------|---------------|-------------|
| **Monthly Active Users** | 1,000+ | Vercel Analytics |
| **Transactions Explained** | 10,000+/month | Internal counter |
| **GitHub Stars** | 100+ | GitHub |
| **Community Contributors** | 10+ | GitHub insights |
| **Package Registry Size** | 50+ protocols | Registry file |
| **Uptime** | 99.5%+ | Monitoring |
| **Mean Time to Compatibility Fix** | <48 hours | Issue tracking |

### 6.2 Sustainability Health Check

Quarterly assessment of sustainability indicators:

| Indicator | Healthy | Warning | Critical |
|-----------|---------|---------|----------|
| **Funding Runway** | >12 months | 6-12 months | <6 months |
| **Maintenance Response Time** | <48 hours | 48h-1 week | >1 week |
| **Open Critical Issues** | 0 | 1-2 | 3+ |
| **Sui Protocol Compatibility** | Current | 1 version behind | 2+ versions behind |
| **Community Engagement** | Growing | Stable | Declining |

---

## 7. Long-Term Roadmap

### Year 1: Foundation (Months 1-12)

| Quarter | Focus | Deliverables |
|---------|-------|--------------|
| **Q1** | Launch & Stabilize | MVP launch, initial package registry, bug fixes |
| **Q2** | Expand Coverage | Stretch goals (visualization) |
| **Q3** | Community Growth | Contribution guidelines, first external PRs merged |
| **Q4** | Sustainability | Funding renewal, Year 2 planning |

### Year 2: Maturation (Months 13-24)

| Quarter | Focus | Deliverables |
|---------|-------|--------------|
| **Q1** | Feature Expansion | API for integrations, batch transaction support |
| **Q2** | Ecosystem Integration | Embed in wallets/explorers, partnership development |
| **Q3** | Decentralization | Maintainer committee formation, governance documentation |
| **Q4** | Handoff Preparation | Transition plan to community or foundation stewardship |

### Year 3+: Steady State

- Community-driven maintenance with minimal core team involvement
- Self-sustaining through sponsorships and ecosystem value
- Potential integration into Sui Foundation tooling portfolio

---

## 8. Risk Mitigation for Long-Term Sustainability

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| **Funding gap** | Medium | High | Diversified funding sources; 12-month runway minimum; low operational costs |
| **Key maintainer departure** | Medium | Medium | Documentation-first approach; multiple contributors with context; simple codebase |
| **Sui protocol major overhaul** | Low | High | Early devnet testing; relationship with Sui team; modular parsing architecture |
| **Competing tool emergence** | Medium | Medium | Focus on simplicity and accuracy; open-source prevents lock-in; community goodwill |
| **Low adoption** | Low | Medium | Integration with existing tools; marketing through Sui channels; demonstrated utility |

---

## 9. Conclusion

The Sui Transaction Explainer is designed for **sustainable, low-maintenance operation** from day one. By combining:

- **Open-source transparency** that invites community contribution
- **Minimal infrastructure** that keeps operational costs negligible
- **Proactive monitoring** that catches compatibility issues early
- **Clear governance transition** that reduces single-point-of-failure risk
- **Diversified funding** that doesn't depend on any single source

...we ensure this tool can serve the Sui ecosystem reliably for years to come.

**Estimated Annual Maintenance Cost:** $9.9K-18.9K  
**Estimated Annual Infrastructure Cost:** $600-1,800  
**Total Annual Sustainability Budget:** $10.5K-20.7K

---

<p align="center">
  <strong>Levuka Venture Labs FZCO</strong><br>
  February 2026
</p>
