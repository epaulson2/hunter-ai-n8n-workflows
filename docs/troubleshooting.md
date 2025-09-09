# Troubleshooting Guide

## Common Issues and Solutions

### Webhook 404 Errors

**Symptoms**: `"The requested webhook is not registered"`

**Solutions**:
1. **Check Workflow Status**: Ensure workflow is activated (green toggle)
2. **Verify Path**: Confirm webhook path matches your request URL
3. **Method Mismatch**: Ensure GET/POST method matches workflow configuration
4. **Cloud Sync**: Wait 30 seconds after activation for registration

**Testing**:
```bash
# Test simple workflow first
curl https://your-workspace.app.n8n.cloud/webhook/simple-test

# If that works, test main workflow
curl -X POST https://your-workspace.app.n8n.cloud/webhook/trigger-enhanced-article \
  -H "Content-Type: application/json" \
  -d '{"content": "Test", "business_categories": ["restaurant"]}'
```

### Environment Variable Issues

**Symptoms**: Supabase connection errors, undefined variables

**Solutions**:
1. **Double-check Names**: Must be exactly `SUPABASE_URL` and `SUPABASE_ANON_KEY`
2. **Verify Values**: Copy-paste to avoid typos
3. **Restart Workflows**: Deactivate → Save → Activate → Save
4. **Check Quotes**: Don't include quotes around values

**Testing**:
```javascript
// Add this to a code node to test variables
console.log('SUPABASE_URL:', process.env.SUPABASE_URL);
console.log('SUPABASE_ANON_KEY exists:', !!process.env.SUPABASE_ANON_KEY);
```

### JSON Parsing Errors

**Symptoms**: `"Unexpected token"`, `"Invalid JSON"`

**Solutions**:
1. **Content-Type Header**: Must include `Content-Type: application/json`
2. **Valid JSON**: Use JSON validator to check request body
3. **Encoding**: Ensure UTF-8 encoding
4. **Quotes**: Use double quotes, not single quotes

**Correct Format**:
```bash
curl -X POST https://your-workspace.app.n8n.cloud/webhook/trigger-enhanced-article \
  -H "Content-Type: application/json" \
  -d '{
    "content": "Article Title",
    "business_categories": ["restaurant", "retail"]
  }'
```

### Package Selection Issues

**Symptoms**: No businesses selected, unexpected businesses

**Solutions**:
1. **Category Matching**: Ensure categories exist in business data
2. **Credit Availability**: Check if businesses have remaining credits
3. **Package Status**: Verify packages are active
4. **Priority Levels**: Review business priority settings

**Debug Categories**:
```json
{
  "content": "Test",
  "business_categories": ["restaurant"]  // Try single category first
}
```

### Performance Issues

**Symptoms**: Slow response times, timeouts

**Solutions**:
1. **Simplify Logic**: Remove unnecessary processing
2. **Optimize Queries**: Efficient database function calls
3. **Cache Results**: Store frequently accessed data
4. **Async Processing**: Use webhooks for long-running tasks

### N8N Cloud Limitations

**Known Limitations**:
- **Execution Time**: 5-minute timeout for workflows
- **Memory Usage**: Limited memory per execution
- **API Calls**: Rate limiting on external requests
- **File Size**: Limited upload/download sizes

**Workarounds**:
- **Break Up Logic**: Split complex workflows into smaller parts
- **External Processing**: Use webhooks to trigger external services
- **Caching**: Store results to reduce repeated processing

## Error Code Reference

### Webhook Errors
- **404**: Webhook not registered → Check activation status
- **405**: Method not allowed → Verify GET vs POST
- **500**: Internal server error → Check workflow logic and variables

### Supabase Errors
- **401**: Authentication failed → Check SUPABASE_ANON_KEY
- **404**: Function not found → Verify database function deployment
- **500**: Database error → Check function parameters and logic

### N8N Errors
- **Execution timeout**: Workflow too complex → Simplify or split
- **Memory limit**: Too much data processing → Optimize or paginate
- **Rate limit**: Too many requests → Add delays or retry logic

## Debugging Steps

### 1. Start Simple
```bash
# Test basic connectivity
curl https://your-workspace.app.n8n.cloud/webhook/simple-test
```

### 2. Verify Environment
- Check environment variables in N8N Cloud settings
- Test Supabase connection separately
- Verify workflow activation status

### 3. Test Components
- Test individual workflow nodes
- Check execution logs in N8N Cloud
- Validate input/output data at each step

### 4. Check Integration
- Test end-to-end workflow
- Verify all expected outputs
- Monitor for any error messages

## Getting Help

### N8N Cloud Support
- **Documentation**: [docs.n8n.io](https://docs.n8n.io)
- **Community**: [community.n8n.io](https://community.n8n.io)
- **Support**: Available through N8N Cloud dashboard

### Package System Support
- **Workflow Issues**: Check GitHub repository for updates
- **Database Issues**: Verify Supabase function deployment
- **Business Logic**: Review package system documentation

### Common Solutions
1. **Restart Everything**: Deactivate → Activate workflows
2. **Check Recent Changes**: Environment variables, workflow modifications
3. **Test in Isolation**: Use simple test workflows first
4. **Monitor Logs**: Check N8N Cloud execution history
5. **Verify Data**: Ensure input data matches expected format
