---
layout: resume
meta_title: Rob Sanheim's Resume
title: Resume
---

[Rob Sanheim](mailto:rsanheim@gmail.com) is a software engineer with over 20 years of experience building products, scaling platforms, and improving developer workflows. He has led teams in building key components at scale for companies as diverse as GitHub, Bold Penguin, Simple.org, and Cognitect. He loves working with small teams of passionate people to build high-quality, sustainable software that puts the human experience front and center.

<h4 class="work-experience">Work Experience</h4>

## [Doximity](https://doximity.com) &middot; Software Engineer &middot; 2024 - current

Technical leader on the core platform messaging team.

- Re-architected internal batch data-update processing around Redis and an internal Kafka pipeline, relieving MySQL saturation and allowing the service to scale from 1–2M to 30–50M operations per day.
- Modernized the core monolith from Rails 6.1 to 8 through incremental, dual-boot rollouts. Upgraded Ruby and enabled YJIT, improving latency on heavily used production endpoints by 10–15%.
- Built an internal CLI to simplify local development, deployments, CI, and agentic development. Automated prerelease and application update workflows used across 12 repositories.

## [Monograph](https://monograph.com) &middot; Staff Software Engineer &middot; 2022 - 2023

Staff engineer for a practice management app for architecture and engineering firms.

- Improved developer experience during a time of rapid growth. Reduced local setup time from multiple days to 1–3 hours via automation and scripting.
- Overhauled the build pipeline, reducing CI time from 25+ minutes to 4–5 minutes through parallel testing and a move to a more capable platform.
- Built a new `Cell` domain layer and schema for timesheet entries, a core component of the app. Reduced P90 response times for several key reports while simplifying reporting. Paired with teammates and led engineering-wide sessions to ease the transition to the new approach.
- Integrated Datadog for APM, alerts, and centralized logging. Mentored teammates on using Datadog in day-to-day work.
- Upgraded the core monolith to Rails 7 and Ruby 3.2 with YJIT using a dual-boot approach.
- Automated PostgreSQL upgrade process, moving from version 10 to 14.

## [Simple.org](https://simple.org) &middot; Principal Software Engineer &middot; 2020 - 2022

<small>_Note: Simple.org is open source, so the links below go to the underlying pull requests._</small>

Lead engineer on a large-scale, open-source hypertension management system serving over 1.2 million patients in India, Bangladesh, and Ethiopia.

