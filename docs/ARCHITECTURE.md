# Architecture notes

AHSIN has evolved through separate sensor, dashboard, and agent experiments. These notes describe their intended relationship and the components recorded in the development material. They are not a deployment inventory.

## Sense: device and telemetry layer

ESP32 experiments provide the hardware side of the project. Historical records discuss firmware boot, CSI callbacks, UDP transmission, and MQTT messages. A node needs a stable logical identifier, a known firmware revision, a declared payload format, and a receiver configured for that format.

The July recovery report describes earlier packet intake from at least one node. A board being powered on, a boot banner, or a connected MQTT client does not establish that valid CSI samples reached the intended consumer. End-to-end validation must correlate a particular node's messages with receiver records.

Do not assume every ESP32 model, firmware image, Wi-Fi adapter, or upstream sensing stack is interchangeable. Record the exact hardware and firmware used for each run privately; publish only the non-identifying details needed to understand the experiment.

## Core: processing and agent framework

Development records describe these responsibilities:

| Component | Responsibility |
| --- | --- |
| Event bus | Distribute events between components |
| State engine | Maintain current system state and transitions |
| Memory | Store and retrieve permitted context |
| Node registry | Track logical devices and their reported state |
| Task queue and agent manager | Coordinate work and agent lifecycle |
| Planner | Propose and sequence work |
| Tool registry | Declare capabilities and enforce access restrictions |
| Model router and adapters | Select a model endpoint and handle requests |
| Knowledge graph | Experimental relationships and extraction work |

The planner should request capabilities through the tool registry. Planning is not permission to execute. Historical test names include read-only behavior, department restrictions, approval requirements, timeouts, and kill-switch handling.

The recorded department experiments include planning, business development, lead generation, real estate, and finance-related analysis. Autonomous financial transactions or external outreach are not established capabilities of this public release.

## Vision: operator interface

Two interfaces appear in the project history:

1. The upstream RuView dashboard used in the earlier Wi-Fi lab.
2. An AHSIN React/Vite dashboard prototype, with separate backend integration work described in later notes.

Static inspection of the supplied AHSIN installer prototype found generated waveform samples, generated counters and events, and fixed connection/presence state. That prototype is a user-interface demonstration. Its apparent activity is not evidence of an active hardware feed.

A trustworthy integrated view needs an explicit data-source label, a last-received timestamp, a stale state, and node-specific counters derived from the backend. See [Validation](VALIDATION.md).

## Deployment boundaries

| Boundary | Required distinction |
| --- | --- |
| Device to receiver | Association, packet arrival, and successful payload decoding |
| Receiver to broker or API | Transport availability versus application-level acceptance |
| API to browser | A page loading versus receiving fresh data |
| Planner to tool | A proposed action versus an authorized execution |
| Local model to caller | Model warm-up, request timeout, and cancellation |
| Private lab to public repository | Reproducible notes versus identifying deployment data |

The public materials intentionally omit real hostnames, network addresses, credentials, SSIDs, device MAC addresses, and deployment topology identifiers. Use role names in diagrams and keep the host map outside Git.
