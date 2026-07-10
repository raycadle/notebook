---
tags:
  - computers/networks/home
  - computers/networking
---
# DD-WRT Configuration

My home DD-WRT configuration for privacy, security, and performance. Documenting mostly so I can remember my preferred settings whenever I update/reset the router.

All settings are kept as default unless otherwise noted below. Sensitive information is annotated with "[REDACTED]".

[Basic Wireless Settings](https://forum.dd-wrt.com/wiki/index.php/Basic_Wireless_Settings)
[Best Wi-Fi Settings](https://forum.dd-wrt.com/phpBB2/viewtopic.php?t=327595)
[NextDNS CLI - Setup Guide](https://forum.dd-wrt.com/wiki/index.php/NextDNS_CLI)

## Current Router

- Model: [Netgear R6700v3](https://www.netgear.com/support/product/r6700v3/)
- [DD-WRT Netgear R6700v3 Wiki](https://wiki.dd-wrt.com/wiki/index.php/Netgear_R6700v3)
- Firmware Version: DD-WRT v3.0-r54682 std (01/02/24)
- [Firmware Downloads](https://dd-wrt.com/support/other-downloads/?path=betas%2Flatest%2Fnetgear-r6700v3%2F)

## 3rd-Party Services

- [NextDNS](https://nextdns.io)

## Configuration

### Setup

#### Basic Setup

##### WAN Setup

###### WAN Connection Type

- Ignore WAN DNS: `✓`[^1]

##### Network Setup

###### Dynamic Host Configuration Protocol (DHCP)

- DHCP Type: `DHCP Server`
- DHCP Server: `Enable`
- Start IP Address: `192.168.1.100`
- Use dnsmasq for DNS: `✓`
- Forced DNS Redirection: `✓`[^2]
- Forced DNS Redirection DoT: `✓`[^2]

###### NTP Client Settings

- Time Zone: [REDACTED]

### Wireless

#### Basic Settings

##### Physical Interface wl0 [2.4 GHz]

- Service Set Identifier (SSID): [REDACTED]
- Network Mode: `N / G Mixed`[^3]
- Channel: {least congested, don't use Auto}[^3]
- TurboQAM (QAM256): `Enable`[^3]
- Advanced Settings: `✓`
- Firmware Type: `VANILLA`[^4]
- TX Power: `30`[^3]
- Protection Mode: `RTS/CTS`[^3]
- RTS Threshold: `Enable`[^3]
- Threshold: `980`[^3]
- Short Preamble: `Enable`[^3]
- Beacon Interval: `400`[^3]
- DTIM Interval: `1`[^3]
- Airtime Fairness: `Disable`[^4]
- Sensitivity Range / ACK Timing: `3150`[^3]

##### Virtual Interfaces wl0.1

- Service Set Identifier (SSID): [REDACTED]
- Advanced Settings: `✓`
- Protection Mode: `RTS/CTS`[^3]
- RTS Threshold: `Enable`[^3]
- Threshold: `980`[^3]
- AP Isolation: `Enable`[^3]
- DTIM Interval: `1`[^3]

##### Physical Interface wl1 [5 GHz/802.11ac]

- Service Set Identifier (SSID): [REDACTED]
- Network Mode: `AC / N Mixed`[^5]
- Channel Width: `VHT80`[^3]
- Channel: {least congested, maybe prefer 149-161, don't use Auto}[^3]
- Extension Channel: {paired with Channel leads to least congested}[^3]
- Advanced Settings: `✓`
- Firmware Type: `VANILLA`[^4]
- TX Power: `30`[^3]
- Protection Mode: `RTS/CTS`[^3]
- RTS Threshold: `Enable`[^3]
- Threshold: `980`[^3]
- Short Preamble: `Enable`[^3]
- Single User Beamforming: `Enable`[^3]
- Beacon Interval: `300`[^3]
- DTIM Interval: `1`[^3]
- Airtime Fairness: `Disable`[^4]
- Sensitivity Range / ACK Timing: `3150`[^5]

#### Wireless Security

##### Physical Interface wl0

- WPA Shared Key: [REDACTED]

##### Virtual Interfaces wl0.1

- Security Mode: `WPA`
- Network Authentication: `WPA2 Personal`
- WPA Shared Key: [REDACTED]

##### Physical Interface wl1

- WPA Shared Key: [REDACTED]

##### Virtual Interfaces wl1.1

- Security Mode: `WPA`
- Network Authentication: `WPA2 Personal`
- WPA Shared Key: [REDACTED]
- Custom Config: `vendor_vht=1`[^3]

### Services

#### Services

##### DHCP Server Setup

- Static Leases:[^1]

  | MAC Address | Hostname | IP Address   | Lease Expiration |
  | --- | --- | --- | --- |
  | [REDACTED] | tv | 192.168.1.10 |  |

##### Dnsmasq Infrastructure

- Enable dnsmasq: `Enable`
- Query DNS in Strict Order: `Enable`
- Maximum Cached Entries: `10000`
- Additional Options: [^1] [^2] [^6]

    ```
    no-resolv
       
    # NextDNS
    server=45.90.30.0
    server=45.90.28.0
    add-cpe-id=[REDACTED]
    
    # end
    ```

### Administration

#### Keep Alive

##### Schedule Reboot

- Enable: `✓`
- At a Set Time: `✓` `02` `00` `Monday`

[^1]: [WireGuard Client Setup Guide](https://forum.dd-wrt.com/phpBB2/viewtopic.php?t=324624)

[^2]: [VPN and DNS Guide](https://forum.dd-wrt.com/phpBB2/viewtopic.php?t=331017)

[^3]: [QCA Wireless Settings](https://wiki.dd-wrt.com/wiki/index.php/Atheros/ath_wireless_settings)

[^4]: [DD-WRT Netgear R7800 Install Guide](https://forum.dd-wrt.com/phpBB2/viewtopic.php?t=320614)

[^5]: [QCA Best Wi-Fi Settings](https://forum.dd-wrt.com/phpBB2/viewtopic.php?t=324014)

[^6]: [NextDNS Setup Guide](https://my.nextdns.io/{REDACTED}/setup)
