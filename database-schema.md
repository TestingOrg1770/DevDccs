# Database Schema Reference

## Overview
CloudSync utilizes a PostgreSQL relational database to store file metadata, user records, and access logs.

## Core Tables

### `users`
- `id` (UUID, Primary Key)
- `email` (String, Unique)
- `created_at` (Timestamp)

### `files`
- `id` (UUID, Primary Key)
- `user_id` (UUID, Foreign Key -> `users.id`)
- `file_name` (String)
- `file_hash` (String, SHA-256)
- `size_bytes` (BigInt)
- `status` (Enum: `PENDING`, `SYNCED`, `FAILED`)

### `sync_logs`
- `log_id` (UUID, Primary Key)
- `file_id` (UUID, Foreign Key -> `files.id`)
- `event` (String: `UPLOAD_START`, `UPLOAD_COMPLETE`, `ERROR`)
- `created_at` (Timestamp)
