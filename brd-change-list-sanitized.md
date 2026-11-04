# BRD change list (sanitized)

Every sensitive value is replaced by a `[PLACEHOLDER]`. Re-add the real values by hand in the working copy. Each section lists only what to change relative to the earlier draft: **Replace** = swap the existing line, **Add** = new line, **Remove** = delete the line, **Append** = add text to the end of the existing line.

## Placeholder legend

| Placeholder | Meaning |
|---|---|
| `[COMPANY]` | Client company name |
| `[PROJECT_ABBR]` | Project short name |
| `[PHASE_NAME]` | Name of the first workstream |
| `[LATER_PHASE]` | Later phase where audio/video is planned |
| `[TA_ABBR]` / `[TA_FULL_NAME]` | Therapeutic area abbreviation and full name (pilot) |
| `[BRAND_NAME]` / `[BRAND_SHORTHAND]` | Brand for the pilot area, and its internal shorthand |
| `[N_...]` | Counts (files, studies, documents) |
| `[PCT]` | Percentage of total |
| `[PARSING_PLATFORM]` | Document parsing platform |
| `[OBJECT_STORAGE]` | Source file store |
| `[DATA_WAREHOUSE]` | Destination warehouse |
| `[TICKETING_TOOL]` | Request tracking tool |
| `[PERSON_A]` ... `[PERSON_G]` | Individual names |
| `[SPONSOR_TEAM]`, `[PLATFORM_TEAM]`, `[DATA_TEAM]`, `[INFRA_TEAM]`, `[IT_TEAM]` | Team names |
| `[BUSINESS_FUNCTION]` | Business team that reviews and uses the output |
| `[TEST_START_DATE]`, `[DEV_DURATION]`, `[EXTRACTION_TIME_RANGE]`, `[COMPLEXITY]` | Dates and estimates from the initial analysis |

## Title
- **Append** to the title: ` - [TA_ABBR] POC`

## 1. Purpose
- **Replace** the corpus count: "...corpus ([N_FILES_TOTAL] files across [N_STUDIES_TOTAL] studies and [N_TA_TOTAL] therapeutic areas) using the [PARSING_PLATFORM] platform." (the number of therapeutic areas was missing before)
- **Add** a new paragraph:
  "For this POC we are starting only with [TA_ABBR]. [TA_ABBR] stands for [TA_FULL_NAME], the therapeutic area for [COMPANY]'s brand [BRAND_NAME] ([BRAND_SHORTHAND]). [TA_ABBR] has [N_TA_FILES] files across about [N_TA_STUDIES] studies. Of these, [N_DOCS_IN_SCOPE] documents (PowerPoint, Excel, Word, PDF) are in scope for this POC, and [N_AV] files ([N_AUDIO] audio and [N_VIDEO] video) are planned for [LATER_PHASE] and are currently out of scope. The other therapeutic areas follow the pilot."

## 2. Business Objective
- **Edit** bullet 1: remove "transcripts, " so it reads "(decks, data tables, reports)".

## 3. Problem Statement
- **Replace** bullet 1: "[PROJECT_ABBR] market research data for [TA_ABBR] exists in unstructured formats such as PPT, Excel, Word and PDF"

## 4. Project Scope
In Scope
- **Replace** the ingest line: "Ingest [PROJECT_ABBR] [PHASE_NAME] MR files for [TA_ABBR] from [OBJECT_STORAGE] (pilot of about [N_TA_STUDIES] studies): [N_DOCS_IN_SCOPE] documents ([N_PPTX] PPTX, [N_XLSX] XLSX, [N_DOCX] DOCX, [N_PDF] PDF)"
- **Remove** "Process transcripts of audio/video files (transcripts provided)"
- **Edit** "Parse and preprocess documents using [PARSING_PLATFORM]" (remove the stray backticks)
- **Replace** "Extract agreed business fields/entities" with "Generate [PARSING_PLATFORM] output JSON (elements and metadata) for each document"
- **Replace** "Deliver output in structured format such as JSON, CSV, or Excel" with "Deliver output as JSON, written directly to [DATA_WAREHOUSE] tables"

