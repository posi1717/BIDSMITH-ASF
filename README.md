# TODS Gateway

## Tenders Official Document Support Platform
### Opportunity-to-Award Gateway for UK Public Procurement

TODS Gateway is an evidence-led public-procurement document inspection and assurance platform for the United Kingdom. Its purpose is to support the checking of tender, procurement, contract and supporting documents against applicable UK procurement law, regulation, policy notes, guidance and controlled evidence before publication, submission, award or reliance.[cite:37][cite:38]

TODS is designed to inspect documentation throughout the Opportunity-to-Award lifecycle. The initial operational focus includes the Procurement Act 2023, the Procurement Regulations 2024, Procurement Policy Notes including PPN 02/24, and related official UK Government guidance and authoritative source documents.[cite:38][cite:59]

TODS does not provide legal advice, certify that a document is compliant, approve an award, or authorise a submission. All consequential findings require accountable human review and sign-off.[cite:38][cite:44]

## Core Purpose

TODS exists to identify missing requirements, incomplete evidence, inconsistent information, document risks and required actions in UK public-procurement documentation before those defects become consequential in the procurement lifecycle.[cite:38]

The platform is intended to help procurement teams, bid teams, document reviewers and governed AI systems inspect documents from the first opportunity through to final award and submission readiness. It is an inspection and assurance gateway, not an automatic approval engine.[cite:44][cite:38]

```text
Opportunity
    ↓
Requirement discovery
    ↓
Document and evidence collection
    ↓
Tender-document inspection
    ↓
Correction and completion
    ↓
Human review and sign-off
    ↓
Submission / publication / award reliance
```

## What TODS Checks

TODS checks whether public-procurement documentation is complete, evidenced, current, traceable and aligned with applicable requirements. It is intended to make visible what is missing, what is inconsistent, what evidence exists, what evidence is absent and what action is required next.[cite:38][cite:59]

The platform should support inspection of at least the following:

- Tender notices and publication information.
- Procurement documents, specifications and scope definitions.
- Evaluation criteria, award criteria and procedure design.
- Supplier-selection, exclusion and debarment records.
- Transparency and procurement-data obligations.
- Contract-management, performance, open-book and change records.
- Supporting evidence, version history, provenance and audit state.[cite:59]

## Architecture Overview

TODS is built on a two-layer architecture with a clear processing boundary. SKBUK is the source-of-truth document store and governance layer, while MOUUK is the expert-knowledge layer comprising 34 specialist modules. MOUUK does not own original source PDFs; it receives references and manifests delivered from SKBUK.[cite:37][cite:59]

```text
UKKB /
├── SKBUK /
│   ├── documents /
│   │   └── <document_id> /
│   │       ├── original.pdf
│   │       └── metadata.json
│   ├── delivery /
│   │   └── MOUUK /
│   │       ├── MOUUK-0001.json
│   │       ├── MOUUK-0002.json
│   │       └── ...
│   ├── audit /
│   │   └── events.jsonl
│   └── source_registry.yaml
│
├── MOUUK /
│   ├── MOUUK-0001/ ... MOUUK-0034/
│   │   ├── manifest.yaml
│   │   ├── rules/
│   │   └── references/
│   └── ...
│
└── uk_kb_collector /
```

The current ingestion boundary is explicit: `discover -> validate -> store in SKBUK -> provenance/audit -> deliver reference manifest -> MOUUK`. Only after the raw corpus is accepted should later phases such as extraction, normalisation, chunking, embedding and retrieval run.[cite:59]

## SKBUK

SKBUK is the Knowledge Supply and Governance layer. It is responsible for storing original PDFs and their metadata, maintaining the approved authoritative-source registry, recording provenance and audit events, and delivering reference manifests to MOUUK modules.[cite:59]

Each source document in SKBUK should retain, where available, its source URL, publisher, version, hash and related metadata. This makes SKBUK the source-of-truth document store rather than a temporary download cache.[cite:59]

SKBUK responsibilities include:

- Discovering approved authoritative sources.
- Validating source and publisher.
- Storing original PDFs and metadata.
- Recording provenance, version and audit events.
- Delivering reference manifests to specialist modules.
- Preserving source-of-truth control over original documents.[cite:59]

## MOUUK

MOUUK is the expert-knowledge layer. Its 34 modules divide procurement expertise into controlled specialist responsibilities so that inspection can be performed by requirement domain rather than by a single general-purpose reasoning layer.[cite:59]

The catalogue defines MOUUK as a specialist layer that uses delivery references only. No MOUUK module may silently replace, modify or become the canonical owner of the original PDF.[cite:59]

### Example specialist modules

