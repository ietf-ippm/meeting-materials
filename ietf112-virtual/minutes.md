# IPPM Agenda IETF 112

When: Thursday 11 November 2021, 16:00-18:00 UTC
Where: Meetecho
Chairs: Tommy Pauly, Marcus Ihlar, & Ian Swett

## Working Group Documents

### Welcome, Note Well, Agenda, Status
*Chairs*
no agenda bashing, let the fun begin

### draft-ietf-ippm-ioam-data-integrity
Tommy Pauly: Couple of questions. One: What is status of implementing solution and testing it? The other question is should we seek early review from the security area and when should we do that? 

Frank Brockners: Not aware of anyone coding the thing up. is Justin here? Maybe others can speak up. Not comfortable requesting security review until security considerations section is complete. Still some work to do.

Justin Lurman (from jabber): No, I did not have time yet and I am not aware of someone doing it right now.

Tommy: Essentially the next step is filling in gaps in draft then we can do that.

Frank B: We have 2 options for ??? in the document right now, but if other people want to consider including additional options please speak up on the list

Tommy: I would hope there is a small set of algorithms.

Frank B: we'll probably give it another round and then ready for review

Tommy: hopefully we can also find out from implementations what algorithms are useful

### draft-ietf-ippm-ioam-deployment

Xiao Min: during my WGLC review I suggested BIER. I want to know if there is any reason BIER OAM is not included?

Frank B: I forgot, sorry, thanks for bringing it up. 

### draft-ietf-ippm-ioam-conf-state

Frank B: comments. 

First on slide 6, we seemingly have an opinionated choice what gets included in the echo reply, kind of a bit field. Inspired by the data types in the data draft but its not the same. Rather than define new types, maybe encapsulate the types in the YANG model. That would avoid redefinition. Would allow a cleaner approach.

Second is ICMP. We want to adopt language like we have in the NETCONF doc, less "cans", more SHOULDs for improved integrity.

Xiao: I recall your comments from previous meetings. I am not sure how to encapsulate YANG model data into the response message. Is that the suggestion?

Frank: Do it similar to what we've done before. Define a container and ship the container. Don't see a reason why we need to do something special here. Just treat ICMP as a carrier (or BIER as a carrier etc.). 

Tommy: I think we're a little overtime on this item. Great discussion and good point to drill into. Maybe something we can take to the list and go into the different options to avoid reinventing the wheel. Does that work for everyone?

Tommy: Any other questions or comments? Nope. Good update, let's hammer out the details.


### draft-mdt-ippm-explicit-flow-measurements

Tommy: comments in the chat trying to clarify the hidden bits, and what each party can see. Good to clarify that maybe.

Mauro Cociglio: the masking can be done (in the client side) both for the Spin bit, by delaying the "closing" of a square wave, and for the Delay bit by delaying the reflection of the marking of the single marked packet, the Delay Sample. ?? *note taker: my internet flaked out so I missed some of the subsequent description sorry*. 

Tommy: the only extra delay is added on the client side not the server side?

Mauro: yes. It's possible to add timing in many ways, we suggest a fixed value for each client. So its impossible to detect if the it's the right distance or the fake distance. 

### draft-ietf-ippm-connectivity-monitoring

Greg Mirsky: When we are referring to something as a connection, it is not only the ability the ability to receive packets for this connection but the ability not to to receive packets not for this connection. With MPLS, we usually refer to the loss of path continuity. The term is BFD (bidirectional forwarding detection). Loss is declared on 3 consecutive lost packets. There is a good reason for 3. Not only similar to ??? but it provides stability. I'm concerned about loss declaration on 1 packet. Does the next packet after it mark the connection as up? That's bouncy. That could cause a lot of confusion. Maybe something that need discussion, related to fault management OAM.

Redinger Geib: Not a BFD expert. Slide 2 shows how 3 packets and sent/received over a timeline

Greg: Ok, we can continue discussion on the list.

### draft-ietf-ippm-stamp-srpm

No comments or suggestions from the room.

## Proposed Work

*Individual drafts that have received list discussion and are candidates for adoption.*

### draft-cpaasch-ippm-responsiveness

Martin Duke: sounds like 2 separate proposals. Methodology and metrics. Methodology: is that just downloading an arbitrarily large resource?

Christoph Paasch: yes

Martin: What is RTT here?

Christoph: Small 1 byte file is used for the latency measurement. E.g for a GET request the time to get the byte back. We expect, for example, a CDN would have this byte locally generated, so there would be no additional latency serving the response.

Nalini Elkins: I think this is interesting. PDM (performance and diagnostics mesaurements for IPv6), installed in client and server. Interested to see what kind of results we might see based on your test data.

Christoph: I'll need to look into this a bit

Lucas Pardue: There's lots of ways implementations of HTTP/2 or QUIC could be "bad", so maybe worthwhile caveting or defining that going forward

Christoph: The choice of "bad" term perhaps wasn't the best to use here.

Lucas: no problem

### draft-morton-ippm-capacity-metric-protocol

Martin Duke: sorry if you said this but how does this relate to protocol in RFC 9097.

Al Morton: It uses that but you can change things to use lots of other things. For example measuring the performance of traffic passively.

### draft-mirsky-ippm-epm

Fan Yang: *microphone issues *

Tommy: please take it to the chat or the list

## Elevator Pitches (20m)

*Each talk is limited to 1 slide.*

#### draft-li-ippm-ref-delay-measurement

#### draft-li-ippm-deterministic-owd-measurement	

#### draft-zhou-ippm-enhanced-alternate-marking

#### draft-mizrahi-ippm-ioam-linux-profile

Tommy: Is this maybe ops more than the thing we normally do? Something to discuss

#### draft-hwyh-ippm-ps-inband-flow-learning

#### draft-gandhi-ippm-simple-direct-loss

#### draft-du-ippm-self-contained-alt-mark

#### draft-song-ippm-postcard-based-telemetry

Tommy: ??? we should discuss on the list

#### draft-elkins-ippm-encrypted-pdmv2

#### draft-cnbf-ippm-user-devices-explicit-

#### draft-csfx-ippm-hipmetrics

Greg Mirsky: Wonder how this is different from EPM? let's discuss on the list

Tommy: maybe folks can combine efforts here, please discuss
