---
name: istreamplanet-live-to-vod-clip
description: Cut a clip from a channel's Live2VOD recording, render it to MP4, and get the download URL.
api: WBD Aventus Channels API
generated: 2026-10-09
method: generated
source: openapi/istreamplanet-aventus-channels-openapi.yml
operations:
  - list-org-vods
  - post-org-vod-clip
  - get-org-task
  - post-org-task-retry
  - post-org-make-mp4
  - get-org-mp4-url
  - get-org-clip-manifests
---
# Live2VOD clip to MP4

1. `list-org-vods` (GET /v2/{org}/channels/{channel-id}/vods) finds the VOD to clip.
2. `post-org-vod-clip` (POST .../vods/{vod_id}/clips) starts a clip job. The job runs asynchronously as a L2V task.
3. Poll `get-org-task` (GET .../tasks/{task-id}) until the task is finished. If it failed, `post-org-task-retry` retries it.
4. `post-org-make-mp4` (POST .../clips/{clip-id}/makemp4) creates the MP4 entity for the clip.
5. `get-org-mp4-url` (GET .../clips/{clip-id}/mp4url) returns the URL to download the MP4. `get-org-clip-manifests` returns the streaming manifests.

The POST calls are not documented as idempotent, so do not resend them blindly. Check the task first.
