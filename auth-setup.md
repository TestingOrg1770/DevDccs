# Authentication Setup

## Overview
CloudSync uses JWT (JSON Web Tokens) for API session management and OAuth2 for authenticating third-party storage providers (e.g., Google Drive, AWS S3).

## Environment Variables Configuration
Set the following variables in your `.env` file:

```env
JWT_SECRET=your_super_secret_jwt_key
JWT_EXPIRATION=3600s
OAUTH_CLIENT_ID=your_oauth_client_id
OAUTH_CLIENT_SECRET=your_oauth_client_secret
