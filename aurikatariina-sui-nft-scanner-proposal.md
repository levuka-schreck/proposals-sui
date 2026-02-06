# Sui Wallet NFT Scanner & Cleaner (Project Aurikatariina)

**Review and Manage Unwanted or Suspicious Wallet Objects**

> Technical Proposal by **Levuka Venture Labs FZCO** | February 2026

---

## Executive Summary

This proposal outlines our approach to building a lightweight, user-friendly web application that helps Sui wallet users identify, classify, and manage unwanted or suspicious NFTs and non-coin objects. The proliferation of spam airdrops, scam tokens, and low-quality NFTs has become a significant user experience problem across blockchain ecosystems, and Sui is no exception.

Our proposed solution combines a **curated allowlist** maintained by the development team with an optional **community-driven rating system**, providing users with clear classification signals and actionable recommendations. The MVP will be delivered as a publicly accessible web application with comprehensive documentation, targeting a **4-6 week development timeline** at a fraction of the cost of enterprise-scale projects.

---

## 1. Skill Mix Required

This is a focused MVP project requiring a lean, agile team. Given the lightweight nature of the deliverable, we recommend a small cross-functional team that can move quickly while maintaining quality.

| Role | Allocation | Responsibilities |
|------|------------|------------------|
| **Full-Stack Developer** | 1 FTE | React/Next.js frontend development; Sui wallet integration using dApp kit; backend API for classification logic and community ratings; database schema and queries |
| **Sui/Web3 Specialist** | 0.5 FTE | Sui RPC integration; object type parsing and metadata extraction; package verification logic; wallet standard implementation; transfer transaction building |
| **UI/UX Designer** | 0.25 FTE | User interface design; intuitive classification display; action recommendation UX; mobile-responsive layouts; design system components |
| **Product Manager** | 0.25 FTE | Requirements refinement; user story prioritization; acceptance criteria; stakeholder communication; documentation review |

**Total team size: 2 FTE equivalent** across the project. This lean structure is appropriate for an MVP with well-defined scope and enables rapid iteration.

---

## 2. Planned Deliverables

### Core MVP Deliverables

- Publicly accessible web application deployed to production hosting (Vercel/Cloudflare)
- Sui wallet connection supporting all major wallets via @mysten/dapp-kit (Sui Wallet, Suiet, Ethos, Martian)
- NFT scanning engine that retrieves and parses all non-coin objects from connected wallet
- Three-tier classification system: **Legit** (green), **Dubious** (yellow), **Scam** (red)
- Curated allowlist of approved/known packages maintained via admin interface or config file
- Action recommendation engine suggesting Hide, Transfer, or Keep for each object
- Simple, intuitive UI with clear visual hierarchy and classification indicators
- Mobile-responsive design for wallet users on mobile devices

### Documentation Deliverables

- Setup guide for local development and self-hosting
- Classification logic documentation explaining scoring algorithms and thresholds
- User guide with screenshots and workflow explanations
- Admin guide for maintaining the approved packages list
- API documentation if backend endpoints are exposed

### Stretch Goal: Community Rating System

- Thumbs-up/thumbs-down voting interface for each NFT package or collection
- Backend storage for community votes with basic anti-gaming measures
- Aggregated community sentiment scores influencing classification
- Optional wallet-signature verification for vote authenticity

---

## 3. Projected Schedule

**Total estimated duration: 4-6 weeks** from kickoff to public MVP launch. The stretch goal (community rating) adds 1-2 weeks if pursued.

| Phase | Duration | Key Milestones |
|-------|----------|----------------|
| **Week 1: Foundation** | 5 days | Project setup; wallet connection implementation; basic UI scaffold; Sui RPC integration for object fetching |
| **Week 2: Core Scanning** | 5 days | NFT parsing and metadata extraction; object type identification; display grid/list with images and details |
| **Week 3: Classification** | 5 days | Allowlist data structure and admin interface; classification algorithm; visual indicators (Legit/Dubious/Scam) |
| **Week 4: Actions & Polish** | 5 days | Action recommendations UI; transfer transaction building; hide/filter functionality; UI/UX refinement; responsive design |
| **Week 5: Testing & Docs** | 5 days | End-to-end testing; edge case handling; documentation writing; deployment pipeline; staging environment validation |
| **Week 6: Launch & Buffer** | 5 days | Production deployment; final QA; bug fixes; stakeholder review; public launch |
| **Stretch: Community Ratings** | 5-10 days | Backend for vote storage; voting UI; aggregation logic; anti-gaming measures; integration with classification |

