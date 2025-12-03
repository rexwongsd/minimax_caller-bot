# Manual Edge Function Deployment Guide

## Issue
The Supabase access token has expired, preventing automatic deployment of the updated `whatsapp-send-message` edge function.

## Solution: Manual Deployment via Supabase Dashboard

### Option 1: Using Supabase Dashboard (Recommended)

1. Go to your Supabase project dashboard: https://supabase.com/dashboard/project/izxpkavpiixnskyzseuq
2. Navigate to **Edge Functions** in the left sidebar
3. Find or create the `whatsapp-send-message` function
4. Replace the function code with the updated version from:
   `/workspace/supabase/functions/whatsapp-send-message/index.ts`
5. Deploy the function

### Option 2: Using Supabase CLI with Fresh Token

1. Login to Supabase CLI:
   ```bash
   supabase login
   ```

2. Link your project:
   ```bash
   supabase link --project-ref izxpkavpiixnskyzseuq
   ```

3. Deploy the function:
   ```bash
   cd /workspace
   supabase functions deploy whatsapp-send-message --project-ref izxpkavpiixnskyzseuq
   ```

## Key Changes in the Updated Function

The updated edge function now:
1. **Fetches credentials from database** instead of using hardcoded values
2. **Uses the correct user credentials** from the `whatsapp_credentials` table
3. **Includes proper error handling** and logging
4. **Validates credentials** before attempting to send messages

## Updated Function Code Location
File: `/workspace/supabase/functions/whatsapp-send-message/index.ts`

## Testing After Deployment

After deploying the edge function:
1. Go to Settings page in the app
2. Verify WhatsApp credentials are displayed correctly
3. Click "Test Connection" - should show success
4. Try sending a test message from the Contacts page
