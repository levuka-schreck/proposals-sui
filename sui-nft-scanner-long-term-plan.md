# Sui Wallet NFT Scanner & Cleaner

## Long-Term Sustainability & Maintenance Plan

> Prepared by **Levuka Venture Lab FZCO** | February 2026

---

## Executive Summary

This document outlines our comprehensive strategy for ensuring the Sui Wallet NFT Scanner & Cleaner remains effective, accurate, and valuable to the Sui ecosystem over the long term. Unlike static developer tools, an NFT scanner faces a unique challenge: **adversarial evolution**. Scammers continuously adapt their tactics, requiring the platform to evolve in response. Sustainability requires not just technical maintenance, but active threat intelligence and community engagement.

Our approach combines proactive threat monitoring, community-powered classification, and a lean operational model that keeps costs low while maintaining high classification accuracy.

---

## 1. Sustainability Model

### 1.1 The Adversarial Challenge

Unlike typical developer tools, the NFT Scanner operates in an **adversarial environment**:

| Challenge | Impact | Response Required |
|-----------|--------|-------------------|
| New scam patterns emerge weekly | Classification accuracy degrades | Continuous blocklist updates |
| Scammers clone legitimate projects | False negatives increase | Heuristic refinement |
| Legitimate projects launch daily | False positives frustrate users | Continuous allowlist expansion |
| Scammers study detection methods | Evasion tactics evolve | Classification algorithm updates |

This reality shapes our entire sustainability approach: **the scanner is never "done"—it requires ongoing vigilance.**

### 1.2 Open-Source Foundation

The NFT Scanner will be released as an **open-source project** under MIT or Apache 2.0 license:

- **Community Contributions:** Security researchers and community members can submit scam reports and allowlist additions
- **Transparency:** Classification logic is auditable, building trust in recommendations
- **Forkability:** Teams can self-host or customize for specific use cases
- **Ecosystem Alignment:** Matches the open-source ethos of Sui

### 1.3 Governance Evolution

| Phase | Timeline | Governance Model |
|-------|----------|------------------|
| **Phase 1** | Months 1-12 | Levuka Venture Lab FZCO maintains full ownership; core team manages all lists |
| **Phase 2** | Months 13-18 | Establish trusted contributor program; 3-5 vetted community members can submit PRs directly |
| **Phase 3** | Months 18-24 | Form classification committee; community votes on disputed classifications |
| **Phase 4** | Month 24+ | Consider DAO structure or transfer to Sui Foundation if adoption warrants |

---

## 2. Maintenance Approach

### 2.1 Maintenance Categories

The NFT Scanner requires three distinct types of maintenance:

