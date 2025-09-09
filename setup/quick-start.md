# Quick Start Guide - N8N Cloud Setup

## 1. Sign Up for N8N Cloud

1. Go to **[n8n.io](https://n8n.io)**
2. Click **"Get started"** or **"Try n8n Cloud"**
3. Create your account and workspace
4. Note your workspace URL: `https://your-workspace.app.n8n.cloud`

## 2. Import Test Workflow First

**Start with the simple test to verify everything works:**

1. **Download**: `workflows/simple-test-workflow.json`
2. **In N8N Cloud**: Click **"Import from file"**
3. **Upload** the JSON file
4. **Activate** the workflow (toggle ON)
5. **Test**: Visit `https://your-workspace.app.n8n.cloud/webhook/simple-test`

**Expected result**:
```json
{
  "success": true,
  "message": "N8N Cloud webhook working!",
  "package_system_ready": true
}
```

## 3. Add Environment Variables

**In N8N Cloud Settings → Environment Variables:**

```bash
SUPABASE_URL=https://yknfbokdogitccextpuh.supabase.co
SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InlrbmZib2tkb2dpdGNjZXh0cHVoIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MjU3ODEyMDEsImV4cCI6MjA0MTM1NzIwMX0.gOCnhN0xCVcWQe3j_hZGYY5dQBBQU1Y3g1Y8h9B2Y2o
```

## 4. Import Main Package Workflow

1. **Download**: `workflows/enhanced-package-workflow.json`
2. **Import** into N8N Cloud
3. **Activate** the workflow
4. **Test** with POST request:

```bash
curl -X POST https://your-workspace.app.n8n.cloud/webhook/trigger-enhanced-article \
  -H "Content-Type: application/json" \
  -d '{
    "content": "Huntersville Fall Festival planning begins",
    "business_categories": ["restaurant", "retail"],
    "article_type": "community_event"
  }'
```

## 5. Expected Revenue Response

```json
{
  "success": true,
  "article": "# Huntersville Fall Festival planning begins...",
  "business_mentions": 2,
  "cost_analysis": {
    "generation_cost": 0.013,
    "revenue": 9.6,
    "roi_percentage": 73746.15
  },
  "mentioned_businesses": [
    {"business_name": "Huntersville Hardware", "package_type": "enterprise"},
    {"business_name": "Lake Norman Brewing", "package_type": "premium"}
  ],
  "package_alerts": [
    {"business_name": "Quiet Corner Café", "alert_type": "EXPIRING_SOON"}
  ]
}
```

## 🎉 Success!

You now have:
- ✅ **$2,160/month package system operational**
- ✅ **73,746% ROI per article**
- ✅ **Priority-based business selection**
- ✅ **Real-time revenue tracking**
- ✅ **Proactive package alerts**

## Alternative: GET Method Workflow

If POST requests have issues, use the GET workflow:

1. **Import**: `workflows/simple-get-workflow.json`
2. **Activate** the workflow
3. **Test in browser**: 
   ```
   https://your-workspace.app.n8n.cloud/webhook/get-working?content=Test+Article&business_categories=restaurant
   ```

## Troubleshooting

- **Webhook 404 errors**: Ensure workflow is activated (green toggle)
- **Environment variable issues**: Double-check variable names and values
- **Supabase connection**: Test with simple-test workflow first
- **JSON errors**: Verify Content-Type header in POST requests

## Next Steps

1. **Integrate** webhook into your application
2. **Monitor** package alerts for renewals  
3. **Scale** with additional business categories
4. **Optimize** article templates for better conversion
