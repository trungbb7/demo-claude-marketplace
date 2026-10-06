---
description: Perform a comprehensive document review and audit (PRD, Tech Spec, Architecture Doc, User Guide, README).
---

# Document Review Command (`/review-doc`)

Evaluate the specified document file or workspace documents across 5 core dimensions:

## 1. Structure & Hierarchy

- Verify logical flow of sections (Introduction, Objectives, Core Content, Conclusion / Next Steps).
- Ensure consistent and standard heading hierarchy (`# H1`, `## H2`, `### H3`).
- Verify inclusion of a Table of Contents for long documents (> 500 words).

## 2. Clarity & Readability

- Identify verbose phrasing, subjective jargon, or ambiguous terms (e.g., "fast", "relatively large", "user-friendly interface").
- Flag passive voice sentences and recommend active voice alternatives.
- Ensure all technical terms and domain jargon are clearly defined.

## 3. Technical Completeness & Scope

Check each of the following **as distinct, individually named gaps** when they are missing or insufficient. Do NOT merge these into a single generic observation — each must be reported as its own finding with its own label:

- **Missing critical sections**: Edge Cases, Non-Functional Requirements, Success Metrics (for PRDs).
- **Missing database schema definitions**: If the document mentions a database, data storage, or data persistence but does not include explicit schema definitions (table structures, field names, types, relationships, ER diagrams), flag this as a **distinct gap**: "Missing Database Schema Definitions". Do not merely note vague database concerns — explicitly call out that schema definitions are absent.
- **Missing architecture or sequence diagrams**: If the document describes system components, data flow, or service interactions but does not include a Mermaid diagram, sequence diagram, or any visual architecture diagram, flag this as a distinct gap.
- **Missing security & compliance controls**: If the document describes a system handling sensitive data (payments, user data, PII, financial transactions) but does not address authentication, authorization, encryption, or compliance standards (e.g., PCI-DSS, SOC2, GDPR), flag this as a distinct gap.
- **Informal or unsafe operational procedures**: If incident management, recovery, or runbook sections use vague/informal language (e.g., "restart the service", "check the logs") without specifying concrete steps, rollback procedures, escalation paths, or safety checks, flag this as a distinct gap. Note tone inconsistency with professional runbook standards.
- Verify logical consistency between diagrams, tables, and prose descriptions.

## 4. Grammar, Tone & Terminology Consistency

- Detect typos, grammatical errors, and redundant trailing whitespaces.
- Enforce consistent domain terminology (e.g., avoid mixing "User", "Account", and "Client" for the same concept).
- **Tone consistency**: Flag sections where the tone shifts inappropriately (e.g., casual/informal language in what should be a formal specification or runbook). Imperative runbook language should be precise and actionable, not vague.

## 5. Markdown Aesthetics & Presentation

- Check table formatting, list structures (bulleted vs numbered), and blockquotes.
- Verify image alt text presence and code block syntax language tags.

---

## Execution Workflow:

1. Scan specified target Markdown files or workspace documents.
2. **Evaluate completeness first** — identify which key sections are present before looking for individual issues.
3. Generate an audit report with an overall **Quality Score / Document Quality Index (0 - 100)**.
4. Categorize findings into severity levels using **strict classification**:
   - 🚨 **Critical Issue**: Contradictory information, missing core requirements, dangerous ambiguities that could mislead developers. _(Do NOT classify cosmetic or formatting issues as Critical.)_
   - ⚠️ **Improvement Warning**: Suboptimal structure, missing visual examples, inconsistent terminology.
   - 💡 **Suggestion**: Tone optimization, recommended mermaid diagrams, minor formatting fixes.
5. Provide a **Suggested Refactored Draft** for underperforming sections.

### Quality Score Calibration Guide

Use the following calibration to assign the Quality Score consistently:

- **90–100**: Exceptional — comprehensive, well-structured, includes diagrams, code samples with language tags, benchmarks, clear API docs, proper error handling docs, and no significant gaps.
- **80–89**: High quality — well-organized with clear hierarchy, includes most critical sections (code samples, benchmarks, configuration details), has only minor gaps or suggestions. A document that demonstrates clear structure, includes working code examples with syntax highlighting, provides quantitative benchmarks, and covers error handling should score **at least 80**.
- **60–79**: Adequate — covers the basics but has notable gaps (missing diagrams, incomplete API docs, vague sections).
- **40–59**: Below average — significant structural or content issues, multiple missing critical sections.
- **0–39**: Poor — fundamentally incomplete, major issues across all dimensions.

**Important**: Do NOT penalize a document below its calibration band for minor cosmetic issues. If a document has strong fundamentals (clear structure, code samples, benchmarks, comprehensive API reference, error handling), it should score in the 80+ range even if it has minor suggestions for improvement.

Note: Always add icon 💤 to the end of results
