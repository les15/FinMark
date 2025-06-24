# Milestone 2 – Secure Network Configuration for FinMark (Network and Cybersecurity Track)

## Objective

To simulate platform protection for the FinMark system, I configured a firewall rule using Windows Defender Firewall 
with Advanced Security. The rule blocks incoming ICMP echo requests (pings), which protects the system from 
basic reconnaissance techniques like network scans and ping floods. This setup emulates how a financial platform’s backend infrastructure 
would harden its public-facing servers.

---

## Tools Used

- **Windows Defender Firewall (Advanced Security)** – to configure and apply the rule
- **Ping (CMD)** – to test reachability before and after the rule was applied
- **Remote Test Host** – another device used to simulate an external attacker or user
- *(Optional tools planned next: `nmap`, `Wireshark`, `iperf3`)*

---

## Configuration Summary

- A **custom inbound firewall rule** was created to block **ICMPv4 echo requests** (ping)
- The rule was applied to all profiles: Domain, Private, and Public
- A test from a remote device (another laptop) confirmed that the ping request was blocked
- After deleting the block rule, the system still did not respond to ping, so a new **“Allow ICMP”** rule was created and applied successfully

---

## Validation and Test Results

| Test | Outcome | Screenshot |
|------|---------|------------|
| Ping test from local machine | Success | `ping_success_mydevice.png` |
| Ping test from remote host | Blocked | `ping_blocked_by_firewall_remotehost.png` |
| Ping test after allow rule | Success | `ping_success_remotehost.png` |
| Firewall rule creation steps | Completed | `create_firewall_rule_1_rule_type.png` → `rule_applied_inbound_rules_list.png` |

---

## Screenshots Provided

Located in `/milestone2/netsec/screenshots/`:

- Rule creation wizard (all steps, 1–7)
- ICMP “Echo Request” customization
- Inbound rule successfully listed
- Before and after ping results from local and remote devices

---

## Challenges Encountered

- Testing with ping on the same machine gave false results, since Windows allows loopback pings
- Firewall settings persisted even after deleting the block rule, requiring an explicit allow rule
- Network visibility varied based on whether the system was set to “Private” or “Public” network profile

---
