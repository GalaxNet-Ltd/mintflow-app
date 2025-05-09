# About MintFlow NetStack

MintFlow NetStack is a new iOS VPN client and Network Debugger, with macOS support coming soon. The app supports WireGuard and is built on Cisco's open-source fd.io VPP (Vector Packet Processing). We believe we may be the first to port this to the Apple platform, leveraging VPP's WireGuard plugin to support multiple WireGuard interfaces and split tunneling directly within the app.

In addition to VPN functionality, MintFlow includes initial network debugging tools such as Ping and TraceRoute support.

### Upcoming Features:
- **Domain-based Split Tunneling:** Allows users to route specific applications through the local internet or remote tunnel based on domain.
- **Packet Capture:** Developers will be able to capture application traffic and save it as a pcap file for analysis in Wireshark.
- **IKEv2/IPSec Protocol Support:** VPP already supports this protocol, and we’ll enable it in our app soon.
- **OpenVPN Protocol Support:** We plan to introduce a new, high-performance OpenVPN client natively built on VPP that can coexist with other VPN protocols.
- **tvOS/macOS Support:** Expanding to more Apple platforms.

MintFlow is a paid app, currently priced at $2.99. You can download it from the following link:

[Download From the App Store](https://apps.apple.com/app/6742394218)

---

# MintFlow Manual

You can read the online manual of MintFlow NetStack here:

[MintFlow NetStack Manual](https://mintflow.643216.xyz/manual)

# About the Repo

This repository is for users to submit issues and feature requests. We track them in our roadmap to ensure we’re addressing user needs and prioritizing improvements.

---

# About the Source Code

At this time, we will not be releasing the full app source code. However, we are considering upstreaming Apple-related changes to the official fd.io VPP repository.
