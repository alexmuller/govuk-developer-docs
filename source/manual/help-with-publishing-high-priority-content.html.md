---
owner_slack: "#govuk-developers"
title: Help with publishing high priority content
section: Publishing
layout: manual_layout
parent: "/manual.html"
last_reviewed_on: 2018-09-19
review_in: 6 months
---

When a department is publishing content that is high priority, it may be
necessary to intervene to ensure it goes out as smoothly as possible.

### [If documents are published and links aren't updated][links]

You might see this happening if the format is still showing as "Coming Soon"
on some pages.

[links]: documents-are-published-but-links-arent-updated.html

### [If the cache (our Varnish or Fastly CDN) needs clearing][cache]

You may need to do this if the content is not showing on the live site quick
enough.

[cache]: cache-flush.html

### [If guidance pages are expected to show on taxon pages but aren't][search]

The guidance pages visible on topic pages like
[/government/brexit](https://www.gov.uk/government/brexit) are populated based
on search ranking, which is only updated over night, so it may be necessary to
set it manually.

[search]: manually-setting-search-popularity-of-content.html