| Code | Module | Responsibility |
|---|---|---|
| MOUUK-0001 | Procurement Act 2023 | Statutory framework, duties, procedures, thresholds and notices [cite:59] |
| MOUUK-0002 | Procurement Regulations 2024 | Regulations made under the Procurement Act, prescribed information and procedures [cite:59] |
| MOUUK-0003 | Legacy Procurement Regulations | Pre-2024 procurement regimes and transitional context [cite:59] |
| MOUUK-0005 | Procurement Policy Notes | PPN applicability, mandatory and recommended actions, effective dates [cite:59] |
| MOUUK-0007 | Plan | Procurement planning and pre-market strategy [cite:59] |
| MOUUK-0008 | Define | Requirements, scope and specification definition [cite:59] |
| MOUUK-0009 | Procure | Tendering, evaluation, award and compliance execution stage [cite:59] |
| MOUUK-0010 | Manage | Post-award contract-management stage [cite:59] |
| MOUUK-0015 | Transparency and Procurement Data | Publication duties, notices and procurement-data obligations [cite:59] |
| MOUUK-0023 | Source Authority | Whether evidence is authoritative and from an approved source tier [cite:59] |
| MOUUK-0024 | Temporal and Version Intelligence | Document currency, update dates and supersession [cite:59] |
| MOUUK-0026 | Evidence and Provenance | Traceability of every knowledge claim [cite:59] |
| MOUUK-0028 | Notices, Standstill and Remedies | Award notices, standstill and remedies [cite:59] |
| MOUUK-0030 | Conflicts of Interest | Identification, mitigation and records [cite:59] |
| MOUUK-0031 | SME, VCSE and Reserved Contracts | Access, reservation and participation policy outcomes [cite:59] |
| MOUUK-0034 | Insurance and Mandatory Policies | Insurance requirements and policy evidence [cite:59] |

The full MOUUK catalogue spans legal instruments, policy notes, procurement lifecycle stages, transparency, supplier participation, sustainability, security, data governance, provenance, procedural controls and contract-management topics.[cite:59]

## Regulatory and Policy Focus

The initial inspection scope should be centred on core UK public-procurement instruments and their supporting guidance. This includes the Procurement Act 2023, the Procurement Regulations 2024, applicable Procurement Policy Notes such as PPN 02/24, and legacy regimes where transitional context still matters.[cite:38][cite:59]

| Instrument or source | Inspection role |
|---|---|
| Procurement Act 2023 | Core statutory duties, procedures, thresholds, notices and framework concepts [cite:59] |
| Procurement Regulations 2024 | Regulatory requirements, prescribed information and procedures [cite:59] |
| Procurement Policy Notes | Policy applicability, effective dates and required actions, including PPN 02/24 within the PPN domain [cite:59] |
| Official guidance | Cabinet Office, gov.uk, legislation.gov.uk and other official guidance where applicable [cite:59] |
| Legacy regulations | Transitional procurement context under pre-2024 regimes [cite:59] |

## Inspection Output

TODS should produce an inspection-oriented output rather than a generic chatbot answer. The purpose of the output is to show what requirement was checked, what evidence supports or fails to support it, which specialist module produced the finding, what source/version was used, what risk exists and what action is required next.[cite:38][cite:59]

A practical TODS inspection record should capture at least:

- Inspection ID or correlation ID.
- Requirement or control being checked.
- Applicable source and version.
- Evidence item or evidence gap.
- Specialist module responsible.
- Finding state such as supported, missing, inconsistent, unclear or escalated.
- Required corrective action.
- Human-review status and sign-off state.[cite:59]

## Assurance Principles

TODS should operate on these principles:

1. Evidence before assertion.
2. Official source governance through SKBUK.
3. Version-aware inspection.
4. Requirement traceability.
5. Specialist-module accountability.
6. Human review before consequential use.
7. No automatic legal or procurement approval.
8. Auditability of source, version, finding and action.[cite:38][cite:59]

Model confidence must never be treated as a replacement for evidence. Likewise, a specialist module must never become the owner of the original document it analyses.[cite:59]

## Human Review Boundary

TODS supports document inspection and assurance, but it does not replace accountable human judgement. It should be used to support review before publication, submission, award or other consequential use in public procurement.[cite:44][cite:38]

A human reviewer remains responsible for accepting findings, requiring more evidence, correcting documents, escalating issues and formally signing off the result.[cite:44]

## Ecosystem Position

Within the wider HoneyB2024 ecosystem, TODS Gateway is the assurance and inspection gate for procurement-document work. It is intended to operate alongside document-workflow and bid-production systems, but with a distinct role as the evidence-led checking and governance layer.[cite:37]

```text
Bidsmith / tender work
        ↓
Doccute / workflow operations
        ↓
TODS Gateway
  ├─ SKBUK source governance
  ├─ MOUUK specialist inspection
  └─ Human review and sign-off
```

## Implementation Priorities

The current implementation priorities should remain aligned with the authoritative processing boundary:

1. Preserve SKBUK as the authoritative source-of-truth document layer.
2. Maintain the approved source registry and provenance records.
3. Maintain the MOUUK 34-module catalogue and specialist boundaries.
4. Deliver authoritative references from SKBUK to MOUUK.
5. Complete raw-PDF corpus acceptance before later extraction or retrieval phases.
6. Build inspection outputs that show requirements, evidence, risk and action.
7. Maintain audit records and version awareness across the lifecycle.[cite:37][cite:59]

## Documentation Rule

TODS should be maintained under a documentation-first discipline. Anyone working on the project should read the authoritative manuals, catalogues and current approved documentation before changing architecture, README content, modules, processing boundaries or operational claims.[cite:48]

Obsolete instructions, superseded temporary installation notes and misleading implementation claims should be reviewed and removed from the active working path once their historical role has been assessed.[cite:47]

## Disclaimer

TODS Gateway supports evidence-led inspection of UK public-procurement documents. It does not provide legal advice, does not certify legal compliance and does not replace accountable procurement, legal or governance review.[cite:44][cite:38]
