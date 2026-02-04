# Sui Transaction Explainer

**Human-Readable Transaction Summaries for the Sui Network**

> Technical Proposal by **Levuka Venture Labs FZCO** | February 2026

---

## Executive Summary

This proposal outlines our approach to building a lightweight, user-friendly web application that transforms complex Sui transaction data into plain-language explanations. Blockchain transactions are notoriously opaque to non-technical users, and even experienced developers often struggle to quickly parse the meaning of a transaction from raw RPC output.

The **Sui Transaction Explainer** will accept a transaction digest, fetch the transaction details from Sui RPC, and present a human-readable summary describing what happened: objects created, transferred, or mutated; Move function calls executed; and gas consumed. An optional visualization will show the flow of assets between addresses.

This is the smallest-scope project of the three proposals, targeting a **2-3 week delivery timeline** with a minimal team. The result will be a polished, publicly hosted MVP with clear documentation.

---

## 1. Skill Mix Required

This is a focused utility application with well-defined scope. A minimal team can deliver effectively, with the primary challenge being deep understanding of Sui transaction structures rather than breadth of engineering work.

| Role | Allocation | Responsibilities |
|------|------------|------------------|
| **Full-Stack Developer** | 1 FTE | React/Next.js frontend; transaction parsing logic; human-readable text generation; visualization component; API integration with Sui RPC |
| **Sui Protocol Specialist** | 0.25 FTE | Transaction structure expertise; Move call interpretation; object change categorization; edge case identification; package/module labeling logic |
| **Product/UX Advisor** | 0.1 FTE | User experience guidance; plain-language copy review; visualization design input; documentation review |

**Total team size: ~1.35 FTE equivalent.** This is the leanest team structure across the three proposals, appropriate for a utility tool with focused functionality.

---

## 2. Planned Deliverables

### Core MVP Deliverables

- Publicly hosted web application accessible at a dedicated URL
- Transaction input supporting both raw digest (hash) and Suiscan/Suivision URLs
- Sui RPC integration fetching full transaction details via `sui_getTransactionBlock`
- Human-readable summary generation covering transfers, object mutations, and creations
- Gas usage display in human-friendly format (e.g., "Gas used: 0.015 SUI")
- Move call labeling showing package name, module, and function with clear formatting
- Object change breakdown: created, mutated, deleted, wrapped, unwrapped counts
- Error handling for invalid digests, failed transactions, and network issues
- Mobile-responsive design for on-the-go transaction lookup

### Documentation Deliverables

- Architecture overview explaining data flow from input to rendered output
- Data source documentation covering Sui RPC endpoints and response parsing
- Usage guide with examples of different transaction types
- Self-hosting instructions for users who want to run their own instance

### Stretch Goals

- Visual flow diagram showing sender → recipient with arrows and object icons
- "Explain another transaction" button for quick iteration during demos
- Share/permalink feature generating shareable URLs for specific transactions
- Transaction history (local storage) showing recently viewed digests

---

## 3. Projected Schedule

**Total estimated duration: 2-3 weeks** from kickoff to public launch. This is the fastest delivery timeline across the three proposals, reflecting the focused scope.

| Phase | Duration | Key Milestones |
|-------|----------|----------------|
| **Days 1-3: Setup & RPC** | 3 days | Project scaffolding; Sui RPC integration; transaction fetching; basic response parsing and logging |
| **Days 4-6: Core Parsing** | 3 days | Transaction structure decomposition; object change extraction; Move call identification; gas calculation |
| **Days 7-9: Text Generation** | 3 days | Plain-language summary engine; template system for different transaction types; edge case handling |
| **Days 10-12: UI Polish** | 3 days | Frontend implementation; input validation; loading states; error displays; responsive design |
| **Days 13-15: Testing & Docs** | 3 days | End-to-end testing with diverse transaction types; documentation writing; deployment pipeline |
| **Stretch: Visualization** | 2-3 days | Flow diagram component; sender/recipient arrows; object icons; "Explain another" button |

---

## 4. Cost Estimates

