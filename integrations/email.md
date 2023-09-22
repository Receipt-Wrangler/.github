# Getting Started

Email integration is a way for users to upload receipts to a group, as a different way to get receipts into the system.
Multiple images can be sent in attachements, and each image will be assumed to be a different receipt. If the image is malformed (corrupted, not acutally an image), then the file will not be processed.

## Configuration

1. Modify config.prod.json
   Email(s) can be configured here, in which the Receipt Wrangler api will connect to once the integration is set up.

Add credentials for your email provider, and polling interval (in seconds)

```json
{
  "emailPollingInterval": 1800, // 30 minutes
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

All of the emails configured in emailSettings will be polled every polling interval, to read unread emails, and process those that match the group settings, set up in the next step.

2. Modify group settings
   Once the email credentials are added to the config, we need to update our group settings to actually read from that email address.

### Enable Email Integration

This field will enable the integration. After the email is enabled, a connection will be attempted to be made to the configured email address on the next polling interval.

### Email to Read Receipts From field

The "Email to Read Receipts From" field must match a username from the email settings configured in the last step, this will tell the api that this group is using this email.

### Subject Line Regexes

These regexes drive which emails are read for this group. If no regexes are set up, then any subject line is permissible for processing.

### Email Whitelist

These emails will allow group owners to only accept emails from certain email addresses. If none are configured, then any incoming email address is permissible for processing.

### Default Paid By

This is the user that will be assigned receipts that are uploaded via email.

### Default Status

This will be the status that will be set on receipts that are uploaded via email.

### Caveats

#### Email attachments

Currently email attachments are required, since emails are processed via ocr/ai. If no attachment is found on the email, the email will not be processed.

#### Multiple attachments

Currently there is no way to group multiple attachments into one receipt. So if 20 attachments are sent, then 20 separate receipts will be created.

#### Overlapping Configurations

Let's say that two groups are configured with the same exact group settings. This means that a group is set up to listen to the same emails.

In this case, nothing is done to prevent this scenario as it is not necessairly a bad thing. So, receipts would be created for both groups.
This could potentially be a privacy issue, since a user could capture another user's emails/receipts if using the same email address to read from. This is going to be addressed by an option to only allow system administrators to edit the group's email settings.