```
┌─────────────────────────────────────────────────────────────────┐
│                 MAINTENANCE CATEGORIES                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. THREAT INTELLIGENCE (Ongoing)                               │
│     └── Scam detection and blocklist updates                    │
│     └── New legitimate project verification                     │
│     └── Classification accuracy monitoring                      │
│     └── Frequency: Weekly                                       │
│                                                                 │
│  2. TECHNICAL MAINTENANCE (Periodic)                            │
│     └── Sui protocol compatibility                              │
│     └── Dependency updates                                      │
│     └── Bug fixes and performance                               │
│     └── Frequency: Weekly to Monthly                            │
│                                                                 │
│  3. FEATURE EVOLUTION (Quarterly)                               │
│     └── New detection heuristics                                │
│     └── UX improvements                                         │
│     └── Integration expansions                                  │
│     └── Frequency: Quarterly releases                           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2.2 Threat Intelligence Operations

This is the **most critical and unique** aspect of NFT Scanner maintenance:

#### Daily Monitoring Activities

| Activity | Method | Time Investment |
|----------|--------|-----------------|
| New package analysis | Automated alerts for high-volume new packages | 60 min/week |
| User report triage | Review submitted scam reports | 60 min/week |
| Blocklist updates | Add verified scams to blocklist | As needed |

#### Weekly Analysis Activities

| Activity | Method | Time Investment |
|----------|--------|-----------------|
| Classification accuracy review | Sample check of recent classifications | 1 hour/week |
| False positive/negative analysis | Review user feedback and disputes | 1 hour/week |
| Allowlist expansion | Verify and add new legitimate projects | 2 hours/week |
| Heuristic effectiveness review | Analyze detection rates by signal type | 1 hour/week |

#### Scam Report Processing Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                 SCAM REPORT PROCESSING                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. INTAKE                                                      │
│     └── Report received via GitHub issue or UI                  │
│     └── Auto-categorize by report type                          │
│                         │                                       │
│                         ▼                                       │
│  2. INITIAL TRIAGE (< 24 hours)                                 │
│     └── Verify package exists on Sui                            │
│     └── Check if already in blocklist/allowlist                 │
│     └── Assess report credibility                               │
│                         │                                       │
│                         ▼                                       │
│  3. INVESTIGATION (< 48 hours)                                  │
│     └── Analyze package metadata and history                    │
│     └── Check for known scam patterns                           │
│     └── Review transaction patterns if available                │
│     └── Cross-reference with other reports                      │
│                         │                                       │
│                         ▼                                       │
│  4. DECISION                                                    │
│     ├── CONFIRMED SCAM → Add to blocklist immediately           │
│     ├── LIKELY SCAM → Add to blocklist with "reported" flag     │
│     ├── INCONCLUSIVE → Monitor; add to watchlist                │
│     └── FALSE REPORT → Close with explanation                   │
│                         │                                       │
│                         ▼                                       │
│  5. DEPLOYMENT                                                  │
│     └── Update blocklist.json                                   │
│     └── Deploy to production                                    │
│     └── Notify reporter of outcome                              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2.3 Technical Maintenance Tiers

#### Tier 1: Critical (Response: < 24 hours)

| Trigger | Action | Frequency |
|---------|--------|-----------|
| Sui RPC breaking changes | Update query logic | Rare (estimate: 1-2x/year) |
| Security vulnerability | Patch and deploy | Rare |
| Major false positive outbreak | Emergency allowlist update | Rare |
| Service outage | Diagnose and restore | Rare |

#### Tier 2: Routine (Response: < 1 week)

| Trigger | Action | Frequency |
|---------|--------|-----------|
| New Sui object types | Add parsing support | Quarterly |
| Dependency security updates | Update and test | Monthly |
| Minor bug fixes | Fix and deploy | As reported |
| Performance optimizations | Profile and improve | Quarterly |

#### Tier 3: Enhancement (Planned releases)

| Trigger | Action | Frequency |
|---------|--------|-----------|
| New detection heuristics | Research, implement, validate | Quarterly |
| UX improvements | Design and implement | Quarterly |
| New wallet support | Add adapter | As needed |
| Community feature requests | Evaluate and prioritize | Quarterly |

### 2.4 Estimated Maintenance Effort

| Activity | Hours/Month | Annual Hours | Annual Cost (at $75/hr) |
|----------|-------------|--------------|--------------------------|
| Threat intelligence (daily) | 15-20 | 180-240 | $13.5K-18K |
| Allowlist/blocklist curation | 8-12 | 96-144 | $7.2K-10.8K |
| Technical maintenance | 4-6 | 48-72 | $3.6K-5.4K |
| Sui protocol compatibility | 2-4 | 24-48 | $1.8K-3.6K |
| Community support | 4-6 | 48-72 | $3.6K-5.4K |
| Documentation updates | 2-3 | 24-36 | $1.8K-2.7K |
| **Total Routine Maintenance** | **35-51** | **420-612** | **$31.5K-45.9K/year** |


---

## 3. Classification System Maintenance

### 3.1 Allowlist Management

The allowlist is the **primary driver of accurate Legit classifications**:

#### Allowlist Structure

```json
{
  "packages": {
    "0x1234...": {
      "name": "Sui Punks",
      "category": "pfp",
      "verified": true,
      "verifiedBy": "team",
      "verifiedAt": "2026-02-15",
      "website": "https://suipunks.io",
      "twitter": "@suipunks",
      "notes": "Verified via official announcement"
    }
  },
  "collections": {
    "0xabcd...::suipunks::SuiPunk": {
      "packageId": "0x1234...",
      "name": "Sui Punks",
      "totalSupply": 10000
    }
  },
  "lastUpdated": "2026-02-15",
  "version": "1.2.0"
}
```

#### Allowlist Addition Criteria

For a project to be added to the allowlist:

| Criterion | Requirement | Verification Method |
|-----------|-------------|---------------------|
| **Mainnet Deployment** | Must be deployed to Sui mainnet | RPC verification |
| **Verifiable Team** | Website, social media, or known team members | Manual verification |
| **Transaction Volume** | >500 transactions or notable ecosystem role | On-chain analysis |
| **No Scam History** | No previous scam reports or rug pulls | Community check |
| **Active Project** | Recent activity within 90 days | On-chain analysis |

#### Allowlist Sources

| Source | Process | Update Frequency |
|--------|---------|------------------|
| **Proactive Research** | Monitor Sui ecosystem announcements, launches | Weekly |
| **Community Submissions** | GitHub PR with verification evidence | Ongoing |
| **Marketplace Partnerships** | Verified collections from partner marketplaces | As contracted |
| **Wallet Partnerships** | Curated lists from partner wallets | Monthly sync |
| **Automated Discovery** | Flag high-volume packages for review | Weekly report |

### 3.2 Blocklist Management

The blocklist captures **confirmed and suspected scams**:

#### Blocklist Structure

```json
{
  "packages": {
    "0x5678...": {
      "name": "Fake Sui Punks",
      "category": "impersonation",
      "severity": "high",
      "reportedAt": "2026-02-10",
      "confirmedAt": "2026-02-11",
      "evidence": "Impersonates Sui Punks with similar imagery",
      "reportedBy": "community",
      "status": "confirmed"
    }
  },
  "patterns": [
    {
      "type": "name_pattern",
      "pattern": ".*free.*airdrop.*",
      "severity": "medium",
      "reason": "Common scam naming pattern"
    }
  ],
  "lastUpdated": "2026-02-15",
  "version": "1.2.0"
}
```

#### Scam Categories

| Category | Description | Detection Method |
|----------|-------------|------------------|
| **Impersonation** | Clones of legitimate projects | Name/image similarity analysis |
| **Phishing** | NFTs with malicious links in metadata | URL pattern matching |
| **Rug Pull** | Projects that abandoned after sales | Community reports, on-chain analysis |
| **Spam Airdrop** | Unsolicited low-quality airdrops | Volume patterns, metadata quality |
| **Malicious Contract** | Contracts with dangerous functions | Code analysis (advanced) |

### 3.3 Heuristic Evolution

Beyond static lists, heuristics detect **unknown threats**:

#### Current Heuristics (MVP)

| Signal | Weight | Description |
|--------|--------|-------------|
| Missing metadata | Medium | No name, description, or image |
| Recent deployment | Low | Package deployed < 7 days ago |
| Scam keywords | Medium | "free", "airdrop", "claim" in description |
| No website/social | Low | Missing external verification |
| Low transaction count | Low | < 10 transactions total |

#### Planned Heuristic Improvements (Post-MVP)

| Enhancement | Timeline | Description |
|-------------|----------|-------------|
| Image similarity detection | Q2 | Flag NFTs with images similar to known projects |
| Creator reputation scoring | Q2 | Score based on creator's historical activity |
| Metadata quality scoring | Q3 | Analyze completeness and professionalism of metadata |
| Transaction pattern analysis | Q3 | Detect suspicious minting/distribution patterns |
| Cross-chain scam correlation | Q4 | Link to known scammers on other chains |

### 3.4 Classification Accuracy Monitoring

We track accuracy metrics to ensure quality:

| Metric | Target | Measurement |
|--------|--------|-------------|
| **True Positive Rate (Scams)** | >95% | Confirmed scams correctly identified |
| **False Positive Rate** | <2% | Legitimate NFTs incorrectly flagged |
| **False Negative Rate** | <10% | Scams missed by classification |
| **User Override Rate** | <5% | Users disagreeing with classification |
| **Time to Detection** | <48 hours | New scams added to blocklist |

#### Accuracy Review Process

```
Weekly:
├── Sample 50 random classifications
├── Verify against manual analysis
├── Calculate accuracy metrics
└── Identify systematic errors