This is the most cost-effective project of the three proposals, with a tight scope and minimal infrastructure requirements. The primary investment is developer time for transaction parsing logic.

| Component | Effort (Hours) | Phase Cost |
|-----------|----------------|------------|
| Days 1-6: RPC & Parsing | 40-50 | N/A |
| Days 7-12: Text Gen & UI | 40-50 | N/A |
| Days 13-15: Testing & Docs | 20-25 | N/A |
| Sui Protocol Specialist | 15-20 | N/A |
| Product/UX Advisor | 8-12 | N/A |
| ***Infrastructure (6 months)*** | N/A | ***$100-$300 USD*** |
| **MVP SUBTOTAL** | **123-157** | **$12K USD** |
| Stretch: Visualization | 16-24 | N/A |
| **TOTAL WITH STRETCH** | **139-181** | **$15K USD** |

> **Notes:** MVP-only budget is $12K. Infrastructure costs are minimal due to serverless deployment with no database requirements.

---

## 5. Software Stack

The stack is intentionally minimal, prioritizing simplicity and zero operational overhead. No database is required for the core MVP.

### Frontend Technologies

| Technology | Purpose |
|------------|---------|
| **Next.js 14+** | React framework with App Router; can be fully static or use API routes |
| **TypeScript** | Type safety for transaction response parsing |
| **TailwindCSS** | Utility-first styling for clean, minimal UI |
| **@mysten/sui** | Official Sui TypeScript SDK for RPC calls |
| **Radix UI / shadcn/ui** | Accessible component primitives (input, cards, tooltips) |

### Visualization (Stretch Goal)

| Technology | Purpose |
|------------|---------|
| **React Flow** | Node-based diagrams for sender/recipient flow visualization |
| **D3.js** | Custom SVG-based flow arrows if simpler visualization needed |
| **Lucide Icons** | Consistent iconography for object types (coin, NFT, package) |

### Sui Integration

| Technology | Purpose |
|------------|---------|
| **sui_getTransactionBlock** | Primary RPC method fetching full transaction details with effects |
| **sui_multiGetObjects** | Batch fetch object metadata for richer descriptions (optional) |
| **Sui Public RPC** | Default endpoint; can be swapped for dedicated RPC if rate limited |

### Infrastructure

| Technology | Purpose |
|------------|---------|
| **Vercel** | Serverless deployment with edge caching; free tier likely sufficient |
| **GitHub Actions** | CI/CD for automated deployment on push |

---

## 6. Anticipated Risks

This is a low-risk project with limited external dependencies. The primary challenges are interpretive rather than technical.

| Risk | Impact | Description & Mitigation |
|------|--------|--------------------------|
| **Transaction Type Coverage** | 🟡 MEDIUM | Sui supports many transaction types (PTBs, sponsored, etc.); not all may have clean plain-language mappings at MVP. *Mitigation:* Prioritize common types (transfers, swaps, mints); graceful fallback to structured display for complex transactions. |
| **Package/Module Naming** | 🟡 MEDIUM | Move calls show package IDs which are not human-readable; mapping to friendly names requires maintenance. *Mitigation:* Curate list of known packages (Sui Framework, DeepBook, popular DEXs); display raw ID with tooltip for unknowns. |
| **Plain-Language Accuracy** | 🟢 SMALL | Generated summaries could be misleading if parsing logic misinterprets transaction intent. *Mitigation:* Conservative language ("appears to" vs definitive claims); show raw data alongside summary; user feedback mechanism. |
| **RPC Rate Limits** | 🟢 SMALL | High traffic could hit public RPC limits. *Mitigation:* Client-side caching of viewed transactions; consider dedicated RPC endpoint for production if traffic warrants. |
| **Failed Transaction Display** | 🟢 SMALL | Users may paste digests of failed transactions expecting explanation. *Mitigation:* Detect failed status; display error message from transaction; explain gas was still consumed. |
| **URL Parsing Edge Cases** | 🟢 SMALL | Users may paste various URL formats from different explorers. *Mitigation:* Regex patterns for known explorers (Suiscan, Suivision); fallback to treating full input as digest. |

---

## 7. High-Level Architecture