Out of Scope
- **Replace** "Transcription of audio/video files" with: "Audio/video files: [N_AV] of the [N_TA_FILES] [TA_ABBR] files ([N_AUDIO] audio, [N_VIDEO] video), planned for [LATER_PHASE]. Early evaluation/testing of audio/video transcription in [PARSING_PLATFORM] starts once the DEV instance is available and the vendor confirms support (evaluation only)"
- **Add** "Therapeutic areas other than [TA_ABBR]"

## 5. Stakeholders
- **Business Sponsor**: append " / [SPONSOR_TEAM]" after the name.
- **SMEs**: append " - [BUSINESS_FUNCTION] business reviewers (names TBC)"
- **Operations/User Team**: append " - [BUSINESS_FUNCTION] analysts (first users; testing planned from [TEST_START_DATE])"
- **IT/Application Team**: replace the entry with " - [PLATFORM_TEAM]: [PERSON_A] (technical lead), [PERSON_B], [PERSON_C] (primary), [PERSON_D]; [DATA_TEAM] (data ingestion co-owner); [INFRA_TEAM] - [PERSON_E] (warehouse environment and platform)"
- **Security/Compliance**: append " - [COMPANY] Security (consulted); access and security shared by [INFRA_TEAM], [DATA_TEAM] and [PLATFORM_TEAM]"
- **Data Owner**: replace the entry with " - [DATA_TEAM] (research metadata); [PERSON_F] ([BRAND_NAME] data lead); [PERSON_G] / [IT_TEAM] (structured data and semantic layer, [LATER_PHASE])"
- **Add** a line: "Project Management - [PERSON_H] / [IT_TEAM] (risks, blockers, issues); IT requests via [PERSON_G] / [IT_TEAM] ([TICKETING_TOOL])"

## 6. Business Use Case
- **Edit** the first sentence: "...from [PROJECT_ABBR] Market Research documents ([TA_ABBR] studies & reports) for faster review and downstream use."

## 7. Source Data Requirements
- **Replace** "Document sources: ..." with "Document sources: [OBJECT_STORAGE]"
- **Replace** "Supported formats: ..." with "Supported formats: PDF, DOCX, XLSX, PPTX"
- **Replace** "Expected volume: ..." with "Expected volume: [N_TA_FILES] files across about [N_TA_STUDIES] studies ([TA_ABBR]): [N_DOCS_IN_SCOPE] documents in scope; [N_AV] audio/video files planned for [LATER_PHASE] (out of scope)"
- **Replace** "Sample data required for POC: See below" with "Sample data required for POC: [TA_ABBR] in-scope documents ([N_DOCS_IN_SCOPE], see table below). Initial analysis completed on [N_ANALYSED] documents; complexity [COMPLEXITY]; extraction time [EXTRACTION_TIME_RANGE] [CONFIRM per document or in total]"
- **Replace** the file-type table with this one:

| File Type | File Count | % of Total | POC Scope |
|---|---|---|---|
| PowerPoint | [N_PPTX] | [PCT] | In scope |
| Excel | [N_XLSX] | [PCT] | In scope |
| Word | [N_DOCX] | [PCT] | In scope |
| PDF | [N_PDF] | [PCT] | In scope |
| Audio | [N_AUDIO] | [PCT] | Out of scope (planned for [LATER_PHASE]) |
| Video | [N_VIDEO] | [PCT] | Out of scope (planned for [LATER_PHASE]) |
| Documents in scope | [N_DOCS_IN_SCOPE] | [PCT] | POC |
| Audio/video planned for [LATER_PHASE] | [N_AV] | [PCT] | Out of scope for now |
| TOTAL ([TA_ABBR]) | [N_TA_FILES] | 100% | |

## 8. Extraction Requirements
Rewrite the section so it follows the parsing platform's native output JSON:
- **Add** intro: "Extraction output is [PARSING_PLATFORM]'s native output JSON (element-based), written as-is to [DATA_WAREHOUSE] tables. Requirements apply to all in-scope file types (PPTX, XLSX, DOCX, PDF) and assume no custom schema."
- **Replace** the "Required fields/entities to extract:" list with "Required fields in the output JSON (per element):"
  - element ID
  - element type (e.g., title, narrative text, list item, table, image, header, footer)
  - text
  - file name and file type
  - page / slide / sheet number
  - languages
  - parent ID (element hierarchy)
  - table HTML (table elements)
  - source location (storage location and last modified date)
