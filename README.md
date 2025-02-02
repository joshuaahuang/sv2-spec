# Stratum V2 Protocol Specification
This repository contains the Stratum V2 protocol specification.

- [0. Abstract](https://github.com/stratum-mining/sv2-spec/blob/main/00-Abstract.md#0-abstract)
- [1. Motivation](https://github.com/stratum-mining/sv2-spec/blob/main/01-Motivation.md#1-motivation)
- [2. Design Goals](https://github.com/stratum-mining/sv2-spec/blob/main/02-Design-Goals.md#2-design-goals)
- [3. Protocol Overview](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#3-protocol-overview)
  - [3.1 Data Types Mapping](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#31-data-types-mapping)
  - [3.2 Framing](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#32-framing)
  - [3.3 Protocol Security](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#33-protocol-security)
    - [3.3.1 Motivation for Authenticated Encryption with Associated Data](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#331-motivation-for-authenticated-encryption-with-associated-data)
    - [3.3.2 Motivation for Using the Noise Protocol Framework](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#332-motivation-for-using-the-noise-protocol-framework)
    - [3.3.3 Authenticated Key Agreement Handshake](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#333-authenticated-key-agreement-handshake)
    - [3.3.4 Signature Noise Message](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#334-signature-noise-message)
    - [3.3.5 Certificate Format](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#335-certificate-format)
    - [3.3.6 URL Scheme and Pool Authority Key](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#336-url-scheme-and-pool-authority-key)
  - [3.4 Reconnecting Downstream Nodes](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#34-reconnecting-downstream-nodes)
  - [3.5 Protocol Extensions](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#35-protocol-extensions)
  - [3.6 Error Codes](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#36-error-codes)
  - [3.7 Common Protocol Messages](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#37-common-protocol-messages)
    - [3.7.1 SetupConnection (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#371-setupconnection-client---server)
    - [3.7.2 SetupConnection.Success (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#372-setupconnectionsuccess-server---client)
    - [3.7.3 SetupConnection.Error (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#373-setupconnectionerror-server---client)
    - [3.7.4 ChannelEndpointChanged (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/03-Protocol-Overview.md#374-channelendpointchanged-server---client)
- [4. Mining Protocol](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4-mining-protocol)
  - [4.1 Channels](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#41-channels)
    - [4.1.1 Standard Channels](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#411-standard-channels)
    - [4.1.2 Extended Channels](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#412-extended-channels)
    - [4.1.3 Group Channels](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#413-group-channels)
    - [4.1.4 Future Jobs](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#414-future-jobs)
  - [4.2 Hashing Space Distribution](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#42-hashing-space-distribution)
  - [4.3 Mining Protocol Messages](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#43-mining-protocol-messages)
    - [4.3.1 SetupConnection Flags for Mining Protocol](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#431-setupconnection-flags-for-mining-protocol)
    - [4.3.2 OpenStandardMiningChannel (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#432-openstandardminingchannel-client---server)
    - [4.3.3 OpenStandardMiningChannel.Success (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#433-openstandardminingchannelsuccess-server---client)
    - [4.3.4 OpenExtendedMiningChannel (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#434-openextendedminingchannel-client---server)
    - [4.3.5 OpenExtendedMiningChannel.Success (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#435-openextendedminingchannelsuccess-server---client)
    - [4.3.6 OpenMiningChannel.Error (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#436-openminingchannelerror-server---client)
    - [4.3.7 UpdateChannel (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#437-updatechannel-client---server)
    - [4.3.8 UpdateChannel.Error (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#438-updatechannelerror-server---client)
    - [4.3.9 CloseChannel (Client -> Server, Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#439-closechannel-client---server-server---client)
    - [4.3.10 SetExtranoncePrefix (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4310-setextranonceprefix-server---client)
    - [4.3.11 SubmitSharesStandard (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4311-submitsharesstandard-client---server)
    - [4.3.12 SubmitSharesExtended (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4312-submitsharesextended-client---server)
    - [4.3.13 SubmitShares.Success (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4313-submitsharessuccess-server---client)
    - [4.3.14 SubmitShares.Error (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4314-submitshareserror-server---client)
    - [4.3.15 NewMiningJob (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4315-newminingjob-server---client)
    - [4.3.16 NewExtendedMiningJob (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4316-newextendedminingjob-server---client)
    - [4.3.17 SetNewPrevHash (Server -> Client, broadcast)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4317-setnewprevhash-server---client-broadcast)
    - [4.3.18 SetCustomMiningJob (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4318-setcustomminingjob-client---server)
    - [4.3.19 SetCustomMiningJob.Success (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4319-setcustomminingjobsuccess-server---client)
    - [4.3.20 SetCustomMiningJob.Error (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4320-setcustomminingjoberror-server---client)
    - [4.3.21 SetTarget (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4321-settarget-server---client)
    - [4.3.22 Reconnect (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4322-reconnect-server---client)
    - [4.3.23 SetGroupChannel (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/04-Mining-Protocol.md#4323-setgroupchannel-server---client)
- [5. Job Negotiation Protocol](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#5-job-negotiation-protocol)
  - [5.1 Job Negotiation Protocol Messages](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#51-job-negotiation-protocol-messages)
    - [5.1.1 SetupConnection Flags for Job Negotiation Protocol](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#511-setupconnection-flags-for-job-negotiation-protocol)
    - [5.1.2 AllocateMiningJobToken (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#512-allocateminingjobtoken-client---server)
    - [5.1.3 AllocateMiningJobToken.Success (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#513-allocateminingjobtokensuccess-server---client)
    - [5.1.4 CommitMiningJob (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#514-commitminingjob-client---server)
    - [5.1.5 CommitMiningJob.Success (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#515-commitminingjobsuccess-server---client)
    - [5.1.6 CommitMiningJob.Error (Server->Client)](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#516-commitminingjoberror-server-client)
    - [5.1.7 IdentifyTransactions (Server->Client)](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#517-identifytransactions-server-client)
    - [5.1.8 IdentifyTransactions.Success (Client->Server)](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#518-identifytransactionssuccess-client-server)
    - [5.1.9 ProvideMissingTransactions (Server->Client)](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#519-providemissingtransactions-server-client)
    - [5.1.10 ProvideMissingTransactions.Success (Client->Server)](https://github.com/stratum-mining/sv2-spec/blob/main/05-Job-Negotiation-Protocol.md#5110-providemissingtransactionssuccess-client-server)
- [6. Template Distribution Protocol](https://github.com/stratum-mining/sv2-spec/blob/main/06-Template-Distribution-Protocol.md#6-template-distribution-protocol)
  - [6.1 CoinbaseOutputDataSize (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/06-Template-Distribution-Protocol.md#61-coinbaseoutputdatasize-client---server)
  - [6.2 NewTemplate (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/06-Template-Distribution-Protocol.md#62-newtemplate-server---client)
  - [6.3 SetNewPrevHash (Server -> Client)](https://github.com/stratum-mining/sv2-spec/blob/main/06-Template-Distribution-Protocol.md#63-setnewprevhash-server---client)
  - [6.4 RequestTransactionData (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/06-Template-Distribution-Protocol.md#64-requesttransactiondata-client---server)
  - [6.5 RequestTransactionData.Success (Server->Client)](https://github.com/stratum-mining/sv2-spec/blob/main/06-Template-Distribution-Protocol.md#65-requesttransactiondatasuccess-server-client)
  - [6.6 RequestTransactionData.Error (Server->Client)](https://github.com/stratum-mining/sv2-spec/blob/main/06-Template-Distribution-Protocol.md#66-requesttransactiondataerror-server-client)
  - [6.7 SubmitSolution (Client -> Server)](https://github.com/stratum-mining/sv2-spec/blob/main/06-Template-Distribution-Protocol.md#67-submitsolution-client---server)
- [7. Message Types](https://github.com/stratum-mining/sv2-spec/blob/main/07-Message-Types.md#7-message-types)
- [8. Extensions](https://github.com/stratum-mining/sv2-spec/blob/main/08-Extensions.md#8-extensions)
- [9. Discussion](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#9-discussion)
  - [9.1 Speculative Mining Jobs](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#91-speculative-mining-jobs)
  - [9.2 Rolling `nTime`](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#92-rolling-ntime)
    - [9.2.1 Hardware nTime rolling](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#921-hardware-ntime-rolling)
  - [9.3 Notes](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#93-notes)
  - [9.4 Usage Scenarios](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#94-usage-scenarios)
    - [9.4.1 End Device (v2 ST)](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#941-end-device-v2-st)
    - [9.4.2 Transparent Proxy (v2 any -> v2 any)](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#942-transparent-proxy-v2-any---v2-any)
    - [9.4.3 Difficulty Aggregating Proxy (v2 any -> v2 EX)](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#943-difficulty-aggregating-proxy-v2-any---v2-ex)
    - [9.4.4 Proxy (v1 -> v2)](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#944-proxy-v1---v2)
    - [9.4.5 Proxy (v2 -> v1)](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#945-proxy-v2---v1)
  - [9.5. FAQ](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#95-faq)
    - [9.5.1 Why is the protocol binary?](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#951-why-is-the-protocol-binary)
  - [9.6 Terminology](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#96-terminology)
  - [9.7 Open Questions / Issues](https://github.com/stratum-mining/sv2-spec/blob/main/09-Discussion.md#97-open-questions--issues)

## Authors
Pavel Moravec <pavel@braiins.com>  
Jan Čapek <jan@braiins.com>  
Matt Corallo <bipstratum@bluematt.me>