---

## 4. Cost Estimates

This is a lightweight MVP project with a focused scope. Cost estimates reflect the reduced complexity compared to enterprise-scale blockchain platforms.

| Component | Effort (Hours) | Cost |
|-----------|----------------|------------|
| Week 1-2: Foundation & Scanning | 80-100 |     |
| Week 3-4: Classification & Actions | 80-100 |    |
| Week 5-6: Testing, Docs & Launch | 60-80 |    |
| UI/UX Design | 30-40 |    |
| Product Management | 20-30 |    |
| Infrastructure (6 months) | N/A | Included |
| **MVP SUBTOTAL** | **270-350** | **$27K** |
| Stretch: Community Ratings | 40-80 | $7K |
| **TOTAL WITH STRETCH** | **310-430** | **$34K** |

> **Notes:** MVP-only budget is $27K. Infrastructure costs assume serverless deployment (Vercel/Cloudflare) with minimal backend requirements. Ongoing maintenance post-launch would be quoted separately.

---

## 5. Software Stack

### Frontend Technologies

| Technology | Purpose |
|------------|---------|
| **Next.js 14+** | React framework with App Router, SSR for SEO, and API routes for backend logic |
| **TypeScript** | Type safety for wallet interactions and object parsing |
| **TailwindCSS** | Utility-first styling for rapid UI development |
| **@mysten/dapp-kit** | Official Sui wallet adapter supporting all major Sui wallets |
| **@mysten/sui** | Sui TypeScript SDK for RPC calls and transaction building |
| **TanStack Query** | Data fetching and caching for wallet object queries |
| **Radix UI / shadcn/ui** | Accessible, unstyled component primitives for consistent UX |

### Backend Technologies

| Technology | Purpose |
|------------|---------|
| **Next.js API Routes** | Serverless backend for classification logic and community votes |
| **Supabase or PlanetScale** | Managed database for allowlist storage and community ratings (if stretch goal) |
| **Upstash Redis** | Rate limiting and caching for RPC calls (optional) |
| **Zod** | Runtime validation for API inputs and object parsing |

### Sui Integration

| Technology | Purpose |
|------------|---------|
| **Sui JSON-RPC** | Querying owned objects via `suix_getOwnedObjects` with filters |
| **Sui GraphQL API** | Alternative query interface for complex object filtering (optional) |
| **Object Display Standard** | Extracting NFT metadata (name, description, image_url) from Sui objects |

### Infrastructure

| Technology | Purpose |
|------------|---------|
| **Vercel** | Serverless deployment with edge functions and automatic scaling |
| **GitHub Actions** | CI/CD pipeline for automated testing and deployment |
| **Sentry** | Error tracking and performance monitoring |

---

## 6. Anticipated Risks

While this is a relatively low-complexity MVP, several risks should be considered and mitigated proactively.

| Risk | Impact | Description & Mitigation |
|------|--------|--------------------------|
| **Classification Accuracy** | 🟡 MEDIUM | False positives (legitimate NFTs marked as scams) or false negatives (scams marked as legit) could damage user trust. *Mitigation:* Conservative initial classification; clear disclaimers; easy user feedback mechanism; regular allowlist updates. |
| **Evolving Scam Tactics** | 🟡 MEDIUM | Scammers continuously adapt their techniques, potentially outpacing the classification system. *Mitigation:* Design for easy allowlist updates; community reporting; heuristic-based detection alongside curated lists. |
| **Community Vote Gaming** | 🟡 MEDIUM | Bad actors could manipulate community ratings to legitimize scams or defame competitors. *Mitigation:* Wallet-signature verification; rate limiting; weighted voting based on wallet age/activity; admin override capability. |
| **RPC Rate Limits** | 🟢 SMALL | Heavy users with large wallets could hit Sui RPC rate limits. *Mitigation:* Implement pagination; use caching; consider dedicated RPC endpoint for production. |
| **Wallet Compatibility** | 🟢 SMALL | Different wallets may have varying levels of support for Sui wallet standard. *Mitigation:* Test with all major wallets; use official dapp-kit; provide clear error messaging for unsupported wallets. |
| **Object Type Diversity** | 🟢 SMALL | Sui objects have highly varied structures; some may not conform to expected NFT patterns. *Mitigation:* Graceful fallback for unparseable objects; display raw type info when metadata unavailable. |
| **User Trust in Recommendations** | 🟢 SMALL | Users may be hesitant to act on automated recommendations, especially for transfers. *Mitigation:* Clear explanations for each recommendation; educational content; non-destructive default actions (hide vs transfer). |

