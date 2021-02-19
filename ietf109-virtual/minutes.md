# IPPM IETF 109
When: Monday 16 November 2020, 5:00-7:00 UTC

## Working Group Documents

draft-ietf-ippm-stamp-yang has passed last discuss, now with RFC Editor.

Frank Brockners describes updates to IOAM drafts

### IOAM Flags I-D

Tal Mizrahi talks about updates to the IOAM Flags I-D.  Wants to proceed to WGLC.

- Greg Mirsky: How is IOAM different from direct export option?
- Loopback is used by data plane path, so result is reported to originating node. Loopback is intended to trace path, whereas direct export is intended to be used by management plane.
- But destination of an exported packet can be the originating node, so it looks like loopback is a special case of direct export.
- You could implement loopback by direct export, but result will be slightly different.
- Direct export works on each node in the path.
- Yes, but loopback returns a result for each one with a single packet.
- Would like to clarify before moving forward.

- Martin Duke: Concerned about multiple namespaces causing loops, in both this and direct export. Will take that to the list, as it is hard to explain verbally.

- Mirja: Still worried about the amplification attack (one packet solicits many), and think that needs some mitigation (rate limiting?).
- Draft points out problem exists, requires a single data field in loopback packets to reduce amplification potential, discusses rate limiting.
- Serious issue, though, needs more consideration due to magnitude of amplification possible.

### IOAM Direct Export draft

(Tal does this presentation as well.)

- Discuss open issues. Hop count.
- Another open issue: DEX option length.

- Frank: Second option came from design team, as a clean solution, similar to existing mechanism.
- Mirja (Jabber): suggest option 2, as the option itself is an extensibility mechanism.
- Greg Mirsky: I want to contribute as well...
- Hauyou Song -- tech difficulties, could not hear him
- Tommy Pauly: Let's move on in interest of time

## Open Calls for Adoption

### SRPM-related updates to TWAMP and STAMP

Rakesh Gandhi presents. The two presentations are combined, as the drafts are "very similar."

- GM: slide 3 of the first presentation (TWAMP).
    - Disagrees with requirement stated on the slide.
    - Direct-mode Loss Measurement is useful, but you propose two diff. solutions for one problem.
    - You did not respond to my comments on ML, look forward to hearing responses.  (Let's continue discussion on ML)
- Rakesh Gandhi: I have responded...
- MD: Trying to understand the motivation for this work.  IIUC, something is counting losses -=- is that correct?  
- Rakesh: Already have TWAMP-like machinery that collects timestamps.  (Scribe: this is a bit tough to follow)
- MD: Flesh out introduction to this document a bit more.
- Tommy Pauly: this is cross-listed in two WG (the other is SPRING)
- GM: These I-Ds define a new protocol.  Should be viewed as new protocol that does only one thing.

### Connectivity Monitoring

Ruediger Geib presenting.  Pretty diagrams on slide 2.  "I don't want to go into too much detail."  Discuss "temporal resolution of event detection."

- GM: is scale of seconds or hundreds of milliseconds too long a scale?  (Some back-of-envelope calc. follows)  Local switchiover and reroute and $something does not notice.
- Ruediger: I am not sure...  Depends on what you want to measure.

### IOAM Conf State

Xiao Min presents

- Martin: Does every echo request generate multiple echo replies?
- Can use TTL to cause each request to generate one reply.
- Ah, no amplification. Is the intent to determine common capabilities on the path? Could we not send a message with all capabilities and have each hop eliminate the ones it does not support?
- One of the scenarios is that, but another is to simply learn the capabilities of each node, which is useful in other scenarios.
- Frank: Basically this is adding management capability to ICMP and other echo-request protocols. Why? It could be done with Netconf YANG. And, is IPPM the right place to do this.
- Intent is for IOAM encap node to discover capabilities so it can construct IOAM headers, rather than as a management protocol. This is IOAM specific, so belongs in IPPM. Asked for guidance.

### YANG Data Model

- Will go to list with adoption steps.

## Proposed Work

### Hybrid Two-step

Greg Mirsky presents

- Mirja: Wondering if this is in scope for IPPM, as it seems to be a protocol rather than a metric or model.
- Greg: Not that different from Direct Export method. For chairs and AD to decide, but appreciate advice as to where to take this.
- Tommy Pauly: Also, we need to be sure we don't duplicate work.

### Explicit Flow Measurements

Mauro Cociglio presents

- Ian Swett: thanks for merging the drafts, this is pretty interesting work.
- Tommy Pauly: this is one we'd like to consider for adoption.

## Lightning Talks

- Not presented due to lack of time, but slides are available.
