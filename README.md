# mothership-pulse

Övervaknings- och mätmotor för **Mothership Dashboard**-plattformen.

## Översikt
`mothership-pulse` är skrivet i **Go** och använder **MySQL** för tidsserielagring av mätningar. Den ansvarar för:
- Periodisk hälsokontroll (HTTP/TCP ping) av registrerade tjänster.
- Insamling av host-telemetri (CPU, minne, disk, nätverk) via läsning från monterade `/proc` och `/sys`.
- Docker-inventering via Docker-socket (read-only).
- Säkerhetsövervakning (UFW-status, Fail2ban, uppdateringar).
- Statistik-API med aggregerad uptime och svarstider.

## Hälso-endpoints
- `GET /healthz` – Liveness probe
- `GET /readyz` – Readiness probe (kontrollerar MySQL)
- `GET /metrics` – Prometheus-metrik
