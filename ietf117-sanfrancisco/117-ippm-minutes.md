*When*   Monday 24 July 2023, 13:00-15:00 PDT

*Where:*  Golden Gate 6, https://meetings.conf.meetecho.com/ietf117/?group=ippm

*Chairs:* Tommy Pauly & Marcus Ihlar

# Working Group Documents


## Chair Slides (slides-117-ippm-chair-slides)
- Note well 
- Memoriam - Al Morton
- status of draft-ietf-ippm-capacity-protocol to be continued by co-author

## draft-ietf-ippm-pam

Precision Availability Metrics for SLO-Governed End-to-End Services
- observations
- updates
- discussion items
- next steps
- Questions
- Poll (show of hands)
How many poeple read this document ?
7 

## draft-ietf-ippm-ioam-data-integrity 

Integrity of In-situ OAM Data Fields
- status-06
- draft-ietf-ippm-ioam-data-integrity-06
- Header protecrion 
- Integrity protection
- Next
Q: Secdir review ? WGLC? RFC 9326bis should be created?
A(chair): New RFC should indicate that it updates RFC9326, no need for 9326bis. 
Sec directoate review will be done first then depending on outcome, next steps, such as WGLC will be taken.

- Poll (show of hands)
How many read this document?
1 

## draft-ietf-ippm-encrypted-pdmv2
IPv6 Performance and Diagnostic Metrics v2 (PDMv2) Destination Option

- fields in PDMv2: S-S
- proposal to pass PSNTP in clear
- current vs poposed packet layout 
- Question for WG
Q(presenter): To discuss the SECDIR to get a review ?
A(chair): Yes

Q(): Any initial security review ?
A: some initial reviews were done for HPKE.

Q(Martin Duke - Google): Diff between fields?
A: unanswered

Q(chair): Is it a monotonically increasing number?
A: yes

## draft-ietf-ippm-ioam-yang
YANG Data Model for In-Situ OAM
presenter: Tianran Zhou
- comments from IETF116

Q(Gregory Mirsky - Ericson): Assign role for IOAM functionality on the node 
A: discuss offline to put a default action.

- Next
Q(presenter) : Continue ahead? 
A(chair) Conclude discussion with greg, then decide to move forward. 


## draft-ietf-ippm-responsiveness 
Responsiveness under Working Conditions
presenter: Christoph Paasch
- Implementation status 
- RPM-community updates
- invitation to collab and join open source work or slack for weekly meeting

Q(presenter): Next move ?
A(chair): Discuss moving forward after next revision.

- Poll (show of hands)
How many read this document?
5

# Proposed Work

## draft-olden-ippm-qoo
Quality of outcome 
presentor : Bjørn Ivar Teigen

- challenges in network Quality
- design goals that is useful for 
    - end users
    - applications
    - operators 
- proposed solution
- building on TF-452 (QED)
- middleround for QoE, Quality of outcome, QoS
- Formula
- multiple prespective
- example graph on CDF vs latency

Q(Martin Duke - Google): Representation from percentile ?
A : Choice of depiction is to show arbitary CDF for perfection and uselessness

Q(chair): Attributes that define the curve to be tolerant or not at various percentiles?
A: The graph is generated with self created data. Starting points were perfect(ideal) CDF and then more relaistic

Q(Martin Duke - Google): Example may be useful along with graph.
A: Agree

Q(Dave Taht): sampling rate ?
A: Instaneous metrics are used for this work

Q(Gregory Mirsky - Ericson): QED documents are avaiable.
A: 

- Implementation status for the C library and Go
- how it works links 
- Poll (show of hands)
How many read this document?
4
- Poll (Meetcho)
should we adpot Quality of outcome ?
Y: 11, N:5

Q(presenter): Next
A: _

## draft-mirsky-ippm-asymmetrical-pkts
presenter : Gregory Mirsky

- Reflected Test Packet control TLV pac ket structure
- performance monitoring in a multicast network
-  Address Group Sub-TLV in Layer 2 and Layer 3 packets structure
- Next steps and invitation for collaboration

Q(Rakesh Gandhi - Cisco): clarification question- Reflected packet with diff size wasnt clear.
A : Can clarify examples such as when requestor packets will be large.

Q(Rakesh Gandhi - Cisco): When we want only 1 leaf node to reply ?
A: example prefix length based match to network address, thus defining only subset of system that would respond.

Q(Rakesh Gandhi - Cisco): How would sender know each leaf node replied ?
A: Source Address by Route reflector could be used. More in details to come.

Q(Martin Duke- Google): Security in congestion. Set limits ? Misconfiguration risks?
A: Must be authticated to set boundaries for this field.
To look deeper into amplication issues. 
Number of reflected packets in multiucast mode == 1

Q(Xiao Min -ZTE Corporation): Can it be established for peering enviornment ?
A: Yes

- Poll (Meetcho)
Do you think this document should be adopted by IPPM ?
Y:13, N:2

# Lightning Talks

## draft-fz-ippm-alt-mark-deployment
Alternate Marking Deployment Framework
presenter: G. Fioccola

- How to deploy Alt Marking
 
## draft-wang-ippm-stamp-hbh-extensions
STAMP Extensions for Hop-by-Hop OAM Data Collection
presenter: G. Fioccola
- STAMP (RFC8762)  Extensions for Hop-by-Hop OAM Data Collection

Suggestion(Gregory Mirsky - Ericson): Good idea to meaure Hbh but this information can be collected by underlay rather than on STAMP. Such as given by ipv6 plane. 
A: can discuss based on consensus

Q(Rakesh Gandhi - Cisco): How would this work? Describe STAMP processing.
A: It is active measurememnt. Intermediate nodes needs to handle STAMP TLV option. To be discussed.


## draft-wang-ippm-ipv6-distributed-flow-measurement
Distributed Flow Measurement in IPv6
presenter: Haojie Wang (China Mobile) 
- motivation 
- overview 
- Extension of the flow monitor option 

## draft-wang-ippm-ipv6-flow-measurement
presenter: Haojie Wang (China Mobile) 
- overview 
- Running code: lab interop test status and Deployment status
- Next step

Q(Rakesh Gandhi - Cisco): Extension at transport layer such as ipv6 defines destination option too. This draft needs clarification. 
A: _ (TBD: ask later) 


## draft-he-ippm-integrating-am-into-ioam
Integrating the Alternate-Marking Method into In Situ Operations, Administration, and Maintenance (IOAM)
presenter: Xiaoming He (China Telecom)
- Motivation and objective
- Benefits of the integration
- Extended DEX Option - Type Format

Q(Gregory Mirsky - Ericson): Delay meaure and transit delay measurement is already possible. The proposed idea uses seq number. Directed conflicts. 
A : discuss offline

Q(Justin Lurman - University of Liege) : Do we need another option type ? Annother 2 bits needed
A: discuss offline