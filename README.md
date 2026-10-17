# Network Access Control for Unauthorized Device Prevention

A Cisco Packet Tracer project demonstrating Layer 2 network access restriction using switch port security.

## Overview

This project implements Cisco Catalyst 2960 switch port security to restrict permitted MAC addresses on selected interfaces and detect unauthorized device connections.

**Platform:** Cisco Packet Tracer  
**Switch:** Cisco Catalyst 2960  
**Security Mechanism:** Switch Port Security  
**Violation Action:** Shutdown

## Objectives

- Configure port security on selected switch interfaces.
- Restrict protected ports to permitted MAC addresses.
- Test authorized and unauthorized device connections.
- Verify security violations and interface status.
- Document security limitations and potential improvements.

## Network Topology

The simulated network consists of a Cisco Catalyst 2960 switch connected to authorized end devices and an unauthorized test device.

![Network Topology](screenshots/01-network-topology.png)

## Security Implementation

Port security is configured on Fa0/1, Fa0/2, and Fa0/3.

Key security controls include:

- **MAC address restrictions:** Limits permitted MAC addresses per protected port.
- **Maximum address limit:** Configured for one secure MAC address per port.
- **Violation handling:** Uses the `shutdown` action to disable a port after a qualifying violation.
- **Verification:** Uses Cisco IOS commands to inspect secure addresses, interface status, and violation counters.

### Example Configuration

```text
configure terminal
interface fa0/1
switchport mode access
switchport port-security
switchport port-security maximum 1
switchport port-security violation shutdown
```

Repeat for the other protected interfaces. Enable sticky learning only if it matches your actual configuration.

## Verification Commands

```text
show port-security
show port-security interface fa0/1
show port-security address
show interfaces status
```

These commands verify port-security status, secure MAC addresses, interface conditions, and security violations.

## Testing

| Test | Purpose |
|---|---|
| Authorized device | Verify permitted connectivity |
| Secure MAC verification | Inspect learned or configured addresses |
| Unauthorized device | Trigger a qualifying security violation |
| Port shutdown | Verify violation enforcement |
| Port recovery | Verify restoration after remediation |

## Results

The project evaluates whether switch port security can restrict MAC addresses and disable protected interfaces following qualifying violations.

Evidence is provided through Packet Tracer configuration, CLI output,  connectivity tests and screenshots.

## Limitations

- MAC spoofing may bypass MAC-based restrictions.
- Port security does not authenticate user identities.
- Shutdown violations can interrupt legitimate connectivity.
- Packet Tracer results do not establish production deployment behavior.

## Repository Structure

```text
Network-Access-Control/
├── README.md
├── Network_Access_Control.pkt
└── screenshots/
    ├── network-topology.png
    ├── port-security-config.png
    ├── ....
```

## Skills Demonstrated

- Cisco Packet Tracer
- Cisco IOS CLI
- Layer 2 network security
- Switch port security
- MAC address verification
- Security testing and troubleshooting
- Technical documentation

## Results Summary

The show port-security output confirms that Fa0/1, Fa0/2, and Fa0/3 each had one secure MAC address, a maximum of one, and the shutdown violation action configured.

The project demonstrates the configuration and verification of Layer 2 switch port security in a simulated environment.
