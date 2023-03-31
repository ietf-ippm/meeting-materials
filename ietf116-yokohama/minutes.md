# IPPM - Monday 27 March 2023, 9:30-11:30

### Welcome, Note Well, Agenda, Status

Please come to TSVAREA on tuesday, where we will be doing a talk on IPPM!

## Working Group Documents

### draft-ietf-ippm-encrypted-pdmv2

#### (Nalini Elkins)

IPv6 Performance and Diagnostic Metrics v2 (PDMv2) Destination Option
Modifications made to simplify things: Only one needs to be decrypted by other ends - PSNLR (Packet Sequence number Last Received)
Proposal: pass PSNTP in the clear (so oher side never needs to decrypt) - PSNTP become "nonce"
This means that now we do not need topology of primary server/primary client for key exchange, which was required earlier.
This affects the packet layout
Evertyhing after global pointer will be encrypted (fields rearranged in the new layout so all decrypted comes before global pointer - all encrypted comes after).  Simplifies code complexity.  
**Authors:** this is a change for the better, but a big change - hence want feedback from the group

**Tommaso Pecorella (a coauthor):** encourages people to come talk afterwards.  If nobody has input, considered a green light

**Al Morton:** Does this mean the new approach no longer needs earlier key management approach?  Response: exactly, this is nail on the head.  Other side no longer needs key to decrypt. Reduces complexity of key management business.  Offline decryption still applies, can be done offline, to perform analysis.  

**Tommy (chair):** What information could you get from packet sequence number being exposed in the clear?  What are the security implications?  Response: Tommaso - don't think there are more issues than before - there was a nonce already - nature of hte beast - now we simply have another field acting as nonce, would be exposed in any case.  Don't think this is an issue.  If you need more obscurity, go for fully tunneled - PDMv2 would probably no longer apply - just tunnel PDMv2 as a whole.  (Earlier there was a field "random number" acting as nonce - that one is now no longer needed, removed.)  
**Tommy:** Is sequence number unique? **A:** yes.  **Q:** Could that be used as nonce? **A:** yes.  This is the solution presented here. 

Starting to see PDM in the wild - in India.  Need to perform protocol "policing", it's not done right.


### draft-ietf-ippm-capacity-protocol

#### (Al Morton)

New Security Features and Second Sec-dir (early) review - test protocol for one-way IP capacity measurement
New 04 revision resolves discussion on security omdes of operation.  Draft retains 2 authenciation modes and unauhenciated mode.  Adds a new mode for protocol-supported encryption of control/status packets ("partial encryption").  Add option for users to measure within an encrypted tunnel (for fully-encrypted operation)  
Finding this to be a pretty capable protocol.  Supports additional metrics - capaciy in addition to RTT and delay variation, which were always there.  Supports measuring latency with r without max IP-Layer load ("Working Latency" or "Responsiveness"). 
Traffic stream generation computation of interactivity factory as important features to be supported. 
Responses to Brian Weis 2nd sec-dir review/responses.  Brian suggested CBC mode - as AES GCM with long-lived symmetric key might not be safe.  They keep GCM, but can now use AES-CCM instead.  Initialization Vector will be random and sent in the clear.  Need to check if padding is needed, will also need to specify IV generation method. 
Also Brian Weis: "doesn't say tht network addresses and headers are incldued in digest - would be good practice to include". Response: All IPPM test protocols are susceptible to substitution attack, there is no thorough mitigation, but time in the digest is a partial mitigation. 
Other requests for clarifications in the text - authors will take care of that. 
Next steps for the document: more sec ad and sec-dir interactions, WGLC on next version (-05) in mid 2023?  
Authors also plan to share measurements - UDPST next release 8.0.0 - single client tests with multiple flows, multiple servers, resiliency to server failure. 
 
**Tommy (chair):** Agrees that solving substitution attack would be contrary to the nature here.  Asks if this should be brought up in the security considerations.  A: Yes, this is what Brian Weis has suggested too.  They plan to do this.  


### draft-ietf-ippm-pam

#### (Greg Mirsky)

Reiteration of the purpose of this work: caputre violations of SLOs - capture violations - stats re: when precision is available versus when it is not.  Capture periods when acceptable SLO range is breached.  Needed for example for high-precision services.  Use for service assurance (as well as accounting). 
Updates: addressed comments received.  Violated Packets Count and Severly Violated Packets Count introduced.  Worked through and resolved discussion items.  Editorial updates. 
PAM policy vs PAM configuration settings - avoiding term Policy due to being overloaded.  Avoid misinterpretations --> call it configuration settings; they are simply control knobs. 
Resolution of discussion items: Some aspects moved to future work / clarified outside scope here: e.g. YANG data model, IPFIX IEs, Definition of Statistical SLO 
Incorporated with clarifications: PAM configuration settings, considerations to implement an availability state model.
As discussion items have been resolved, ask WG to consider WGLC.

