# Getting Started

Email integration is a way for users to upload receipts to a group, as a different way to get receipts into the system.
Multiple images can be sent in attachements, and each image will be assumed to be a different receipt. If the image is malformed (corrupted, not acutally an image), then the file will not be processed.

## Configuration

1. Modify config.prod.json
   Email(s) can be configured here, in which the Receipt Wrangler api will connect to once the integration is full set up.

```json
{
  "emailSettings": [
    {
      "host": "smtp.qq.com",
      "port": 465,
      "username": "test",
      "password": "test"
    }
  ]
}
```

2. Modify group settings
   Once the email credentials are added to the config, we need to update our group settings to actually read from that email address.

### Enable Email Integration

This field will enable the integration. After the email is enabled, a connection will be attempted to be made to the configured email address, assuming everything is configured correctly.

### Email to Read Receipts From field

The "Email to Read Receipts From" field must match a username from the email settings configured in the last step, this will tell the api that this group is using this email.

### Subject Line Regexes

These regexes drive which emails are read for this group. If no regexes are set up, then any subject line is permissible.

### Email Whitelist

These emails will allow group owners to only accept emails from certain email addresses. If none are configured, then any incoming email address is permissible.

### Overlapping Configurations

Let's say that two groups are configured with the same exact group settings. This means that a group is set up to listen to the same emails.

In this case, nothing is done to prevent this scenario as it is not necessairly a bad thing. So, receipts would be created for both groups.
