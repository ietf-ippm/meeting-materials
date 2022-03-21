# IPPM IETF 113

## Working Group Documents

### [draft-ietf-ippm-capacity-protocol](https://datatracker.ietf.org/doc/html/draft-ietf-ippm-capacity-protocol)
Al Morton (AT&T Labs) presented status of the draft.

Frank Brockners (Cisco) asked about Open Source status.
Repo is OpenBroadband UDP Speed Test project: https://github.com/BroadbandForum/obudpst

Chairs will request early SECDIR review, and add tag for implementation to datatracker.

### [draft-ietf-ippm-responsiveness](https://datatracker.ietf.org/doc/html/draft-ietf-ippm-responsiveness)
Randall Meyer (Apple) presented information about Open Source server implementation.

William Hawkins (University of Cincinnati) presented information about client implementation written in Go. (Tested with Go 1.16; may work with earlier versions.) Some work still needs to be done to calibrate the RPM scores relative to the Apple ```networkQuality``` tool.

Christoph Paasch (Apple) described recent updates to the draft, and explained methodology. The tool intentionally meaures entire end-to-end resposiveness, including network and end-system delays, including TCP, TLS, and HTTP overhead, because 

J. Ignacio Alvarez-Hamelin (Universidad de Buenos Aires - CONICET) asked about how to simulate a large number of clients operating at the same time.

J. Ignacio Alvarez-Hamelin (Universidad de Buenos Aires - CONICET) asked about how TCP backs off after packet loss. Christoph explained that this is why the test uses multiple parallel TCP streams, to make the load more uniform.

Al Morton (AT&T Labs) suggested refinements about how capacity is calculated, and suggested adding wording about how different congestion control algorithms can affect queue occupancy.

### [draft-ietf-ippm-ioam-conf-state](https://datatracker.ietf.org/doc/html/draft-ietf-ippm-ioam-conf-state)
Xiao Min (ZTE Corporation) presented status of the draft.
Requested Working Group Last Call for this draft.
Tommy Pauly asked if anyone had concerns doing that.
No one spoke up with any objections.
Chairs will discuss.

### [draft-ietf-ippm-ioam-data-integrity](https://datatracker.ietf.org/doc/html/draft-ietf-ippm-ioam-data-integrity)
Justin Iurman (University of Liege) presented status of the draft.
Tommy Pauly asked if we should ask for any external reviews.

### [draft-ietf-ippm-ioam-deployment](https://datatracker.ietf.org/doc/html/draft-ietf-ippm-ioam-deployment)
Frank Brockners (Cisco) presented status of the draft. The draft-01 update was not ready in time for the submission deadline.

### [draft-ietf-ippm-ioam-yang](https://datatracker.ietf.org/doc/html/draft-ietf-ippm-ioam-yang)
Tianran Zhou presented status of the draft.
Yang doctor review is requested (Chairs will initiate this).

### [draft-ietf-ippm-explicit-flow-measurements](https://datatracker.ietf.org/doc/html/draft-ietf-ippm-explicit-flow-measurements)
Mauro Cociglio (Telecom Italia) presented status of the draft.
Tommy Pauly suggested presenting this work to QUIC, CoAP, etc.

### [draft-ietf-ippm-stamp-srpm](https://datatracker.ietf.org/doc/html/draft-ietf-ippm-stamp-srpm)
Rakesh Gandhi (Cisco Systems) presented status of the draft.
Xiao Min (ZTE Corporation) pointed out that enhanced-srpm is not a working group document. The filename is “draft-gandhi-spring-enhanced-srpm”, not “draft-ietf” as shown in the slides.

## Proposed Work

### [draft-elkins-ippm-encrypted-pdmv2](https://datatracker.ietf.org/doc/html/draft-elkins-ippm-encrypted-pdmv2)
Ameya Neeraj Deshpande (NITK Surathkal) presented the draft.
Tommy Pauly asked how many people are engaged with this work.
Nalini Elkins (Inside Products, Inc.) said the first side meeting had 30-40 people; the second had about 20. Several people participated in the Hackathon.
Michael Ackermann (Blue Cross) spoke to say he supports this work.
Al Morton (AT&T Labs) supports adopting this.
Martin Duke (Google) says that if we adopt, we should get early SECDIR review.

### [draft-mirsky-ippm-hybrid-two-step](https://datatracker.ietf.org/doc/html/draft-mirsky-ippm-hybrid-two-step)
Gregory Mirsky (Ericsson) presented the draft.
Tommy Pauly asked for discussion on the mailing list.

### [draft-mhmcsfh-ippm-pam](https://datatracker.ietf.org/doc/html/draft-mhmcsfh-ippm-pam)
Gregory Mirsky (Ericsson) presented the draft.
No questions from the meeting partipants.
Tommy Pauly asked for discussion on the mailing list.

### [draft-weis-ippm-ioam-eth](https://datatracker.ietf.org/doc/html/draft-weis-ippm-ioam-eth) / [draft-spiegel-ippm-ioam-rawexport](https://datatracker.ietf.org/doc/html/draft-spiegel-ippm-ioam-rawexport)
Frank Brockners (Cisco) presented the drafts.
Two mature drafts, recenrly refreshed.
For both drafts the question is adopt, or sunset?
Martin Duke (Google): What is the difference between raw export and direct export?
Frank Brockners: They are complementary.
Tommy Pauly: Are the authors willing to resume this work?
Frank Brockners: Probably not.

### [draft-li-ippm-otwamp-on-lag](https://datatracker.ietf.org/doc/html/draft-li-ippm-otwamp-on-lag)
Tianran Zhou presented the draft.
No questions from the meeting partipants.
Tommy Pauly asked for discussion on the mailing list.
