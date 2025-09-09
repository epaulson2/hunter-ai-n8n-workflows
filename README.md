# Hunter AI N8N Workflows

Package-aware article generation workflows for N8N Cloud deployment.

## 🎯 **Business Value**

- **$2,160/month** recurring revenue from package portfolio
- **73,746% ROI** per article generation
- **$4.80 revenue** per business mention
- **Priority-based** business selection (Enterprise → Premium → Basic)

## 📋 **Workflows Included**

1. **[Enhanced Package-Aware Workflow](./workflows/enhanced-package-workflow.json)** - Complete 7-node production workflow
2. **[Simple GET Working Solution](./workflows/simple-get-workflow.json)** - GET-method compatible workflow
3. **[Dual Webhook Solution](./workflows/dual-webhook-workflow.json)** - GET + POST method support
4. **[Multi-Method Test](./workflows/multi-method-test.json)** - Basic testing workflow

## 🚀 **Quick Start for N8N Cloud**

### **1. Import Main Workflow**
- Download: `workflows/enhanced-package-workflow.json`
- In N8N Cloud: **Settings** → **Import from file**
- Upload the JSON file

### **2. Add Environment Variables**
In N8N Cloud Settings → Environment Variables:
```bash
SUPABASE_URL=https://yknfbokdogitccextpuh.supabase.co
SUPABASE_ANON_KEY=your-supabase-anon-key-here
```

### **3. Activate & Test**
- Activate the imported workflow
- Test webhook: `https://your-workspace.app.n8n.cloud/webhook/trigger-enhanced-article`

## 📊 **Package System Overview**

### **Current Portfolio**
- **Huntersville Hardware** (Enterprise): 220 credits, $1,200/month
- **Lake Norman Brewing** (Premium): 82 credits, $480/month  
- **Main Street Diner** (Basic): 41 credits, $240/month
- **Quiet Corner Café** (Basic): 7 credits, $240/month

### **Business Logic**
- **Priority Selection**: Enterprise (9) → Premium (7) → Basic (5/4)
- **Credit Protection**: Cannot exceed package limits
- **Revenue Tracking**: $4.80 per mention automatically calculated
- **Proactive Alerts**: Expiring package notifications

## 🔧 **Workflow Details**

### **Enhanced Package-Aware Workflow**
**Webhook Path**: `/webhook/trigger-enhanced-article`
**Method**: POST
**Nodes**: 7 (optimized pipeline)

**Input Format**:
```json
{
  "content": "Article title or topic",
  "business_categories": ["restaurant", "retail"],
  "article_type": "community_event"
}
```

**Expected Output**:
```json
{
  "success": true,
  "article": "Generated article with business mentions...",
  "business_mentions": 2,
  "package_insights": {
    "package_types_used": ["enterprise", "premium"],
    "avg_priority_level": 8
  },
  "cost_analysis": {
    "generation_cost": 0.013,
    "revenue": 9.6,
    "roi_percentage": 73746.15
  },
  "mentioned_businesses": [
    {"business_name": "Huntersville Hardware", "package_type": "enterprise"},
    {"business_name": "Lake Norman Brewing", "package_type": "premium"}
  ],
  "package_alerts": [...]
}
```

## 🧪 **Testing Commands**

### **POST Request (Main Workflow)**
```bash
curl -X POST https://your-workspace.app.n8n.cloud/webhook/trigger-enhanced-article \
  -H "Content-Type: application/json" \
  -d '{
    "content": "Huntersville Fall Festival planning begins",
    "business_categories": ["restaurant", "retail"],
    "article_type": "community_event"
  }'
```

### **GET Request (Alternative Workflow)**
```
https://your-workspace.app.n8n.cloud/webhook/get-working?content=Huntersville+Fall+Festival&business_categories=restaurant
```

## 📚 **Database Functions Used**

The workflows use these Supabase database functions (already deployed):

1. **`get_business_mentions_for_categories()`** - Package-aware business selection
2. **`consume_business_mention_credit()`** - Credit consumption tracking  
3. **`check_package_alerts()`** - Proactive package monitoring

## 🔄 **Migration from Self-Hosted**

If migrating from Railway/self-hosted N8N:
1. **Export existing workflows** from your current N8N
2. **Import into N8N Cloud** using the JSON files
3. **Update webhook URLs** in your applications
4. **Test functionality** immediately

## 💰 **Revenue Calculation**

- **Generation Cost**: ~$0.013 per article
- **Mention Revenue**: $4.80 per business mentioned
- **Typical Article**: 2 mentions = $9.60 revenue
- **Net Profit**: $9.587 per article
- **ROI**: 73,746% return on investment

## 🚨 **Important Notes**

1. **Package Credits**: System automatically prevents over-consumption
2. **Priority Algorithm**: Higher-tier packages get preference in selection
3. **Alert System**: Monitors expiring packages (like Quiet Corner Café - expires in 4 days)
4. **Revenue Tracking**: All financial metrics calculated in real-time

## 📞 **Support**

For issues with the package system or workflow configuration, the workflows include comprehensive error handling and logging.

---

**Ready to generate revenue with package-aware article generation!** 🚀