# Configuration reference

This is a map of configuration responsibilities, not a ready-to-run configuration file. Do not infer that every service listed here is part of one deployed system.

## Host roles

Use names such as **sensor node**, **collector**, **broker**, **API**, **dashboard**, and **model host** in public documentation. Store their actual connection details in a private local file or secret store.

## Historical service ports

| Component or experiment | Port recorded in notes | Scope |
| --- | --- | --- |
| RuView web interface | TCP 3000 | Earlier Wi-Fi lab |
| RuView WebSocket service | TCP 3001 | Earlier Wi-Fi lab |
| CSI intake | UDP 5005 | Referenced by RuView and sensor experiments |
| Mosquitto MQTT | TCP 1883 | Historical broker experiment; transport security must be configured separately |
| AHSIN FastAPI service | TCP 3010 | July recovery report |
| Alternate backend experiment | TCP 8080 | Separate dashboard launcher |
| Vite development server | TCP 5173 or 8081 | Revision-dependent development configuration |

Port numbers describe historical roles. They do not identify a current endpoint or authorize public exposure. A development server should remain restricted to the intended lab environment.

## Configuration groups

| Group | Values to resolve privately | Common failure |
| --- | --- | --- |
| Sensor firmware | Board target, firmware revision, Wi-Fi credentials, receiver destination | Correct boot but wrong destination or incompatible payload |
| Receiver | Transport, listener, payload format, freshness timeout | Packets arrive but cannot be decoded |
| MQTT | Broker, credentials, topic rules, transport security | Connection succeeds but subscriber watches a different topic |
| API and dashboard | Backend URL, allowed origin, source mode, stale threshold | UI loads while its feed is disconnected or simulated |
| Model adapter | Endpoint, model identifier, request timeout | Cold model startup exceeds a different timeout layer |
| Tool permissions | Department scope, risk level, approval policy, read-only mode | A planned action exceeds the caller's permissions |

## Timeout investigation notes

The published photograph shows several timeout values in configuration and adapter code. This matters because a longer setting in one layer will not help if another layer ends the request earlier.

Trace the request from caller to transport and model service. Identify which timeout fired, distinguish startup delay from a stuck request, and retest cancellation as well as successful completion. The historical values are diagnostic observations, not universal recommended settings.

## Local configuration policy

- Keep populated environment/configuration files outside the public repository.
- Publish only reviewed templates with obvious placeholders, if templates are later added.
- Never put credentials in commands that will appear in screenshots or shell history.
- Use logical node identifiers in public records rather than network addresses or device identifiers.
- Do not copy old host-specific paths or addresses into a new installation.
