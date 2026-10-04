# BidSmith ASF - TODS Gateway

## Tenders Official Document Support Platform

TODS Gateway is an evidence-led inspection and assurance platform for UK public-procurement documents. It supports review across the opportunity-to-award lifecycle while preserving source authority, version control, provenance and accountable human sign-off.

TODS is not legal advice, an automatic compliance certificate, an award approval system or a replacement for accountable procurement and legal review.

## Core workflow

```text
Opportunity -> Plan -> Define -> Procure -> Evaluate -> Award -> Manage
```

## UKKB architecture

```text
SKBUK (source-of-truth documents and governance)
        -> delivery references/manifests
MOUUK (34 specialist expert-knowledge modules)
        -> inspection findings and evidence traceability
TODS review output -> human review and sign-off
```

## SKBUK

SKBUK is the source-of-truth document store and governance layer. It stores original PDFs, metadata, source URLs, publishers, versions, hashes, source-registry decisions and audit events.

MOUUK receives references and manifests from SKBUK. MOUUK does not own original PDFs.

```text
UKKB/
├── SKBUK/
│   ├── documents/<document_id>/original.pdf
│   ├── documents/<document_id>/metadata.json
│   ├── delivery/MOUUK/MOUUK-0001.json ... MOUUK-0034.json
│   ├── audit/events.jsonl
│   └── source_registry.yaml
├── MOUUK/MOUUK-0001 ... MOUUK-0034/
└── docs/MOUUK_MODULE_CATALOGUE.md
```

## MOUUK expert layer

MOUUK is the expert-knowledge layer containing exactly 34 modules. Each module has a defined identity and responsibility. A module may contain a manifest, specialist rules and delivery references, but the original source document remains canonical in SKBUK.

## Complete module catalogue

The modules are intentionally listed in numeric order from `MOUUK-0001` to `MOUUK-0034`.

