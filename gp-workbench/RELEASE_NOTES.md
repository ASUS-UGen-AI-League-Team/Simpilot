# Release-only changes

Base: latest local source after the target-navigation and interface simplification updates. All three engine packages, static files and 13 existing CLI entry points are retained.

Added: five sanitized CSV/manifest pairs; relative example projects; example loader/API/button; no-browser runner; portable launchers and separate default runtime workspace; pinned runtime environment; minimal public tests and upload scan; English and Traditional Chinese documentation; explicit data/licensing status.

Security changes: cross-site GET checks, session-guarded report reads/downloads, port-scoped HttpOnly/SameSite cookie, direct-child report-root containment, and updated HTTP/IDNA dependencies. These affect the release copy; the research working copy and its environment were not modified.

No original trajectories, private source records, cached frame arrays, existing models/reports, credentials, personal project exports or Git history are included. Published SHA256 fingerprints support integrity, not proof of ownership or a data license. RELEASE_FILES.json lists all shipped files except itself; its own hash is intentionally not recursive. The ZIP has a separate SHA256 checksum file.
