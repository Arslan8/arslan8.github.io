---
layout: page
title: "CSE 544 - Systems Security"
---

# Systems Security

This course provides a systems-oriented introduction to computer security, focusing on the mechanisms used to protect modern operating systems, applications, and computing platforms. The course examines how security policies are translated into concrete system mechanisms, how these mechanisms are implemented in modern systems, and how failures in software and hardware abstractions can undermine their security guarantees.

The course begins with memory safety, exploitation, and modern exploit mitigations before moving into kernel security and classical protection mechanisms such as access control, mandatory access control, and SELinux. We then study virtualization and confidential computing, followed by the Linux isolation primitives underlying modern containers and sandboxes, including namespaces, cgroups, capabilities, seccomp, and filesystem isolation. Students will use these mechanisms to understand how systems such as Docker and Bubblewrap actually construct security boundaries.

The course also covers compartmentalization, accelerator and heterogeneous-system security, confidential accelerators and machine-learning workloads, and emerging security challenges involving agentic systems. Throughout the course, the emphasis is on understanding the underlying mechanisms rather than treating modern security systems as black boxes.

# Course Materials

* GitHub: TBD
* Discord: TBD
* Additional course material, code, examples, and assignments will be made available through GitHub.

# Location (Fall 26)

* Leonhard Bldg 203
* TuTh 10:35AM - 11:50AM

# Schedule

**The following schedule is tentative and subject to change throughout the semester. Topics, ordering, quiz dates, and the amount of time devoted to individual modules may be adjusted based on class progress, student background, and emerging systems-security developments.**

All code used in class will be made available on GitHub when possible.

Short quizzes will be given after major course modules to assess understanding of systems-security concepts, mechanisms, attacks, and design tradeoffs.

<div class="d-flex justify-content-between align-items-center mb-3 mt-4">
  <span class="text-muted small"><i class="fas fa-info-circle me-1"></i> Click on any week to expand or collapse topics and readings.</span>
  <div>
    <button class="btn btn-sm btn-outline-dark py-0 px-2" onclick="toggleSchedule(true)">Expand All</button>
    <button class="btn btn-sm btn-outline-secondary py-0 px-2" onclick="toggleSchedule(false)">Collapse All</button>
  </div>
