# Process Injection — Concepts, Risks and Detection Methods

## Overview

This project is based on my final-year thesis (*Travail de Fin d'Études — TFE*), completed during an academic internship at **Fraunhofer FKIE**, in Bonn, Germany, within the **Cyber Analysis and Defense (CAD)** department.

The thesis explores Windows process injection techniques, direct system calls, and their implications for endpoint security. The practical work involved developing and testing a proof of concept (PoC) in a controlled Windows environment to better understand how these techniques operate and how security solutions may detect them.

**This project is strictly academic. All experiments were conducted in controlled testing environments for educational and defensive research purposes.**

## Objectives

The main objectives of this project were to:

- Understand Windows user mode and kernel mode interactions.
- Study the role of `ntdll.dll` in Windows system calls.
- Investigate direct system calls and System Service Numbers (SSNs).
- Understand user-mode API hooking and its role in endpoint detection.
- Study and compare several frameworks for generating system call wrappers.
- Develop and test a proof of concept in a controlled environment.
- Observe how antivirus solutions respond to different implementations.
- Explore the limitations of static and dynamic detection mechanisms.

## Frameworks Studied

The project focused on the following frameworks and techniques:

| Framework | Description | Scope |
|---|---|---|
| **SysWhispers1** | Generates assembly stubs and wrappers for direct system calls. | Implemented and tested |
| **FreshyCalls** | Explores alternative mechanisms for invoking Windows system calls. | Implemented and tested |
| **SysWhispers3** | Supports different system call invocation techniques. | Implemented and tested |
| **ShellWasp** | Studied as an alternative approach to system call invocation. | Theoretical study only |

ShellWasp was not fully implemented or experimentally evaluated because of time constraints.

## Experimental Methodology

The practical work involved developing a proof of concept to study process injection and system call invocation in Windows.

The test scenario attempted to launch Windows Calculator (`calc.exe`) from within an already running Notepad (`notepad.exe`) process.

The experiments were performed in two configurations:

1. **Unprotected environment:** The implementations were compiled and executed to verify their basic functionality.
2. **Antivirus-protected environment:** The implementations were tested to observe whether the security products detected them.

The results were recorded for each tested implementation and compared under the specific experimental conditions.

### Security Products

The tests included the following antivirus solutions:

- Microsoft Defender
- Avast
- AVG

Detection results were treated as observations from the tested configurations, rather than as universal conclusions about the capabilities of each security product.

## Results

### Execution Tests

In the unprotected test environment, all three implemented frameworks — SysWhispers1, FreshyCalls, and SysWhispers3 — compiled and executed successfully.

### Antivirus Detection Results

The following table summarizes the observations obtained during the experiments.

| Framework | Microsoft Defender | Avast | AVG |
|---|---|---|---|
| **SysWhispers1** | Detected | Detected | Detected |
| **FreshyCalls** | Not detected | Detected | Detected |
| **SysWhispers3** | Detected | Detected | Detected |

These results apply only to the specific implementations, configurations, and testing conditions used during the project. They should not be interpreted as a general ranking of antivirus products or as a guarantee of detection or evasion in other environments.

One relevant implementation detail is that the tested SysWhispers3 implementation did not include an egghunter, which may have influenced the observed detection results.

## Technical Stack

The project involved the following technologies and tools.

### Programming Languages

- C
- C++
- x86-64 Assembly

### Development and Analysis Tools

- **Visual Studio:** Development and compilation.
- **x64dbg:** Dynamic debugging and runtime analysis.
- **Ghidra:** Static analysis and reverse engineering.

### Windows Internals and Security Concepts

- Windows user mode and kernel mode
- `ntdll.dll`
- System Service Numbers (SSNs)
- Direct and dynamic system call invocation
- User-mode API hooking
- Process memory and remote thread execution
- Static and dynamic analysis
- Antivirus detection mechanisms

## Limitations

The findings of this project are subject to several limitations:

- The experiments were conducted in a controlled academic environment.
- Detection outcomes depend on the tested implementation, system configuration, and security product version.
- The results represent observations from a limited set of experiments and do not establish the general effectiveness of a security product.
- ShellWasp was studied theoretically but was not fully implemented or tested.
- The tested SysWhispers3 implementation did not include an egghunter.

These limitations should be considered when interpreting the results.

## Skills Demonstrated

This project provided practical experience in:

- Windows internals and operating system concepts.
- Low-level programming in C, C++, and x86-64 Assembly.
- System call mechanisms and process interaction.
- Static analysis, debugging, and reverse engineering.
- Experimental testing and technical documentation.
- Understanding endpoint security and antivirus detection mechanisms.
- Conducting security research in a controlled environment.

## Academic Context and Responsible Use

This work was completed as part of an academic final-year thesis during an internship at Fraunhofer FKIE in Bonn, Germany.

All practical tests were conducted in controlled environments for educational and defensive research purposes. The project is intended to document operating system mechanisms, analyze security behavior, and support further study of detection and mitigation techniques.

It is **not intended for unauthorized access, deployment against third-party systems, or malicious use**.

## Future Work

The repository also serves as a foundation for further personal research into Windows internals, reverse engineering, and defensive detection techniques.

- **Finalize ShellWasp:** Complete the technical study and conduct a controlled experimental evaluation.
- **Expand detection analysis:** Investigate Windows telemetry, Sysmon events, and detection rules using Wazuh.
- **Test across Windows versions:** Compare observations across different Windows versions and builds.
- **Automate experiments:** Develop a Python script to collect logs, organize results, and generate reports.
- **Investigate additional detection mechanisms:** Explore ETW and kernel-level telemetry from a defensive perspective.
- **Extend the evaluation:** Study additional security products and compare the observable behaviors of selected system call techniques.

These are the main areas I plan to explore as I continue developing this project.

## Author

**Emre Duran**

Bachelor's degree in Computer Science — Application Development  
Haute École de la Province de Liège (HEPL)

**Internship:** Fraunhofer FKIE — Cyber Analysis and Defense (CAD)  
**Location:** Bonn, Germany  
**Academic year:** 2025–2026