Monthly:
├── Analyze all user-reported disputes
├── Review false positive patterns
├── Adjust heuristic weights
└── Update classification thresholds
```

---

## 4. Community Engagement & Support

### 4.1 Support Channels

| Channel | Purpose | Response Target |
|---------|---------|-----------------|
| **GitHub Issues** | Bug reports, scam reports, allowlist requests | < 48 hours |
| **GitHub Discussions** | Feature requests, general questions | < 72 hours |

### 4.2 Community Contribution Program

We actively encourage community participation in threat intelligence:

#### Contribution Types

| Contribution | Difficulty |
|--------------|------------|
| Scam report (verified) | Easy |
| Allowlist submission (verified) | Easy |
| Heuristic improvement PR | Medium |
| Bug fix PR | Medium |
| Major feature PR | Hard |

#### Trusted Contributor Program

After 10+ verified contributions, community members can become **Trusted Contributors**:

- Direct commit access to allowlist/blocklist (with review)
- Priority response on reports
- Monthly sync calls with core team
- Recognition on project README
- Future bounty & project opportunities

### 4.3 Scam Alert System

For high-severity scams, we issue **community alerts**:

```
┌─────────────────────────────────────────────────────────────────┐
│                    SCAM ALERT WORKFLOW                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. HIGH-SEVERITY SCAM DETECTED                                 │
│     └── Impersonation of major project, OR                      │
│     └── Phishing with active victims, OR                        │
│     └── Widespread airdrop spam                                 │
│                         │                                       │
│                         ▼                                       │
│  2. IMMEDIATE ACTIONS (< 1 hour)                                │
│     └── Add to blocklist                                        │
│     └── Deploy update                                           │
│     └── Draft alert message                                     │
│                         │                                       │
│                         ▼                                       │
│  3. COMMUNITY ALERT                                             │
│     └── Post to Sui Discord                                     │
│     └── Tweet with details                                      │
│     └── Notify partner wallets/marketplaces                     │
│                         │                                       │
│                         ▼                                       │
│  4. FOLLOW-UP                                                   │
│     └── Monitor for variants                                    │
│     └── Update heuristics if new pattern                        │
│     └── Post-incident report if significant                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 5. Infrastructure & Operations

