# Reporting use cases

Currently, web site owners who fund their business with advertising can get accurate impression and revenue reporting with a high granularity (e.g., across many dimensions) in near-real time (e.g., under 15 minutes of delay). This information supports numerous use cases, such as financial reporting, A/B testing of potential enhancements, QA of code deployments, monitoring of partner performance and more. If browsers reduce access to the granular information available to web publishers, this will degrade their ability to operate their business. It is difficult to exactly articulate what degradations are acceptable and by what quantity.

As stated in the TURTLEDOVE documentation, "the essential operation of knowing how much money … each publisher receives" is critical to web publishers.  It is indeed essential for a publisher to understand, at a very granular level, how much money they are making (and many other data points). Advertising is core (or a primary) part of most web publishers’ business, they need this granular revenue information in a timely fashion. 

The existing Privacy Sandbox documentation about reporting focuses on aggregated reporting across domains and/or across advertisers. Since a publisher controls their domains, it isn't clear if these restrictions are (or even should be) applicable to publishers. , It's also not clear how an ad served in a fenced frame would deliver any information back to the publisher that isn't aggregated to the same degree as provided to other stakeholders.

At a basic level:

1. Publishers need to know how much they are earning from each ad placement, in specific geographies, across different timeframes, by advertiser and vertical, by ad size/type, by device, and other dimensions important to funding and optimizing the web experience they provide to their visitors.
   1. Revenue needs to be reported at frequent (intra-hour) intervals
   2. No noise can be added to the counts associated with delivery. Publishers have contractual obligations to deliver exact reports and need to know exact revenue amounts.
   3. Publishers need to cross-check and reconcile data provided by and to multiple partner companies, and to receive correct payment even in the event of an error by one partner company.
2. Publishers need to be able to develop and test changes to their sites, including fixing or rolling back any change that causes a problem with web experiences or ad reporting. Publishers need to evaluate changes across many dimensions quickly to find potential issues. Publishers need to be able to confirm that in-browser auctions are indeed functioning as intended.
   1. Because of the variety of browsers and limited testing resources, many errors are only visible in production. Reporting needs to be rapid enough to maintain a practical cycle of site enhancement and deployment.
   2. Publishers need to be able to run reports on site changes within minutes, so as not have to wait multiple cycles for the information to be usable
   3. In the event of a bug in a new browser version that breaks reporting, publishers need to be able to report the bug and begin a workaround.
3. Publishers need to be able to A/B test a variety of experiments with site code, design, and selection of ad partner companies.
   1. Publishers need to be able to get very precise measurements, relatively quickly, to see which experiments are most valuable.
   2. Publishers need to be able to evaluate alternative services by testing with a fraction of a site’s traffic.
   3. Any noise introduced into reporting must not limit the usability of reported data. A level of noise that would be acceptable for a large national publisher could be prohibitive for a small or niche publisher--or limit the applicability of sophisticated experimental design to only high-traffic sites.
4. Publishers need proof of the delivery or non-delivery of ads by advertiser, category or other dimensions
   1. For brand safety purposes, publishers need to be able to show a credible report showing that a particular problematic ad never appeared on a site, or that an ad did not appear after a user complaint was received and acted on.

Publishers seek to constantly improve their sites and to avoid lock-in, whether to a set of obsolete code and layouts, or to a set of incumbent business partners and models. Accurate reporting is necessary for a site to grow and evolve, and to protect or increase revenue and other metrics. Without accurate and timely reporting, publishers won't use the privacy sandbox, and instead rely purely on contextual and first-party advertising placements (where reporting remains accurate and timely), defeating the purpose of building out this new platform.

[Up to main README](README.md)
