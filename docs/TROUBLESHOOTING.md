# Troubleshooting notes

These cases combine historical observations with a method for narrowing the next failure. They should be checked against the actual application revision before making changes.

| Symptom | Inspect first | Next controlled action |
| --- | --- | --- |
| ESP32 boots, no receiver data | Firmware target, configured destination, UDP listener, route, and firewall | Confirm one node's packets reach the receiver before changing dashboard code |
| MQTT client connects, no expected readings | Exact publisher/subscriber topics and payload schema | Correlate a node message with a subscriber record; connection status alone is insufficient |
| Dashboard animates with devices offline | Source selector and frontend data-generation code | Label simulation explicitly and test whether backend timestamps become stale |
| Backend responds, UI is empty | API path, browser console, origin policy, and WebSocket URL | Check the actual failing browser request and match it to backend logs |
| Requests time out | Caller, adapter, transport, and model-server limits | Trace the first timeout and test model warm-up separately |
| Verifier says files are missing or stale | Branch, revision, working-tree changes, and verifier version | Compare against the intended revision before restoring specific files |
| Test counts differ from a manual | Test discovery scope and revision | Report the new run with its revision; do not assume a larger historical number applies |
| Docker reports a missing argument | Full command and continuation characters | Ensure the image name belongs to the same command; review before executing |
| Docker service runs but the dashboard is unavailable | Image digest, published port, service logs, and UI route | Verify the image contains the expected UI and the browser uses the correct route |

## A documented wireless troubleshooting lesson

Historical AHSIN notes describe an experiment in which removing an Alfa adapter from the setup was associated with resolving an allocation/UDP problem. This is a result from that particular configuration. It is not evidence that the adapter is universally incompatible, or that an external adapter is mandatory for all CSI workflows.

Repeat the comparison under controlled conditions before generalizing: same firmware, same node, same receiver, one changed variable, and recorded packet/decoder results.

## A documented UI lesson

The supplied React dashboard installer contains generated values and fixed connection state. It is useful as a prototype of the interface. It should not be used as evidence of live packet flow or detection accuracy.

The integration acceptance test is straightforward: correlate a real node record with the backend and UI, disconnect that node, observe a stale state, and reconnect it. Keep simulation available as a separate, visibly labeled mode.

## Recovery discipline

Use the last known-good application revision and a private backup of its configuration. Inspect the working tree before reverting anything. Restore only understood files, then repeat the check that originally failed and the relevant regression tests.

Do not execute copied terminal text containing deletion commands, global process termination, or unrelated account actions as part of routine recovery.