---

## 7. High-Level Architecture

### 7.1 Overall System Architecture

We recommend a **lightweight, serverless architecture** optimized for simplicity and low operational overhead. The application will be primarily client-side with minimal backend requirements, leveraging Sui RPC directly from the browser for wallet queries.

- **Client-First Approach:** Wallet connection and object fetching happen entirely in the browser using @mysten/dapp-kit and @mysten/sui
- **Thin Backend:** Next.js API routes handle only allowlist storage, community votes, and server-side classification logic
- **Serverless Deployment:** Vercel or Cloudflare for automatic scaling and minimal DevOps

### 7.2 Wallet Integration Flow

The wallet connection flow follows Sui wallet standard best practices:

```
1. User clicks "Connect Wallet" → dapp-kit presents available wallet options
2. Upon connection → fetch wallet address and trigger object scan
3. Query suix_getOwnedObjects with pagination, filtering for non-Coin types
4. Parse Display metadata for each object (name, description, image_url, creator)
5. Pass objects to classification engine for scoring
```

### 7.3 Classification Algorithm

The classification system uses a **multi-signal approach** combining curated data with heuristics:

```
┌─────────────────────────────────────────────────────────────────┐
│                  CLASSIFICATION SIGNALS                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Signal 1: ALLOWLIST MATCH                                      │
│  └── Package ID in curated approved list? → Legit               │
│                                                                 │
│  Signal 2: BLOCKLIST MATCH                                      │
│  └── Package ID in known scam list? → Scam                      │
│                                                                 │
│  Signal 3: COMMUNITY RATING (stretch)                           │
│  └── Aggregate thumbs-up/down ratio                             │
│      ├── High positive ratio → boost score                      │
│      └── High negative ratio → lower score                      │
│                                                                 │
│  Signal 4: HEURISTICS                                           │
│  └── Flag suspicious patterns:                                  │
│      ├── Missing metadata                                       │
│      ├── Very recent package deployment                         │
│      └── Known scam keywords in description                     │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│  FINAL SCORE (0-100)                                            │
│  ├── 70-100: Legit   🟢                                         │
│  ├── 30-69:  Dubious 🟡                                         │
│  └── 0-29:   Scam    🔴                                         │
└─────────────────────────────────────────────────────────────────┘
```

### 7.4 Action Recommendation Logic

Based on classification, the system suggests appropriate actions:

| Classification | Recommendation | Details |
|----------------|----------------|---------|
| **Legit** 🟢 | Keep | No further action needed |
| **Dubious** 🟡 | Hide | Stored in local storage or backend preference; option to re-classify |
| **Scam** 🔴 | Transfer | Send to burn address (0x0 or designated spam sink); removes permanently |

**Batch Actions:** Support multi-select for hiding or transferring multiple objects at once.

### 7.5 Data Storage Strategy

Storage requirements are minimal for the MVP:

| Data Type | MVP Storage | Future Migration |
|-----------|-------------|------------------|
| **Allowlist/Blocklist** | JSON file in repository | Database (Supabase) if update frequency increases |
| **User Preferences** | Local storage | Backend persistence with wallet-signature auth |
| **Community Votes** | PostgreSQL table | Indexed for fast aggregation (package_id, wallet_address, vote_direction, timestamp) |

### 7.6 UI/UX Principles

The interface should prioritize clarity and user confidence:

- **Clear Visual Hierarchy:** Color-coded badges (green/yellow/red) for instant classification recognition
- **Progressive Disclosure:** Show summary first, expand for details and reasoning behind classification
- **Non-Destructive Defaults:** Never auto-execute transfers; always require explicit user confirmation
- **Educational Tooltips:** Explain why an NFT was classified a certain way to build user understanding
- **Filter and Sort:** Allow users to view by classification, sort by date received, search by name

---

## 8. Conclusion and Next Steps

The Sui Wallet NFT Scanner represents a valuable utility for the Sui ecosystem, addressing a real pain point for users dealing with spam and scam airdrops. Our proposed approach balances speed-to-market with extensibility, delivering a functional MVP within **4-6 weeks** while laying groundwork for community-driven enhancements.

---

<p align="center">
  <strong>Levuka Venture Labs FZCO</strong><br>
  February 2026
</p>
