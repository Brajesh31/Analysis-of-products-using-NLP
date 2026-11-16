# 🧭 Architecture and workflow diagrams

This page collects the editable Mermaid diagrams used to explain the project. Diagrams describe current boundaries and proposed future flows separately. Dashed arrows and labels such as “proposed” must not be interpreted as implemented integrations.

## 1. Current repository boundary

```mermaid
flowchart TB
  subgraph External
    F[Flipkart product review page]
    M[Myntra product review page]
  end
  subgraph Notebooks
    FN[Flipkart scraping notebook]
    MN[Myntra scraping notebook]
  end
  subgraph Static frontend
    H[Home HTML]
    L[Listing HTML]
    CSS[Page CSS]
    AS[Local assets]
  end
  F --> FN
  M --> MN
  H --> CSS
  L --> CSS
  H --> AS
  L --> AS
```

## 2. Proposed data lifecycle

```mermaid
flowchart TD
  A[Permitted source] --> B[Collection adapter]
  B --> C[Raw record]
  C --> D[Schema validation]
  D -->|Invalid| E[Reject with reason]
  D -->|Valid| F[Deduplicate]
  F --> G[Versioned preprocessing]
  G --> H[Exploratory analysis]
  H --> I[Optional model]
  I --> J[Evaluation]
  J --> K[Report with provenance]
```

## 3. Proposed review record lifecycle

```mermaid
sequenceDiagram
  participant N as Notebook
  participant S as Source page
  participant V as Validator
  participant D as Local dataset
  participant A as Analysis
  N->>S: Request permitted page
  S-->>N: HTML response
  N->>N: Parse minimum review fields
  N->>V: Submit candidate records
  V->>V: Validate types, rating scale, and text
  V-->>D: Accepted records and run manifest
  V-->>N: Rejection reasons and quality counts
  D->>A: Versioned dataset snapshot
  A->>A: EDA and optional NLP
  A-->>D: Derived report metadata
```

## 4. Proposed CI validation

```mermaid
flowchart TD
  P[Pull request] --> C[Checkout]
  C --> J[Validate notebook JSON]
  C --> M[Check Markdown links and whitespace]
  C --> H[Check static HTML references]
  J --> R{All checks pass?}
  M --> R
  H --> R
  R -->|Yes| OK[Ready for human review]
  R -->|No| FIX[Fix validation failures]
```

CI should not send requests to retail platforms. Use synthetic fixtures for deterministic tests.

## 5. Diagram maintenance rules

- Keep Mermaid source in Markdown, not screenshots alone.
- Use descriptive node labels and explicit decision branches.
- Label proposed or optional components clearly.
- Update diagrams when implementation boundaries change.
- Verify rendering on GitHub after editing.
- Do not add made-up database tables, endpoints, or model stages to the current architecture diagram.
