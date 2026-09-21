# Incident Response & Business Continuity / Disaster Recovery

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/license-CC0--1.0-lightgrey.svg)](LICENSE)

A curated, practitioner-oriented guide to **incident response (IR)** and **business continuity / disaster recovery (BC/DR)** — building an IR plan and CSIRT, scenario-specific playbooks, tabletop exercises, digital forensics basics, the Business Impact Analysis, RTO/RPO-driven DR strategy, and post-incident review, with starting templates for each.

**Scope:** the operational response discipline for both a security incident (technical, attacker-driven) and a broader business disruption (natural disaster, outage, pandemic). Breach notification's *legal* timelines are covered by the companion [Privacy Compliance](https://github.com/garynair/privacy) list; the risk-scoring and register structure these plans feed into is covered by the companion [Risk Management](https://github.com/garynair/risk-management) list.

**Why this list treats IR and BC/DR together:** they are run by different teams with different training, but they are the same discipline applied at different scales — both ask "how do we keep operating, or get back to operating, when something goes wrong," and a mature organization runs one coordinated response, not two competing plans that collide during an actual event.

Contributions welcome.

---

## Contents

- [Incident Response vs. Business Continuity vs. Disaster Recovery](#incident-response-vs-business-continuity-vs-disaster-recovery)
- [How to Approach Building an IR and BC/DR Program](#how-to-approach-building-an-ir-and-bcdr-program)
- [Incident Response Standards (NIST SP 800-61, SANS PICERL)](#incident-response-standards-nist-sp-800-61-sans-picerl)
- [Building an Incident Response Plan and CSIRT](#building-an-incident-response-plan-and-csirt)
- [IR Playbooks by Scenario](#ir-playbooks-by-scenario)
- [Digital Forensics Basics](#digital-forensics-basics)
- [Tabletop Exercises and IR Testing](#tabletop-exercises-and-ir-testing)
- [Business Continuity Planning (ISO 22301, BIA)](#business-continuity-planning-iso-22301-bia)
- [Disaster Recovery (RTO/RPO and DR Strategy)](#disaster-recovery-rtorpo-and-dr-strategy)
- [Crisis Communications](#crisis-communications)
- [Post-Incident Review and Lessons Learned](#post-incident-review-and-lessons-learned)
- [Templates in This Repo](#templates-in-this-repo)
- [Cross-Framework Mapping and Platforms](#cross-framework-mapping-and-platforms)
- [Certifications and Training](#certifications-and-training)
- [Government and Standards Bodies](#government-and-standards-bodies)
- [Learning Resources](#learning-resources)
- [Related Lists](#related-lists)

---

## Incident Response vs. Business Continuity vs. Disaster Recovery

These three terms get used interchangeably in casual conversation and mean specifically different things in a mature program:

- **Incident Response (IR)** is the technical, security-focused process of detecting, containing, eradicating, and recovering from a security incident (a breach, ransomware, an insider threat) — typically owned by security/IT, measured in hours to days.
- **Business Continuity (BC)** is the organizational discipline of keeping critical business functions running during *any* disruption (a security incident, a natural disaster, a key-vendor failure, a pandemic) — owned by the business, not just IT, and concerned with people and process as much as technology.
- **Disaster Recovery (DR)** is the specific, technical subset of business continuity focused on restoring IT systems and data after a disruption — the mechanism (backup sites, failover, restoration procedures) that makes a business continuity plan's IT-dependent functions actually achievable.

A security incident can trigger all three: IR handles the technical response, BC keeps the business running (manual workarounds, alternate processes) while systems are down, and DR restores the systems themselves. Plans built in isolation from each other tend to conflict exactly when they're needed most — the DR team restoring from a backup before the IR team has confirmed the backup itself is clean, for example.

---

## How to Approach Building an IR and BC/DR Program

1. **Run a Business Impact Analysis (BIA) first.** You cannot set a meaningful recovery objective for anything until you know which business functions matter most and how quickly their loss becomes unacceptable — see Business Continuity Planning below.
2. **Build the IR plan and stand up (or formally designate) a CSIRT.** Define roles, authority, and escalation paths before an incident, not during one.
3. **Write scenario-specific playbooks** for your most likely and most damaging incident types (ransomware, business email compromise, data breach) — a generic IR plan is too abstract to execute quickly under pressure.
4. **Set RTOs and RPOs per critical system**, derived from the BIA, and build (and test) the DR capability needed to actually meet them — an RTO nobody has verified against the real backup/restore process is just a hope.
5. **Coordinate IR and privacy/legal explicitly.** Breach notification clocks (see the companion Privacy Compliance list) start running before an IR investigation typically concludes — build the two processes to run in parallel with a shared timeline, not sequentially.
6. **Test everything with tabletop exercises**, on a defined cadence and after any material change to systems, team, or threat landscape — an untested plan is a hypothesis, not a plan.
7. **Establish crisis communications in advance** — internal, customer-facing, regulatory, and (where relevant) media — with pre-approved templates and a clear decision-maker for what gets said and when.
8. **Run a blameless post-incident review after every real incident and every major exercise**, and feed findings back into the plan, the BIA, and the risk register.
9. **Feed unresolved gaps (an RTO the current DR capability can't meet, a playbook that doesn't exist yet) into the risk register** — see the companion [Risk Management](https://github.com/garynair/risk-management) list.
10. **Review and re-test on a cadence** — see Post-Incident Review and the periodic review guidance in the companion Risk Management list for suggested intervals.

---

## Incident Response Standards (NIST SP 800-61, SANS PICERL)

**Path to adoption:** both are voluntary, free, and non-certifiable frameworks; most IR plans and playbooks in production today are built on one or a blend of both.

- [NIST SP 800-61 Revision 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final) - "Incident Response Recommendations and Considerations for Cybersecurity Risk Management," NIST's current incident response guidance, restructured around the CSF 2.0 functions (Govern, Identify, Protect, Detect, Respond, Recover) rather than the prior standalone lifecycle.
- [SANS Incident Handler's Handbook](https://www.sans.org/white-papers/33901/) - The widely taught PICERL model (Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned), a simpler, six-phase lifecycle many practitioners find easier to operationalize than NIST's fuller guidance.

---

## Building an Incident Response Plan and CSIRT

**How to build it:**
1. Define the CSIRT's membership by role, not just by name: incident commander, technical lead, communications lead, legal/privacy liaison, and executive sponsor, each with a named backup.
2. Establish the incident commander's authority explicitly — during a live incident, this role needs the standing authority to make fast decisions (isolating a system, engaging outside counsel) without waiting for a full leadership sign-off chain.
3. Define severity levels with objective criteria (systems affected, data types involved, business impact) and map each level to a specific response team size, executive notification requirement, and target response time.
4. Pre-arrange external resources before you need them: outside counsel, a digital forensics/incident response (DFIR) retainer firm, and a cyber insurance carrier's incident hotline — negotiating these during a live incident costs time you don't have.
5. Keep the plan itself short and usable under pressure — a 40-page document nobody can navigate during an incident is worse than a laminated one-page decision tree plus detailed playbooks behind it.

See [`templates/incident-response-plan-template.md`](templates/incident-response-plan-template.md) in this repo for a starting structure.

- [CISA Incident Response Plan (Basics)](https://www.cisa.gov/sites/default/files/publications/Incident-Response-Plan-Basics_508c.pdf) - CISA's free, concise guide to the core elements a small-to-mid-sized organization's IR plan should contain.

---

## IR Playbooks by Scenario

**How to build one:**
1. Pick your highest-likelihood, highest-impact scenarios first (ransomware and business email compromise cover a large share of real-world incidents for most organizations) rather than trying to write a playbook for every conceivable attack.
2. Structure each playbook around the same lifecycle (Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned) so responders don't have to learn a new structure per scenario under pressure.
3. Write containment steps as specific commands/actions where possible ("isolate host via EDR console," "disable the compromised account in the IdP"), not general guidance like "contain the threat."
4. Include decision points explicitly: when to engage law enforcement, when to activate the cyber insurance carrier, when a ransomware event crosses from "IT incident" to "board-notification event."
5. Cross-reference the breach-notification decision tree in the companion Privacy Compliance list at the point in the playbook where notification obligations are typically triggered.

See [`templates/ransomware-playbook-template.md`](templates/ransomware-playbook-template.md) in this repo for a worked example you can adapt to other scenarios.

- [CISA #StopRansomware Guide](https://www.cisa.gov/stopransomware/ransomware-guide) - A free, detailed joint CISA/MS-ISAC guide covering ransomware prevention and a full response checklist, one of the most widely used free playbook references.
- [SANS Incident Response Playbooks](https://www.sans.org/white-papers/) - SANS publishes and regularly updates free scenario-specific playbook templates and whitepapers across ransomware, phishing, and insider-threat scenarios.

---

## Digital Forensics Basics

**Key principles:**
1. Preserve the order of volatility — collect the most volatile evidence first (CPU registers/cache, RAM, network state, running processes) before less volatile evidence (disk, logs, backups), since some evidence is destroyed by the act of investigating or by simply powering off a system.
2. Maintain chain of custody for every piece of evidence collected — who collected it, when, how, and everyone who has handled it since — from the moment of collection, since evidence without documented chain of custody is far weaker in any subsequent legal action.
3. Work from forensic copies, never the original system, wherever feasible, so the original evidence remains unaltered for independent verification.
4. Document everything contemporaneously (commands run, timestamps, findings) rather than reconstructing the investigation narrative afterward.
5. Know when to call in outside DFIR expertise — most organizations don't do forensics often enough to keep the skill sharp, which is exactly why a pre-arranged retainer firm (see Building an IR Plan above) matters.

- [NIST SP 800-86](https://csrc.nist.gov/pubs/sp/800/86/final) - "Guide to Integrating Forensic Techniques into Incident Response," NIST's foundational, free guide to forensic data collection and analysis in an IR context.
- [SANS Digital Forensics and Incident Response (DFIR) Resources](https://www.sans.org/digital-forensics-incident-response/) - Free posters, cheat sheets, and whitepapers covering the order of volatility, evidence collection, and forensic tool usage.

---

## Tabletop Exercises and IR Testing

**How to run one:**
1. Pick a realistic scenario tied to your actual environment and threat profile, not a generic template scenario nobody in the room recognizes.
2. Include the right participants: not just security/IT, but legal, communications, HR (for insider-threat scenarios), and an executive sponsor — a tabletop that never leaves the security team never tests the parts of the plan that usually fail first.
3. Inject complications mid-exercise (the incident commander is unreachable, the primary containment action doesn't work, a journalist calls) to test the plan's resilience, not just whether people can read it aloud.
4. Time-box the exercise and appoint a facilitator whose only job is to keep it moving and capture issues, not to also play a role in the scenario.
5. Document findings as specific, owned action items with due dates — a tabletop that produces only a vague "went well overall" summary wasn't worth running.
6. Run at least one full tabletop annually, plus a shorter, more frequent exercise (quarterly) walking through a single playbook end to end.

See [`templates/tabletop-exercise-template.md`](templates/tabletop-exercise-template.md) in this repo for a starting scenario and facilitation structure.

- [CISA Tabletop Exercise Packages (CTEP)](https://www.cisa.gov/resources-tools/services/cisa-tabletop-exercise-packages) - Free, ready-to-use tabletop exercise scenario packages across multiple sectors and threat types, including facilitator guides.

---

## Business Continuity Planning (ISO 22301, BIA)

**Path to adoption:** ISO 22301 is voluntary and certifiable via an accredited certification body; a Business Impact Analysis is the foundational internal artifact regardless of whether formal certification is pursued.

- [ISO 22301:2019 — Business Continuity Management Systems](https://www.iso.org/standard/75106.html) - The internationally recognized, certifiable standard for a business continuity management system (BCMS), structured on the same Plan-Do-Check-Act model as ISO 27001.
- [FEMA: Business Impact Analysis](https://www.ready.gov/business-impact-analysis) - FEMA's free, practical guide (part of the Ready.gov business continuity toolkit) to identifying critical functions, dependencies, and impact-over-time for a BIA.

**How to run a BIA:**
1. Identify every business function/process, not just IT systems, and interview the actual process owners about what happens if it stops.
2. For each function, determine the Maximum Tolerable Downtime (MTD) — the point past which the disruption becomes unacceptable to the business (financial, regulatory, reputational, safety).
3. Identify dependencies for each function: people, systems, facilities, vendors, and data — a function's true recovery time is bounded by its slowest dependency.
4. Derive Recovery Time Objectives (RTOs) for underlying systems from the business function's MTD, working backward, not the other way around — the business impact should drive the technical target, not the reverse.
5. Prioritize recovery sequencing across functions based on MTD and interdependency, and get this sequencing formally approved by leadership, since it will determine what gets restored first during an actual event.

See [`templates/business-impact-analysis-template.csv`](templates/business-impact-analysis-template.csv) in this repo.

---

## Disaster Recovery (RTO/RPO and DR Strategy)

**Key concepts:**
- **Recovery Time Objective (RTO):** the maximum acceptable time to restore a system or function after a disruption.
- **Recovery Point Objective (RPO):** the maximum acceptable amount of data loss, measured in time (e.g., an RPO of 4 hours means losing up to 4 hours of data is acceptable, driving your backup frequency).
- **DR site strategies**, from cheapest/slowest to most expensive/fastest: cold site (infrastructure exists but must be provisioned and restored — days to weeks), warm site (partially configured and kept reasonably current — hours to a day), hot site / active-active (fully redundant and live — minutes or less).
- **The 3-2-1 backup rule:** keep at least 3 copies of data, on 2 different media types, with at least 1 copy offsite (or, in a modern cloud context, in a separate account/region with independent credentials, specifically to survive a ransomware event that targets connected backups).

**How to build the DR capability:**
1. Match the DR strategy (cold/warm/hot) to each system's actual RTO from the BIA — over-provisioning a hot site for a system with a generous RTO wastes money; under-provisioning for a tight RTO makes the objective unachievable.
2. Ensure backups are isolated from the credentials and network path an attacker who compromises production would also have — ransomware that also encrypts or deletes connected backups is one of the most common reasons a DR plan fails in practice.
3. Test actual restoration, not just backup completion — a backup job reporting "success" for years is not evidence the data is actually restorable.
4. Document and rehearse the failover/failback procedure itself, not just the existence of a secondary site — the procedure is usually where untested plans fail.
5. Revisit RTO/RPO targets whenever the underlying business function's criticality changes, not on a fixed schedule alone.

---

## Crisis Communications

**How to build it:**
1. Pre-identify audiences and their distinct needs: employees, customers, regulators, media, and (for public companies) investors — each needs different content, timing, and channel.
2. Draft holding statements and initial notification templates in advance for your most likely scenarios, so the first communication goes out in minutes, not after a drafting committee convenes mid-crisis.
3. Designate a single approved spokesperson and a clear internal approval chain for anything external-facing, so mixed or contradictory messages don't reach the public.
4. Coordinate crisis communications timing explicitly with legal/privacy's breach-notification obligations (see the companion Privacy Compliance list) — a premature public statement can complicate a legally required regulatory notification, and vice versa.
5. Rehearse crisis communications as part of the tabletop exercise, not as a separate, untested workstream.

---

## Post-Incident Review and Lessons Learned

**How to run one:**
1. Hold the review within a defined window after incident closure (commonly 1-2 weeks) while details are still fresh, but after the immediate response has stabilized.
2. Run it blameless — the goal is understanding what happened and why the plan/process did or didn't work, not assigning individual fault, or people will stop giving the candid detail the review needs.
3. Build a timeline of the incident from detection to closure, cross-referencing every team's logs, and identify where the actual timeline diverged from what the plan assumed.
4. Capture specific, owned action items with due dates — updates to the IR plan, a playbook gap that needs filling, a control gap that let the incident happen in the first place.
5. Feed every action item into the risk register (see the companion Risk Management list) with an owner and target date, exactly like any other risk-treatment plan, so it doesn't quietly disappear after the meeting.
6. Update the relevant playbook and, if the incident revealed a BIA assumption was wrong, revisit the BIA itself.

See [`templates/post-incident-review-template.md`](templates/post-incident-review-template.md) in this repo.

---

## Templates in This Repo

- [`templates/incident-response-plan-template.md`](templates/incident-response-plan-template.md) - A starting IR plan structure covering CSIRT roles, severity levels, and escalation.
- [`templates/ransomware-playbook-template.md`](templates/ransomware-playbook-template.md) - A worked scenario-specific playbook example, adaptable to other incident types.
- [`templates/tabletop-exercise-template.md`](templates/tabletop-exercise-template.md) - A facilitation guide and scenario structure for running a tabletop exercise.
- [`templates/business-impact-analysis-template.csv`](templates/business-impact-analysis-template.csv) - A BIA tracker covering MTD, dependencies, and derived RTO per business function.
- [`templates/post-incident-review-template.md`](templates/post-incident-review-template.md) - A blameless post-incident review structure with a timeline and action-item tracker.

---

## Cross-Framework Mapping and Platforms

- [PagerDuty](https://www.pagerduty.com/) - Widely used incident response orchestration and on-call alerting platform, commonly the operational backbone of a live IR process.
- [Resilience/Continuity Software](https://www.fusionrm.com/) (Fusion Risk Management) - Commercial BC/DR planning and BIA software with dependency mapping and plan-testing workflows.
- [Dradis](https://dradisframework.com/) - Free (community edition) and commercial reporting/collaboration platform useful for consolidating IR findings, also referenced in the companion [VAPT](https://github.com/garynair/vapt) list.
- [Secure Controls Framework (SCF)](https://securecontrolsframework.com/) - Free, open (Creative Commons) meta-framework with explicit incident response and business continuity domain mappings. Shared with the companion [Security Frameworks](https://github.com/garynair/security-frameworks) list.

---

## Certifications and Training

- [GCIH (GIAC Certified Incident Handler)](https://www.giac.org/certifications/certified-incident-handler-gcih/) - SANS/GIAC's widely recognized incident handling certification, closely aligned with the PICERL model.
- [GCFA (GIAC Certified Forensic Analyst)](https://www.giac.org/certifications/certified-forensic-analyst-gcfa/) - SANS/GIAC's certification for deeper digital forensics and incident response work.
- [CBCP (Certified Business Continuity Professional)](https://www.dri.org/certification/cbcp) - DRI International's widely held business continuity certification, covering BIA methodology and BC/DR program management.
- [MBCI (Member of the Business Continuity Institute)](https://www.thebci.org/training-qualifications.html) - The BCI's professional membership/certification path, an internationally recognized alternative to DRI's credentials.

---

## Government and Standards Bodies

- [CISA](https://www.cisa.gov/) - Publisher of the #StopRansomware Guide, Tabletop Exercise Packages, and the IR Plan Basics guide referenced above.
- [Disaster Recovery Institute International (DRI)](https://www.dri.org/) - The organization behind the CBCP certification and widely used BC/DR practice guidance.
- [Business Continuity Institute (BCI)](https://www.thebci.org/) - A leading global professional body for business continuity and resilience practitioners.
- [NIST Computer Security Resource Center (CSRC)](https://csrc.nist.gov/) - Publisher of SP 800-61 (Incident Response) and SP 800-86 (Forensics).
- [FEMA](https://www.fema.gov/) - Publisher of the Ready.gov business continuity toolkit, including the BIA guidance referenced above.

---

## Learning Resources

- [CISA #StopRansomware Guide](https://www.cisa.gov/stopransomware/ransomware-guide) - Free, detailed, and the single best starting point for a ransomware-specific playbook.
- [SANS Digital Forensics and Incident Response (DFIR) Resources](https://www.sans.org/digital-forensics-incident-response/) - Free cheat sheets, posters, and whitepapers.
- [Ready.gov Business Continuity Planning Suite](https://www.ready.gov/business-continuity-plan) - FEMA's free, structured toolkit for building a BIA and BC plan from scratch.
- [CISA Tabletop Exercise Packages (CTEP)](https://www.cisa.gov/resources-tools/services/cisa-tabletop-exercise-packages) - Free, ready-to-run tabletop scenarios across multiple threat types.

---

## Related Lists

- [Privacy Compliance](https://github.com/garynair/privacy) - A companion curated list covering the legal breach-notification timelines (GDPR, US state laws) that run alongside this list's technical incident response process.
- [Risk Management](https://github.com/garynair/risk-management) - A companion curated list covering the risk register that unresolved IR/BC/DR gaps and post-incident action items feed into.
- [Security Frameworks](https://github.com/garynair/security-frameworks) - A companion curated list covering the control frameworks (NIST CSF's Respond/Recover functions) this list's IR process operationalizes.
- [VAPT](https://github.com/garynair/vapt) - A companion curated list covering the offensive-testing side of security, including MITRE ATT&CK, which is commonly used to map an incident's observed techniques during investigation.
- [Cloud Security](https://github.com/garynair/cloud-security) - A companion curated list covering cloud-specific security controls, relevant when a DR strategy relies on cloud-based failover.
- [Federal Compliance](https://github.com/garynair/federal-compliance) - A companion curated list covering FedRAMP, CMMC, and NIST SP 800-53/171 — the federal-sector-specific controls and SSP/POA&M process related to this list.
- [Healthcare Compliance](https://github.com/garynair/healthcare-compliance) - A companion curated list covering HIPAA, HITECH, and HITRUST CSF.

---

## Contributing

PRs welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for the criteria a new entry must meet.

## License

This list is published under [CC0 1.0 Universal](LICENSE). The linked resources retain their own licenses. Templates in the `templates/` directory are original works released under the same CC0 license — use, modify, and redistribute them freely.
