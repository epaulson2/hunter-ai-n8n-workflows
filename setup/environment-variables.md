# Environment Variables for N8N Cloud

Add these environment variables in your N8N Cloud workspace:

## Required Supabase Configuration

```bash
# Supabase Database Connection
SUPABASE_URL=https://yknfbokdogitccextpuh.supabase.co
SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InlrbmZib2tkb2dpdGNjZXh0cHVoIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MjU3ODEyMDEsImV4cCI6MjA0MTM1NzIwMX0.gOCnhN0xCVcWQe3j_hZGYY5dQBBQU1Y3g1Y8h9B2Y2o
```

## How to Add in N8N Cloud

1. **Login to N8N Cloud**: Go to your workspace URL
2. **Navigate to Settings**: Click the settings/gear icon
3. **Environment Variables**: Find the "Environment Variables" section
4. **Add Variables**: Click "Add Variable" for each:
   - **Name**: `SUPABASE_URL`
   - **Value**: `https://yknfbokdogitccextpuh.supabase.co`
   - **Name**: `SUPABASE_ANON_KEY` 
   - **Value**: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InlrbmZib2tkb2dpdGNjZXh0cHVoIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MjU3ODEyMDEsImV4cCI6MjA0MTM1NzIwMX0.gOCnhN0xCVcWQe3j_hZGYY5dQBBQU1Y3g1Y8h9B2Y2o`

## Package System Database Functions

These functions are already deployed in your Supabase database:

- `get_business_mentions_for_categories()` - Smart business selection
- `consume_business_mention_credit()` - Credit consumption tracking
- `check_package_alerts()` - Package expiration monitoring

## Testing the Connection

Once variables are added, test with the simple test workflow:
```
https://your-workspace.app.n8n.cloud/webhook/simple-test
```

Should return:
```json
{
  "success": true,
  "message": "N8N Cloud webhook working!",
  "package_system_ready": true
}
```