| Code | Module | Responsibility | Key properties | Primary evidence |
|---|---|---|---|---|
| `MOUUK-0001` | Procurement Act 2023 | Expert on the Procurement Act 2023 statutory framework | Statutory interpretation, duties, procedures, thresholds, notices | legislation.gov.uk + official gov.uk guidance |
| `MOUUK-0002` | Procurement Regulations 2024 | Expert on regulations made under the Procurement Act | Regulatory requirements, prescribed information, notices, procedures | legislation.gov.uk + gov.uk |
| `MOUUK-0003` | Legacy Procurement Regulations | Expert on pre-2024 procurement regimes and transition | PCR 2015, UCR 2016, CCR 2016, DSPCR 2011, transitional context | legislation.gov.uk |
| `MOUUK-0004` | Other Relevant Legislation | Expert on legislation affecting procurement outside the core Procurement Act | Cross-law applicability, statutory constraints, subject-specific legislation | legislation.gov.uk + official department guidance |
| `MOUUK-0005` | Procurement Policy Notes and Policy Notices | Expert on Cabinet Office PPN requirements and policy notices | PPN applicability, mandatory/recommended actions, effective dates | gov.uk / Cabinet Office |
| `MOUUK-0006` | National Procurement Policy Statement | Expert on NPPS priorities and applicability | National priorities, contracting-authority duties, policy alignment | gov.uk / Cabinet Office |
| `MOUUK-0007` | Plan | Expert for procurement planning and pre-market strategy | Pipeline, objectives, governance, market strategy, route planning | Official government guidance / buyer policy |
| `MOUUK-0008` | Define | Expert for requirements and specification definition | Outcomes, scope, requirements, evaluation design, market engagement | Official guidance / buyer documentation |
| `MOUUK-0009` | Procure | Expert for the procurement execution stage | Procedures, tendering, evaluation, award, notices, compliance | Legislation + official guidance |
| `MOUUK-0010` | Manage | Expert for post-award contract management | Performance, governance, change, payment, termination | Official contract-management guidance |
| `MOUUK-0011` | Social Value | Expert on social-value procurement policy | Social-value objectives, evaluation, commitments, delivery | gov.uk + official policy |
| `MOUUK-0012` | TOMs | Specialist child module of Social Value for Themes, Outcomes and Measures | TOMs mapping, measurement, metrics, social-value evidence | Official buyer/framework materials |
| `MOUUK-0013` | Supplier Selection | Expert on supplier qualification and conditions of participation | SQ, conditions, selection criteria, financial/technical capability | Legislation + official guidance |
| `MOUUK-0014` | Exclusion and Debarment | Expert on supplier exclusion and debarment | Mandatory/discretionary grounds, debarment list, due diligence | Legislation + Cabinet Office guidance |
| `MOUUK-0015` | Transparency and Procurement Data | Expert on transparency obligations and procurement data | Notices, publication, Contracts Finder/CDP data, disclosure | Legislation + official platforms |
| `MOUUK-0016` | Framework Agreements | Expert on framework procurement structures | Framework design, call-offs, award mechanisms, rules | Legislation + official guidance |
| `MOUUK-0017` | Dynamic Markets | Expert on Dynamic Markets | Admission, operation, competition, supplier access | Legislation + official guidance |
| `MOUUK-0018` | Contract Management and Open Book | Expert on contract performance and open-book management | KPIs, payment, open book, modification, governance | Official guidance + contract policy |
| `MOUUK-0019` | Sustainability and Carbon | Expert on environmental and carbon requirements | Net zero, carbon reduction, environmental criteria, reporting | Official government policy/guidance |
| `MOUUK-0020` | Modern Slavery and Responsible Supply Chain | Expert on modern slavery and responsible sourcing | Due diligence, supply-chain risk, reporting, remediation | Legislation + gov.uk guidance |
| `MOUUK-0021` | Security and National Security | Expert on security-sensitive procurement | National security, security controls, supplier risk, classified context | Legislation + official security guidance |
| `MOUUK-0022` | Data Protection and Information Governance | Expert on data protection and information governance in procurement | UK GDPR, DPA 2018, DPIA, information governance, records | Legislation + ICO/official guidance |
| `MOUUK-0023` | Source Authority | Governance expert that determines whether evidence is authoritative | Source tier, publisher, jurisdiction, authority status, allow/reject | SKBUK Source Registry + official domains |
| `MOUUK-0024` | Temporal and Version Intelligence | Governance expert for document currency | Publication/update dates, supersession, version comparison, effective periods | SKBUK provenance/version metadata |
| `MOUUK-0025` | Cross-Governance Relationships | Expert on relationships between laws, policies, guidance and modules | Dependencies, conflicts, applicability, cross-module links | SKBUK provenance + official sources |
| `MOUUK-0026` | Evidence and Provenance | Expert on traceability of every knowledge claim | Document ID, source URL, hash, citation chain, evidence status | SKBUK document metadata + audit trail |
| `MOUUK-0027` | Procedures and Award Criteria | Expert on procurement procedure selection and award criteria design | Procedures, award criteria, evaluation | Legislation + official guidance |
| `MOUUK-0028` | Notices, Standstill and Remedies | Expert on award notices, standstill and procurement remedies | Notices, challenge periods, remedies, court process | Legislation + official guidance |
| `MOUUK-0029` | Below-threshold and Covered Procurement | Expert on below-threshold and covered procurement | Coverage, thresholds, procedures, transparency | Legislation + official guidance |
| `MOUUK-0030` | Conflicts of Interest | Expert on conflicts of interest in procurement | Identification, mitigation, declarations, records | Legislation + official guidance |
| `MOUUK-0031` | SME, VCSE and Reserved Contracts | Expert on SME, VCSE and reserved-contract policy | Access, reservation, participation, policy outcomes | Legislation + official guidance |
| `MOUUK-0032` | Devolved and Sector Regimes | Expert on devolved administrations and sector-specific regimes | Jurisdiction, utilities, defence, sector rules | Legislation + official guidance |
| `MOUUK-0033` | Economic and Financial Standing | Expert on supplier economic and financial standing | Financial assessment, insurance, evidence, proportionality | Legislation + official guidance |
| `MOUUK-0034` | Insurance and Mandatory Policies | Expert on insurance and mandatory procurement policies | Insurance requirements, policy compliance, evidence | Legislation + official guidance |

## Processing boundary

The current ingestion phase is raw-PDF only:

```text
discover -> validate -> store in SKBUK -> provenance/audit -> deliver reference manifest -> MOUUK
```

Only after the raw corpus is accepted should the later processing phase run:

```text
PDF -> extract -> normalize -> chunk -> embed -> retrieval
```

No MOUUK module may silently replace, modify or become the canonical owner of an original PDF.

Git does not persist empty directories; runtime creates module and reference directories when a document is delivered.

## Inspection output

A TODS inspection should identify:

- The requirement checked.
- The applicable MOUUK module.
- The source document.
- The source version and effective period.
- Evidence found or missing.
- Finding status.
- Risk or consequence.
- Required action.
- Human-review and sign-off state.

Suggested statuses:

```text
supported
missing
incomplete
inconsistent
outdated
unauthorised
unclear
escalated
accepted
rejected
```

## Human review boundary

TODS supports evidence-led inspection. It does not provide legal advice, certify compliance, approve procurement or replace accountable human judgement.

Consequential findings require human review and sign-off.

## Implementation priorities

1. Preserve original PDFs in SKBUK.
2. Validate sources against the approved source registry.
3. Record provenance, versions, hashes and audit events.
4. Deliver controlled references to MOUUK.
5. Maintain all 34 module boundaries.
6. Accept the raw corpus before extraction, embedding or retrieval.
7. Produce traceable findings with evidence and required actions.

## Disclaimer

TODS Gateway supports evidence-led inspection of UK public-procurement documents.

It does not provide legal advice, certify legal compliance, approve procurement activity or replace accountable procurement, legal, governance or contracting-authority review.