### 5.1 Hosting Strategy

| Component | Provider | Cost | Redundancy |
|-----------|----------|------|------------|
| **Frontend Hosting** | Vercel (Pro) | ~$20/month | Global edge, auto-failover |
| **Database (if stretch goal)** | Supabase (Free/Pro) | $0-25/month | Managed backups |
| **Domain & DNS** | Cloudflare | ~$15/year | DDoS protection |
| **Monitoring** | Sentry (Free tier) | $0 | Error tracking |
| **Analytics** | Vercel Analytics | Included | Usage metrics |

**Annual Infrastructure Cost:** ~$300-600/year (minimal due to serverless architecture)

### 5.2 Deployment Strategy

```
┌─────────────────────────────────────────────────────────────────┐
│                 DEPLOYMENT PIPELINE                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ALLOWLIST/BLOCKLIST UPDATES (Fast Path)                        │
│  └── Update JSON file                                           │
│  └── Commit to main branch                                      │
│  └── Auto-deploy via Vercel (< 2 minutes)                       │
│  └── No code review required for list updates                   │
│                                                                 │
│  CODE CHANGES (Standard Path)                                   │
│  └── Create PR with changes                                     │
│  └── Automated tests run                                        │
│  └── Code review required                                       │
│  └── Merge to main                                              │
│  └── Auto-deploy to staging                                     │
│  └── Manual promotion to production                             │
│                                                                 │
│  EMERGENCY FIXES (Hotfix Path)                                  │
│  └── Direct commit to main (core team only)                     │
│  └── Immediate deploy                                           │
│  └── Post-hoc review within 24 hours                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 5.3 Uptime & Reliability

| Metric | Target | Monitoring |
|--------|--------|------------|
| **Availability** | 99.5% uptime | Vercel status + UptimeRobot |
| **Classification Latency** | < 3 seconds for wallet scan | Vercel Analytics |
| **List Update Latency** | < 5 minutes from commit to live | GitHub Actions |
| **Error Rate** | < 1% of scans | Sentry |

---

## 6. Long-Term Roadmap

### Year 1: Foundation & Threat Response (Months 1-12)

| Quarter | Focus | Deliverables |
|---------|-------|--------------|
| **Q1** | Launch & Stabilize | MVP launch; initial allowlist (50+ projects); blocklist seeding; community feedback loop |
| **Q2** | Accuracy & Coverage | Stretch goal (community ratings); 150+ allowlist projects; heuristic refinements |
| **Q3** | Integrations | Wallet integration partnerships (2-3); marketplace data sharing; API for third parties |
| **Q4** | Sustainability | Trusted contributor program; funding renewal; Year 2 planning |

### Year 2: Scale & Automation (Months 13-24)

| Quarter | Focus | Deliverables |
|---------|-------|--------------|
| **Q1** | Detection Improvements | Image similarity detection; creator reputation scoring |
| **Q2** | Ecosystem Integration | Embedded in 2+ wallets; marketplace pre-listing checks |
| **Q3** | Automation | Automated scam pattern detection; reduced manual triage |
| **Q4** | Governance | Classification committee formation; potential DAO structure evaluation |

### Year 3+: Ecosystem Standard

- Position as the **de facto scam detection layer** for Sui ecosystem
- Potential integration into wallet defaults
- Cross-chain expansion consideration (other Move chains)
- Self-sustaining through ecosystem partnerships

---

## 7. Risk Mitigation for Long-Term Sustainability

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| **Funding gap** | Medium | High | Diversified funding (grants + partnerships + bounties); low operational costs; 12-month runway minimum |
| **Key maintainer burnout** | Medium | High | Threat intelligence is demanding; build trusted contributor pipeline early; automate where possible |
| **Scam evolution outpaces detection** | Medium | Medium | Continuous heuristic research; community intelligence network; rapid response capability |
| **False positive backlash** | Low | High | Conservative classification defaults; clear dispute process; transparent methodology |
| **Competitor emergence** | Medium | Low | Open-source community moat; ecosystem partnerships; first-mover advantage |
| **Sui ecosystem decline** | Low | High | Cross-chain expansion capability; transferable threat intelligence |

---

## 8. Success Metrics & Sustainability Indicators

### 8.1 Key Performance Indicators

| Metric | Year 1 Target | Measurement |
|--------|---------------|-------------|
| **Monthly Active Users** | 2,000+ | Vercel Analytics |
| **Wallets Scanned** | 10,000+/month | Internal counter |
| **Scams Detected** | 500+ unique scam packages | Blocklist size |
| **Allowlist Coverage** | 200+ verified projects | Allowlist size |
| **Community Contributors** | 20+ | GitHub insights |
| **False Positive Rate** | < 2% | User feedback |
| **Time to Detection** | < 48 hours average | Internal tracking |

### 8.2 Sustainability Health Check

Quarterly assessment of sustainability indicators:

| Indicator | Healthy | Warning | Critical |
|-----------|---------|---------|----------|
| **Funding Runway** | > 12 months | 6-12 months | < 6 months |
| **Blocklist Update Frequency** | Weekly+ | Bi-weekly | Monthly or less |
| **Scam Detection Rate** | > 90% | 80-90% | < 80% |
| **False Positive Rate** | < 2% | 2-5% | > 5% |
| **Community Engagement** | Growing | Stable | Declining |
| **Response Time** | < 48 hours | 48h-1 week | > 1 week |

---

## 9. Conclusion

The Sui Wallet NFT Scanner & Cleaner requires a **different sustainability model** than typical developer tools due to its adversarial operating environment. Scammers don't stop, so neither can we.

Our sustainability strategy is built on:

- **Continuous threat intelligence** with daily monitoring and rapid response
- **Community-powered classification** scaling human intelligence beyond our core team
- **Lean infrastructure** keeping operational costs minimal (~$300-600/year)
- **Diversified funding** reducing single-source dependency
- **Transparent methodology** building trust through open-source and clear processes

**Estimated Annual Sustainability Budget:**

| Category | Annual Cost |
|----------|-------------|
| Threat Intelligence & Maintenance | $$31.5K-45.9K |
| Infrastructure | $0.3K-0.6K |
| **Total** | **$31.8K-46.5K/year** |

This is a significant ongoing investment, but justified by the **ecosystem-wide protection** the scanner provides. A single prevented scam affecting 1,000 users easily justifies the annual cost in protected value and ecosystem trust.

---

<p align="center">
  <strong>Levuka Venture Lab FZCO</strong><br>
  February 2026
</p>
