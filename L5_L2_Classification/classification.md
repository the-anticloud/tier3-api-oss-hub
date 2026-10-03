# L5 Narrow / L2 General Classification — api-oss-hub
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign project registry: metadata, versioning, discovery for 123 Anticloud projects

## L5 Narrow
api-oss-hub specializes in sovereign project registry: metadata, versioning, discovery for 123 anticloud projects within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means api-oss-hub is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B is used for intelligent project discovery: 'Which projects support HIPAA biosignal processing?' triggers a PAX semantic search over the registry metadata.

## AIOSS Audit Relevance
Every registry event (project name + version + metadata hash + publish/update/deprecate) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
ISO/IEC 19770 (software asset management), NIST SP 800-161 (supply chain)
