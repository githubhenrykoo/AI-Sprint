# PKC Environment Configuration Guide

## Table of Contents
1. [Introduction](#introduction)
2. [.env File Structure](#env-file-structure)
3. [Configuration Parameters](#configuration-parameters)
4. [Environment-Specific Settings](#environment-specific-settings)
5. [Security Best Practices](#security-best-practices)
6. [Troubleshooting](#troubleshooting)

## Introduction

The `.env` file is a crucial configuration file for your PKC (Private Knowledge Center) deployment. It contains environment-specific settings that control various aspects of your PKC instance, including authentication, API endpoints, and operational modes.

## .env File Structure

Create a new file named `.env` in your PKC project root directory with the following structure:

```env
# Application Environment
NODE_ENV=development

# Authentication
PUBLIC_AUTHENTIK_URL=https://auth.pkc.pub
PUBLIC_AUTHENTIK_CLIENT_ID=YQ6Us24EhfFoQjIabvpuTZM8CJjdG0t52TjHM3jz
PUBLIC_AUTHENTIK_CLIENT_SECRET=UTZsI3AyxUHKXyzXctgGzpJdDmjMnvbIdAKg25MC2T6PpMFkuOmwV618MPwD9tdxeuqO0msqVlKArdx5a11hF8AITtXeR72fm7lr4LFxc2frvISI8UYPQt0Scp4Kbva5
PUBLIC_AUTHENTIK_REDIRECT_URI=http://localhost:4321/auth/callback

# API Endpoints
PUBLIC_MCARD_API_URL=http://localhost:49384/v1
PUBLIC_RAG_API_URL=http://localhost:28302/api/v1
```

## Configuration Parameters

### Application Environment
- `NODE_ENV`
  - **Purpose**: Specifies the application's runtime environment
  - **Values**: `development`, `production`, `staging`
  - **Default**: `development`
  - **Note**: Affects logging, error handling, and some default behaviors

### Authentication
- `PUBLIC_AUTHENTIK_URL`
  - **Purpose**: Base URL for the Authentik Identity Provider
  - **Example**: `https://auth.pkc.pub`
  - **Required**: Yes
  - **Note**: Must be HTTPS in production

- `PUBLIC_AUTHENTIK_CLIENT_ID`
  - **Purpose**: Client ID for OAuth2 authentication
  - **Example**: `YQ6Us24EhfFoQjIabvpuTZM8CJjdG0t52TjHM3jz`
  - **Required**: Yes

- `PUBLIC_AUTHENTIK_CLIENT_SECRET`
  - **Purpose**: Secret key for OAuth2 authentication
  - **Example**: `UTZsI3AyxUHKXyzXctgGzpJdDmjMnvbIdAKg25MC2T6PpMFkuOmwV618MPwD9tdxeuqO0msqVlKArdx5a11hF8AITtXeR72fm7lr4LFxc2frvISI8UYPQt0Scp4Kbva5`
  - **Required**: Yes
  - **Security**: Keep this secret and never commit it to version control

- `PUBLIC_AUTHENTIK_REDIRECT_URI`
  - **Purpose**: Callback URL for OAuth2 authentication
  - **Example (Development)**: `http://localhost:4321/auth/callback`
  - **Example (Production)**: `https://your-domain.com/auth/callback`
  - **Required**: Yes

### API Endpoints
- `PUBLIC_MCARD_API_URL`
  - **Purpose**: Base URL for the MCard API service
  - **Example**: `http://localhost:49384/v1`
  - **Required**: Yes

- `PUBLIC_RAG_API_URL`
  - **Purpose**: Base URL for the RAG (Retrieval-Augmented Generation) API
  - **Example**: `http://localhost:28302/api/v1`
  - **Required**: Yes

## Environment-Specific Settings

### Development Environment
```env
NODE_ENV=development
PUBLIC_AUTHENTIK_REDIRECT_URI=http://localhost:4321/auth/callback
```

### Production Environment
```env
NODE_ENV=production
PUBLIC_AUTHENTIK_REDIRECT_URI=https://your-production-domain.com/auth/callback
# Additional production-specific settings would go here
```

## Security Best Practices

1. **Never commit sensitive data**
   - Add `.env` to your `.gitignore` file
   - Create a `.env.example` file with placeholder values for documentation

2. **Use environment-specific configurations**
   - Maintain separate `.env` files for different environments
   - Example: `.env.development`, `.env.production`

3. **Rotate secrets regularly**
   - Change client secrets periodically
   - Revoke and regenerate compromised credentials immediately

4. **Use secure protocols**
   - Always use HTTPS in production
   - Validate all URLs and redirect URIs

## Troubleshooting

### Common Issues

1. **Authentication Failures**
   - Verify `PUBLIC_AUTHENTIK_*` values match your Authentik configuration
   - Check that redirect URIs are correctly configured in Authentik

2. **API Connection Issues**
   - Verify all API endpoints are accessible from the PKC server
   - Check for CORS issues in the browser console

3. **Environment Variables Not Loading**
   - Ensure the `.env` file is in the project root
   - Restart your application after changing environment variables
   - Verify variable names match exactly (case-sensitive)

### Verifying Configuration

To verify your configuration is being loaded correctly, you can add a test route or log the environment variables (in development only):

```javascript
// Example for debugging (remove in production)
console.log('Environment:', {
  nodeEnv: process.env.NODE_ENV,
  authUrl: process.env.PUBLIC_AUTHENTIK_URL,
  // Add other variables as needed
});
```

## Next Steps

After configuring your `.env` file, you can proceed with:
1. Starting the PKC services
2. Verifying the configuration
3. Testing authentication flows
4. Connecting to the API endpoints

Remember to restart your application after making changes to the `.env` file for the changes to take effect.
