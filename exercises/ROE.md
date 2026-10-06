NEXORA TRAINING  /  MODULE 01  /  LAB 02

NEXORA TRAINING

Cybersecurity Lab Report

Module 01  |  Lab 02

Rules of Engagement preparation and network reachability check



## 1. Cover page and metadata

Report metadata

Value

Organization / lab

Nexora Training

Assessment type

Controlled training lab preparation

Observed activity date

5 October 

Report date

6 October 2026

Author: Abiye Fred


OVERALL STATUS  Preparation completed; target reachability and authorization remain unconfirmed.


Cybersecurity Lab Report  |  06 October 2026

NEXORA TRAINING  /  MODULE 01  /  LAB 02

## 1. Executive summary

The lab workspace was created, Kali network addressing was recorded, a two-packet ICMP reachability check was attempted, and Rules of Engagement (RoE) files were staged and hashed. The peer at 192.168.51.20 returned “Destination Host Unreachable” for both probes. RoE validation passed the required section checks but reported unresolved authorization start, end, and maximum-duration placeholders. The evidence therefore documents preparation and a failed reachability check only; it does not establish an approved or completed security assessment.

## 2. Objectives

Prepare the Module 01 Lab 02 working area, inspect the tester interface, check reachability of the intended lab peer, validate the RoE document structure, and preserve integrity evidence for the RoE copies.

## 3. Scope and limitations

The observed scope is limited to the Kali host at 192.168.51.10/24 and an attempted ICMP check to 192.168.51.20. The terminal transcript contains no successful target interaction, port scan, service enumeration, exploitation, or other security testing. The full RoE, approval record, VM configuration, and referenced evidence files were not supplied. The exact year for the October 5 terminal activity is not visible. No conclusions about vulnerabilities or the peer’s security posture can be drawn.

## 4. Environment and tools

Observed details

Operating environment

Kali Linux shell; working directory ~/nexora-training/labs/module-01/lab-02

Network interfaces

lo: 127.0.0.1/8 and ::1/128; eth0 UP: 192.168.51.10/24

Intended peer

192.168.51.20

Commands and utilities

ip, ping, find, cp, chmod, nano, tee, sha256sum, ls, cat, validate-roe.sh

Evidence directories

evidence, hashes, review

## 5. Methodology

The operator created the lab directories, inspected interface addresses with `ip -brief address`, and attempted `ping -c 2 192.168.51.20`. RoE and validator files were located in `/media/sf_kali`, copied to the lab directory, and assigned restrictive permissions. The RoE validator output was captured with `tee`; a draft copy was hashed with SHA-256, then a file named v1.1-approved was copied, set read-only for its owner, and hashed. The transcript shows a checksum verification command returning OK.

## 6. Results and evidence

ID

Evidence observed

Result

E-01

`ip -brief address` output

eth0 UP at 192.168.51.10/24.

E-02

`ping -c 2 192.168.51.20` output

2 transmitted, 0 received, 100% packet loss; both replies from local host state Destination Host Unreachable.

E-03

RoE validator output

All 14 section checks passed; three time-window placeholders remained; both approved VM addresses were present.

E-04

SHA-256 outputs

Draft and file named v1.1-approved each show 3461e2906fef11fd899d5d25bbf35dfab9c0c6ed1dc4b1482ad8e2435e0f0a65.

E-05

Checksum verification

`sha256sum -c hashes/roe-v1.1-approved.sha256` returned “rules-of-engagement-v1.1-approved.md: OK”.

E-06

File permissions

Draft listed as -rw-------; v1.1-approved listed as -r--------.

The saved E-001 validator file is referenced in the command but was not provided independently. The attempted validator exit-code print produced no visible value. Some initial missing-file and copy-command errors were corrected later in the session.

## 7. Analysis

The tester interface is configured with an address in the apparent same /24 subnet as the intended peer, but ICMP failed with a local “Destination Host Unreachable” message. This may reflect a link, virtual network, addressing, or peer availability issue; the transcript cannot distinguish among these causes. RoE document structure validation is not equivalent to authorization. Because time-window placeholders remained unresolved, and no signed approval was provided, authorization cannot be confirmed. The identical hashes show byte-for-byte equality between the two copies at the time they were hashed, but do not prove approval or correctness.

## 8. Risk and impact

No technical vulnerability or compromise was identified because target testing did not occur. The operational risk is that proceeding while the approval window is incomplete could exceed the intended authorization. The reachability failure also creates a risk of testing the wrong network or target if addressing is not verified before proceeding. Evidence reliability is limited by the missing original files and the absent visible validator exit status.

## 9. Mitigation and recommendations

Complete the RoE start time, end time, maximum duration, approver identity, and required signatures; re-run the validator and retain its full output and exit status.

Verify the intended target IP and the VM network mode, virtual switch, and host connectivity before repeating the ICMP check.

Proceed only within the signed authorization window and with the expressly approved addresses and actions.

Preserve the original RoE and validator, record SHA-256 checksums after final approval, and verify them using the matching checksum file.

Capture commands and outputs without shell errors or blank status fields; retain evidence in the designated evidence directory.

## 10. Conclusion

The lab completed workspace setup, documented local network configuration, attempted target reachability, and demonstrated RoE file hashing. The intended peer was unreachable during the attempt, and unresolved approval-window placeholders prevent confirmation of authorization. No security assessment finding can be reported. Resolve authorization and network prerequisites before conducting any additional in-scope activity.

## 11. References

R-01. User-supplied Kali terminal transcript for Nexora Training Module 01 Lab 02, attached 6 October 2026. No external references or underlying files were supplied.

## 12. Appendices

## Appendix A  Evidence register

Evidence item

Transcript path or command

Availability

E-01

`ip -brief address`

Output included in pasted transcript

E-02

`ping -c 2 192.168.51.20`

Output included in pasted transcript

E-03

`evidence/E-001-roe-validation-draft.txt`

File path referenced; underlying file not supplied

E-04

`hashes/roe-v1.0-draft.sha256`; `hashes/roe-v1.1-approved.sha256`

Hash output included in transcript

E-05

`sha256sum -c hashes/roe-v1.1-approved.sha256`

Verification result included in transcript

## Appendix B  Key command excerpts

`ip -brief address`

`ping -c 2 192.168.51.20`

`./validate-roe.sh rules-of-engagement.md | tee evidence/E-001-roe-validation-draft.txt`

`sha256sum rules-of-engagement-v1.0-draft.md`

`sha256sum -c hashes/roe-v1.1-approved.sha256`


