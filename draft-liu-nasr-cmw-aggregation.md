---
title: Conceptual Message Wrapper Aggregation
abbrev: cmw aggregation
category: info

docname: draft-liu-nasr-cmw-aggregation-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Security"
workgroup: "Network Attestation for Secure Routing"
keyword:
 - next generation
 - unicorn
 - sparkling distributed ledger
venue:
  group: "Network Attestation for Secure Routing"
  type: "Working Group"
  mail: "nasr@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/nasr"
  github: "liuchunchi/cmw-aggregation"
  latest: "https://liuchunchi.github.io/cmw-aggregation/draft-liu-nasr-cmw-aggregation.html"

author:
 -
    fullname: Peter Chunchi Liu
    organization: Huawei
    email: liuchunchi@huawei.com

normative:

informative:


--- abstract

TODO Abstract


--- middle

# Introduction

Conceptual Messages Wrapper (CMW) {{?draft-ietf-rats-msg-wrap-11}} provides a type of encapsulation format that can be used for any RATS messages, such as Evidence, Attestation Results, Endorsements, and Reference Values.

In NASR, the operator wishes to provide a verifiable proof of security to the orchestrated connectivity service that client requested from him. As a result, the simplest way to acquire the Attestation Results or Evidences (using CMWs) from all devices of a path and aggregate them. This is usually conducted over control plane or controller southbound channels before the service is actually delivered.


# Format Considerations

Entity Attestation Tokens (EATs) permits nesting of EATs. The simplest way is to treat the CMW as a claim and combine them.

~~~~~~~~~~
  {
    "node1": ({<CMW>}),
    "node2": ({<CMW>}),
    ...
  }
~~~~~~~~~~
Collection of CMWs.

Another format is to keep only one set of claims, but the values becomes an array. For example

~~~~~~~~~~
  {
    "claim1": [
      "node1",
      "node2"
    ],
    "claim2": [
      "node1",
      "node2"
    ],
    ...
  }
~~~~~~~~~~

Another format is to process the collected claims according to certain statistical rules, keeping only one value to each claim. The statistical rule is decided by the controller, including for example but not limited to average, medium, min, max.

~~~~~~~~~~
  {
    "claim1": processed_value1,
    "claim2": processed_value2,
    ...
  }
~~~~~~~~~~

# Modes

Different work modes indicates different content a CMW carries. There are 4 cases:

1. Simple Aggregation of Attestation Results
2. Queried Aggregation of Attestation Results
3. Simple Aggregation of Evidences
4. Queried Aggregation of Evidences

# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
