# Active Directory Project Home Lab

## Machines
- **Active Directory Domain Controller:** Windows Server
- **SIEM:** Ubuntu Server (Splunk)
- **Target:** Windows 10 (domain-joined)
- **Attacker:** Kali Linux

  ## Setup Steps
1. Deploy Windows Server, promote to Domain Controller.
2. Join Windows 10 to the domain.
3. Install Splunk on Ubuntu, configure log forwarding.
4. Use Kali Linux for attack simulations.

## Key Demonstrations
- User/group management via AD
- GPO creation & enforcement
- Log collection & monitoring with Splunk
- Detection of attacks (e.g., password spray, brute force)
