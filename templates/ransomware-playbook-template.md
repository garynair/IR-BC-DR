# Ransomware Incident Response Playbook

Adapt the structure below for other scenario-specific playbooks (business email compromise, data breach, insider threat).

## Preparation (Standing Readiness — Verify Before an Incident)

- [ ] Backups are isolated from production credentials and network path (immutable/offline where possible).
- [ ] EDR/antivirus deployed and current on all endpoints and servers.
- [ ] DFIR retainer firm and cyber insurance carrier contact information current (see IR plan).
- [ ] Network segmentation limits lateral movement between critical systems.

## Identification

1. Confirm indicators: unusual file encryption activity, ransom note presence, unexpected service/process behavior, EDR/SIEM alerts.
2. Determine scope: which hosts, shares, and systems show signs of compromise or encryption.
3. Identify the ransomware family if possible (ransom note, file extension, known IOCs) — informs whether a public decryptor exists.
4. Activate the Incident Response Plan at the appropriate severity level.

## Containment

**Short-term:**
1. Isolate affected hosts from the network (disable network adapter/switch port, or use EDR isolation) without powering off (preserves volatile evidence — see Digital Forensics Basics).
2. Disable or reset credentials suspected of compromise, prioritizing privileged/admin accounts.
3. Block identified command-and-control indicators at the firewall/proxy.
4. Determine whether backups have been affected or deleted; if not yet affected, further isolate backup systems immediately.

**Long-term:**
1. Patch or remediate the confirmed initial access vector before reconnecting isolated systems.
2. Force a full credential reset for all potentially exposed accounts, not just confirmed-compromised ones.

## Eradication

1. Rebuild affected systems from known-good images rather than attempting to "clean" a compromised host, wherever feasible.
2. Validate no persistence mechanisms remain (scheduled tasks, new admin accounts, registry run keys, web shells).
3. Confirm the initial access vector is fully closed before proceeding to recovery.

## Recovery

1. Restore from verified-clean backups, validating data integrity before returning systems to production.
2. Restore in priority order per the Business Impact Analysis's recovery sequencing.
3. Monitor restored systems closely for signs of reinfection before declaring recovery complete.

## Decision Points

- [ ] **Ransom payment:** Escalate to executive sponsor, legal counsel, and cyber insurance carrier before any payment decision — never a unilateral technical-team decision.
- [ ] **Law enforcement engagement:** Notify per organizational policy (often required by cyber insurance policy terms).
- [ ] **Regulatory/breach notification:** Escalate to legal/privacy liaison immediately — see the companion Privacy Compliance list's breach notification checklist. Ransomware involving data exfiltration (not just encryption) very likely triggers notification obligations.

## Lessons Learned

- Reference the post-incident review template after closure.