</div>

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 1 — August 25 & 27: Systems Security Foundations & Readings
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vTV0TNwT-lx08PQ_JpDApmHh0QGAV_Cj_sAXEZaflJshKiRSplE3_0D6wbC1uyTbTkstHR2beqT4lD3/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Systems Security Foundations
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
    <ul>
      <li>Threat models and security goals</li>
      <li>Security policies versus mechanisms</li>
      <li>Trusted Computing Base</li>
      <li>Reference monitors</li>
      <li>Protection domains</li>
      <li>Least privilege</li>
      <li>User/kernel boundary</li>
      <li>Attack surfaces</li>
      <li>Fundamental principles of secure-system design</li>
    </ul>

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings: Foundations of Systems Security: Least Privilege and Protection</h6>

    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>Nick Roessler et al.</strong> "μSCOPE: A Methodology for Analyzing Least-Privilege Compartmentalization in Large Software Artifacts." <em>RAID</em>, 2021. Presents a methodology for reasoning about and quantifying least privilege in complex software systems. Using the Linux kernel as a case study, the paper examines overprivilege, protection domains, compartmentalization, and the tradeoff between stronger privilege separation and enforcement overhead. [<a href="https://cs.brown.edu/~vpk/papers/uscope.raid21.pdf" target="_blank">Paper</a>]
      </li>
    </ul>

    <p class="fw-bold mb-1 text-secondary">Optional Readings</p>
    <ul>
      <li>
        <strong>Adam Barth, Collin Jackson, Charles Reis, and the Google Chrome Team.</strong> "The Security Architecture of the Chromium Browser." 2008. Demonstrates how a real-world system applies protection domains, privilege separation, sandboxing, and attack-surface reduction. It also provides a concrete example of reasoning from an explicit threat model to a security architecture. [<a href="https://seclab.stanford.edu/websec/chromium/chromium-security-architecture.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Tianneng Shi, Jingxuan He, Zhun Wang, Linyu Wu, Hongwei Li, Wenbo Guo, and Dawn Song.</strong> "Progent: Programmable Privilege Control for LLM Agents." 2025. Applies the principle of least privilege to agentic systems by enforcing fine-grained policies over tool calls and their arguments. It explores how an agent's privileges can be dynamically restricted according to the task being performed. [<a href="https://arxiv.org/abs/2504.11703" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Jinhao Zhu, Kevin Tseng, Gil Vernik, Xiao Huang, Shishir G. Patil, Vivian Fang, and Raluca Ada Popa.</strong> "MiniScope: A Least Privilege Framework for Authorizing Tool Calling Agents." 2025. Develops a least-privilege authorization model for tool-calling agents by reconstructing permission hierarchies and granting agents only the permissions necessary to perform a task. [<a href="https://arxiv.org/abs/2512.11147" target="_blank">Paper</a>]
      </li>
    </ul>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 2 — September 1 & 3: Memory Safety and Exploitation & Readings
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vSvrC6oirb5vkX3-tb24r1AQi_OSANt5_uTJJ7p6GQIFEvgkIwbyGeFsBxtx-iiL_JL9FbDwuxV5nk9/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Memory Safety & Exploitation
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
    <ul>
      <li>Process memory layout</li>
      <li>Stack and heap memory</li>
      <li>Buffer overflows</li>
      <li>Stack corruption</li>
      <li>Heap corruption</li>
      <li>Use-after-free vulnerabilities</li>
      <li>Double-free vulnerabilities</li>
      <li>Integer vulnerabilities</li>
      <li>Spatial and temporal memory safety</li>
      <li>Control-flow hijacking</li>
      <li>Return-Oriented Programming</li>
    </ul>

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings: Memory Safety and Exploitation</h6>

    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>Adriaan Jacobs, Mahmoud Ammar, and Stijn Volckaert.</strong> "SoK: On the Fragility of Memory Error Exploit Mitigations." <em>35th USENIX Security Symposium (USENIX Security '26)</em>, 2026. [<a href="https://www.usenix.org/conference/usenixsecurity26/presentation/jacobs" target="_blank">Paper</a>]
      </li>
    </ul>

    <p class="fw-bold mb-1 text-secondary">Optional Readings</p>
    <ul>
      <li>
        <strong>Aleph One.</strong> "Smashing the Stack for Fun and Profit." <em>Phrack Magazine</em>, Vol. 7, Issue 49, 1996. [<a href="http://phrack.org/issues/49/14.html" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Jonathan Pincus and Brandon Baker.</strong> "Beyond Stack Smashing: Recent Advances in Exploiting Buffer Overruns." <em>IEEE Security & Privacy</em>, 2004. [<a href="https://www.cs.jhu.edu/~fabian/courses/CS600.424/Course-Papers/BeyondStackSmashing.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Hovav Shacham, Matthew Page, Ben Pfaff, Eu-Jin Goh, Nagendra Modadugu, and Dan Boneh.</strong> "On the Effectiveness of Address-Space Randomization." <em>ACM Conference on Computer and Communications Security (CCS)</em>, 2004. [<a href="https://www.cs.utexas.edu/~shmat/courses/cs380s_fall09/shacham.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Hovav Shacham.</strong> "The Geometry of Innocent Flesh on the Bone: Return-into-libc without Function Calls (on the x86)." <em>ACM Conference on Computer and Communications Security (CCS)</em>, 2007. <em>(Canonical ROP paper)</em>. [<a href="https://hovav.net/ucsd/dist/geometry.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>László Szekeres, Mathias Payer, Tao Wei, and Dawn Song.</strong> "SoK: Eternal War in Memory." <em>IEEE Symposium on Security and Privacy (S&P)</em>, 2013. [<a href="https://www.ieee-security.org/TC/SP2013/papers/4977a048.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Kevin Z. Snow, Fabien Monrose, Lucas Davi, Alexandra Dmitrienko, Christopher Liebchen, and Ahmad-Reza Sadeghi.</strong> "Just-In-Time Code Reuse: Bypassing Exploit Mitigation on Browsers." <em>IEEE Symposium on Security and Privacy (S&P)</em>, 2013. [<a href="https://cs.unc.edu/~fabian/papers/oakland2013.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Alexander Sotirov.</strong> "Heap Feng Shui in JavaScript." <em>Black Hat USA</em>, 2007. [<a href="https://www.blackhat.com/presentations/bh-usa-07/Sotirov/Presentation/bh-usa-07-sotirov.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Andrea Bittau, Adam Belay, Ali Mashtizadeh, David Mazières, and Dan Boneh.</strong> "Hacking Blind." <em>IEEE Symposium on Security and Privacy (S&P)</em>, 2014. <em>(BROP)</em>. [<a href="https://www.scs.stanford.edu/brop/bittau-brop.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Felix Schuster, Thomas Tendyck, Christopher Liebchen, Lucas Davi, Ahmad-Reza Sadeghi, and Thorsten Holz.</strong> "Counterfeit Object-Oriented Programming: On the Difficulty of Preventing Code Reuse Attacks in C++ Applications (COOP)." <em>IEEE Symposium on Security and Privacy (S&P)</em>, 2015. [<a href="https://syssec.rub.de/media/emma/veroeffentlichungen/2015/03/28/COOP-Oakland15.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Nicholas Carlini, Antonio Barresi, Mathias Payer, David Wagner, and Thomas R. Gross.</strong> "Control-Flow Bending: On the Effectiveness of Control-Flow Integrity." <em>USENIX Security Symposium</em>, 2015. [<a href="https://www.usenix.org/conference/usenixsecurity15/technical-sessions/presentation/carlini" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Hong Hu, Shweta Shinde, Sendroiu Adrian, Zheng Leong Chua, Prateek Saxena, and Zhenkai Liang.</strong> "Data-Oriented Programming: On the Expressiveness of Non-Control Data Attacks." <em>IEEE Symposium on Security and Privacy (S&P)</em>, 2016. [<a href="https://www.comp.nus.edu.sg/~prateeks/papers/DOP.pdf" target="_blank">Paper</a>]
      </li>
    </ul>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 3 — September 8 & 10: Memory-Safety Defenses & Readings
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vSvrC6oirb5vkX3-tb24r1AQi_OSANt5_uTJJ7p6GQIFEvgkIwbyGeFsBxtx-iiL_JL9FbDwuxV5nk9/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Memory-Safety Defenses & Protection
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
    <ul>
      <li>Stack canaries</li>
      <li>NX / DEP</li>
      <li>Address Space Layout Randomization</li>
      <li>RELRO</li>
      <li>Control-Flow Integrity</li>
      <li>Shadow stacks</li>
      <li>Pointer Authentication</li>
      <li>Memory tagging</li>
      <li>Hardware-assisted memory safety</li>
      <li>Memory-safe programming languages</li>
      <li>Limitations and bypasses of modern mitigations</li>
    </ul>

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings for Memory Safety</h6>
    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>László Szekeres, Mathias Payer, Tao Wei, and Dawn Song.</strong> "SoK: Eternal War in Memory." <em>IEEE Symposium on Security and Privacy (S&P)</em>, 2013. A broad overview of memory corruption, spatial and temporal memory safety, exploitation techniques, and major classes of defenses. [<a href="https://www.ieee-security.org/TC/SP2013/papers/4977a048.pdf" target="_blank">Paper</a>]
      </li>
    </ul>

    <p class="fw-bold mb-1 text-secondary">Optional Readings</p>
    <ul>
      <li>
        <strong>Crispin Cowan et al.</strong> "StackGuard: Automatic Adaptive Detection and Prevention of Buffer-Overflow Attacks." <em>USENIX Security</em>, 1998. Classic stack-canary work. Useful for distinguishing exploit mitigation from complete memory safety. [<a href="https://www.usenix.org/conference/7th-usenix-security-symposium/stackguard-automatic-adaptive-detection-and-prevention" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Santosh Nagarakatte, Jianzhou Zhao, Milo M. K. Martin, and Steve Zdancewic.</strong> "SoftBound: Highly Compatible and Complete Spatial Memory Safety for C." <em>PLDI</em>, 2009. A canonical metadata-based approach for enforcing spatial memory safety. [<a href="https://llvm.org/pubs/2009-06-PLDI-SoftBound.html" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Santosh Nagarakatte, Jianzhou Zhao, Milo M. K. Martin, and Steve Zdancewic.</strong> "CETS: Compiler Enforced Temporal Safety for C." <em>ISMM</em>, 2010. A companion to SoftBound focused on temporal memory safety, including dangling pointers and use-after-free. [<a href="https://llvm.org/pubs/2010-06-ISMM-CETS.html" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Konstantin Serebryany, Derek Bruening, Alexander Potapenko, and Dmitry Vyukov.</strong> "AddressSanitizer: A Fast Address Sanity Checker." <em>USENIX ATC</em>, 2012. The foundational paper behind AddressSanitizer, covering shadow memory and practical detection of memory errors. [<a href="https://www.usenix.org/conference/atc12/technical-sessions/presentation/serebryany" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Jonathan Woodruff et al.</strong> "The CHERI Capability Model: Revisiting RISC in an Age of Risk." <em>ISCA</em>, 2014. Introduces the CHERI capability architecture and hardware-supported pointer bounds and authority. [<a href="https://www.cl.cam.ac.uk/research/security/ctsrd/pdfs/201406-isca2014-cheri.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Ralf Jung et al.</strong> "RustBelt: Securing the Foundations of the Rust Programming Language." <em>POPL</em>, 2018. Provides a formal foundation for Rust's ownership-based memory-safety guarantees, including interaction with <code>unsafe</code> code. [<a href="https://plv.mpi-sws.org/rustbelt/popl18/" target="_blank">Paper</a>]
      </li>
    </ul>

    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 4 — September 15 & 17: Kernel Security
  </summary>
  <div class="card-body">
    <ul>
      <li>Kernel attack surface</li>
      <li>System calls and the user/kernel boundary</li>
      <li>Kernel memory corruption</li>
      <li>Kernel privilege escalation</li>
      <li>Kernel drivers</li>
      <li>Driver security</li>
      <li>Kernel exploitation</li>
      <li>Kernel hardening</li>
      <li>Kernel attack-surface reduction</li>
      <li>Modern kernel defense mechanisms</li>
    </ul>
    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 5 — September 22 & 24: Access Control
  </summary>
  <div class="card-body">
    <ul>
      <li>Access-control matrix</li>
      <li>Access Control Lists</li>
      <li>Unix file permissions</li>
      <li>Users and groups</li>
      <li>UID, EUID, and SUID</li>
      <li><code>setuid</code> and <code>setgid</code></li>
      <li>Linux capabilities</li>
      <li>Discretionary Access Control</li>
      <li>Confused deputy attacks</li>
      <li>Capability-based security</li>
      <li>Privilege transitions</li>
    </ul>
    <div class="alert alert-warning py-2 px-3 mt-3 mb-0 small">
      <strong>Important Milestone:</strong> Research-based semester project proposals are due <strong>Thursday, September 24</strong>. Students without an approved research proposal will complete the instructor-defined project.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 6 — September 29 & October 1: Mandatory Access Control and SELinux
  </summary>
  <div class="card-body">
    <ul>
      <li>Discretionary versus Mandatory Access Control</li>
      <li>Bell-LaPadula</li>
      <li>Biba</li>
      <li>Multi-Level Security</li>
      <li>Linux Security Modules</li>
      <li>SELinux</li>
      <li>AppArmor</li>
      <li>Labels and security domains</li>
      <li>Type Enforcement</li>
      <li>Policy transitions</li>
      <li>Landlock</li>
      <li>Reference-monitor implementation</li>
    </ul>
    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 7 — October 6 & 8: Virtualization
  </summary>
  <div class="card-body">
    <ul>
      <li>Virtual machines and hypervisors</li>
      <li>Type-1 and Type-2 hypervisors</li>
      <li>Privileged and unprivileged execution</li>
      <li>Hardware-assisted virtualization</li>
      <li>VM exits</li>
      <li>CPU virtualization</li>
      <li>Memory virtualization</li>
      <li>Extended/Nested Page Tables</li>
      <li>Device virtualization</li>
      <li>Emulated and paravirtualized devices</li>
      <li>KVM and QEMU</li>
      <li>VirtIO</li>
      <li>VM isolation</li>
      <li>VM escape attacks</li>
      <li>Virtual machines as security boundaries</li>
    </ul>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 8 — October 13 & 15: Confidential Computing
  </summary>
  <div class="card-body">
    <ul>
      <li>Threat models in cloud computing</li>
      <li>Trusted Execution Environments</li>
      <li>Intel SGX</li>
      <li>Intel TDX</li>
      <li>AMD SEV</li>
      <li>AMD SEV-SNP</li>
      <li>Memory encryption</li>
      <li>Confidential virtual machines</li>
      <li>Protecting workloads from the hypervisor</li>
      <li>Remote attestation</li>
      <li>Measurement and trust establishment</li>
      <li>I/O challenges in confidential systems</li>
      <li>Limitations of confidential computing</li>
    </ul>
    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 9 — October 20 & 22: Linux Isolation Primitives
  </summary>
  <div class="card-body">
    <p class="text-muted small">This module examines the mechanisms from which modern Linux containers and application sandboxes are constructed.</p>
    <ul>
      <li><code>chroot</code></li>
      <li>Filesystem isolation</li>
      <li>Mounts and bind mounts</li>
      <li><code>pivot_root</code></li>
      <li>Linux namespaces (User, PID, Mount, Network, IPC, UTS)</li>
      <li>cgroups</li>
      <li>Linux capabilities</li>
      <li><code>seccomp</code> and seccomp-BPF</li>
      <li><code>no_new_privs</code></li>
      <li><code>unshare</code> and <code>nsenter</code></li>
      <li>Rootless isolation</li>
    </ul>
    <p class="small text-muted mb-0">Students leave this module understanding the individual mechanisms behind a container rather than viewing containers as a single monolithic primitive.</p>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 10 — October 27 & 29: Containers and Sandboxing
  </summary>
  <div class="card-body">
    <ul>
      <li>What a container actually is</li>
      <li>Constructing containers from Linux isolation primitives</li>
      <li>OCI container model</li>
      <li><code>runc</code> and containerd</li>
      <li>Docker architecture</li>
      <li>Container root filesystems and OverlayFS</li>
      <li>Rootless vs. Privileged containers</li>
      <li>Container capabilities & escape vulnerabilities</li>
      <li>Dangerous mounts and Docker socket exposure</li>
      <li>Bubblewrap (<code>bwrap</code>), Firejail, <code>systemd-nspawn</code></li>
      <li>Building application sandboxes from first principles</li>
      <li>Containers versus virtual machines</li>
    </ul>
    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 11 — November 3 & 5: Compartmentalization
  </summary>
  <div class="card-body">
    <ul>
      <li>Privilege separation and least-privilege decomposition</li>
      <li>Process-based compartmentalization</li>
      <li>Capability-oriented systems (Capsicum, <code>pledge</code>, <code>unveil</code>)</li>
      <li>Intel Memory Protection Keys (MPK) & ERIM</li>
      <li>RLBox and WebAssembly sandboxing</li>
      <li>Automatic compartmentalization</li>
      <li>Compartment interfaces and cross-compartment communication</li>
      <li>Attack-surface reduction and performance tradeoffs</li>
    </ul>
    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 12 — November 10 & 12: Accelerators and Heterogeneous-System Security
  </summary>
  <div class="card-body">
    <p class="text-muted small">Modern applications, particularly machine-learning systems, increasingly depend on GPUs and other accelerators.</p>
    <ul>
      <li>CPU-accelerator architecture & GPU execution model</li>
      <li>Host and device memory & GPU virtual memory</li>
      <li>GPU runtimes, drivers, and PCIe communication</li>
      <li>Direct Memory Access (DMA) & IOMMUs</li>
      <li>Device assignment and passthrough</li>
      <li>Accelerator multi-tenancy & GPU process isolation</li>
      <li>SR-IOV, MIG, and hardware partitioning</li>
      <li>Accelerator drivers as part of the Trusted Computing Base</li>
      <li>CPU-GPU trust boundaries & isolation failures</li>
    </ul>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 13 — November 17 & 19: Confidential Accelerators and Agentic Systems
  </summary>
  <div class="card-body">
    <h6 class="fw-bold border-bottom pb-1">Confidential Accelerators & ML Systems</h6>
    <ul>
      <li>Confidential GPU computing & accelerator attestation</li>
      <li>Confidential VMs with accelerators (Intel TDX, AMD SEV-SNP)</li>
      <li>Protected CPU-GPU communication & Trusted I/O</li>
      <li>Model confidentiality, training-data confidentiality</li>
      <li>Confidential inference and training</li>
    </ul>

    <h6 class="fw-bold border-bottom pb-1 mt-3">Agentic Systems Security</h6>
    <ul>
      <li>Agent architectures & LLM-to-tool trust boundaries</li>
      <li>Tool permissions, capabilities, and agent sandboxing</li>
      <li>Untrusted tool outputs & prompt injections into agent loop</li>
      <li>Persistent agent state and memory security</li>
      <li>Multi-agent trust boundaries & autonomous action risks</li>
    </ul>
    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<div class="card border-0 bg-light p-3 mb-3 text-center text-muted rounded">
  <strong>November 22–28: Thanksgiving Holiday — No Classes</strong>
</div>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 14 — December 1 & 3: Semester Project Presentations & Demonstrations
  </summary>
  <div class="card-body">
    <p class="mb-0">The final two instructional weeks are reserved entirely for semester projects. Students will present their systems, demonstrate technical artifacts, explain their design decisions, discuss security models and evaluation, and answer technical questions.</p>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 15 — December 8 & 10: Semester Project Presentations & Demonstrations
  </summary>
  <div class="card-body">
    <p class="mb-0">Semester project presentations and demonstrations continue.</p>
  </div>
</details>

<script>
  function toggleSchedule(openState) {
    document.querySelectorAll('.week-dropdown').forEach(d => {
      d.open = openState;
    });
  }
</script>

# Semester Project

The semester project is the central component of the course and accounts for **70% of the final grade**.

Students have two options for completing the semester project.

### Option 1: Research-Based Semester Project

Students interested in conducting systems-security research may propose their own research project.

You will have approximately **one month from the beginning of the semester to develop and submit a project proposal**. Research-based project proposals are due **Thursday, September 24**.

During this period, you should investigate the problem, understand existing work, and determine whether the proposed idea represents a meaningful technical contribution.

The proposal should clearly describe:

* the systems-security problem being addressed;
* why the problem is important;
* the relevant threat model;
* limitations of existing approaches;
* the proposed technical idea;
* how the system will be implemented;
* how the system will be evaluated; and
* why the proposed work is sufficiently different from existing work.

Students choosing the research-project track are expected to conduct enough background investigation to establish the novelty of their idea. Discovering late in the semester that the proposed idea has already been extensively explored will negatively affect the project evaluation.

Research projects must include a substantive technical artifact. A Work-In-Progress result is acceptable when appropriately justified, but an idea or literature survey without a corresponding implementation and evaluation is not sufficient.

Research projects will be evaluated based on technical difficulty, novelty, quality of the artifact, quality of the evaluation, and demonstrated understanding of the security problem.

### Option 2: Instructor-Defined Semester Project

Students who do not wish to conduct a research-based project may complete the semester project provided by the instructor.

Students who do not submit an approved research proposal by **September 24** will follow this project track.

The instructor-defined project will involve designing, implementing, analyzing, attacking, or defending a real system using techniques covered throughout the course. Detailed specifications, milestones, and evaluation criteria will be provided during the semester.

The instructor-defined project is not a lesser project option. Both project tracks are expected to require substantial systems-security engineering, experimentation, and technical understanding.

# Grading

There are **no traditional midterm or final exams** for this course.

Your final grade will be determined as follows:

* **Semester Project: 70%**
* **Module Quizzes: 30%**

Quizzes will be given after major course modules and will focus on understanding the concepts, mechanisms, attacks, and design tradeoffs discussed in class.

There will be **no required paper presentations or paper-reading component** this semester. Relevant research papers and systems may still be discussed during lectures when they are useful for explaining important concepts or the development of modern systems-security mechanisms.

# AI Usage Policy

Students are permitted to use Generative AI (GenAI) tools as part of their coursework. However, if a student chooses to do so, it is their responsibility to verify the accuracy of any information, code, analysis, or claims produced by the AI. Any errors, hallucinations, insecure code, incorrect analyses, or misleading outputs generated by such tools remain the responsibility of the student.

Students must be able to explain and defend any work they submit, including code, vulnerability analyses, system designs, experimental results, and technical decisions. The instructor may ask students to explain any portion of submitted work in order to verify their understanding.

Students should not treat GenAI systems as an “answering oracle.” These tools should instead be used as assistants for learning, research, debugging, analysis, and engineering. They are not a substitute for understanding the underlying systems-security concepts.

For assignments where requested by the instructor, students may also be required to submit relevant GenAI interaction logs or otherwise document how GenAI tools were used.

# Disability Accommodation Statement

Penn State welcomes students with disabilities into the University’s educational programs. Every Penn State campus has an office for students with disabilities. The [Student Disability Resources website](https://studentaffairs.psu.edu/student-disability-resources) provides contact information for every Penn State campus. For further information, please visit the Student Disability Resources website.

In order to receive consideration for reasonable accommodations, you must contact the appropriate disability services office at the campus where you are officially enrolled, participate in an intake interview, and provide documentation. If the documentation supports your request for reasonable accommodations, your campus’s disability services office will provide you with an accommodation letter. Please share this letter with your instructors and discuss the accommodations with them as early in your courses as possible. You must follow this process for every semester that you request accommodations.

# Counseling and Psychological Services (CAPS) Statement

Many students at Penn State face personal challenges or have psychological needs that may interfere with their academic progress, social development, or emotional well-being. The university offers a variety of confidential services to help you through difficult times, including individual and group counseling, crisis intervention, consultations, online chats, and mental health screenings. These services are provided by staff who welcome all students and embrace a philosophy respectful of clients’ cultural and religious backgrounds, and sensitive to differences in race, ability, gender identity, and sexual orientation.

* Counseling and Psychological Services at University Park (CAPS): [http://studentaffairs.psu.edu/counseling/](http://studentaffairs.psu.edu/counseling/) — 814-863-0395
* Counseling and Psychological Services at Commonwealth Campuses: [https://senate.psu.edu/faculty/counseling-services-at-commonwealth-campuses/](https://senate.psu.edu/faculty/counseling-services-at-commonwealth-campuses/)
* Penn State Crisis Line (24 hours/7 days/week): 877-229-6400
* Crisis Text Line (24 hours/7 days/week): Text LIONS to 741741

# Education Equity and Reporting Bias

Penn State takes great pride in fostering a diverse and inclusive environment for students, faculty, and staff. Acts of intolerance, discrimination, or harassment due to age, ancestry, color, disability, gender, gender identity, national origin, race, religious belief, sexual orientation, or veteran status are not tolerated and can be reported through Educational Equity via the [Report Bias webpage](http://equity.psu.edu/reportbias/).
