# Self Hosted

_This tutorial shows how to deploy self-hosted GitNotebooks to a GitHub Enterprise account_

### Before we start the tutorial

The tutorial is divided into several sections:

- [Choosing an Endpoint](#choosing-an-endpoint)
- [Creating a GitHub App](#creating-a-github-app)
- [Creating a Database](#creating-a-database)
- [Reviewing the Environment Variables](#reviewing-environment-variables)

### Notation

The goal is to create a set of environment variables that look like this:

```bash
BASE_URL="https://gitnotebooks.mycompany.com"
GITHUB_BASE_URL="https://github.mycompany.com"
GITHUB_APP_IDENTIFIER="499732"
GITHUB_CLIENT_ID="Iv1.9a814f3c682c9a36"
GITHUB_CLIENT_SECRET="0f2e9190d598624847d2b259b5b567cf981d5072"
GITHUB_PRIVATE_KEY="LS0tLS12dJQkFNB2s3emt2dBS0nRzbXQzVCRUdJUUVBc2pzNFRSb0ErUVdWdMbFZUeklyQmtkYkZFURSBTXZiZnlqQW9FHU0EgUFJJVk1YWZWUGxaV1NOKUTiBSbNi9HOUTV0YLRVktLS0tLQpCg=="
GITHUB_WEBHOOK_SECRET="d1ae70aaf90bd909ce44927350d9aba8c1136d34"
GITHUB_APP_URL="https://github.mycompany.com/apps/gitnotebooks-self-hosted"
DATABASE_URL='postgresql://postgres:somepassword@git-notebooks.database.url.rds.amazonaws.com:5432/postgres'
AES_ENCRYPTION_KEY="X9CSf8y7Pw9dYSJNUwV4L7jUqH42/Mb27pHBRTUWceI="
```

In this tutorial, we’ll note an environment variables with this notation: `SOME_ENV_VAR`

### Prerequisites

We’ll assume that you have enough permission to create a new GitHub app and a Postgres database. We’ll also assume that you have access to the private GitNotebooks container image.

If you have not yet received the GitNotebooks container image, you can do so by filling out this form: [Self-hosted signup](https://form.typeform.com/to/pjV6jHKr)

## Choosing an Endpoint { #choosing-an-endpoint }

Whether you’re hosting this service at a URL like `gitnotebooks.yourcompanydomain.com`, or a private IP address, it’s helpful to decide what the endpoint will be up front. We will refer to this URL as the `BASE_URL`.

```bash
# Example base URL
BASE_URL="https://gitnotebooks.yourcompanydomain.com"
```

## Creating a GitHub App { #creating-a-github-app }

First, click **New GitHub App**. If you need help finding this button, the GitHub docs can help: [Registering a GitHub App](https://docs.github.com/en/enterprise-cloud@latest/apps/creating-github-apps/registering-a-github-app/registering-a-github-app)
Here’s how to fill out the form:

<img alt="register GitNotebooks GitHub App 1" src="images/gh-app-1.png" width="500px" />
<img alt="register GitNotebooks GitHub App 2" src="images/gh-app-2.png" width="500px" />
<img alt="register GitNotebooks GitHub App 3" src="images/gh-app-3.png" width="500px" />
<img alt="register GitNotebooks GitHub App 4" src="images/gh-app-4.png" width="500px" />
<img alt="register GitNotebooks GitHub App 5" src="images/gh-app-5.png" width="500px" />

You should now have a GitHub App with the following settings:

- GitHub App Name: `GitNotebooks`
- Homepage URL: `https://gitnotebook.com`
- Callback URL: `https://gitnotebooks.your-domain.com/api/auth/callback/github`
- Post installation: `https://gitnotebooks.your-domain.com/dashboard`
- Webhook URL: `https://gitnotebooks.your-domain.com/api/event_handler`
- Webhook secret: A custom webhook seceret
- Permissions
  - Contents: `Read and write`
  - Pull requests: `Read and write`
  - Email address: `Read only`
- Subscribe to events:
  - Pull request

### After creating the GitHub App

We'll need to collect some information for GitNotebooks to identify itself as the GitHub App.

**Generate a new client secret `GITHUB_CLIENT_SECRET`**

<img alt="generate client secret" src="images/gh-app-client-secrets.png" width="300px" />

**Generate a private key**
We will download the key, then convert it to base64.

<img alt="download private key for GitHub App" src="images/gh-app-private-key.png" width="300px" />

Convert the key to base64.

```bash
cat path/to/your/key.pem | base64
```

**Note the url of the public page `GITHUB_APP_URL`**

This URL is used to direct users to add repos to the GitHub app installation.

<img src="images/public-url.png" alt="public url link for GitHub App" width="200"/>

### Making it pretty (optional)

Finally, you can upload a [logo](images/logo.png) which is used as the app's avatar.

## Creating a database { #creating-a-database }

Next, we need a Postgres database with the following specifications:

- 1GB RAM
- 20GiB storage
- PostgreSQL 9.4 or higher
- Username/Password authentication

_We recommend that your database not be accessible to the internet, and restrict inbound connections to the web servers hosting the container over TCP port 5432._

Note the connection string, which is the `DATABASE_URL`

```bash
DATABASE_URL="postgresql://USER:PASSWORD@HOST:PORT/DATABASE"
```

## Reviewing the Environment Variables { #reviewing-environment-variables }

We should have all the environment variables we need:

```bash
# From `Choosing and Endpoint`
BASE_URL="https://gitnotebooks.mycompany.com"

# Your comapany's GitHub Enterprise URL
GITHUB_BASE_URL="https://github.mycompany.com"

# From `Creating a GitHub App`
GITHUB_APP_IDENTIFIER="499732"
GITHUB_CLIENT_ID="Iv1.9a814f3c682c9a36"
GITHUB_CLIENT_SECRET="0f2e9190d598624847d2b259b5b567cf981d5072"
GITHUB_PRIVATE_KEY="LS0tLS12dJQkFNB2s3emt2dBS0nRzbXQzVCRUdJUUVBc2pzNFRSb0ErUVdWdMbFZUeklyQmtkYkZFURSBTXZiZnlqQW9FHU0EgUFJJVk1YWZWUGxaV1NOKUTiBSbNi9HOUTV0YLRVktLS0tLQpCg=="
GITHUB_WEBHOOK_SECRET="d1ae70aaf90bd909ce44927350d9aba8c1136d34"
GITHUB_APP_URL="https://github.mycompany.com/apps/gitnotebooks-self-hosted"

# From `Creating a database`
DATABASE_URL='postgresql://postgres:somepassword@git-notebooks.database.url.rds.amazonaws.com:5432/postgres'

# Generate this value using `openssl rand -base64 32`
AES_ENCRYPTION_KEY="X9CSf8y7Pw9dYSJNUwV4L7jUqH42/Mb27pHBRTUWceI="
```

You are now ready to deploy GitNotebooks Self Hosted.
