# Tathabbut — Expert Review Forms

Two **Arabic-first HTML forms** for collecting fiqh rule reviews and expert case annotations. The pages are static, self-contained and designed for use during an in-person meeting, either online via GitHub Pages or offline from downloaded files. A start page is also included.

## Open the application

**Published website:** [Tathabbut Expert Review Workspace](https://fhamdimed.github.io/tathabbut-expert-review/)

Open the link in a modern browser to choose **Rule Validation** or **Case Annotation**. No account or installation is required. The application can also be downloaded and run offline using `index.html`.

## Files

| File | Purpose |
|---|---|
| `index.html` | Start page; links to both forms. |
| `rule-validation.html` | Create, review and export rule records. |
| `case-annotation.html` | Create, review and export question–answer annotation records. |
| `expert_rule_template.csv` | Empty rule template with the expected column names. |
| `evaluation_annotation_template.csv` | Empty case annotation template with the expected column names. |
| `QUICK_START_AR.md` | Short instructions for students and experts in Arabic. |

The pages include all their own styles and JavaScript. They **do not submit entered form data to a server**. Opening the hosted site downloads its static files from GitHub Pages; the records themselves are handled in your browser. No user account or database is needed.

## How to use

1. Open the [published workspace](https://fhamdimed.github.io/tathabbut-expert-review/) in Chrome, Edge or Firefox. For offline use, unzip the folder on a computer and open `index.html` instead.
2. Open **Rule Validation**. Add one record per rule, save its source details, conditions, exceptions, applicable cases, reviewer identifier and review decision.
3. Use **Download CSV** to save the records. Only records with `review_status=APPROVED` should be used as approved knowledge; the export also includes other statuses for documentation.
4. Open **Case Annotation**. Optionally click **Load approved rules from CSV**, selecting the CSV downloaded in step 3. This makes approved rule IDs available as suggestions and can fill linked source IDs.
5. Enter each Arabic question, answer and claim, record question facts and the expert's classification and rationale, and download the case CSV.
6. Send **both exported CSV files** to the research team. The names contain a date; they may be renamed to `expert_rule_records.csv` and `reviewed_cases.csv` for the handover.

## Saving, backups and privacy

- Text is saved automatically in the **local browser**, when the browser permits storage. This is a convenience, not a guaranteed backup. Browser settings, private mode and file-based storage rules may vary.
- **Online and offline copies do not share local storage.** Records saved at the GitHub Pages URL are specific to that browser and website origin; records saved from local HTML files may be stored separately. Export your data before switching devices, browsers, or between the hosted and offline versions.
- **Always download CSV after a review session** and keep a copy outside the browser. JSON backup and CSV/JSON re-import are available in each form.
- Importing a CSV or JSON **replaces** the existing local list in that form after a confirmation prompt. Export a backup first.
- Data stays on the device unless a person explicitly exports and shares the files. The files may contain reviewers' names and sensitive unpublished annotations, so share them through a secure institutional channel.
- The browser does **not authenticate the expert** or validate jurisprudential correctness. An `APPROVED` field records a manually entered decision, not a cryptographically signed approval.

## CSV compatibility and encoding

The forms export CSV in **UTF-8 with BOM**, supporting Arabic display in many versions of Excel, and correctly quote commas, double quotes and multiline fields. The exported column order matches the corresponding blank CSV template distributed with the app:

- Rule form: 20 columns, from `rule_id` through `comments`.
- Case form: 21 columns, from `instance_id` through `notes`.

Some extra user-friendly fields are packed into existing columns to **preserve template compatibility**:

- Rule reasoning features, examples inside coverage, and examples outside coverage are placed into labeled blocks inside `comments`.
- Missing or ambiguous case information is placed into a labeled block inside `notes`.

The pages decode these blocks when re-importing their own CSVs. Downstream scripts should retain these fields as text or parse the bracketed section names.

## Research safeguards

- Distinguish `NOT_REVIEWED`, `REVISE`, `UNRESOLVED`, `REJECTED` and `APPROVED` records.
- Never invent an exception, precedence relation, source reference or expert decision.
- Mark constructed diagnostic cases as `CONSTRUCTED`; distinguish them from real `LLM_GENERATED` answers.
- Gold labels (`Violation`, `NoViolationDetected`, `InsufficientInformation`, `UnableToVerify`) must be determined by an expert based on the approved source, without seeing system predictions.
- The tool is for research data capture, **not for issuing fatwas**.

## Browser compatibility

The pages use standard modern HTML/JavaScript. The recommended entry point is the [GitHub Pages website](https://fhamdimed.github.io/tathabbut-expert-review/). They can also be opened by double-clicking `index.html` in current desktop browsers. If local file restrictions prevent persistent storage, export still works, or the files can be served from a simple local static HTTP server.
