> ## Documentation Index
> Fetch the complete documentation index at: https://docs.magichour.ai/llms.txt
> Use this file to discover all available pages before exploring further.

# Authentication

> Create and manage API keys to authenticate your requests to the Magic Hour API.

## Overview

Magic Hour uses API keys to authenticate requests. Your API keys carry many privileges, so be sure to keep them secure! Do not share your secret API keys in publicly accessible areas such as GitHub, client-side code, and so forth.

All API requests must be authenticated by including your API key in the `Authorization` header:

```bash theme={null}
Authorization: Bearer your_api_key_here
```

## Creating Your First API Key

<Steps>
  <Step title="Sign in to Magic Hour">
    Visit [magichour.ai](https://magichour.ai/sign-up?utm_source=docs\&utm_medium=referral\&utm_campaign=authentication) and sign in to your account. If you don't have an account yet, you can create one for free.

    <img src="https://mintcdn.com/magichour/jj1tYAcivRE8aZA_/get-started/images/sign-in-to-magic-hour.jpg?fit=max&auto=format&n=jj1tYAcivRE8aZA_&q=85&s=3704d89dd82ddf3caf3d1eb5c559b237" alt="Sign in page" width="1024" height="527" data-path="get-started/images/sign-in-to-magic-hour.jpg" />
  </Step>

  <Step title="Navigate to Developer Hub">
    Once signed in, go directly to the [API Keys section of the Developer Hub](https://magichour.ai/developer?tab=api-keys\&ref=docs-authentication\&utm_source=docs\&utm_medium=referral\&utm_campaign=authentication).

    <img src="https://mintcdn.com/magichour/jj1tYAcivRE8aZA_/get-started/images/navigate-to-developer-hub.jpg?fit=max&auto=format&n=jj1tYAcivRE8aZA_&q=85&s=6c57bb8db62ebdd324c32e4752aea5f4" alt="Developer Hub with API Keys" width="1024" height="524" data-path="get-started/images/navigate-to-developer-hub.jpg" />
  </Step>

  <Step title="Create New API Key">
    Click the **"Create API Key"** button to generate a new key.

    <img src="https://mintcdn.com/magichour/jj1tYAcivRE8aZA_/get-started/images/create-new-api-key.jpg?fit=max&auto=format&n=jj1tYAcivRE8aZA_&q=85&s=eb4243d87433148524a35f864cd67600" alt="Create API Key button" width="1024" height="524" data-path="get-started/images/create-new-api-key.jpg" />
  </Step>

  <Step title="Configure Your API Key">
    Give your API key a descriptive name to help you identify its purpose later:

    * **Name**: Choose a clear name (e.g., "Production App", "Development Testing", "Mobile App")
    * **Permissions**: Select the appropriate permissions for your use case

          <img src="https://mintcdn.com/magichour/jj1tYAcivRE8aZA_/get-started/images/configure-your-api-key.jpg?fit=max&auto=format&n=jj1tYAcivRE8aZA_&q=85&s=42c65e5410b7a5289fa18a6de9753860" alt="API Key configuration" width="1024" height="526" data-path="get-started/images/configure-your-api-key.jpg" />

    Click **"Create Key"** to generate your new API key.
  </Step>

  <Step title="Copy and Store Your API Key">
    **Important**: Your API key will only be shown once. Copy it immediately and store it securely.

    <img src="https://mintcdn.com/magichour/jj1tYAcivRE8aZA_/get-started/images/copy-and-store-api-key.jpg?fit=max&auto=format&n=jj1tYAcivRE8aZA_&q=85&s=8680e299f848c4ede67cc6184a15d3f4" alt="API Key created" width="1024" height="524" data-path="get-started/images/copy-and-store-api-key.jpg" />

    <Warning>
      **Save your API key now!** You won't be able to see the full key again after closing this dialog. If you lose it, you'll need to create a new one.
    </Warning>
  </Step>
</Steps>

## Managing Your API Keys

### Viewing API Keys

In the Developer Hub, you can see all your API keys with:

* **Name**: The descriptive name you gave the key
* **Last 4 Characters**: The last 4 characters of the key
* **Created**: When the key was created

<img src="https://mintcdn.com/magichour/jj1tYAcivRE8aZA_/get-started/images/managing-your-api-keys.jpg?fit=max&auto=format&n=jj1tYAcivRE8aZA_&q=85&s=adc387d0090d0d9d2f523a17e3ba53be" alt="API Keys list" width="1024" height="527" data-path="get-started/images/managing-your-api-keys.jpg" />

### Revoking API Keys

To revoke an API key:

1. Find the key in your API Keys list
2. Click the **Delete (Trash Icon)** button next to the key
3. Click "Delete key" to confirm the revocation

<img src="https://mintcdn.com/magichour/jj1tYAcivRE8aZA_/get-started/images/revoking-api-keys.jpg?fit=max&auto=format&n=jj1tYAcivRE8aZA_&q=85&s=1188aa2945e5de10e26474c0ecdec50c" alt="Revoke API Key" width="1024" height="527" data-path="get-started/images/revoking-api-keys.jpg" />

<Warning>
  **Immediate Effect**: Revoked keys stop working immediately. Any applications using the revoked
  key will start receiving authentication errors.
</Warning>

### Rotating API Keys

For security best practices, regularly rotate your API keys:

1. **Create a new API key** with the same permissions
2. **Update your applications** to use the new key
3. **Test thoroughly** to ensure everything works
4. **Revoke the old key** once you're confident the new key is working

## Using API Keys

### In Code

<CodeGroup>
  ```python Python SDK theme={null}
  from magic_hour import Client

  import os

  # Initialize client with your API key, or read it from an environment variable
  client = Client(token=os.getenv("MAGIC_HOUR_API_KEY", "your_api_key_here"))
  ```

  ```javascript Node.js SDK theme={null}
  import { Client } from "magic-hour";

  // Initialize client with your API key, or read it from an environment variable
  const client = new Client({
    token: process.env.MAGIC_HOUR_API_KEY ?? "your_api_key_here",
  });
  ```

  ```bash cURL theme={null}
  curl -X POST "https://api.magichour.ai/v1/ai-image-generator" \
    -H "Authorization: Bearer your_api_key_here" \
    -H "Content-Type: application/json" \
    -d '{
      "image_count": 1,
      "aspect_ratio": "16:9",
      "resolution": "1k",
      "style": {
        "prompt": "A beautiful sunset over mountains"
      }
    }'
  ```
</CodeGroup>

### Environment Variables

Store your API key as an environment variable for security:

<CodeGroup>
  ```bash .env file theme={null}
  MAGIC_HOUR_API_KEY=your_api_key_here
  ```

  ```bash Shell Export theme={null}
  export MAGIC_HOUR_API_KEY=your_api_key_here
  ```

  ```bash Windows theme={null}
  set MAGIC_HOUR_API_KEY=your_api_key_here
  ```
</CodeGroup>

## Security Best Practices

### ✅ Do

* **Store keys securely** in environment variables or secure key management systems
* **Use different keys** for different environments (development, staging, production)
* **Rotate keys regularly** (every 90 days recommended)
* **Revoke unused keys** immediately
* **Monitor key usage** in the Developer Hub
* **Implement proper error handling** for authentication failures

### ❌ Don't

* **Never commit keys** to version control (Git, SVN, etc.)
* **Don't expose keys** in client-side code (JavaScript, mobile apps)
* **Don't share keys** via email, chat, or other insecure channels
* **Don't use production keys** in development environments
* **Don't ignore security warnings** about exposed keys

### Key Storage Solutions

**For Development:**

* Environment variables (`.env` files)
* Local configuration files (excluded from version control)

**For Production:**

* AWS Secrets Manager
* Azure Key Vault
* Google Secret Manager
* HashiCorp Vault
* Kubernetes Secrets

## Authentication Errors

Common authentication errors and how to resolve them:

### `401 Unauthorized`

**Cause**: Invalid or missing API key
**Solutions**:

* Check that your API key is correct
* Ensure the `Authorization` header is properly formatted
* Verify the key hasn't been revoked

## Monitoring Usage

<Note>
  **Usage-Based Billing Only**: Analytics & Billing monitoring is only available for accounts with
  usage-based billing. Subscription users can view basic key information in the API Keys section.
</Note>

With usage-based billing, track your API key usage in the Developer Hub:

* **Credit Usage**: Credits consumed by your requests

This helps you:

* Detect unusual activity that might indicate a compromised key
* Plan for capacity and billing

## Next Steps

<CardGroup cols={2}>
  <Card title="Quick Start Guide" icon="rocket" href="/get-started/quick-start">
    Make your first API call with your new API key
  </Card>

  <Card title="Google Colab Cookbook" icon="code" href="https://colab.research.google.com/drive/1NTHL_lr_s-qBJ-mSecSXPzRLi9_V5JiU?usp=sharing" openInNewTab>
    Try the Magic Hour APIs with ready-to-run sample code. Just add your API key.
  </Card>

  <Card title="SDKs" icon="code" href="/integration/adding-api-to-your-app">
    Use official SDKs for easier integration
  </Card>

  <Card title="Pricing" icon="credit-card" href="/billing/overview">
    Understand how API usage affects billing
  </Card>

  <Card title="Webhooks" icon="webhook" href="/integration/webhook/overview">
    Set up webhooks for real-time notifications
  </Card>
</CardGroup>

## Need Help?

If you're having trouble with authentication:

* Check our [troubleshooting guide](/get-started/quick-start#troubleshooting)
* Contact support at [support@magichour.ai](mailto:support@magichour.ai)
* Join our community on [Discord](https://discord.gg/JX5rgsZaJp)

<Info>
  **Security Concern?** If you believe your API key has been compromised, revoke it immediately in
  the Developer Hub and create a new one.
</Info>
