# LearnLink Platform

LearnLink is an AI-operated education, community, live-class, jobs, and creator-channel platform designed for the Build with Gemini XPRIZE hackathon.

The platform is split into separate repositories so each service can be developed, deployed, and scaled independently.

## Repository Map

| Repository | Purpose |
|---|---|
| [learnlink-frontend](https://github.com/Babar860/learnlink-frontend.git) | Next.js UI for the home feed, courses, jobs, community, and admin entry points |
| [learnlink-backend-gateway](https://github.com/Babar860/learnlink-backend-gateway.git) | API gateway, auth/onboarding boundary, Stripe webhook intake, and service routing |
| [learnlink-service-community](https://github.com/Babar860/learnlink-service-community.git) | Communities, channels, follows, subscriptions, user posts, AI moderation, and feed ranking |
| [learnlink-service-courses](https://github.com/Babar860/learnlink-service-courses.git) | Course CRUD, teacher upload, quizzes, live classes, premium key points, and grading |
| [learnlink-service-jobs](https://github.com/Babar860/learnlink-service-jobs.git) | Recruiter job posting, paid activation, job search, applications, and premium seeker features |
| [learnlink-service-agents](https://github.com/Babar860/learnlink-service-agents.git) | FastAPI AI-agent service using Gemini integration points for autonomous platform operations |
| [learnlink-infra](https://github.com/Babar860/learnlink-infra.git) | Docker Compose, PostgreSQL schema, feature flags, Firebase notes, and Stripe architecture notes |

## Architecture

```text
learnlink/
├── learnlink-frontend
├── learnlink-backend-gateway
├── learnlink-service-community
├── learnlink-service-courses
├── learnlink-service-jobs
├── learnlink-service-agents
└── learnlink-infra
```

## Core Platform Capabilities

- Home feed with AI-ranked posts from communities, channels, followed users, and platform-wide posts.
- Fully autonomous AI moderation for all post types before publishing and during scheduled re-analysis.
- Automated channel-creation eligibility based on account age, activity score, profile completeness, and moderation health.
- Course discovery personalized by onboarding answers, resume keywords, and completed learning tracks.
- Teacher course upload with video hosting abstraction and AI quiz conversion.
- Live classes with organization/grade validation, one active device per session, in-class quizzes, premium key points, and paid auto-grading.
- LinkedIn-style jobs service with recruiter paid posting, search, apply, and premium job-seeker features.
- Admin dashboard philosophy: read-only oversight plus agent configuration, not manual approval workflows.

## Tech Stack

- Frontend: Next.js 14 + Tailwind CSS
- Gateway and domain services: Node.js + Express
- Agent service: Python + FastAPI + Gemini integration points
- Database: PostgreSQL
- Payments: Stripe and Stripe Connect
- Notifications: Firebase Cloud Messaging
- Cloud target: Google Cloud Platform

## Local Development Order

1. Start infrastructure from `learnlink-infra`.
2. Start `learnlink-service-agents`.
3. Start domain services: community, courses, jobs.
4. Start `learnlink-backend-gateway`.
5. Start `learnlink-frontend`.

Each service repository includes its own README with service-specific run commands.

## Deployment URLs

- Frontend: https://learnlink-frontend-kappa.vercel.app
- Production gateway: set `NEXT_PUBLIC_GATEWAY_URL` after the public backend URL is deployed.

## Required Environment

The local workspace already has the credentials you shared for PostgreSQL, JWT, Gemini/Google project metadata, Firebase web push, SMTP/Gmail, and Mux configured in the root `.env`. Do not commit the real `.env` file.

Still needed for full production behavior:

- Google OAuth Web Client ID and Client Secret for the login button.
- GitHub OAuth App Client ID and Client Secret for the login button.
- Stripe keys/webhook/connect credentials for paid courses, subscriptions, and payouts.
- SMS provider credentials for teacher class reminders.
- Public backend URL after the gateway is deployed, then set it as `NEXT_PUBLIC_GATEWAY_URL` for Vercel.

Core runtime:

- `DATABASE_URL`
- `JWT_SECRET`
- `GATEWAY_PORT`
- `COMMUNITY_PORT`
- `COURSES_PORT`
- `JOBS_PORT`
- `AGENTS_PORT`
- `ADMIN_EMAIL`
- `ADMIN_PASSWORD`
- `ADMIN_NAME`
- `NEXT_PUBLIC_GATEWAY_URL`

AI and cloud integrations:

- `GEMINI_API_KEY`
- `GOOGLE_CLOUD_PROJECT`
- `GOOGLE_CLOUD_PROJECT_NUMBER`
- `GOOGLE_CLOUD_PROJECT_NAME`
- `FIREBASE_PROJECT_ID`
- `FIREBASE_WEB_PUSH_KEY`
- `FCM_SERVER_KEY`

Messaging and media:

- `SMTP_HOST`
- `SMTP_PORT`
- `SMTP_USER`
- `SMTP_PASSWORD`
- `SMTP_FROM`
- `MUX_TOKEN_ID`
- `MUX_TOKEN_SECRET`

Payments:

- `STRIPE_SECRET_KEY`
- `STRIPE_WEBHOOK_SECRET`
- `STRIPE_CONNECT_CLIENT_ID`