- **Remove** these old bullets: document ID, Study ID, title/name, date, author/sender, Therapeutic Area, Brand Name, Respondent Type, customer/vendor/entity name, key identifiers/reference numbers, amounts/units, clauses/terms, other business specific attributes.
- **Add** one bullet: "Business attributes (document ID, Study ID, Therapeutic Area, Brand Name ([COMPANY]/Competitor), Respondent Type (HCP/Caregiver/Patient), title/name, date, author/sender) are not produced by [PARSING_PLATFORM]. They are derived downstream from the stored JSON, the storage file path and the [DATA_TEAM] study registry."
- **Edit** the source reference bullet: "Extraction should preserve source reference where possible. (page/slide/sheet) via page number and source location" (also fixes the "timesatamp" typo).
- **Append** to the confidence bullet: " (e.g., detection confidence in the output)"
- Keep "Exceptions or unreadable files should be flagged."
- **Add** a bullet: "Exact fields to be confirmed against the sample output from the initial analysis [CONFIRM]"

## 9. Functional Requirements
- **Edit** "Parse and partition content using [PARSING_PLATFORM]" (remove the stray backticks).
- **Replace** "Extract predefined fields/entities" with "Generate [PARSING_PLATFORM] output JSON (elements and metadata) for each document"
- **Replace** "Export results into structured output" with "Write output JSON directly to [DATA_WAREHOUSE] tables"

## 11. Integration Requirements
- **Append** to "Input sources to connect with": ": [OBJECT_STORAGE]"
- **Replace** "Output destination such as ..." with "Output destination: [DATA_WAREHOUSE], with JSON written directly to tables"
- **Append** to "Any batch scheduling or trigger requirements": "; approach for new market research added after the initial set is open (raised at kickoff) [CONFIRM]"

## 13. Security and Compliance
- **Append** to "Define access restrictions by role": " (applied by therapy-area group in the application)"
- **Add** a line: "[LATER_PHASE] audio/video: personal and health details must be removed from transcripts before the content becomes searchable [CONFIRM owner, and whether this stays with the approved service if transcription is enabled in [PARSING_PLATFORM]]"

## 14. Assumptions
- **Replace** "Transcripts for audio/video files will be provided" with "Audio/video files ([N_AV] of [N_TA_FILES]) are planned for [LATER_PHASE] and are out of scope; transcription in [PARSING_PLATFORM] will be evaluated once the DEV instance is available, subject to vendor confirmation"
- **Add** "Business attributes (Study ID, Therapeutic Area, Brand Name, Respondent Type) are not part of [PARSING_PLATFORM] output and will be derived downstream by the [DATA_TEAM] metadata/rules build"
- **Add** "Development is estimated at approximately [DEV_DURATION]"

## 15. Risks
- **Add** "Charts and images within the [N_PPTX] PowerPoint files may not be fully captured as text"
- **Add** "[LATER_PHASE] audio/video transcription in [PARSING_PLATFORM] is not yet confirmed by the vendor and depends on DEV instance availability, so early evaluation may be delayed"

## 16. Success Criteria
- **Edit** the first line: "Process [N_DOCS_IN_SCOPE] [TA_ABBR] sample documents within [Y] time (initial analysis: [N_ANALYSED] documents, [EXTRACTION_TIME_RANGE])"
- **Add** "Extraction accuracy validated and signed off by business stakeholders post extraction"

## 17. Acceptance Criteria
- **Append** to "Output format matches agreed structure": " ([PARSING_PLATFORM] output JSON loaded to [DATA_WAREHOUSE] tables)"
- **Add** "Verification completed for accuracy, completeness and consistency"

## Items to re-check after re-adding real values
- Whether the extraction time range is per document or in total.
- Who removes personal and health details from transcripts.
- How new market research is added after the pilot.
- That the output JSON fields match a real sample output.
- `[Y]` and `[X%]` in section 16 still need numbers from the business.
