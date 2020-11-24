# in-browser-auction-publisher-issues

Summary and links to web publisher considerations for in-browser ad placements


# Introduction

A significant number of issues have been raised about how to make
TURTLEDOVE (and other related bird-themed proposals for in-browser ad
auctions) work for marketers, but little has been discussed about how
this can work for publishers. We have identified a number of potential
issues in TURTLEDOVE that would have a significant negative impact on
publishers\' businesses unless they were resolved.

This document covers ad placement. We plan to create a
similar document around reporting issues from the Privacy Sandbox
proposals and how they impact publishers\' businesses. 

These issues also present problems for users, who are likely to
experience problems with exposure to malware or otherwise harmful or
undesirable ads, and a lower-quality experience as more ads are able to
game the system and fail to support high-engagement publisher
properties.

This document refers to a "web property" and not a site, to recognize
that the set of locations with common data stewardship and advertising
management may not necessarily be a "site" as defined in web standards.
A web property may span multiple subdomains, registerable domains and
schemas. (We suggest the use of this term as we agree with [a recent
suggestion that the distinctions among the terms "first party" and
"third party" are not easily understood by web users and developers](https://tess.oconnor.cx/2020/10/parties).)

# Existing related issues

We will update this document with links to relevant issues.  Two general issues
that have raised related points are:

 * [Capabilities of the proposal for publishers · Issue #51 · WICG/turtledove](https://github.com/WICG/turtledove/issues/51)

 * [TurtleDove: Ambiguity in level of decision making. · Issue #73 · WICG/turtledove](https://github.com/WICG/turtledove/issues/73)


# Publisher use cases

This document will cover key publisher use cases that will need to be 
handled by TURTLEDOVE or other browser-based ad placement
proposals. Gatekeeper variants (e.g., SPARROW) do seem to handle at
least some of these issues currently.

The current TURTLEDOVE architecture allows for the browser to decide
which ad wins a specific auction based on a rank value that each ad has
associated with it. That rank may be modified, but the mechanisms for
that are currently unspecified. There are several publisher use cases
that are clearly not yet supported:

1.  Publishers need to be able to control which ads, including
    interest-group-based ads, appear on their web
    properties.  Publishers want to control what content appears
    on their web property for multiple reasons:

    1.  Ad quality/publisher-determined brand safety rules - there are many
        categories of content or specific advertising brands, categories of
        advertising brands, or specific ads that a given publisher would not
        want to appear on their site. (Related issue: [Capabilities of the proposal for publishers · Issue #51 · WICG/turtledove](https://github.com/WICG/turtledove/issues/51))

    2.  Malvertising - Some ads may contain (or link to) malware. If this
        isn\'t detected prior to a bundle being delivered to the browser,
        publishers need a mechanism to block malware from being served to
        their sites' users and to take appropriate action against the source
        of the malware.

        1.  In the event that a malvertising campaign is discovered, publishers
            require mechanisms to block an ad from appearing on their sites.

        2.  Publishers use third-party malvertising detection services to
            prevent malvertising from serving to their users.

        3.  In the event that an ad server or DSP is compromised and may have
            served malware, the blocking needs to apply to bundles that may
            already have been cached. This could involve the publisher or a
            third-party service.

    3.  Pausing advertising. - Marketers sometimes choose to rapidly pause
        their ads in all media after an adverse news event such as an
        airplane crash. Publishers of any web property on which the marketer's ad
	might appear will need to support this.

2.  Publishers need to be able to fulfill directly sold ad
    placements. Many
    publishers often secure higher-revenue advertising based on the
    ability to deliver guaranteed impressions. Publishers need to
    balance short term optimization of revenue with longer-term
    strategic client relationships, which means serving lower priced ads
    ahead of higher priced ads in certain cases. Being able to control
    this without a time delay is critical to publishers meeting their
    contractual and strategic goals.  Publishers can currently make
    direct and RTB work together using a variety of techniques.

    1.  The highest bid should not always win. Publishers need the
        flexibility to be able to optimize their revenue and strategic goals
        by controlling which ads are delivered for given placements, which
        rely on configurable rules that compare direct sold ads, and
        indirect sold ads, regardless of why the marketer wants to engage a
        particular end user (e.g., contextual or interest-based targeting)
        Example rules include only overriding a guaranteed placement if it
        is over a target bid. The target amount may change over time. Related issue: [Publisher ad network control over ad eligibility and auction ranking · Issue #70 · WICG/turtledove](https://github.com/WICG/turtledove/issues/70)

        1.  For example, the Google Ad Manager "dynamic allocation" feature (if
            a direct deal is pacing correctly, complete at original price, if
            pacing falls behind then increase bid CPM to win more often. If the
            direct deal is pacing ahead, then cut the bid)

        2.  Direct deals that are pacing behind need to compete in the
            TURTLEDOVE auction at a higher effective price, and those that are
            pacing ahead need to compete at a lower price. The changes
            publishers make to rule sets must be immediately applied by
            TURTLEDOVE auctions.

3.  Publishers need to set floor rates based on several criteria. (Related issue: [Capabilities of the proposal for publishers · Issue #51 · WICG/turtledove](https://github.com/WICG/turtledove/issues/51))

    1.  A publisher may not want an ad to serve at all, if it is below a
        minimum \"floor\" set for that page, section, or site.

    2.  A publisher may not want an ad from a certain brand,
        vertical or campaign unless it is above a minimum floor set for that
        brand, vertical, or campaign.

        1.  For example, a publisher may set a "floor for automotive"

        2.  Publishers choose to protect their direct sales business, by not
            allowing marketers to undercut their pricing via indirect sales
            channel on the open market.

4.  Publishers need to honor contractual terms preventing competitors
    from appearing together. If the contextual system serves an ad for one brand in one slot on
    the page, the decision process in other ad slots needs to know not
    to serve direct competitor ads. The publisher needs to control which
    brands are considered competitors. (For example, Amazon.com might be
    blocked as a direct competitor of a local bookstore ad on a book
    review site, while an IT site might not block Amazon.com for competing with a
    database ad.)

5.  The bid price set by the marketer is not necessarily the price at
    which it should compete in the auction. Publishers need to
    apply their own weighted prices, not necessarily the bid price. The
    \"price\" of a given ad is assigned by the buyer, but that price may
    not be what the publisher gets paid. In this case the publisher
    needs to apply an adjustment for auction purposes. Adjustment must
    be applied by the publisher in a 1st-party context. (Related issue: [Ad Pricing · Issue #14 · WICG/turtledove](https://github.com/WICG/turtledove/issues/14)) 

    1.  VAST errors: If a given ad is known to have VAST errors 20% of the
        time (e.g., does not serve) then it needs to have its bid price
        reduced by 20%, by the publisher.

    2.  Post-bid brand safety blocking: If a given buyer has brand-safety
        controls that prevent an ad from serving on a page, the publisher
        ultimately does not get paid. Publishers can currently adjust for
        this by reducing the effective bids for impressions from a given
        buyer (e.g., if some ads serve, but others do not).

    3.  Reporting discrepancies: For many reasons, buyer and seller
        reporting (and third parties) does not match, and publishers need to
        be able to reduce (or increase) the bid price based on those
        discrepancies to ensure the ads compete at a price that is equal to
        what the publisher actually gets paid.

6.  Publishers need to comply with regulatory requirements.

    1.  For example, COPPA compliance in the US might forbid a certain
        interest-group ad from being served on a given page.

    2.  Even if machine learning can classify underage drinkers into a
        cohort with legal age drinkers, they still can't get alcohol ads.
        How would a site signal to the auction that this given user is not
        eligible for alcohol ads?


## Conclusion: why we believe these needs are necessary for a viable replacement to existing cross-publisher IDs

The goal of improving advertising must ensure publishers are not
negatively impacted by new W3C standards as this would have a negative
impact on the availability, diversity, quality or publisher web content
and services. If browser APIs interferes or disproportionately impacts
publisher ability to compete against larger rivals, then web
publishers are likely to avoid support for in-browser ad placement
proposals.


## References

[Parties and browsers](https://tess.oconnor.cx/2020/10/parties)

[WICG/turtledove: TURTLEDOVE](https://github.com/WICG/turtledove)