- Built a unified [Regions domain model](https://github.com/simpledotorg/simple-server/pull/1381) to replace incompatible geographic models, simplifying patient-data access, API sync, and reporting.
- Re-architected the reporting system to simplify the API, improve performance, and reduce defects. [[1]](https://github.com/simpledotorg/simple-server/pull/2436) [[2]](https://github.com/simpledotorg/simple-server/pull/3007).
- Improved traceability and observability by integrating Datadog, [centralized JSON logging](https://github.com/simpledotorg/simple-server/pull/1367), and StatsD.
- Led efforts to grow a [continuous delivery](https://github.com/simpledotorg/simple-server/pull/2605) culture through tech talks, mentoring, and establishing tools and processes.
- [Rebuilt the seed generation strategy](https://github.com/simpledotorg/simple-server/pull/1039) for safety and performance, generating production-sized seed data 5–10× faster.

## [Bold Penguin](https://boldpenguin.com) &middot; Staff Software Engineer &middot; 2019 - 2020

- Built a webhooks system to send insurance application updates to partners in real time.
- Reworked the main Rails test suite from hand-built mocks to simplified fixtures, dramatically improving developer experience and ease of testing.
- Created an end-to-end automated test suite to increase confidence across the four core microservices.

## [First Leads](https://news.remax.com/exclusive-to-remax-the-first-app-one-of-the-best-tools-in-real-estate) &middot; VP of Technology &middot; 2018 - 2019

Leader of the product engineering organization. Moved the team to continuous delivery via chat ops, increasing deployment frequency to approximately 20 per day with greater reliability and transparency. Lead application engineer for multiple product initiatives, including:

- Overhauled user onboarding, rebuilding signup as an automated Chargebee workflow.
- Built dynamic content campaigns for the mobile app's front page.
- Built an in-place, dual-boot system for the Rails app to allow incremental upgrades to Rails 5 and 6.
- Mentored other developers through pair programming, presentations, and code review.

## [NationBuilder](https://nationbuilder.com) &middot; Lead Software Engineer &middot; 2017 - 2018

Team lead on an SSL automation project, helping to set up and monitor SSL certificates for over 10,000 customer subdomains. Led a payments overhaul that rewrote and consolidated billing code onto the Stripe Connect platform.

## [GitHub](https://github.com) &middot; Senior Software Engineer &middot; 2012 - 2017

Senior engineer and team lead at GitHub.com. Instrumental in shipping the following features:

### [Pull Request Reviews](https://github.com/blog/2256-a-whole-new-github-universe-announcing-new-tools-forums-and-features#code-better-with-reviews)

Leader on a team dedicated to overhauling code review at GitHub. He worked closely with colleagues to architect and build the new code review system. This included backend modeling and engineering, overhauling the frontend to support a new conversation threading system, and integrating the system with Protected Branches.

### [Protected Branches](https://github.com/blog/2051-protected-branches-and-required-status-checks)

Core member of the team that shipped the first version of this highly requested feature. Worked on the backend and frontend, and helped craft and focus the product vision to make sure we shipped something great.

### Rails 3.2 Upgrade

Led the project planning effort and secured buy-in from colleagues for this huge undertaking; shepherded the system through a long, careful production rollout.

### Other key contributions

Primary developer for features such as [team mentions](https://github.com/blog/1121-introducing-team-mentions), the [commit status API](https://github.com/blog/1227-commit-status-api), [email verification](https://github.com/blog/1215-email-verification), and the first version of [live updates](https://github.com/blog/1174-auto-updating-comments). Also improved team processes through retrospectives, pair programming, and continuous testing.

## [Relevance, Inc / Cognitect](http://cognitect.com/) &middot; Principal &middot; 2007 - 2012

Rob was employee number five at Relevance and a key leader in helping it become a leading Ruby on Rails consultancy.

- Converted Relevance to Git and GitHub in 2008, migrating away from SVN.
- Led the conversion to a pull request workflow for collaboration and code review.
- Led projects in roles including project manager, architect, lead developer, and client liaison.
- Brought a "calming, experienced" leadership style to projects.
- Worked on a wide range of successful client projects, including [Plotwatt](https://plotwatt.com/), [CXO](http://vivisimo.com/solutions/cxo.html), and [Contegix Cloud](https://contegix.com/).

## [Seeking Alpha](http://seekingalpha.com/) &middot; Software Engineer &middot; 2006 - 2007

Senior Ruby developer for a successful financial blog platform. Responsible for migrating the PHP platform to Rails and scaling it to support upwards of 70,000 visitors a day. Built a user-generated content feature to build community and enhance the content model. Set up continuous integration and DevOps automation.

## [Sanheim Software](https://rsanheim.com) &middot; Founder &middot; 2005 - current

Consulting and custom application development for several startups.

#### Technologies

Ansible, CSS (SCSS / Sass), Elasticsearch, Git, Go, GraphQL, JavaScript, Kafka, Karafka, Memcached, MySQL, PostgreSQL, Ruby, Ruby on Rails, Redis, Resque, RSpec, Rust, Sidekiq, Typescript, Unicorn, and many others.

#### Community & presentations

Rob has presented at many conferences and user groups, including RubyConf, RubyKaigi, and RailsConf. He has contributed to many open-source projects over the years, including Rails, RSpec, and Rcov. He was an editor of Ajaxian.com from 2005 to 2006 and co-founder of the Madison Ruby user group.

#### Education

UW–Whitewater — B.S., Management Computer Systems, 2001

#### Contact

email: [rsanheim@gmail.com](mailto:rsanheim@gmail.com) &middot; web: [rsanheim.com](https://rsanheim.com) &middot; GitHub: [@rsanheim](https://github.com/rsanheim)
