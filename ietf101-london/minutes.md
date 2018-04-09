
# Main Agenda Minutes

*When:* 15:50 - 18:20 UTC, Tuesday 20 March 2018

*Where:* Richmond/Chelsea/Tower, Hilton Metropole, London

*Chairs:* Brian Trammell and Bill Cerveny (remote)

*Notes:* Roni Even and Chris Wood (?); many thanks!

## Welcome, Note Well, Agenda, Status - B. Trammell

## [draft-ietf-ippm-2330-ipv6][1] - A. Morton

## [draft-ietf-ippm-metric-registry][2] & [draft-ietf-ippm-initial-registry][3] - A. Morton 

New element for handshake; new definition for QUIC as well.

Looking at how TCP heuristics change when looking at a version of QUIC enabled with spin-bit approach. This doesn't get RTT information with each packet, but in number of RTTs.

Brian Trammell (individual): Discussion on spin-bit is the schedule for Thursday in QUIC. Please come by! Method here is not QUIC-specific. We did experimentation, and it actually gets better RTT measurement than it does when measuring within the encrypted stream.

Al: Wasn't planning on adding QUIC here, just paving the way. We'd need a new metric for QUIC anyway.

Actions:
- Yaakov, Brian, and Rachael will review TCP section
- Ignacio will review DNS section
- XRBlock meeting on Thursday, (Al?) will bring feedback to the group

Matt: Does this mean we'll have a small document for every new entry?

Al: These aren't one-line RFCs, they do need text around them

## [draft-ietf-ippm-port-twamp-test][4] - A. Morton

Action: 
- Looks like the IANA table has an error, Al to double check that

## [draft-ietf-ippm-route][5] - A. Morton 

Generalized definitions: The scope is to Internet/IP, and others if desired. Host is general, but is IP address for Internet. Etc.

Yaakov: Another appendix beyond IP to add is Ethernet

Ignacio: From traceroute at IP level, it's best effort to get the same forward path every time. The hops are not necessarily connected physically. Tunnels may not be detected.

Al: Yes, we need a sentence at the front to indicate that this isn't perfect

Rudiger: Adding MPLS or Ethernet would delay the document, maybe not add all of these

Brian: There is an RFC for storage for traceroute—let's not do that. Whatever
format we have should capture that we don't know that A is connected to B, but
that we have packets between interfaces. We can't assume we know the real
hops, just what we could measure at a distance. Look at MapIt and BorderMap.

Open questions to WG:
- add appendix on applicability beyond IP?
- investigate: how much can we use temporal stability on certain hops to optimize the measurements?

Actions:
- Jason Weil to review sections 4, 5, 6.
- Jari Arkko to discuss efficient hop distance measurement tool

## [draft-ietf-ippm-stamp][6] &  [draft-ietf-ippm-stamp-yang][7] - G. Mirsky

Yaakov: Use of encryption and auth are relatively limited. Auth makes more
sense than encryption. Why do we need encryption on these test packets?

Greg: For YANG model, change security to authentication. Defined new timestamp format.

Yaakov: This draft looks good, updates are great

Yaakov: Even a "dumb" reflector should maintain a notion of a session, as a
security item.

## [draft-ietf-ippm-ioam-data][8] - F. Brockners

Frank: New section on timestamp formats in IOAM. Introduction of IOAM type.
Single codepoint for next protocol fields. Harmonize on single codepoint,
solves GRE draft problem.

Yaakov: Glad it's extensible. Proof of transit doesn't currently check
ordering, and I'd like to add order checking to that.

Frank: Secret sharing doesn't have ordering, unwrapping does have

Yaakov: I have a way to confirm ordering even with just secret sharing

(Frank and Yaakov to follow up offline)

Three timestamp formats: PTP/1588, NTP, and POSIX.

Next steps: 
- Aspiration is to have WGLC by Montreal.


# Lightning Talk Notes

## draft-brockners-ippm-ioam-vxlan-gpe, -geneve, -gre - F. Brockners & B. Weis

Greg: there is an overlay design team and draft. Similar solution. Will be
presented and call for adoption and should be reference. Where to put the
information, three drafts or in the overlay design team document?

Frank: it is not the same. Approach the same but cannot use the header. How
many octets to use?

Brian (as chair) / Mirja (as TSV AD): need to check the charter of the WGs
(NVO3) for this item of data encapsulation. Who specifies the code points?

(The conversation will continue in NVO3 this week)


[1]: https://tools.ietf.org/html/draft-ietf-ippm-2330-ipv6
[2]: https://tools.ietf.org/html/draft-ietf-ippm-metric-registry
[3]: https://tools.ietf.org/html/draft-ietf-ippm-initial-registry
[4]: https://tools.ietf.org/html/draft-ietf-ippm-port-twamp-test
[5]: https://tools.ietf.org/html/draft-ietf-ippm-route
[6]: https://tools.ietf.org/html/draft-ietf-ippm-stamp
[7]: https://tools.ietf.org/html/draft-ietf-ippm-stamp-yang
[8]: https://tools.ietf.org/html/draft-ietf-ippm-ioam-data