**Q chairs:** how many people here have read it?  (Not many raise hands)  Tommy asks for people to review document, take an eye / get more comments before moving further.  


### draft-ietf-ippm-stamp-on-lag / draft-ietf-ippm-otwamp-on-lag

#### (Tianran Zhou)

Recap on motivation: Link delays of LAG members vary because of different transport paths.  LAG introduces jitter for time-sensitivie traffic.  ...
Proposed solutions: extend OAMP/TWAMP/STAMP to implemnt perf measuremnet on every member link of a LAG. Micro sessions for measurements.  New fields in control messages for this.  Similar for test messages (including micro session parameters/IDs in packet fields).  
Discussion in list: STAMP supports stateful and stsateless modes - how about PM on LAG?  A: Microsession procedures will be stateless. 
Authors believe the draft is ready for WGLC.  

**Q chairs:** how many people have read it?  (5 raise hands)  Tommy Paul: will get it in the queue (presumably for WGLC)


### draft-ietf-ippm-responsiveness

#### (Christoph Paasch)

This is a major update over previous - closed 12 issues, eneriely revised algorithm, discovery through DNS of service endpoints, well-known URL for configuration.  
Revised algorithm: changes to load-generation (add one load-generating connectionper interval), to stability detection (standard deviation of last 4 intervals is within 5% of moving average, first try to achieve stability for capacity, but then also for responsiveness - measure buffer bloat on the network), to responsiveness computation (95th percentile trimmed mean of last 4 intervals)

**Greg Mirsky Q:** Do you see a value to make percentile thresholds configurable - e.g. 95 vs 99 vs 99.9 percentiles etc?  
**A:** Yes, absolutely, draft calls out parameters that can be tuned.  Their experience is tha the settings chosen give good results. Note that changing parameters is risky because results might not be able to converge (so something to be aware of).  

**Tommy Pauly Q:** Agrees this is something that is important to write down.  How would we know that these parameters would converge in all network enviornments, even the ones that are chosen? 
**A:** Good question.  Agree that this needs to be written down / considered further.

**Al Morton Q:** How long does it take to run test in sequential mode: A: under 30 seconds.  Al Morton: sometimes 30 seconds may not be enough - capacity might vary - something to consider.  
**A:** Goal to have relatively quick results.  Accept limitations of temporary variance.  Might get different values in successive measurements.  
**Al Morton:** be careful of making assumptions. Risk - might not always be acceptable.  Something to think about.  

Next steps for the draft: minor cleanups, review working of algorithm description.  There are several implementation.  Authors think the draft is basically good to go and ready to take the next steps. 

**Al Morton:** Can code be shared? - wants to run on old Mac.  
**A:** Cannot share the code.  Can download something based on Golang.  
**Al Morton:** did this last time, but large difference between this and native code.  
**A:** will be happy to fix issues that are found.  

**Marcus (Chair):** You measure responsiveness (primary), capcity (secondary).  Al Morton the other way round.  Which method to use where?  This should be discussed.  Would an informal draft be required?  
**Al Morton:** one (Christoph Paasch's) is TCP-based, the other (Al Morton's) UDP based.  Different transport layers. There is a real gap between the two drafts.  Quic eats the Internet and is UDP-based.  
**Christoph:** It's not about TCP in their draft, but really it's about HTTP.  They want to use protocols used by end users - this is HTTP - it's about HTTP flows.  Al Morton: bottom line - Al Morton's tries to measure network contriubtion to responsiveness, avoid getting mixed up with host stack, this is a difference to Christoph Paasch's.  
**Tommy Pauly:** nods violently.  Dccuments should really clarify focus of end-to-end nature.  Make it clear in the titles - be very precise and unambiguous, even if more verbose. 

### draft-ietf-ippm-ioam-data-integrity 

#### (Justin Iurman)

