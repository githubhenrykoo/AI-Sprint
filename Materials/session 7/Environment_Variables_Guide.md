# PKC Environment Variables Guide

## What is PKC?
PKC (Private Knowledge Center) is a secure, self-hosted knowledge management system that allows you to organize, store, and retrieve information in a private and controlled environment. It provides features like document management, search, and integration with AI-powered tools while keeping your data on your infrastructure.

## Understanding .env Files

A `.env` (dot-env) file is a simple configuration file used to store environment variables for your application. These variables are key-value pairs that configure various aspects of your application's behavior. Here's why they're important:

- **Security**: Keeps sensitive information (like API keys) out of your codebase
- **Configuration**: Allows different settings for development, testing, and production
- **Portability**: Makes it easy to move your application between different environments
- **Collaboration**: Team members can have their own local configurations without affecting others

## Task: Create .env File

### Option 1: Using a Code Editor (Recommended)
1. Open your PKC project in your preferred code editor (e.g., VS Code, Sublime Text, Atom)
2. Right-click in the file explorer panel and select "New File"
3. Name the file `.env` (make sure to include the dot at the beginning)
4. Copy and paste the following configuration into the file:

```env
NODE_ENV=development
PUBLIC_AUTHENTIK_URL=https://auth.pkc.pub
PUBLIC_AUTHENTIK_CLIENT_ID=YQ6Us24EhfFoQjIabvpuTZM8CJjdG0t52TjHM3jz
PUBLIC_AUTHENTIK_CLIENT_SECRET=UTZsI3AyxUHKXyzXctgGzpJdDmjMnvbIdAKg25MC2T6PpMFkuOmwV618MPwD9tdxeuqO0msqVlKArdx5a11hF8AITtXeR72fm7lr4LFxc2frvISI8UYPQt0Scp4Kbva5
PUBLIC_MCARD_API_URL=http://localhost:49384/v1
# For local development, you need to add this new environment variable:
PUBLIC_AUTHENTIK_REDIRECT_URI=http://localhost:4321/auth/callback
PUBLIC_RAG_API_URL=http://localhost:28302/api/v1
```

### Option 2: Using Command Line
1. Navigate to your PKC project root directory:
   ```bash
   cd /path/to/pkc
   ```
2. Create and edit the `.env` file:
   ```bash
   # For Linux/macOS
   nano .env
   
   # Or for Windows (using Notepad)
   notepad .env
   ```
3. Paste the configuration above and save the file

## Verification

1. Verify the file was created and contains the correct content:
   ```bash
   # List the file with details
   ls -la .env
   
   # View the file contents
   cat .env
   ```

## Important Notes

- 🔒 **Security Warning**: The `.env` file contains sensitive information. Never commit it to version control.
- ➕ Add `.env` to your `.gitignore` file to prevent accidental commits.
- 🔄 If you're working in a team, share the `.env.example` file with placeholder values instead of the actual `.env` file.
- ⚠️ Keep your environment variables secure and never share them publicly.
- 🔄 Restart your development server after making changes to the `.env` file for the changes to take effect.
