---
title: "Overview"
---

# Project Overview: CloudSync API

## Introduction

CloudSync is a lightweight REST API designed for real-time file synchronization across multi-cloud environments. It acts as a single gateway between local client storage and cloud storage providers.

## Key Architecture Components

1. **Authentication Gateway**: Managed via JWT and OAuth2 tokens (see `auth-setup.md`).
2. **Sync Engine**: Core pipeline handling file hashing, chunking, and upload queues (see `sync-engine.md`).
3. **Database Layer**: PostgreSQL database for metadata storage and user mapping (see `database-schema.md`).
4. **Troubleshooting & Support**: Common errors, logs, and diagnostic steps (see `troubleshooting.md`).

## System Requirements

- Node.js v18.0 or higher
- PostgreSQL v14+
- Redis v6.2+ (for queue processing)
