# Validation checklist

Use this checklist to turn a working experiment into a repeatable record. Store raw logs privately and publish only reviewed summaries or selected screenshots.

## Software baseline

- [ ] Record the application revision and whether the working tree is modified.
- [ ] Record dependencies, container digest, and relevant firmware revision.
- [ ] Run the actual revision's tests; save exit status, count, and failures.
- [ ] Verify permission-denied, approval-required, read-only, timeout, and cancellation behavior where implemented.
- [ ] Confirm that documentation identifies features that are not yet integrated.

## One-node telemetry

- [ ] Declare the mode: simulated, recorded, or live hardware.
- [ ] Observe the intended firmware boot and logical node label.
- [ ] Confirm receiver-side traffic and successful payload decoding.
- [ ] Correlate timestamps or sequence values through the intended pipeline.
- [ ] Verify that the dashboard uses backend values rather than independent generated values.
- [ ] Disconnect the node and confirm stale/offline behavior.
- [ ] Reconnect and record recovery behavior.

## Multiple nodes

- [ ] Complete the one-node checks for each logical node separately.
- [ ] Run nodes together and verify distinct identities and recent records.
- [ ] Check for duplicate identifiers, mixed streams, dropped messages, and reordered samples.
- [ ] Document duration, load, and limitations of the run.
- [ ] Publish a verified active-node count only for that recorded run.

## Sensing experiment

- [ ] Obtain consent from everyone in the test area.
- [ ] Define a testable question and a known ground-truth condition.
- [ ] Record empty-room and controlled-motion baselines.
- [ ] Keep placement and environmental variables consistent between comparisons.
- [ ] Report false positives, missed events, and uncertainty alongside successful examples.
- [ ] Treat through-wall and physiological measurements as separate experiments requiring separate validation.

## Public evidence review

- [ ] Exclude credentials, account details, IP/MAC addresses, SSIDs, and private hostnames.
- [ ] Check browser tabs, terminal scrollback, window titles, and background applications.
- [ ] Remove image metadata and embedded thumbnails.
- [ ] Add a caption explaining exactly what the evidence proves and its date/revision if known.
- [ ] Inspect staged files and links before committing.

## Result template

```text
Experiment:
Revision and firmware:
Mode and logical node count:
Test duration and conditions:
Expected result:
Observed result:
Failure/stale/recovery behavior:
Known limits:
Next experiment:
```