### 7.1 Overall System Architecture

The architecture is intentionally simple: a single-page application that makes direct RPC calls from the browser. No backend server is strictly required, though API routes can be used for RPC proxying if CORS or rate limiting becomes an issue.

- **Client-Only Option:** Direct browser-to-RPC calls using @mysten/sui; simplest deployment
- **Proxied Option:** Next.js API route forwards RPC requests; allows caching and rate limit management
- **No Database:** Transaction data is fetched on-demand; no persistence required for MVP

### 7.2 Data Flow

The application follows a straightforward request-response flow:

```
1. User pastes transaction digest or explorer URL into input field
2. Input parser extracts digest from URL if needed, validates format (64-char hex)
3. RPC call fetches transaction block with showEffects, showInput, showObjectChanges options
4. Parser extracts structured data: sender, gas, object changes, Move calls, status
5. Text generator produces plain-language summaries using templates
6. UI renders summary cards, gas info, and optional visualization
```

### 7.3 Transaction Parsing Strategy

The parser must handle Sui's Programmable Transaction Blocks (PTBs) which can contain multiple operations. Key extraction points:

| Data Point | Source Path | Notes |
|------------|-------------|-------|
| **Sender** | `transaction.transaction.data.sender` | The address that signed |
| **Gas** | `effects.gasUsed` | Compute, storage, rebate values; convert MIST to SUI |
| **Object Changes** | `objectChanges` array | Categorized as created, mutated, deleted, wrapped, unwrapped |
| **Move Calls** | `transaction.data.transaction.transactions` | Extract package, module, function |
| **Transfers** | TransferObjects commands | Map to recipient addresses |

### 7.4 Plain-Language Generation

The text generation engine uses template-based composition with smart defaults:

```
Transfer Template:    "{sender_short} transferred {object_type} to {recipient_short}"
Coin Transfer:        "{sender_short} sent {amount} {coin_type} to {recipient_short}"
Object Creation:      "{count} new object(s) were created" with type breakdown
Move Call:            "Called {module}::{function} on {package_name}"
Gas Summary:          "Gas used: {total_sui} SUI ({compute} compute + {storage} storage - {rebate} rebate)"
Address Shortening:   Display as "0x1234...abcd" with full address in tooltip
```

### 7.5 Known Package Registry

To improve readability, maintain a curated mapping of package IDs to human-friendly names:

| Package ID | Friendly Name |
|------------|---------------|
| `0x2` | Sui Framework (coin, transfer, etc.) |
| `0xdee9...` | DeepBook (order book DEX) |
| Popular DEX packages | "Cetus", "Turbos", etc. |
| NFT standards | "Kiosk", "Display", collection names where known |

Store as JSON config file; easy to extend over time.

### 7.6 UI Component Structure

The interface is organized into clear sections:

- **Input Section:** Large text input with placeholder showing expected format; "Explain" button
- **Summary Card:** Plain-language explanation in natural prose; status badge (success/failed)
- **Gas Card:** Human-readable gas breakdown with MIST → SUI conversion
- **Object Changes Card:** Grouped by type (created, mutated, etc.) with counts and details
- **Move Calls Card:** List of function calls with package labels
- **Flow Visualization (stretch):** Sender → Action → Recipient diagram

---

## 8. Conclusion and Next Steps

The Sui Transaction Explainer is a high-value, low-effort utility that will benefit developers, users, and the broader Sui ecosystem. By transforming opaque transaction data into plain-language summaries, we lower the barrier to understanding on-chain activity and support adoption.

This is the smallest and fastest project of the three proposals, delivering a polished MVP in **2-3 weeks** at a budget of **$15K-30K**. The focused scope minimizes risk while providing clear, demonstrable value.

### Proposed Next Steps

1. Brief kickoff call to confirm scope and prioritize stretch goals
2. Gather 10-20 example transaction digests covering diverse transaction types for testing
3. Initial package registry seeding with Sui Framework and top 10 protocols
4. Development kickoff immediately following agreement

---

<p align="center">
  <strong>Levuka Venture Labs FZCO</strong><br>
  February 2026
</p>
