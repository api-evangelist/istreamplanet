---
name: istreamplanet-ad-signaling
description: Insert SCTE-35 or ID3 signals into a live Aventus channel and review the signaling history.
api: WBD Aventus Channels API
generated: 2026-10-09
method: generated
source: openapi/istreamplanet-aventus-channels-openapi.yml
operations:
  - insert-org-scte35
  - insert-org-id3
  - post-org-signals
  - get-org-signals
  - list-raw-scte-history-by-channel
  - get-org-signal-logs
---
# Live ad and metadata signaling

1. `insert-org-scte35` (POST /v2/{org}/channels/{channel-id}/scte35) inserts a SCTE-35 formatted binary payload into the running channel.
2. `insert-org-id3` (POST .../id3) inserts timed ID3 metadata.
3. `post-org-signals` and `get-org-signals` (.../signals) write and read the channel's signals.
4. `list-raw-scte-history-by-channel` (GET .../scte-history) and `get-org-signal-logs` (GET .../beta/logs/signaling, a beta endpoint) let you audit what was sent.

Each insert fires into a live stream and none is idempotent, so never retry one automatically.
