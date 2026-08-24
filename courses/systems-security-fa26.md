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

Short quizzes will be given after major course modules. These quizzes are intended to assess understanding of systems-security concepts, mechanisms, attacks, and design tradeoffs.

### Week 1 — August 25 & 27: Systems Security Foundations

* Threat models and security goals
* Security policies versus mechanisms
* Trusted Computing Base
* Reference monitors
* Protection domains
* Least privilege
* User/kernel boundary
* Attack surfaces
* Fundamental principles of secure-system design

### Week 2 — September 1 & 3: Memory Safety and Exploitation

* Process memory layout
* Stack and heap memory
* Buffer overflows
* Stack corruption
* Heap corruption
* Use-after-free vulnerabilities
* Double-free vulnerabilities
* Integer vulnerabilities
* Spatial and temporal memory safety
* Control-flow hijacking
* Return-Oriented Programming

### Week 3 — September 8 & 10: Memory-Safety Defenses

* Stack canaries
* NX / DEP
* Address Space Layout Randomization
* RELRO
* Control-Flow Integrity
* Shadow stacks
* Pointer Authentication
* Memory tagging
* Hardware-assisted memory safety
* Memory-safe programming languages
* Limitations and bypasses of modern mitigations

**Module Quiz**

### Week 4 — September 15 & 17: Kernel Security

* Kernel attack surface
* System calls and the user/kernel boundary
* Kernel memory corruption
* Kernel privilege escalation
* Kernel drivers
* Driver security
* Kernel exploitation
* Kernel hardening
* Kernel attack-surface reduction
* Modern kernel defense mechanisms

**Module Quiz**

### Week 5 — September 22 & 24: Access Control

* Access-control matrix
* Access Control Lists
* Unix file permissions
* Users and groups
* UID, EUID, and SUID
* `setuid` and `setgid`
* Linux capabilities
* Discretionary Access Control
* Confused deputy attacks
* Capability-based security
* Privilege transitions

**Research-based semester project proposals are due Thursday, September 24.**

Students who wish to pursue their own research project must submit a proposal by this date. Students without an approved research proposal will complete the instructor-defined semester project.

### Week 6 — September 29 & October 1: Mandatory Access Control and SELinux

* Discretionary versus Mandatory Access Control
* Bell-LaPadula
* Biba
* Multi-Level Security
* Linux Security Modules
* SELinux
* AppArmor
* Labels and security domains
* Type Enforcement
* Policy transitions
* Landlock
* Reference-monitor implementation

**Module Quiz**

### Week 7 — October 6 & 8: Virtualization

* Virtual machines and hypervisors
* Type-1 and Type-2 hypervisors
* Privileged and unprivileged execution
* Hardware-assisted virtualization
* VM exits
* CPU virtualization
* Memory virtualization
* Extended/Nested Page Tables
* Device virtualization
* Emulated and paravirtualized devices
* KVM and QEMU
* VirtIO
* VM isolation
* VM escape attacks
* Virtual machines as security boundaries

### Week 8 — October 13 & 15: Confidential Computing

* Threat models in cloud computing
* Trusted Execution Environments
* Intel SGX
* Intel TDX
* AMD SEV
* AMD SEV-SNP
* Memory encryption
* Confidential virtual machines
* Protecting workloads from the hypervisor
* Remote attestation
* Measurement and trust establishment
* I/O challenges in confidential systems
* Limitations of confidential computing

**Module Quiz**

### Week 9 — October 20 & 22: Linux Isolation Primitives

This module examines the mechanisms from which modern Linux containers and application sandboxes are constructed.

* `chroot`
* Filesystem isolation
* Mounts and bind mounts
* `pivot_root`
* Linux namespaces
* User namespaces
* PID namespaces
* Mount namespaces
* Network namespaces
* IPC namespaces
* UTS namespaces
* cgroups
* Linux capabilities
* `seccomp`
* seccomp-BPF
* `no_new_privs`
* `unshare`
* `nsenter`
* Rootless isolation

Students should leave this module understanding the individual mechanisms behind a container rather than viewing containers as a primitive provided by the operating system.

### Week 10 — October 27 & 29: Containers and Sandboxing

* What a container actually is
* Constructing containers from Linux isolation primitives
* OCI container model
* `runc`
* containerd
* Docker architecture
* Container root filesystems
* OverlayFS
* Rootless containers
* Privileged containers
* Container capabilities
* Container escape vulnerabilities
* Dangerous mounts and configurations
* Docker socket exposure
* Bubblewrap (`bwrap`)
* Firejail
* `systemd-nspawn`
* Building application sandboxes from first principles
* Containers versus virtual machines

**Module Quiz**

### Week 11 — November 3 & 5: Compartmentalization

* Privilege separation
* Least-privilege decomposition
* Process-based compartmentalization
* Capability-oriented systems
* Capsicum
* `pledge` and `unveil`
* Intel Memory Protection Keys
* ERIM
* RLBox
* Automatic compartmentalization
* Compartment interfaces
* Cross-compartment communication
* Attack-surface reduction
* Security and performance tradeoffs

**Module Quiz**

### Week 12 — November 10 & 12: Accelerators and Heterogeneous-System Security

Modern applications, particularly machine-learning systems, increasingly depend on GPUs and other accelerators. This module examines how these devices interact with operating-system security mechanisms.

* CPU-accelerator architecture
* GPU execution model
* Host and device memory
* GPU virtual memory
* GPU runtimes and drivers
* PCIe
* Direct Memory Access
* IOMMUs
* Device assignment and passthrough
* Accelerator multi-tenancy
* GPU process isolation
* SR-IOV
* MIG and hardware partitioning
* Accelerator drivers as part of the Trusted Computing Base
* CPU-GPU trust boundaries
* Isolation failures in heterogeneous systems
* Security implications for machine-learning workloads

### Week 13 — November 17 & 19: Confidential Accelerators and Agentic Systems

#### Confidential Accelerators and ML Systems

* Confidential GPU computing
* GPU and accelerator attestation
* Confidential VMs with accelerators
* Intel TDX and accelerator workloads
* AMD SEV-SNP and accelerator workloads
* Protected CPU-GPU communication
* Trusted I/O
* Device identity and attestation chains
* Model confidentiality
* Training-data confidentiality
* Confidential inference
* Confidential training
* Security boundaries in modern ML infrastructure

#### Agentic Systems Security

* Agent architectures
* LLM-to-tool trust boundaries
* Tool permissions and capabilities
* Agent sandboxing
* Untrusted tool outputs
* Persistent agent state and memory
* Security of autonomous actions
* Multi-agent trust boundaries
* Risks introduced by increasingly autonomous systems

**Module Quiz**

### November 22-28: Thanksgiving Holiday — No Classes

There are no classes during Penn State's Thanksgiving holiday.

### Week 14 — December 1 & 3: Semester Project Presentations and Demonstrations

The final two instructional weeks are reserved entirely for semester projects.

Students will present their systems, demonstrate their technical artifacts, explain their design decisions, discuss their security model and evaluation, and answer technical questions about their work.

### Week 15 — December 8 & 10: Semester Project Presentations and Demonstrations

Semester project presentations and demonstrations continue.

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
