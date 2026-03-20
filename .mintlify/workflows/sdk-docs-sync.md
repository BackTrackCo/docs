---
name: Update SDK Documentation
on:
  push:
    - repo: BackTrackCo/x402r-sdk
      branch: main
---

Review the diff from the latest push to BackTrackCo/x402r-sdk.
Identify changed function signatures, new exports, or removed functions.
Update the relevant SDK documentation pages under sdk/.
Only modify SDK pages. Do not touch protocol or contract documentation.
Follow the writing style in CLAUDE.md.
