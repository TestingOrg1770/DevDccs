---
title: "Sync Engine"
---

# Sync Engine Mechanics

## Architecture Overview

,The Sync Engine handles high-performance file ingestion, chunk splitting, and differential sync to minimize network bandwidth usage.

## Ingestion Pipeline Workflow

1. **File Hashing**: Generates an SHA-256 hash to check if the file already exists on the server.
2. **Chunking Process**: Files larger than 5MB are split into 1MB chunks.
3. **Queue Assignment**: Upload jobs are pushed to a Redis queue with a maximum concurrency limit of 5 jobs per user.
4. **Storage Adapter Routing**: Chunks are streamed directly to the configured storage backend.

## Error Handling Limits

- **Retry Logic**: Failed chunk uploads are retried up to **3 times** before the job status changes to `FAILED`.
- **Timeout Limit**: Individual chunk transfers time out after **30 seconds**.
