![image](https://github.com/Receipt-Wrangler/.github/assets/44912201/48922c60-d3c9-44d1-8354-4c54e8b5d657)

# 🧾 Introduction 🧾

Welcome, thanks for taking a look! Receipt Wrangler is an easy to use self hosted Receipt manager.
The goal of Receipt Wrangler is to allow users to:

- Create receipts effortlessly and quickly
- Catagorize receipts, to search on and filter by
- Share receipts amongst system users
- Keep track of who owes who at any given time

I personally daily drive Receipt Wrangler to keep track of my expenses with my significant other, and I hope that Receipt Wrangler can help you wrangle your receipts as well!

[Demo App](https://demo.receiptwrangler.io)

# Features

- Multi User
- Utilizes groups to divide expenses
- Receipt Searching
- Receipt Filtering
- Partial receipt creation with OCR/AI from receipt image to help automate Receipt creation
- Email integration to upload receipts via email

# General Roadmap

- Dashboard(s) per group for spending analytics
- OCR/AI implementation to fully automate Receipt creation
- Mobile app

# Getting Started

We'll go step by step in getting everything installed.

## Step 1: Set up docker-compose.yaml

**Important Note:**
If you decide to use the built in proxy, the service names in the compose must remain as they are in the examples, otherwise the proxy will not work.
The ports of each service are free to change, though.

Receipt Wrangler can be set up as either a monolithic app (all in one container), or as microservices (each part as its own container).
Check out the examples to see which one is better for you.

- [Examples](https://github.com/Receipt-Wrangler/.github/tree/main/examples)

## Step 2: Set up config.prod.json

This config needs to be in the directory that gets mounted to /go/api/config from the docker-compose.yaml above.

See the [config documentation](https://github.com/Receipt-Wrangler/.github/tree/main/configuration/configuration.md) for samples and explanations of each value.

## Step 3: Add proxy in NPM Proxy Manager (Optional):

**If you are using the proxy container in the docker compose stack, skip this step**

Forward api calls to backend
Lastly, we need to forward api calls to backend if you are not using the preconfigured proxy from the proxy.
Below is an example using NGINX proxy manager. Without this step, the requests sent to paths at /api/ will not make it to the backend. Instead, the frontend will attempt to interpert those requests.

## Details Tab

![image](https://github.com/Receipt-Wrangler/.github/assets/44912201/9690b448-93d2-41d7-8852-ef411d7283b5)

## Locations Tab

![image](https://github.com/Receipt-Wrangler/.github/assets/44912201/2fe17995-b4c2-40c1-91d3-c046a6666f4d)

## Step 4: Deploy

If using the proxy container, deploy the stack and point all traffic to the proxy container.
If you are not using the proxy container, point all traffic to the frontend container.

# After Deployment

After the app is deployed, a default user will be created with the following credentials:
username: admin
password: admin

Your credentials can be changed by opening the sidebar, clicking on your user avatar on the top left hand corner and then clicking settings.
There in the user profile, your displayname and username can be changed.

For now, your username cannot be changed from this screen, but can be changed from the the manage users list. This will be remidied in the future.

Now it's time to wrangle!

# Integrations

Receipt Wrangler currently supports uploading receipts via email. Check out the documentation on how to set it up. [See Documentation](https://github.com/Receipt-Wrangler/.github/tree/main/integrations)
