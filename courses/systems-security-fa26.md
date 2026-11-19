---
layout: page
title: "CSE 544 - Systems Security"
---

# Systems Security

This course provides a systems-oriented introduction to computer security, focusing on the mechanisms used to protect modern operating systems, applications, and computing platforms. The course examines how security policies are translated into concrete system mechanisms, how these mechanisms are implemented in modern systems, and how failures in software and hardware abstractions can undermine their security guarantees.

The course begins with memory safety, exploitation, and modern exploit mitigations before moving into kernel security, classical protection mechanisms (access control, mandatory access control, SELinux/LSM), and Linux container and sandboxing isolation primitives. We then study modern policy engines (Flask architecture, Cedar, and Rego/OPA) and virtualization (hypervisors, microVMs, and TCB disaggregation), followed by an in-depth module on agentic AI security (LLM orchestration, RAG and memory poisoning, multi-agent systems, tool trust boundaries, and execution isolation defenses). Throughout the course, the emphasis is on understanding the underlying mechanisms rather than treating modern security systems as black boxes.

# Course Materials

* **Semester Project Workspace:** [slangGraph Tool Security Workspace](https://github.com/Arslan8/slanggraph/blob/course/security-modules/workspace/README.md)
* **GitHub Repository:** [https://github.com/Arslan8/slanggraph/tree/course/security-modules](https://github.com/Arslan8/slanggraph/tree/course/security-modules)
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

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 5 — September 22 & 24: Access Control & Readings
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vT82agjCRYHyG2KfsQL4rRxzD97fP8SbHIBuLHKXK1YMQrMCBbt6c7R3XTeiYGiuzi4DgwX9-y5N93o/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Access Control, Privilege Escalation & LSM
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
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

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings: Access Control and Privilege Management</h6>

    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>Hao Chen, David Wagner, and Drew Dean.</strong> "Setuid Demystified." <em>11th USENIX Security Symposium</em>, 2002. Analyzes Unix user-ID management semantics, formulates formal state-machine models for privilege transitions, and highlights subtle vulnerabilities that lead to privilege escalation. [<a href="https://www.usenix.org/conference/11th-usenix-security-symposium/setuid-demystified" target="_blank">Paper</a>]
      </li>
    </ul>

    <p class="fw-bold mb-1 text-secondary">Optional Readings</p>
    <ul>
      <li>
        <strong>Jerome H. Saltzer and Michael D. Schroeder.</strong> "The Protection of Information in Computer Systems." <em>Proceedings of the IEEE</em>, 1975. Foundational survey outlining design principles for protection mechanisms including least privilege, complete mediation, and fail-safe defaults. [<a href="https://www.cs.virginia.edu/~evans/cs551/saltzer/" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Norm Hardy.</strong> "The Confused Deputy: (or why I know that the 'substitute Programmer' is not a bug)." <em>ACM SIGOPS Operating Systems Review</em>, 1988. The classic paper identifying the confused deputy vulnerability and explaining how capability systems solve ambient-authority pitfalls in access control. [<a href="https://doi.org/10.1145/54289.848445" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Butler W. Lampson.</strong> "Protection." <em>ACM SIGOPS Operating Systems Review</em>, 1974. Introduced the foundational Access Control Matrix model formalizing subjects, objects, access rights, and domain switching. [<a href="https://doi.org/10.1145/775265.775268" target="_blank">Paper</a>]
      </li>
    </ul>

    <div class="alert alert-warning py-2 px-3 mt-3 mb-0 small">
      <strong>Important Milestone:</strong> Research-based semester project proposals are due <strong>Thursday, September 24</strong>. Students without an approved research proposal will complete the instructor-defined project.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 6 — September 29 & October 1: Mandatory Access Control and SELinux & Readings
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vT82agjCRYHyG2KfsQL4rRxzD97fP8SbHIBuLHKXK1YMQrMCBbt6c7R3XTeiYGiuzi4DgwX9-y5N93o/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Access Control, Privilege Escalation & LSM
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
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

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings: Mandatory Access Control and Kernel Security Modules</h6>

    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>Peter Loscocco and Stephen Smalley.</strong> "Integrating Flexible Support for Security Policies into the Linux Operating System." <em>USENIX Annual Technical Conference (FREENIX Track)</em>, 2001. Introduces NSA's Security-Enhanced Linux (SELinux) and the Flask architecture, separating policy enforcement mechanisms in the OS kernel from decision logic to provide fine-grained Mandatory Access Control. [<a href="https://www.usenix.org/legacy/publications/library/proceedings/freenix01/loscocco.html" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Chris Wright, Crispin Cowan, Stephen Smalley, James Morris, and Greg Kroah-Hartman.</strong> "Linux Security Modules: General Security Support for the Linux Kernel." <em>11th USENIX Security Symposium</em>, 2002. Describes the design and implementation of the Linux Security Modules (LSM) framework providing mediation hooks across kernel operations. [<a href="https://www.usenix.org/conference/11th-usenix-security-symposium/linux-security-modules-general-security-support-linux-kernel" target="_blank">Paper</a>]
      </li>
    </ul>

    <p class="fw-bold mb-1 text-secondary">Optional Readings</p>
    <ul>
      <li>
        <strong>Xiaolan Zhang, Antony Edwards, and Trent Jaeger.</strong> "Using Cqual for Static Analysis of Authorization Hook Placement." <em>11th USENIX Security Symposium</em>, 2002. Uses type qualifier analysis via Cqual to verify authorization hook placement in the Linux kernel and prove the absence of unmediated access paths in LSM. [<a href="https://www.usenix.org/conference/11th-usenix-security-symposium/using-cqual-static-analysis-authorization-hook-placement" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>David E. Bell and Leonard J. LaPadula.</strong> "Secure Computer Systems: Unified Exposition and Multics Interpretation." <em>MITRE Technical Report</em>, 1976. The foundational mathematical model for mandatory confidentiality security policies (no read-up, no write-down). [<a href="https://apps.dtic.mil/sti/citations/ADA023588" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Kenneth J. Biba.</strong> "Integrity Considerations for Secure Computer Systems." <em>MITRE Technical Report</em>, 1977. The canonical integrity reference model establishing strict integrity access rules (no read-down, no write-up). [<a href="https://apps.dtic.mil/sti/citations/ADA039324" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Stephen Smalley and Robert Craig.</strong> "Security Enhanced (SE) Android: Bringing Flexible MAC to Android." <em>Network and Distributed System Security Symposium (NDSS)</em>, 2013. Demonstrates the adaptation of SELinux and Type Enforcement to mobile computing to sandbox third-party apps and contain privilege escalation attacks. [<a href="https://www.ndss-symposium.org/ndss2013/security-enhanced-se-android-bringing-flexible-mac-android/" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Mickaël Salaün.</strong> "Landlock LSM: Unprivileged Access Control." <em>Linux Kernel Documentation & LPC</em>, 2021. Overview of the Landlock security module, allowing unprivileged processes to create scoped sandbox restrictions for filesystems and networking. [<a href="https://docs.kernel.org/security/landlock.html" target="_blank">Documentation</a>]
      </li>
    </ul>

    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 7 — October 6 & 8: Extended SELinux / LSM & Linux Isolation Primitives
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vT82agjCRYHyG2KfsQL4rRxzD97fP8SbHIBuLHKXK1YMQrMCBbt6c7R3XTeiYGiuzi4DgwX9-y5N93o/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Access Control, Privilege Escalation & LSM
      </a>
    </div>
    <p class="text-muted small">Continuation of Mandatory Access Control / LSM enforcement and the Linux isolation primitives from which modern containers and sandboxes are constructed.</p>
    <ul>
      <li>SELinux policy enforcement, domain transitions, and LSM hook mediation</li>
      <li><code>chroot</code>, mounts, bind mounts, and <code>pivot_root</code></li>
      <li>Linux namespaces (User, PID, Mount, Network, IPC, UTS)</li>
      <li><code>cgroups</code> and resource isolation</li>
      <li>Linux capabilities, <code>no_new_privs</code>, and <code>seccomp-BPF</code></li>
      <li><code>unshare</code>, <code>nsenter</code>, and rootless isolation</li>
    </ul>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown">
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 8 — October 13 & 15: Containers and Application Sandboxing
  </summary>
  <div class="card-body">
    <ul>
      <li>Constructing containers from Linux isolation primitives</li>
      <li>OCI container model, <code>runc</code>, <code>containerd</code>, and Docker architecture</li>
      <li>Container root filesystems and OverlayFS</li>
      <li>Rootless vs. privileged containers</li>
      <li>Container capability misconfigurations and escape vulnerabilities</li>
      <li>Dangerous mounts and Docker socket exposure</li>
      <li>Application sandboxes: Bubblewrap (<code>bwrap</code>), Firejail, and <code>systemd-nspawn</code></li>
      <li>Containers versus virtual machines as security boundaries</li>
    </ul>
    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 9 — October 20 & 22: Policy Engines & Authorization Architectures (Flask & Cedar) & Readings
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vREZvTsXgxjjJTLwXJOXJhe1h0b4byw7L37FcNJJIpEOUzDw2Yizcn_cWbuU8D9tBZKcDP3bhyKemSR/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Policy Engines (Flask, Cedar & Rego/OPA)
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
    <ul>
      <li>Flask security architecture: separating Policy Enforcement Points (PEP / Object Managers) from Policy Decision Points (PDP / Security Server)</li>
      <li>Access Vector Cache (AVC), dynamic policy reloads, and reference-monitor guarantees</li>
      <li>Policy as Code and core features of modern authorization languages</li>
      <li>Cedar authorization engine: structured Principal–Action–Resource–Context (PARC) request model</li>
      <li>Entity hierarchies, first-class entity graphs, and attribute-based reasoning (RBAC, ABAC, ReBAC)</li>
      <li>Cedar evaluation semantics: <code>permit</code>, <code>forbid</code>, and default-deny guarantees</li>
      <li>Policy construction, schemas, static typechecking, and policy validation</li>
    </ul>

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings: Flask Architecture and Cedar Authorization</h6>

    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>Ray Spencer, Stephen Smalley, Peter Loscocco, Mike Hibler, David Andersen, and Jay Lepreau.</strong> "The Flask Security Architecture: System Support for Diverse Security Policies." <em>8th USENIX Security Symposium</em>, 1999. Defines the foundational Flask architecture decoupling policy decision logic from enforcement mechanisms. [<a href="https://www.usenix.org/conference/8th-usenix-security-symposium/flask-security-architecture-system-support-diverse-security" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Joseph W. Cutler et al.</strong> "Cedar: A New Language for Expressive, Fast, Safe, and Analyzable Authorization." <em>OOPSLA (PACMPL)</em>, 2024. Introduces the design, formal semantics, type system, and automated verification of the Cedar policy language. [<a href="https://arxiv.org/abs/2403.04651" target="_blank">Paper</a>]
      </li>
    </ul>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 10 — October 27 & 29: Declarative Policy Engines (Rego / OPA) & Policy Verification
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vREZvTsXgxjjJTLwXJOXJhe1h0b4byw7L37FcNJJIpEOUzDw2Yizcn_cWbuU8D9tBZKcDP3bhyKemSR/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Policy Engines (Flask, Cedar & Rego/OPA)
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
    <ul>
      <li>Open Policy Agent (OPA) and the Rego declarative policy language</li>
      <li>Datalog foundations, rule definitions, logical unification, and virtual documents</li>
      <li>Evaluating policies over arbitrary JSON (<code>input</code> and <code>data</code> document hierarchies)</li>
      <li>Architectural tradeoffs: Cedar vs. Rego (first-class entity graphs vs. arbitrary JSON; structured PARC vs. general-purpose queries)</li>
      <li>Typing, schemas, decidability, and SMT-based formal policy verification</li>
      <li>Applying policy engines to agentic systems and tool-execution runtimes (<code>slangGraph</code>)</li>
    </ul>

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings: Declarative Policy Engines & Verification</h6>

    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>Open Policy Agent (OPA).</strong> "Policy Language (Rego) & Architecture." <em>CNCF Documentation</em>. Comprehensive guide to Rego's declarative query model, rule evaluation, and JSON document matching. [<a href="https://www.openpolicyagent.org/docs/latest/policy-language/" target="_blank">Documentation</a>]
      </li>
    </ul>

    <p class="fw-bold mb-1 text-secondary">Optional Readings</p>
    <ul>
      <li>
        <strong>Cedar Team.</strong> "Cedar Policy Language Reference & Validation Guide." Covers entity schemas, template-linked policies, and formal verification of authorization invariants. [<a href="https://docs.cedarpolicy.com/" target="_blank">Documentation</a>]
      </li>
    </ul>

    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 11 — November 3 & 5: Virtualization & Hypervisor Security & Readings
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vRGzHhG9PjtHNEfKUYVufw8J6MehM19dDAMcvR5esXF_usnWR0psV1mGQVMvF_tEiA4NJylBRe0WfYW/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Virtualization
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
    <ul>
      <li>OS vs. Hypervisor Trusted Computing Base ("Is the OS the best TCB?")</li>
      <li>Popek and Goldberg Virtualization Theorem (privileged vs. sensitive instructions, trap-and-emulate)</li>
      <li>Dynamic Binary Translation (DBT) for non-virtualizable architectures</li>
      <li>Hardware-assisted virtualization (Intel VT-x / AMD-V, root vs. non-root operation, VM exits, EPT/NPT)</li>
      <li>Paravirtualization, hypercalls, and VirtIO</li>
      <li>Types of Virtual Machine Monitors (Type-1 vs. Type-2 hypervisors)</li>
      <li>The TCB Disaggregation Problem across VMM architectures:
        <ul>
          <li><code>KVM + QEMU</code> and ARM Virtualization Host Extensions (<code>VHE</code>)</li>
          <li><code>Xen + Dom0</code> split-driver architectures</li>
          <li>Unikernels and library operating systems</li>
          <li>Lightweight MicroVMs: <code>AWS Firecracker</code></li>
          <li>Hardware-offloaded hypervisors: <code>AWS Nitro</code></li>
        </ul>
      </li>
      <li>Virtualization attack vectors, emulated device vulnerabilities, and VM escape attacks</li>
    </ul>

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings: Virtualization Architectures and TCB Disaggregation</h6>

    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>Keith Adams and Ole Agesen.</strong> "A Comparison of Software and Hardware Techniques for x86 Virtualization." <em>12th International Conference on Architectural Support for Programming Languages and Operating Systems (ASPLOS)</em>, 2006. Analyzes classical x86 virtualization challenges, dynamic binary translation, and hardware-assisted virtualization tradeoffs. [<a href="https://dl.acm.org/doi/10.1145/1168857.1168860" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Alexandru Agache et al.</strong> "Firecracker: Lightweight Virtualization for Serverless Applications." <em>17th USENIX Symposium on Networked Systems Design and Implementation (NSDI)</em>, 2020. Examines TCB bloat in traditional QEMU/KVM stacks and introduces AWS Firecracker's minimalist microVM architecture for multi-tenant isolation. [<a href="https://www.usenix.org/conference/nsdi20/presentation/agache" target="_blank">Paper</a>]
      </li>
    </ul>

    <p class="fw-bold mb-1 text-secondary">Optional Readings</p>
    <ul>
      <li>
        <strong>Gerald J. Popek and Robert P. Goldberg.</strong> "Formal Requirements for Virtualizable Third Generation Architectures." <em>Communications of the ACM</em>, 1974. Establishes the foundational theorem characterizing instruction-set virtualizability via privileged and sensitive instructions. [<a href="https://dl.acm.org/doi/10.1145/361011.361073" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Paul Barham et al.</strong> "Xen and the Art of Virtualization." <em>19th ACM Symposium on Operating Systems Principles (SOSP)</em>, 2003. Introduces high-performance paravirtualization and the Xen hypervisor + Dom0 management architecture. [<a href="https://www.cl.cam.ac.uk/research/srg/netos/papers/2003-xensosp.pdf" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Patrick Colp et al.</strong> "Breaking Up is Hard to Do: Security and Functionality in a Commodity Hypervisor." <em>23rd ACM Symposium on Operating Systems Principles (SOSP)</em>, 2011. Tackles the Xen Dom0 TCB disaggregation problem by decomposing the monolithic control VM into single-purpose service VMs (Xoar). [<a href="https://dl.acm.org/doi/10.1145/2043556.2043575" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Anil Madhavapeddy et al.</strong> "Unikernels: Library Operating Systems for the Cloud." <em>ASPLOS</em>, 2013. Demonstrates extreme TCB reduction by compiling applications with minimal library OS kernels directly atop a hypervisor. [<a href="https://dl.acm.org/doi/10.1145/2451116.2451167" target="_blank">Paper</a>]
      </li>
    </ul>

    <div class="alert alert-secondary py-1 px-3 mt-3 mb-0 small">
      <strong>Module Quiz</strong> follows this topic.
    </div>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 12 — November 10 & 12: Agentic AI Security I — Architectures, Memory & Attack Surfaces & Readings
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vSfeVV_-njIxaE4GCCtrxFi__ZxeR01bEjJQHrcukNVlguGi-F4TIj9bGo3XDNTIcg1P7Go2ZhrI_0k/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Agentic AI Security
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
    <ul>
      <li>What makes an LLM: embeddings, tokenization, context assembly, next-token sampling, and recency bias</li>
      <li>Prompt Injection 101: direct vs. indirect prompt injection and instruction/data conflation</li>
      <li>What is an agent? Stateless LLMs, Reason-and-Act (<code>ReAct</code>) loops, and agent orchestration runtimes</li>
      <li>Components of agent orchestration: short-term session memory vs. long-term memory</li>
      <li>Retrieval-Augmented Generation (RAG), query rewriting, condensed prompts, and why <code>RAG != Long-Term Memory</code> (<code>Event &gt; State &gt; Memory</code>)</li>
      <li>Attack surfaces in agent memory and retrieval: indirect prompt injection, knowledge corruption (<code>PoisonedRAG</code>), and persistent memory poisoning</li>
      <li>Multi-agent systems (e.g., <code>CrewAI</code>), delegation chains, and cross-agent trust boundaries</li>
    </ul>

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings: Agentic Architectures, Prompt Injection & Memory Poisoning</h6>

    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>Kai Greshake, Sahar Abdelnabi, Shailesh Mishra, Christoph Endres, Thorsten Holz, and Mario Fritz.</strong> "Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection." <em>AISec @ ACM CCS</em>, 2023. Establishes indirect prompt injection across external data sources, retrieval pipelines, and tool outputs. [<a href="https://arxiv.org/abs/2302.12173" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Wei Zou, Runpeng Geng, Binghui Wang, and Jinyuan Jia.</strong> "PoisonedRAG: Knowledge Corruption Attacks to Retrieval-Augmented Generation of Large Language Models." <em>34th USENIX Security Symposium (USENIX Security '25)</em>, 2025. Demonstrates knowledge-database poisoning attacks against RAG pipelines. [<a href="https://arxiv.org/abs/2402.07867" target="_blank">Paper</a>]
      </li>
    </ul>

    <p class="fw-bold mb-1 text-secondary">Optional Readings</p>
    <ul>
      <li>
        <strong>Shunyu Yao, Jeffrey Zhao, Dian Yu, Nan Du, Izhak Shafran, Karthik Narasimhan, and Yuan Cao.</strong> "ReAct: Synergizing Reasoning and Acting in Language Models." <em>ICLR</em>, 2023. Introduces the foundational Reason-and-Act loop underlying modern tool-calling LLM agents. [<a href="https://arxiv.org/abs/2210.03629" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Zhaorun Chen et al.</strong> "AgentPoison: Red-teaming LLM Agents via Poisoning Memory or Knowledge Bases." <em>NeurIPS</em>, 2024. Examines how poisoning long-term memory or RAG stores hijacks autonomous agent decision-making. [<a href="https://arxiv.org/abs/2407.12784" target="_blank">Paper</a>]
      </li>
    </ul>
  </div>
</details>

<details class="card border mb-3 shadow-sm week-dropdown" open>
  <summary class="card-header bg-light fw-bold py-2" style="cursor: pointer;">
    Week 13 — November 17 & 19: Agentic AI Security II — Systems Vulnerabilities & Defenses & Readings
  </summary>
  <div class="card-body">
    <div class="mb-3">
      <a href="https://docs.google.com/presentation/d/e/2PACX-1vSfeVV_-njIxaE4GCCtrxFi__ZxeR01bEjJQHrcukNVlguGi-F4TIj9bGo3XDNTIcg1P7Go2ZhrI_0k/pub?start=false&loop=false&delayms=3000" target="_blank" class="btn btn-sm btn-outline-primary">
        <i class="fas fa-file-powerpoint me-1"></i> Lecture Slides: Agentic AI Security
      </a>
    </div>

    <h6 class="fw-bold border-bottom pb-1">Topics</h6>
    <ul>
      <li>Systems aspect of agentic systems: bridging untrusted LLM outputs to privileged system execution</li>
      <li>Remote code execution and framework vulnerabilities in LLM-integrated apps: <code>LLMSmith</code> and serialization exploits (<code>LangGrinch</code>)</li>
      <li>Exploiting and fuzzing the LLM-orchestrator-tool trust boundary (<code>ToFu</code>)</li>
      <li>Evaluating and defending agentic systems:
        <ul>
          <li>Model evaluation and emulated sandboxes (<code>ToolEmu</code>) and safety classifiers (<code>LlamaGuard</code>)</li>
          <li>Channel separation: <code>Spotlighting</code> (delimiting, datamarking, encoding) and <code>Structured Queries (StruQ)</code></li>
          <li>Model-level alignment: <code>Instruction Hierarchy</code> and <code>Constitutional AI</code></li>
          <li>System-level execution isolation: <code>SecGPT</code> (<code>IsolateGPT</code>) and capability-enforced tool runtimes</li>
        </ul>
      </li>
    </ul>

    <h6 class="fw-bold mt-4 border-bottom pb-1">Readings: Agentic Systems Vulnerabilities, Channel Separation & Execution Isolation</h6>

    <p class="fw-bold mb-1 text-primary">Required Reading</p>
    <ul>
      <li>
        <strong>Yuhao Wu, Franziska Roesner, Tadayoshi Kohno, Ning Zhang, and Umar Farooq.</strong> "IsolateGPT: An Execution Isolation Architecture for LLM-Based Agentic Systems." <em>Network and Distributed System Security Symposium (NDSS)</em>, 2025. Introduces system-level execution isolation (SecGPT / IsolateGPT) separating untrusted apps, data channels, and tool execution in LLM agent platforms. [<a href="https://arxiv.org/abs/2403.04960" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Md Nazmul Islam Ananto, Pierre Prevost-Avenel, Colin Smith, Kyungtae Kim, Taegyu Kim, and Arslan Khan.</strong> "ToFu: Exploiting and Fuzzing the LLM-Orchestrator-Tool Trust Boundary." <em>arXiv preprint arXiv:2610.13651</em>, 2026. Analyzes the LLM-orchestrator-tool trust boundary across MCP servers and automatically derives CWE-guided semantic checks and fuzzing harnesses for LLM tools. [<a href="https://arxiv.org/abs/2610.13651" target="_blank">Paper</a>]
      </li>
    </ul>

    <p class="fw-bold mb-1 text-secondary">Optional Readings</p>
    <ul>
      <li>
        <strong>Tong Liu, Zizhuang Deng, Guozhu Meng, Yuekang Li, and Kai Chen.</strong> "Demystifying RCE Vulnerabilities in LLM-Integrated Apps." <em>ACM Conference on Computer and Communications Security (CCS)</em>, 2024. Systematically analyzes remote code execution vulnerabilities (LLMSmith) across real-world LLM orchestration frameworks. [<a href="https://arxiv.org/abs/2309.02926" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Sizhe Chen, Julien Piet, Chawin Sitawarin, and David Wagner.</strong> "StruQ: Defending Against Prompt Injection with Structured Queries." <em>34th USENIX Security Symposium (USENIX Security '25)</em>, 2025. Separates instructions and untrusted data channels using structured query interfaces and front-end filtering. [<a href="https://arxiv.org/abs/2402.06363" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Keegan Hines et al.</strong> "Defending Against Indirect Prompt Injection Attacks With Spotlighting." <em>CAMLIS</em>, 2024. Introduces datamarking, encoding, and delimiting transformations to help LLMs distinguish untrusted data from system instructions. [<a href="https://arxiv.org/abs/2403.14720" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Eric Wallace, Kai Xiao, Reimar Leike, Lilian Weng, Johannes Heidecke, and Alex Beutel.</strong> "The Instruction Hierarchy: Training LLMs to Prioritize Privileged Instructions." <em>arXiv preprint arXiv:2404.13208</em>, 2024. Defines explicit privilege levels across system prompts, user messages, and untrusted tool outputs. [<a href="https://arxiv.org/abs/2404.13208" target="_blank">Paper</a>]
      </li>
      <li>
        <strong>Yangjun Ruan et al.</strong> "Identifying the Risks of LM Agents with an LM-Emulated Sandbox (ToolEmu)." <em>ICLR</em>, 2024. Evaluates unsafe tool execution and failure modes of language-model agents using an emulated sandbox. [<a href="https://arxiv.org/abs/2309.15817" target="_blank">Paper</a>]
      </li>
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

### Option 2: Instructor-Defined Semester Project — slangGraph Tool Security

Students who do not follow the research-based project track will complete the instructor-defined project focused on **least-privilege policy inference and capability enforcement for agentic systems**.

* **Project Specification & Workspace:** [`slangGraph Security Workspace README`](https://github.com/Arslan8/slanggraph/blob/course/security-modules/workspace/README.md)
* **Project Branch:** [`course/security-modules`](https://github.com/Arslan8/slanggraph/tree/course/security-modules/workspace)

#### Overview

In agentic AI frameworks and graph-execution runtimes (such as **slangGraph**), autonomous agents execute actions by invoking external tools. Because tools interact with the physical operating system, network endpoints, file systems, databases, and peripheral devices, granting tools excessive ambient authority introduces severe security risks.

The goal of this project is to build an automated, explainable **Policy Inference Engine** that analyzes tool implementations, descriptors, and execution traces to synthesize precise, least-privilege capability manifests and enforce them at runtime using **Cedar** access control policies.

#### The Workspace & Hands-on Examples

The project workspace provides progressive reference examples demonstrating the runtime security contract:

1. `workspace/01_quickstart.py`: Minimal execution graph and tool invocation.
2. `workspace/02_dac_quickstart.py`: Tool-level Cedar discretionary access control.
3. `workspace/03_dac_principal_quickstart.py`: Authenticated caller principals passed during graph invocation.
4. `workspace/04_resource_grant_quickstart.py`: Mapping tool arguments to normalized resource operations, Cedar authorization, and exact enforceable grants.
5. `workspace/05_custom_class_quickstart.py` & `workspace/05_pump_simulator.py`: Fine-grained device operations on a custom `pump` class over a Unix-domain socket (demonstrating that transport access does not equal device authority).

#### What Students Must Build

Students are tasked with building a **Policy Inference Engine** that infers what authority a tool needs. The core pipeline is:

```text
tool implementation + descriptor + examples or traces
                         |
                         v
              inferred resource operations
                         |
                         v
          candidate manifest with supporting evidence
                         |
                         v
              review, validation, and refinement
                         |
                         v
             Cedar authorization per invocation
                         |
                         v
                 exact enforceable grant
```

The inference engine must determine:
* Which resources a tool can access (filesystem paths, database tables, Unix sockets, device controls, network origins).
* Which exact operations are performed on each resource (e.g., `inspect`, `start`, `set_flow`, `read`, `write`).
* Which tool arguments determine resource identity, and which trusted normalizers canonicalize them.
* Which capabilities are unconditionally required versus conditionally invoked based on input arguments or control flow.
* Overprivilege detection: whether the inferred manifest grants more authority than the implementation requires.
* Evidence and uncertainty: identifying code paths supported by concrete trace evidence versus untested paths.
* Robustness against adversarial inputs: verifying whether hostile inputs can escape inferred resource boundaries.
* Runtime grant enforcement: verifying that tool execution remains strictly within the authorized grant.

#### Success Criteria

A successful project must demonstrate:
1. **Least-Privilege Precision:** Allowed calls receive only the exact operations and resource identities they need.
2. **Fail-Closed Enforcement:** Missing or unauthorized operations prevent tool execution before dispatch.
3. **Overprivilege Detection:** Unnecessary operations or ambient permissions are flagged and eliminated.
4. **Resilient Normalization:** Path traversal and alternate spellings cannot bypass resource policies.
5. **Robust Error Handling:** Malformed, unknown, or adversarial inputs fail safely with informative diagnostics.
6. **Explainability:** Inferred policies include supporting evidence, confidence levels, and coverage gaps.
7. **Inspectable Artifacts:** Generated Cedar schemas, policies, and grant requests can be audited independently.

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
