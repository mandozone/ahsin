# Operator manual

This is a runbook for an authorized AHSIN lab installation. **Cloning this documentation repository does not install AHSIN.** Application entry points and configuration must come from the actual, trusted application checkout.

## 1. Establish the baseline

Before starting services, record privately:

- Application revision and working-tree changes.
- Operating system, Python environment, container image digest, and firmware revision where applicable.
- Which nodes are expected, which are connected, and which are still planned.
- The selected data source: simulation, recorded input, or hardware.
- Service roles and local configuration location.

From the application checkout, these read-only commands help establish context:

```bash
git status --short
git log -1 --oneline
python3 --version
docker --version
docker ps --format 'table {{.Names}}\t{{.Status}}\t{{.Image}}'
```

Run only commands relevant to the installed components. Keep unredacted output private. Stop if the source checkout, configuration, or firmware does not match the intended baseline.

## 2. Start one layer at a time

1. Start the required receiver, broker, or backend using that checkout's documented command.
2. Confirm that the intended process is running and listening on the expected transport and port.
3. Start one sensor node. Observe boot and connection output before adding additional nodes.
4. Verify packet arrival, decoding, logical node identity, and recent timestamps.
5. Start the API and dashboard. Confirm that the interface reflects the receiver's data source.
6. Start model services and agent components only after their configuration and permission rules are checked.

The exact commands depend on the application revision. Old manual snippets are not a substitute for checking the current entry point. Do not start every historical service simultaneously: some experiments reused ports and alternative backends.

## 3. Check the data path

| Check | Evidence to collect privately | What it establishes |
| --- | --- | --- |
| Firmware boot | Node label and firmware revision | The intended image started |
| Transport | Receiver-side packet count or broker session | Traffic arrived at one layer |
| Decode | Valid payload count and rejected-message count | The consumer understands the data |
| Identity | Logical node label and sequence/timestamp correlation | The expected node supplied the record |
| Freshness | Last-received time and changing sequence | Data is current |
| Dashboard | Matching backend values and declared data source | The UI is presenting the expected feed |
| Disconnect | A node becomes stale after removal | Activity is not just an independent animation |

Do not substitute a dashboard's confidence percentage for these checks. A listening socket or successful HTTP response is necessary for some paths but does not prove sensor integration.

## 4. Validate the software revision

Historical application notes use the following test command:

```bash
python3 -m unittest discover -s tests -v
```

Run it only in an application revision that actually contains the appropriate `tests` directory and dependencies. Record the revision, test count, failures, and exit status. An old screenshot is not the result of a new run.

Some historical revisions also have a file-verification script. Use the script shipped with that same revision. A missing or stale file must be reconciled with version control; do not replace it merely to make a count match an older note.

## 5. Operate and stop cleanly

- Start with one node and expand only after its path is understood.
- Change one variable at a time and keep the prior configuration available privately.
- Observe CPU/memory use, request latency, queue growth, and stale data during longer runs.
- Stop the named service or process you started. Avoid broad process-killing commands.
- Record the last known-good revision and the next unresolved issue before ending a session.

## Daily note template

```text
Date and application revision:
Goal for this session:
Data source: simulation / recorded / hardware
Expected logical nodes:
Observed logical nodes:
Checks performed and results:
Change made:
Regression check:
Known limitation:
Next action:
```

Keep private connection details and raw logs in the private lab record. Public notes should use logical names and concise, reviewed results.
