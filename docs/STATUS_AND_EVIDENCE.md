# Status and evidence register

**Documentation review: October 10, 2026.** This page consolidates records from different development stages. It is not a live status page.

## Evidence labels

| Label | Meaning |
| --- | --- |
| Captured | A supplied image visibly shows the stated result |
| Reported | A project note or manual records the result; the run was not independently reproduced during this documentation update |
| Inspected | A supplied file was examined without running it |
| Planned | A goal or unverified integration, not a completed capability |

## Development record

| Period or source | Observation | Label and limit |
| --- | --- | --- |
| May 2026 Wi-Fi lab | Docker deployment and RuView interface experiments | Captured; this stage includes simulation |
| May 2026 AHSIN documentation | Sensor hardware, broker, and integration planning | Reported; procurement and configuration are not end-to-end validation |
| June 19 manual | Sensor/collector progress and remaining ingestion/registry work | Reported; stages differ across the manual |
| July status reconciliation | Historical packet intake from at least one node and partially integrated services | Reported; broader sensing and agent goals remain experimental |
| July 12 recovery report | 52 of 52 files, 397 of 397 tests, and Milestone 3A recorded as complete | Reported snapshot; no corresponding source checkout was tested here |
| Undated command manual | Later baseline described as 66 files and 455 tests | Reported; date and revision not established by this public record |
| Published test photograph | `Ran 365 tests` and `OK`; tool access and timeout cases visible | Captured historical run; revision and capture date not established |
| Supplied dashboard installer | Randomized metrics/events and fixed status values in frontend code | Inspected; a simulated UI prototype, not live sensor proof |

The counts above are not a single chronological test-growth chart. The records have different dates, revisions, and evidence quality. No current passing-test badge is used because this public repository does not contain or execute the application test suite.

## Published photographs

| File | What is visible | What is not established |
| --- | --- | --- |
| [Timeout investigation](../assets/evidence/timeout-investigation.jpg) | Configuration and adapter inspection with multiple timeout values | A final fix, measured improvement, or current runtime health |
| [Historical 365-test run](../assets/evidence/historical-tests-365.jpg) | Test output ending in `OK`, including tool-control cases | Current branch status, complete test source, hardware validation, or coverage percentage |

Photographs were selected to avoid visible network addresses, credentials, and private contact details. Image pixels are unchanged. Original metadata and embedded thumbnails were removed; the test photograph has minimal orientation metadata for readability. [Image checksums](../assets/evidence/manifest.json) identify the published copies.

Raw manuals, full terminal dumps, private configuration, and unreviewed original screenshots are intentionally excluded from this publication.

## Claims this repository supports

- A documented, iterative lab project spanning Linux, containers, sensor experiments, dashboards, and agent-tool controls.
- Historical testing and troubleshooting work, with the evidence limits stated above.
- A concrete plan for improving repeatability, source labeling, and multi-node validation.

## Claims that need additional evidence

- A current end-to-end installation with a verified count of simultaneously active hardware nodes.
- Reliable through-wall localization or pose estimation under measured conditions.
- Validated breathing, heart-rate, stress, or other health measurements.
- An operational production deployment or autonomous external actions.

For the next evidence capture, follow [Validation](VALIDATION.md) and attach the application revision, test conditions, and observed result.
