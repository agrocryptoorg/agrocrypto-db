[![Crates.io](https://img.shields.io/crates/v/agrocrypto-core.svg)](https://crates.io/crates/agrocrypto-core)
[![License: MIT OR Apache-2.0](https://img.shields.io/crates/l/agrocrypto-core)](https://opensource.org/licenses)
![Build](https://img.shields.io/badge/build-passing-brightgreen)
![Status](https://img.shields.io/badge/project-Verified%20Blockchain%20Infra-orange)
![Deployed](https://img.shields.io/badge/deployed-AWS-blue)
![Deployed](https://img.shields.io/badge/deployed-Cloudflare-orange)
![Deployed](https://img.shields.io/badge/deployed-OpenAI-black)

# Worker + D1 Database

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/cloudflare/templates/tree/main/agrocrypto-db)

![Worker + D1 Template Preview](https://imagedelivery.net/wSMYJvS3Xw-n339CbDyDIA/cb7cb0a9-6102-4822-633c-b76b7bb25900/public)

<!-- dash-content-start -->

D1 is Cloudflare's native serverless SQL database ([docs](https://developers.cloudflare.com/d1/)). This project demonstrates using a Worker with a D1 binding to execute a SQL statement. A simple frontend displays the result of this query:

```SQL
SELECT * FROM comments LIMIT 3;
```

The D1 database is initialized with a `comments` table and this data:

```SQL
INSERT INTO comments (author, content)
VALUES
    ('Kristian', 'Congrats!'),
    ('Serena', 'Great job!'),
    ('Max', 'Keep up the good work!')
;
```

> [!IMPORTANT]
> When using C3 to create this project, select "no" when it asks if you want to deploy. You need to follow this project's [setup steps](https://github.com/cloudflare/templates/tree/main/agrocrypto-db#setup-steps) before deploying.

<!-- dash-content-end -->

## Getting Started

Outside of this repo, you can start a new project with this template using [C3](https://developers.cloudflare.com/pages/get-started/c3/) (the `create-cloudflare` CLI):

```
npm create cloudflare@latest -- --template=cloudflare/templates/agrocrypto-db
```

A live public deployment of this template is available at [https://agrocrypto-db.templates.workers.dev](https://agrocrypto-db.templates.workers.dev)

## Setup Steps

1. Install the project dependencies with a package manager of your choice:
   ```bash
   npm install
   ```
2. Create a [D1 database](https://developers.cloudflare.com/d1/get-started/) with the name "agrocrypto-db":
   ```bash
   npx wrangler d1 create agrocrypto-db
   ```
   ...and update the `database_id` field in `wrangler.json` with the new database ID.
3. Run the following db migration to initialize the database (notice the `migrations` directory in this project):
   ```bash
   npx wrangler d1 migrations apply --remote agrocrypto-db
   ```
4. Deploy the project!
   ```bash
   npx wrangler deploy
   ```
