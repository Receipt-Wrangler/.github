# Introduction

Receipt Wrangler has one main configuration file to set up. The details of what everything does will be detailed here.

# Configuration

Sample config:

```json
{
  "secretKey": "secretKey",
  "aiSettings": {
    "type": "openAi or llamagpt",
    "url": "urlToLocallyHostedLLM",
    "key": "openAiKey"
  },
  "emailPollingInterval": 1800,
  "emailSettings": [
    {
      "host": "emailHost",
      "port": "emailPort",
      "username": "emailAddress",
      "password": "password/apiKey"
    }
  ],
  "features": {
    "enableLocalSignUp": true,
    "aiPoweredReceipts": true
  },
  "database": {
    "user": "wrangler",
    "password": "changeMe",
    "name": "wrangler",
    "host": "localhost",
    "port": 3306,
    "engine": "sqlite or mysql or mariadb or postgresql",
    "filename": "wrangler.sqlite"
  }
}
```

- aiSettings: These settings are used to configure the AI Integration. These values are detailed [here](https://github.com/Receipt-Wrangler/.github/tree/main/integrations/ai.md).
- emailSettings: These settings are used to configure the Email Integration. These values are detailed [here](https://github.com/Receipt-Wrangler/.github/tree/main/integrations/email.md).
- secretKey: This key is used to sign jwts generated from the server.
- features.enabledLocalSignUp: This field will enable local sign up. If set to false, then only admins can register usrs
- features.aiPoweredReceipts: This field will enable the AI powered receipts. If set to false, then the AI integration will be disabled.
- database.rootPassword: This is the root password for the database
- database.user: This is the user that will be used to connect to the database
- database.password: This is the password for the user that will be used to connect to the database
- database.name: This is the name of the database
- database.host: This is the host of the database
- database.port: This is the port of the database (Only used for postgresql connections)
- database.engine: This is the engine of the database. Valid options are: sqlite, mysql, mariadb, and postgresql
- database.filename: This is the filename of the sqlite database. This is only used if the engine is set to sqlite.
