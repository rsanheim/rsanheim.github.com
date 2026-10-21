---
layout: resume
meta_title: Rob Sanheim's Resume
title: Resume
---

[Rob Sanheim](mailto:rsanheim@gmail.com) is a software engineer with over 20 years of experience building products, scaling platforms, and improving developer workflows. He has led teams in building key components at scale for companies as diverse as GitHub, Bold Penguin, Simple.org, and Cognitect. He loves working with small teams of passionate people to build high-quality, sustainable software that puts the human experience front and center.

<h4 class="work-experience">Work Experience</h4>

## [Doximity](https://doximity.com) &middot; Software Engineer &middot; 2024 - current

Technical leader for core platform messaging team.

- Re-architected internal data update batch processing around Redis and internal Kafka pipeline, relieving MySQL saturation and allowing the service to scale from 1-2M operations a day to 30-50M a day. 
- Modernized the core monolith from Rails 6.1 to 8 through incremental, dual-boot rollouts. Upgraded Ruby and enabled YJIT, improving latency on heavily used production endpoints by 10-15%.
- Built an internal CLI to simplify local development, deployments, CI, and agentic development. Automated prerelease and application update workflows used across 12 repositories.

## [Monograph](https://monograph.com) &middot; Staff Software Engineer &middot; 2022 - 2023

Staff engineer for a practice management app for Architecture & Engineering firms.

- Improved developer experience during a time of rapid growth. Reduced local setup time from multiple days to 1-3 hours via automation and scripting.
- Overhauled build pipeline, reducing CI time from 25+ mins to 4-5 mins via parallel testing and moving to a more capable platform.
- Built new `Cell` domain layer and schema for timesheet entries, a core component of the app. Reduced P90 response time for several key reports, as well as simplifying reporting complexity. Paired and led eng-wide sessions to ease transition to new approach.
- Integrated Datadog for APM, alerts, and centralized logging. Mentored teammates on how to best use Datadog in day to day work.
  - Upgraded core monolith to Rails 7 and Ruby 3.2 w/ YJIT using dual boot approach
  - Automated and documented PostgreSQL upgrade process, moving from v10 to 14

## [Simple.org](https://simple.org) &middot; Principal Software Engineer &middot; 2020 - 2022

<small>_note: Simple.org is open source, so links below go to the underlying pull requests_</small>

Lead engineer on a large scale, open-source hypertension management system serving over 1.2 million patients in India, Bangladesh, and Ethiopia.

