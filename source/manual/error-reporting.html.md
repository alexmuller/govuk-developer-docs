---
title: Error reporting with Sentry
parent: "/manual.html"
layout: manual_layout
section: Monitoring
owner_slack: "#govuk-2ndline"
last_reviewed_on: 2018-04-12
review_in: 6 months
---

We use [Sentry][] to notify us of exceptions that happen in all environments.

We configure Sentry using [govuk-saas-config][]. It reads a list of apps from the docs and makes sure that all configuration is set up correctly.

Use the [govuk_app_config][] gem to configure your application to talk to Sentry.

[Sentry]: https://sentry.io/govuk
[govuk-saas-config]: https://github.com/alphagov/govuk-saas-config
[govuk_app_config]: https://github.com/alphagov/govuk_app_config
