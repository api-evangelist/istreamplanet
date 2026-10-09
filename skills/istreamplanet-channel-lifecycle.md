---
name: istreamplanet-channel-lifecycle
description: Create or update an Aventus live channel for an organization, turn it on or off, and check transcoder status.
api: WBD Aventus Channels API
generated: 2026-10-09
method: generated
source: openapi/istreamplanet-aventus-channels-openapi.yml
operations:
  - list-orgs
  - list-org-sources
  - put-org-channel
  - get-org-channel
  - put-org-channel-desired-state
  - org-get-transcoder-status
  - delete-org-channel
---
# Aventus channel lifecycle

1. `list-orgs` (GET /v2/orgs) lists the organizations you can act on, and `list-org-sources` (GET /v2/{org}/sources) lists the ingest sources available to them.
2. `put-org-channel` (PUT /v2/{org}/channels/{channel-id}) creates or updates the channel configuration: inputs, transcoding, and outputs. Because it is a PUT to a caller-chosen id, sending it again with the same body is safe.
3. `get-org-channel` reads the stored configuration back.
4. `put-org-channel-desired-state` (PUT .../desired-state) sets DesiredState to ON or OFF.
5. `org-get-transcoder-status` (GET .../transcoder-status) shows whether the channel is running.
6. `delete-org-channel` deletes the channel. This is destructive, so confirm with the user before calling it.

Auth: an OAuth 2.0 bearer token from WBD SSO. Use the client-credentials (`m2m`) flow for automation and authorization code (`authcode`) for a user. The spec declares no scopes. Note that iStreamPlanet was shut down in August 2023.
