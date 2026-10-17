Basics of Shell scripting 


Hi Team,

We would like to reiterate the expected BAU behaviour during ET maintenance activities, particularly over weekends.

As you are aware, the ET vendor performs maintenance activities periodically, during which the ET Trapeze adapter may be temporarily unavailable. Consequently, rate requests routed from the channels to ET through Kong may not receive a rate from ET. This is an expected scenario during maintenance and does not, by itself, indicate an application or channel issue.

The existing fallback mechanism is designed to handle precisely this situation:

1. The channel sends the rate request to ET through Kong.
2. If ET is unavailable, the channel receives the corresponding error/return code.
3. Based on this response, the channel invokes the fallback mechanism and obtains the applicable board rate from Hub, sourced through UREX.
4. The transaction proceeds using the fallback rate.

Our observations confirm that this mechanism is functioning as expected, with no channel-side transaction failures attributable to these ET maintenance windows.

Given that the ET vendor performs such maintenance periodically and the fallback mechanism is already in place, it is neither practical nor necessary to circulate individual maintenance notifications to all channels and stakeholders for every occurrence, provided the existing fallback process continues to function as designed. Repeated escalations for expected ET unavailability, when transactions are successfully handled through Hub fallback rates, create unnecessary concern and involve multiple teams without requiring further intervention.

Accordingly, ET unavailability during planned maintenance should be treated as a known BAU scenario rather than an incident, provided the fallback mechanism is working and transactions are processing successfully. Escalation would be warranted if the fallback itself fails, transactions are impacted, or the observed behaviour deviates from the expected flow.

We trust this clarifies the process and request that this understanding be followed during future maintenance windows to avoid unnecessary escalations.

If any further clarification is required, we can arrange a call on Sunday to walk through the end-to-end flow.