Status: -03 published after IETF 115.  IANA approved early allocation.  Editorial changes.  Early implementation is finished and looks good.  Looking for more results.  Pending modifications is to fix the integrity validation algorithm.   
Reminder: IOAM node only signs the data fields that it writes.  (data fields modified by other IOAM nodes are exlcuded from the signature.  
E2E option type no transit node involved, encapsulating node signs its data fields, decap node checks signature of encap node.  
Trace option-type: each transit node signs its data fields. Decap node needs to check the entire chain of signatures.  
Header protection: should IOAM node only sign data fields that it writes, or anything that it writes (more general) 
E.g. include trace option-type header including namespace ID (not just data fields)

**Tommy Pauly:** Are you proposing we define it only for the 2 flags that have been allocated - how extensible?  
**A:** by default excluded if not defined yet.  
**Tommy Pauly:** Might require update each time new fields are introduced to clarify if included in integrity check.  

Header protection? Author propose: put back DEX option type support.  (Note: Did not catch all the details here)
**Tommy Pauly:** Why was it decided otherwise?
**A:** does not make sense to exclude
**Tommy Pauly:** Sounds reasonable, also given that there is now more experience with this.  


### draft-ietf-ippm-ioam-yang

#### (Tianran Zhou)

Many comments on WGLC received, discussed at IETF 115.  Latest updates remove IOAM-DEX and two IOAM flags to align with RFC 9197, as well as a few other updates.  
Further discussions - request for IOAM-DE option.  Suggestion is to move this draft forward is it is now, start a new dedidcated draft for IOAM-DEX (because IOAM-DEX config model and usage are quite different from other IOAM options).  

**Greg Mirsky:** Not sure what you mean that IOAM-DEX is different.  YANG data model does not control the transport options.  It controls what telemetry data is capable of being supported etc, which is independent of / orthogonal to whatever transport options are supported.  Having this as part of the same data model will be helpful to operators.  
**A:** Consider several points.  Is IOAM-DEX integral part of IOAM - no.  DEX needs to configure a bunch of things - filter, match rules, export, across nodes.  IOAM only ingress node.  
**Greg:** Transport options here should not be part of / impact this data model.  9197 defines mechanisms of what to collect and how to export, but not how to identify data of interest.  Separate data model from how it is being transported.  Does not see principle difference between 9197 and IOAM-DEX. 
**A:** Can compare the options in the mailing list.  For sake of time to move to mailing list.  

**Thomas Graf:** Concurs to keep IOAM-DEX in the data model - would be helpful to operators.  Distinguish data from other configuration aspects.  
**A:** does not matter if we do one or two drafts.  Will work together to make it better.   

**Benoît Claise (from chat)**
Agree with the chair. Including DEX in YANG now is just more efficient from a process and timeline point of view.

### draft-ietf-ippm-stamp-yang

#### (Greg Mirsky)

Various editorial updates.  Small updates - surrounding keys "stamp-session-id" - could be auto-generated by sender, not necessarily be provisioned, rolling back an earlier change. 

Footer Foote / Nokia: Where are key parameters pulled out?  Greg: (did not capture response details, but seemed to answer the question to satisfaction)

Stamp-session-id - now a union (to allow for both auto-generation and for provisioning)
Next steps: they believe that comments in early yang doctor review have been addressed, WGLC after one more version.  


## Lightning Talks

### draft-mzbc-ippm-transit-measurement-option

#### (Tal Mizrahi)

New IPv6 option for recording transit delay and congestion status along a paths
Accumulate one-way transit delay, record per-hop congestion status (as part of a bitmap - hops set a bit, each using ECN state of node).  


### draft-wang-ippm-alt-mark-yang

#### (Xiao Min) 

draft now in -02, updated from -00 at IETF 115
Editorial cleanups, new coauthors, added some key references. 
Next steps: will ask for WG adoption 


### draft-teigen-ippm-app-quality-metric-reqs

#### (Bjørn Teigen)

Requirements for network quality ramework useful for applications users and operatiors
Purpose: calculate meaningful metric for all parties re: quality: 
Capture probability of meeting network requirements.  Composable - isolate quantify account for contributions of different sub-outcomes and sub-paths. Be applicable for operators, applications, and users.  


### draft-olden-ippm-qoo

#### (Bjørn Teigen)

Quality of Outcome.  Proposal to meet the requirements from draft from Talk 3.  Proposal includes a structure for network quality measuremnets, calculate distance between perfection and uselessness, base this on composable latency distributions and load.

### draft-song-ippm-postcard-based-telemetry

#### (Haoyu Song) 

Postcard-based on-path telemetry using packet parking (PTB-M) draft-song-ippm-postcard-based-telemetry-15
Use cases: SRv6 OAM O-flag (RFC 9259), MPLS MNA P-Flag (draft-song-mpls-flag-based-opt)
Wants to cover flow-path discovery, correlate postcard data (which postcards belong to the same packet on different nodes), data control (which data is needed), export method, security issues /implications.  
Request for WG adoption.  

**Martin Duke (Responsible AD) (From chat):** There are a few presentations here that post alternatives to IOAM due to its overhead.What is this overhead getting us that these proposals are, presumably, giving up?

### draft-ahuang-ippm-dex-timestamp-ext

#### (Alex Huang)
Aggregate on-path delay, add this to IPFIX 

### draft-ahuang-ippm-ioam-on-path-delay

#### (Alex Huang)
Here, you export on-path delay in postcard mode using IOAM.

### draft-ietf-opsawg-ipfix-on-path-telemetry

### draft-zhou-ippm-enhanced-alternate-marking
#### (Giuseppe Fioccola) 
Additional points to Alternate Marking per RFC 9341, 9342: e.g. deployment experience requirements such as entropy of FlowMonID, multipoint measurements, exploring cases when protocols do not allow additional bits for marking to be used.  

