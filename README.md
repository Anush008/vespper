# Vespper - open-source AI on-call developer

<div align="center">
    <a href="https://vespper.co">
      <img src="./assets/logo-cat.png" alt="Vespper-logo" width="30%"/>
    </a>
</div>
<br />
<div align="center">
   <div>
      <a href="https://docs.vespper.com"><strong>Docs</strong></a> ·
      <a href="https://www.loom.com/share/85dc64d021cc40c4b1064389c20782a6?sid=91b063df-8111-40f0-9ea4-793d5fbe3f6f"><strong>Demo</strong></a> ·
      <a href="https://github.com/vespperhq/vespper/issues"><strong>Report Bug</strong></a> ·
      <a href="https://github.com/orgs/vespper/discussions"><strong>Feature Request</strong></a> ·
      <a href="https://vespper.com/blog"><strong>Blog</strong></a> ·
      <a href="https://join.slack.com/t/vesppercommunity/signup"><strong>Slack</strong></a> 
   </div>
</div>
<br />
<div style="display: flex" style="margin-bottom: 20px">
<a href="https://vespper.com/?utm_source=github"><img src="https://img.shields.io/badge/Website-blue?logo=googlechrome&logoColor=orange"/></a>
  <a href="https://calendly.com/dudu-vespper/45-minute-meeting"><img src="https://img.shields.io/badge/Book%20a%20Call-blue" /></a>
<a href="https://github.com/vespperhq/vespper/blob/main/LICENSE.md"><img src="https://img.shields.io/badge/License-Apache 2.0-red.svg?style=flat-square" alt="Apache 2.0 License"></a>
<a href="https://github.com/vespperhq/vespper/actions/workflows/ci.yml/badge.svg?branch=main">
<img src="https://github.com/vespperhq/vespper/actions/workflows/ci.yml/badge.svg?branch=main" alt="main-workflow">
</a>
<a href="https://github.com/prettier/prettier">
<img src="https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square" alt="code style: prettier">
</a>
<a href="https://join.slack.com/t/vesppercommunity/signup">
<img src="https://img.shields.io/badge/slack-vespper-E01E5A.svg?logo=slack" alt="slack-logo" />
</a>
</div>


Note: If you want to use vespper for your team or for your organisation please reach out to us.
This open-source project is suited for single individual use. Any advanced investigation features will be under vespper-ee.

</p>


## Overview 💫

Vespper is an AI-powered on-call engineer. It can automatically jump into incidents & alerts with you, and provide you useful & contextual insights and RCA in real time.


## Why ❓

Most people don't like to do on-call shifts. It requires engineers to be swift and solve problems quickly. Moreover, it takes time to reach to the root cause of the problem. That's why we developed Vespper. We believe Gen AI can help on-call developers solve issues faster.

## Table of Contents

