# Introduction

Receipt Wrangler has one main configuration file to set up. The details of what everything does will be detailed here.

# Configuration

Sample config:

```json
{
  "aiSettings": {
    "type": "type",
    "url": "url",
    "key": "key"
  },
  "secretKey": "randomlyGeneratedSecureString"
}
```

- aiSettings: These settings are used to configure the AI Integration. These values are detailed [here](https://github.com/Receipt-Wrangler/.github/tree/main/integrations/ai.md).
- secretKey: This key is used to sign jwts generated from the server.
