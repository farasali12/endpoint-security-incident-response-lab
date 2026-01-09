# Endpoint Security Monitoring & Incident Response Lab

## Overview
This project demonstrates endpoint security monitoring and incident response
techniques in a controlled attacker/defender virtual lab. The focus is on
detecting suspicious activity, analyzing system and network behavior,
containing the incident, and validating remediation — rather than on exploit
or payload mechanics.

This repository is intentionally written to be role-agnostic and applicable
to SOC, incident response, penetration testing, cloud security, and general
security analyst positions.

---

## Lab Environment

| Component | Details |
|--------|--------|
| Attacker System | Kali Linux |
| Defender System | Windows 10 |
| Network | Internal (isolated, no internet access) |
| Monitoring Tools | Task Manager, Resource Monitor, Netstat |
| Security Controls | Windows Defender Firewall |

⚠️ **Disclaimer**  
This lab was conducted in a fully isolated virtual environment for academic
and professional learning purposes. No production systems or external networks
were involved. Offensive tooling details are intentionally omitted from public
documentation.

---

## Objective
The objective of this lab was to:

- Identify exposed services on a Windows endpoint
- Detect unauthorized or suspicious process execution
- Analyze runtime and network behavior
- Apply containment and prevention controls
- Validate system stability after remediation
- Document the incident in a clear, professional manner

---

## Phase 1: Network Exposure Identification
The Windows system was assessed to identify exposed services that could
increase attack surface. An externally accessible service was identified,
demonstrating how misconfiguration can introduce risk.

**Key takeaway:**  
Service exposure should be continuously monitored and minimized.

📁 Evidence:  
`screenshots/nmap_rdp_open.png`

---

## Phase 2: Detection of Suspicious Execution
A suspicious executable was observed running on the Windows endpoint.
Initial detection was performed using native system monitoring tools to
identify abnormal process behavior.

**Indicators observed:**
- Unexpected executable name
- Active execution under a user context
- Resource utilization inconsistent with normal usage

📁 Evidence:  
`screenshots/task_manager_suspicious_file_running.png`

---

## Phase 3: Runtime Behavior Analysis
Further investigation was conducted using Resource Monitor to analyze
the process’s runtime characteristics, including CPU usage, threads,
and execution state.

**Purpose:**  
To distinguish between benign activity and potentially malicious behavior.

📁 Evidence:  
`screenshots/resource_monitor_process.png`

---

## Phase 4: Network Activity Correlation
Network connections associated with the suspicious process were analyzed
to determine whether unauthorized or unexpected communication was occurring.

**Analysis goals:**
- Correlate process activity with network connections
- Identify active or persistent connections
- Assess potential external communication risk

📁 Evidence:  
`screenshots/netstat_active_connection.png`

---

## Phase 5: Containment & Prevention
After confirming suspicious behavior, containment actions were taken:

- The full process tree was terminated using administrative privileges
- The executable location was identified
- An outbound firewall rule was created to block further execution or
  network communication associated with the file

This ensured both immediate containment and prevention of recurrence.

📁 Evidence:  
`screenshots/firewall_block_rule.png`

---

## Phase 6: Post-Containment Verification
The system was monitored after containment to verify:

- The process did not restart
- No residual network activity remained
- The system returned to a stable state

Validation confirms that remediation actions were effective.

📁 Evidence:  
`screenshots/resource_monitor_after.png`

---

## Incident Timeline (Summary)

- T0: Exposed service identified on Windows endpoint
- T1: Suspicious process detected running
- T2: Runtime behavior analyzed
- T3: Network connections correlated
- T4: Process terminated and firewall controls applied
- T5: System stability verified post-containment

---

## Lessons Learned

- Process termination alone may not be sufficient without prevention controls
- Native Windows tools provide strong visibility for initial investigations
- Correlating system and network activity improves detection confidence
- Validation after remediation is critical in incident response
- Responsible documentation is as important as technical execution

---

## Ethical & Professional Considerations
This project emphasizes responsible security practices. Offensive tooling was
used only to generate observable activity in a controlled environment.
Specific exploit and payload details are intentionally excluded from public
documentation and can be discussed verbally in interviews if required.

---

## Key Skills Demonstrated

- Endpoint security monitoring
- Incident detection and response
- Windows process and network analysis
- Firewall-based containment
- Security documentation and reporting
- Attacker/defender lab methodology

---