- Re-architected reporting system to simplify and consolidate API, improve performance, and lower cost of changes. [[1]](https://github.com/simpledotorg/simple-server/pull/2436) [[2]](https://github.com/simpledotorg/simple-server/pull/3007).
- Improved traceability and observability by integrating Datadog, [centralized JSON logging](https://github.com/simpledotorg/simple-server/pull/1367) and StatsD integration.
- Led efforts to grow [continuous delivery](https://github.com/simpledotorg/simple-server/pull/2605) culture, via tech-talks, mentoring, and setting up tools and processes. 
- [Rebuilt seed generation strategy](https://github.com/simpledotorg/simple-server/pull/1039) for safety and performance: reduced time to produce prod-sized seed data by 5-10x

## [Bold Penguin](https://boldpenguin.com) &middot; Staff Software Engineer &middot; 2019 - 2020

- Built webhooks system to send insurance application updates in real-time to partners
- Reworked main Rails test suite from hand-built mocks to simplified fixtures; dramatically improving developer experience and ease of testing
- End-to-end automated test suite to increase confidence across the four core microservices

## [First Leads](https://news.remax.com/exclusive-to-remax-the-first-app-one-of-the-best-tools-in-real-estate) - VP of Technology - 2018 - 2019

Leader of the product engineering organization. Moved the team to continuous delivery via chat ops, increasing deployments ~20x a day with greater reliability and transparency. Lead application engineer for multiple product initiatives, including:

- User on-boarding overhaul, rebuilt signup as automated Chargebee workflow
- Dynamic content campaigns to serve the front page of mobile app
- In-place, dual boot system for Rails app to allow incremental upgrade to Rails 5/6
- Mentored other developers via pair programming, presentations, and code review

## [NationBuilder](https://nationbuilder.com) &middot; Lead Software Engineer &middot; 2017 - 2018

Team lead on SSL automation project - helping to setup and monitor SSL certification for over 10,000 customer subdomains. Lead on payments overhaul, which rewrote and consolidated billing code onto Stripe Connect platform.

## [GitHub](https://github.com) &middot; Senior Software Engineer &middot; 2012 - 2017

Senior engineer and team lead at GitHub.com. Instrumental in shipping the following features:

**[Pull Request Reviews](https://github.com/blog/2256-a-whole-new-github-universe-announcing-new-tools-forums-and-features#code-better-with-reviews)**

Leader on a team dedicated to overhauling code review at GitHub. He worked closely with colleagues to architect and build the new code review system now in use at GitHub. This included back end modeling and engineering, overhauling the front end to support a new conversation threading system, and tying the entire system into the Protected Branches feature on GitHub.

**[Protected Branches](https://github.com/blog/2051-protected-branches-and-required-status-checks)**

Core member of the team that shipped the first version of this highly requested feature. Worked on the backend, frontend, and in crafting and focusing the product vision to make sure we shipped something great.

**Rails 3.2 Upgrade**

Led effort in developing project plan, getting buy-in from colleagues on this huge undertaking; shepherded the system through a long, careful production rollout.

**Other key contributions**

Primary server developer for features such as [team mentions](https://github.com/blog/1121-introducing-team-mentions), [commit status API](https://github.com/blog/1227-commit-status-api), [email verification](https://github.com/blog/1215-email-verification), and [live updates](https://github.com/blog/1174-auto-updating-comments). Rob also helped improve team processes continually at GitHub, by initiating and leading retrospectives, increased pair-programming, or general changes to day to day process to tighten feedback loops.

## [Relevance, Inc / Cognitect](http://cognitect.com/) &middot; Principal &middot; 2007 - 2012

Rob was employee number five at Relevance, and was a key leader in helping Relevance become a leading Ruby on Rails consultancy.

- Converted Relevance to Git & Github in 2008, migrating away from SVN
- Led conversion to pull request workflow for collaboration and code review
- Led projects across all roles: project manager, architect, lead developer, and client liaison
- Brings a "calming, experienced" leadership role to projects assigned
- Wide range of successful client projects, including [Plotwatt](https://plotwatt.com/), [CXO](http://vivisimo.com/solutions/cxo.html), and [Contegix Cloud](https://classic.contegix.com/session/new).

## [Seeking Alpha](http://seekingalpha.com/) &middot; Software Engineer &middot; 2006 - 2007

Senior Ruby developer for a successful financial blog platform. Responsible for overhauling PHP platform into new Rails
platform. Ensure scalability for features and ensuring scalability for upwards of 70,000 visitors a day. Built user generated content feature to build community and enhance content model. Set up continuous integration and devops automation.

## [Sanheim Software](https://rsanheim.com) &middot; Founder &middot; 2005 - current

Consulting and custom application development for several startups.

#### Earlier Experience

- Smart Solutions - Consultant - 2005 - 2006
- Brown Shoe - Programmer Analyst - 2001 - 2005
- Wm. K. Walthers - Production Specialist 1996 - 1999

#### Technologies

Ansible, AWS, CSS (SCSS / SASS), Elasticsearch, Git, Go, GraphQL, Java, Javascript, Kafka, Karafka, Memcached, MySQL, PostgreSQL, Puppet, Ruby, Ruby on Rails, Redis, Resque, RSpec, Sidekiq, Sinatra, Unicorn, and many others

#### Community & presentations

Rob has presented at many conferences and user groups, including RubyConf, Ruby Kaigi, and RailsConf. He has contributed to many open source projects over the years, including Rails, RSpec, and Rcov. Editor of Ajaxian.com from 2005 to 2006, and co-founder of the Madison Ruby user group.

#### Education

UW Whitewater - B.S., Management Computer Systems 2001

#### Contact

email: [rsanheim@gmail.com](mailto:rsanheim@gmail.com) &middot; web: [rsanheim.com](https://rsanheim.com) &middot; GitHub: [@rsanheim](https://github.com/rsanheim)
