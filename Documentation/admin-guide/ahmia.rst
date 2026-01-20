=====
ahmia
=====

ahmia is a security-first Linux distribution profile focused on a hardened
kernel, privacy-preserving defaults, and defensive tooling for incident
response, network visibility, and secure development. The goals below can be
implemented by integrators and downstream distributions that use this kernel
tree as a base.

Goals
=====

* Reduce the default attack surface while preserving usability.
* Enable strong isolation for applications, services, and user sessions.
* Provide privacy-protecting defaults for network activity.
* Ship a curated toolchain for assessment, response, and verification.
* Make integrity, update, and auditing workflows straightforward.

Core components
===============

* Tor Browser as the default privacy-focused web browser.
* Network analysis: nmap, wireshark, tcpdump, iproute2, nftables.
* Endpoint visibility: auditd, journald with forwarding, logrotate defaults.
* Incident response: rkhunter, chkrootkit, yara, osquery, clamav.
* Hardening tools: lynis, openscap, sbctl, fwupd, tpm2-tools.
* Secure bootstrapping: openssh, gpg, age, cryptsetup, fscrypt.
* Secure development: clang, llvm, rust, gcc, gdb, strace, perf.
* Recovery and forensics: ddrescue, sleuthkit, foremost, volatility.
* Security automation: ansible, opentofu, podman, systemd-nspawn.
* Privacy utilities: dnscrypt-proxy, tor, i2p, wireguard-tools.
* Essentials: asci art tools such as figlet and lolcat for terminal identity.

Kernel hardening defaults
=========================

These defaults are intended to be part of the ahmia kernel configuration and
system policy. Integrators may tune for hardware constraints.

* Memory safety and isolation: KASLR, PTI, PAN where supported, page allocator
  hardening, SLAB freelist randomization, and hardened usercopy.
* Control-flow protection: CFI where supported, strict module signatures, and
  lockdown mode for production.
* Restrict kernel interfaces: disable legacy syscalls, limit perf, kexec, and
  kprobes in production builds.
* Namespaces and cgroups: enable for service isolation and container hardening.
* Integrity: IMA appraisal, EVM, fs-verity for system binaries.
* Filesystems: dm-verity, fscrypt, and per-mount restrictions such as nosuid,
  nodev, noexec where applicable.

User-space hardening defaults
=============================

* Mandatory access control via SELinux or AppArmor with strict profiles.
* systemd hardening: sandboxing directives for all services by default.
* Immutable base system or verified boot for core OS images.
* Enforced full-disk encryption with TPM-backed sealing and recovery keys.
* Automatic security updates and signed repository metadata.
* DNS over HTTPS or DNSCrypt with fallback control.

Operational guidance
====================

* Provide a security baseline checklist with system health status.
* Ship hardened firewall defaults and a guided ruleset wizard.
* Include attack surface audit scripts that produce actionable reports.
* Maintain a hardware compatibility list with secure boot validation steps.
* Provide offline documentation for all included security tools.