- [Overview](#overview-)
- [Why](#why-)
- [Key Features](#key-features-)
- [Demo](#demo-)
- [Getting started](#getting-started-)
  - [Prerequisites](#prerequisites-)
  - [Quick Installation](#quick-installation-)
  - [Updating Vespper](#updating-vespper-️-)
  - [Deployment](#deployment-)
  - [Visualize Knowledge Base](#visualize-knowledge-base-)
- [Support and feedback](#support-and-feedback-️)
- [Contributing to Vespper](#contributing-to-vespper-️)
- [Troubleshooting](#troubleshooting-️)
- [Telemetry](#telemetry-)
- [License](#license-)
- [Learn more](#learn-more-)
- [Contributors](#contributors-)

## Key features 🎯

- **Automatic RCA**: Vespper automatically listens to production incidents/alerts and automatically investigates them for you.
- **Slack integration**: Vespper lives inside your Slack. Simply connect it and enjoy an on-call engineer that never sleeps.
- **Integrations**: Vespper integrates with popular observability/incident management tools such as Datadog, Coralogix, Opsgenie and Pagerduty. It also integrates to other tools as GitHub, Notion, Jira and Confluence to gain insights on incidents.
- **Intuitive UX**: Vespper offers a familiar experience. You can talk to it and ask follow-up questions.
- **Secure**: Self-host Vespper and own your data. Always.
- **Open Source**: We love open-source. Self-host Vespper and use it for free.

## Demo 🎥

Checkout our [demo video](https://www.loom.com/share/85dc64d021cc40c4b1064389c20782a6?sid=1178d76f-5036-4fb2-887b-63b7f4f9aaac) to see Vespper in action.

## Getting started 🚀

In order to run Vespper, you need to clone the repo & run the app using Docker Compose.

### Prerequisites 📜

Ensure you have the following installed:

- **Docker & Docker Compose** - The app works with Docker containers. To run it, you need to have [Docker Desktop](https://docs.docker.com/desktop/), which comes with Docker CLI, Docker Engine and Docker Compose.
<!-- - **Ngrok** - Ngrok allows you to open HTTPS tunnel to your local machine. This is needed in order to get events from PagerDuty/Opsgenie. Install ngrok cli and create an account (see [here](https://ngrok.com/)). -->

### Quick installation 🏎️

You can find the installation video [here](https://www.loom.com/share/1f562cb067364517b1c1e7bf7f789db7?sid=8ea35183-893e-4e74-b450-c3e2e1cc1f11).

1. Clone the repository:

   ```bash
   git clone git@github.com:vespper/vespper.git && cd vespper
   ```

2. Configure LiteLLM Proxy Server:

   We use [LiteLLM Proxy Server](https://docs.litellm.ai/docs/simple_proxy) to interact with 100+ of LLMs in a unified interface (OpenAI interface).

   1. Copy the example files:

      ```bash
      cp config/litellm/.env.example config/litellm/.env
      cp config/litellm/config.example.yaml config/litellm/config.yaml
      ```

   2. Define your **OpenAI key** and place it inside `config/litellm/.env` as `OPENAI_API_KEY`. You can get your API key [here](https://platform.openai.com/api-keys). Rest assured, you won't be charged unless you use the API. For more details on pricing, check [here](https://openai.com/pricing).

3. Copy the `.env.example` file:

   ```bash
   cp .env.example .env
   ```

4. Open the `.env` file in your favorite editor (vim, vscode, emacs, etc):

   ```bash
   vim .env # or emacs or vscode or nano
   ```

5. Update these variables:

   - `SLACK_BOT_TOKEN`, `SLACK_APP_TOKEN` and `SLACK_SIGNING_SECRET` - These variables are needed in order to talk to Vespper on Slack. Please follow [this guide](https://github.com/vespperhq/vespper/tree/main/config/slack/README.md) to create a new Slack app in your organization.

   - (Optional) `SMTP_CONNECTION_URL` - This variable is needed in order to invite new members to your Vespper organization via email and allow them to use the bot. It's not mandatory if you just want to test Vespper and play with it. If you do want to send invites to your team members, you can use a service like SendGrid/Mailgun. Should follow this pattern: `smtp://username:password@domain:port`.

6. Launch the project:
   ```bash
   docker compose up -d
   ```

That's it. You should be able to visit Vespper's dashboard in http://localhost:5173.
Simply create a user **(with the same e-mail as the one in your Slack user)** and start to configure your organization. If something does not work for you, please checkout our [troubleshooting](#troubleshooting-️) or reach out to us via our [support channels](#support-and-feedback-️).

The next steps are to configure your organization a bit more (connect incident management tools, build a knowledge base, etc). Head over to the [connect & configure](https://docs.vespper.com/Getting%20started/Configure%20&%20connect) section in our docs for more information 💫

#### Using DockerHub images

If you want, you can pull our [Docker images](https://hub.docker.com/u/vespper) from DockerHub instead of cloning the repo & building from scratch.

In order to do that, follow these steps:

1. Download configuration files:

   ```bash
   curl https://raw.githubusercontent.com/vespper/vespper/main/tools/scripts/download_env_files.sh | sh
   ```

2. Follow steps 2 and 5 above to configure LiteLLM Proxy and your `.env` file respectively. Namely, you'd need to configure your OpenAI key at `config/litellm/.env` and configure your Slack credentials in the root `.env`.

3. Spin up the environment using docker compose:
   ```bash
   curl https://raw.githubusercontent.com/vespper/vespper/main/tools/scripts/start.sh | sh
   ```

That's it 💫 You should be able to visit Vespper's dashboard in http://localhost:5173.

### Updating Vespper 🧙‍♂️

1. Pull the latest changes:

   ```bash
   git pull
   ```

2. Rebuild images:

   ```bash
   docker-compose up --build -d
   ```

### Deployment ☁️

Visit our [example guides](https://github.com/vespperhq/vespper/tree/main/examples) in order to deploy Vespper to your cloud.

### Visualize Knowledge Base 🗺️

We use ChromaDB as our vector DB. We also use [vector admin](https://vectoradmin.com/) in order to see the ingested documents. To use vector admin, simply run this command:

```bash
docker compose up vector-admin -d
```

This command starts vector-admin at port 3001. Head over to http://localhost:3001 and configure your local ChromaDB. **Note:** Since vector-admin runs inside a docker container, in the "host" field make sure to insert `http://host.docker.internal:8000` instead of `http://localhost:8000`. This is because "localhost" doesn't refer to the host inside the container itself.

Moreover, in the "API Header & Key", you'd need to put "X-Chroma-Token" as the header and the value you have inside .env `CHROMA_SERVER_AUTHN_CREDENTIALS` as the value.

To learn how to use VectorAdmin, visit the [docs](https://github.com/Mintplex-Labs/vector-admin).

## Support and feedback 👷‍♀️

In order of preference the best way to communicate with us:

- **GitHub Discussions**: Contribute ideas, support requests and report bugs (preferred as there is a static & permanent for other community members).
- **Slack**: community support. Click [here](https://vespper.com/#community) to join.
- **Privately**: contact at support@vespper.com

## Contributing to Vespper ⛑️

If you're interested in contributing to Vespper, checkout our [`CONTRIBUTING.md`](https://github.com/vespperhq/vespper/blob/main/CONTRIBUTING.md) file 💫 🧙‍♂️

## Troubleshooting ⚒️

If you encounter any problems/errors/issues with Vespper, checkout our [troubleshooting guide](https://github.com/vespperhq/vespper/tree/main/TROUBLESHOOTING.md). We try to update it regularly, and fix some of the urgent problems there as soon as possible.

Moreover, feel free to reach out to us at our [support channels](#support-and-feedback-️).

## Telemetry 🔢

By default, Vespper automatically sends basic usage statistics from self-hosted instances to our server via PostHog.

This allows us to:

- Understand how Vespper is used so we can improve it.
- Track overall usage for internal purposes and external reporting, such as for fundraising.

Rest assured, the data collected is not shared with third parties and does not include any sensitive information. We aim to be transparent, and you can review the specific data we collect [here](https://github.com/vespperhq/vespper/blob/main/services/api/src/telemetry/listener.ts).

If you prefer not to participate, you can easily opt-out by setting `TELEMETRY_ENABLED=false` inside your `.env`.

## License 📃

This project is licensed under the Apache 2.0 license - see the [LICENSE](https://github.com/vespperhq/vespper/tree/main/LICENSE.md) file for details

## Learn more 🔍

Check out the official website at https://vespper.com for more information.

## Contributors ✨

Built with ❤️ by Dudu & Topaz

Dudu: [Github](https://github.com/david1542), [Twitter](https://twitter.com/DavidLasry17164)

Topaz: [Github](https://github.com/topaztee), [Twitter](https://twitter.com/topaz_tee)
