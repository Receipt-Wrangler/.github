# 🧾 Introduction 🧾

Welcome, thanks for taking a look! Receipt Wrangler is an easy to use self hosted Receipt manager.
The goal of Receipt Wrangler is to allow users to:

* Create receipts effortlessly and quickly
* Catagorize receipts, to search on and filter by
* Share receipts amongst system users
* Keep track of who owes who at any given time

I personally daily drive Receipt Wrangler to keep track of my expenses with my significant other, and I hope that Receipt Wrangler can help you wrangle your receipts as well!

# Features
* Multi User
* Utilizes groups to divide expenses
* Receipt Searching
* Receipt Filtering

# General Roadmap
* Dashboard(s) per group for spending analytics
* OCR/AI implementation to help automate Receipt creation
* Syncing bank transactions to create receipts

# Getting Started
We'll go step by step in getting everything installed.

Step 1: Set up docker-compose.yaml
Below is a sample. Change passwords, and volumes as needed.
```yaml
version: '3.5'
services:
  db:
    image: library/mariadb:10
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: change_me
      MYSQL_USER: wrangler
      MYSQL_PASSWORD: change_me
      MYSQL_DATABASE: wrangler
    volumes:
      - ./mariadb:/var/lib/mysql
    healthcheck:
      test: ["CMD", "mysqladmin" ,"ping", "--silent"]
      interval: 10s
      timeout: 10s
      retries: 5

  api:
    image: noah231515/receipt-wrangler:api
    restart: always
    environment:
      MYSQL_HOST: db:3306
      MYSQL_USER: wrangler
      MYSQL_PASSWORD: change_me
      MYSQL_DATABASE: wrangler
    working_dir: /go/api
    command: ./api --env prod
    ports:
      - 9080:8081
    volumes:
      - ./config:/go/api/config
      - ./data:/go/api/data
    depends_on:
      db:
        condition: service_healthy

  frontend:
     image: noah231515/receipt-wrangler:desktop
     restart: always
     ports:
       - 9081:80
```

Step 2: Set up config.prod.json
This config needs to be in the directory that gets mounted to /go/api/config from the docker-compose.yaml above.
```json
{
  "secretKey": "randomlyGeneratedSecureString"
}
```

Step 3: Set up feature-config.prod.json
This config also needs to be in the directory that gets mounted to /go/api/config
```json
{
  "enabledLocalSignUp": false
}
```

# After Deployment
Currently there is no set up process after deployment. Meaning, your first user can be created through the auth screen.
Since it will be the first user of the system, this user will be automatically made system administrator.

Now it's time to wrangle!
