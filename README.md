# LearnLink Platform

LearnLink is an AI-operated education, community, live-class, jobs, and creator-channel platform designed for the Build with Gemini XPRIZE hackathon.

The platform is split into separate repositories so each service can be developed, deployed, and scaled independently.

## Research Motivation

AI-assisted learning platforms need more than content delivery: they need moderation, personalization, community trust, and agentic workflows that can support students and creators safely. LearnLink explores how a modular education platform can provide a foundation for applied AI research in learning support, content moderation, and autonomous educational agents.

## Research Problem

How can a microservice-based learning platform integrate AI agents, moderation workflows, community features, and course/job services while keeping service boundaries clear enough for experimentation and future research?

## Objectives

- Build an AI-ready education platform with independently runnable services.
- Separate frontend, gateway, course, job, community, and agent responsibilities.
- Support moderation-first content workflows for safer community interaction.
- Provide a cloud-ready architecture for future AI agent experiments.
- Keep adapters and infrastructure explicit for reproducible local development.

## Project Contribution

LearnLink contributes a practical reference architecture for AI-assisted education systems. It connects social learning, course discovery, live classes, jobs, creator channels, moderation, and agent services in one platform so future research can test AI behavior inside realistic product workflows rather than isolated demos.

## Research Relevance

This project is relevant to supervisors interested in AI for education, responsible platform moderation, agentic workflow orchestration, and intelligent learning support. The strongest research angle is studying how AI agents can personalize learning, moderate community content, and support platform operations while preserving oversight and service-level accountability.

## System Architecture

LearnLink is organized as a microservice platform with a Next.js frontend, API gateway, domain services for courses, jobs, and community, a Python-based agent service, and infrastructure definitions for local development. Service boundaries are designed to support independent experimentation and deployment.

## Experimental Setup

- Local development uses environment-driven configuration and service-specific ports.
- Community moderation begins with pending content states before visibility.
- Agent services can be run separately to test AI-assisted workflows.
- Infrastructure definitions support repeatable local testing across services.

## Future Research

- Evaluate AI-assisted moderation quality and false-positive rates.
- Add retrieval-augmented tutoring or course recommendation agents.
- Study learner engagement signals and personalized intervention workflows.
- Compare single-agent and multi-agent support patterns in educational platforms.
- Add responsible AI monitoring for moderation and recommendation features.

## Citation

```bibtex
@software{saeed2026learnlink,
  author = {Saeed, Babar},
  title = {LearnLink AI Platform},
  year = {2026},
  url = {https://github.com/Babar860/learnlink}
}
```

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
|-- learnlink-frontend
|-- learnlink-backend-gateway
|-- learnlink-service-community
|-- learnlink-service-courses
|-- learnlink-service-jobs
|-- learnlink-service-agents
`-- learnlink-infra
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

Do not commit real `.env` files. Production setup requires provider credentials for PostgreSQL, JWT, Gemini/Google Cloud, Firebase, SMTP, media hosting, OAuth, and Stripe.

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
