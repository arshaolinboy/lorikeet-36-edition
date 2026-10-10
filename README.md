# Lorikeet 36 Edition

**Power system study automation, analysis, and reporting for PSS®E 36.**

Lorikeet is a Windows desktop application developed to make everyday power system planning studies more manageable. It brings scenario preparation, simulation execution, results analysis, and reporting into one workspace.

The application is available free of charge for engineers at utilities, system operators, consultancies, and other power-sector organisations.

## Download

Open the **Releases** section of this repository, select the latest release, and download **Lorikeet 36 Edition.exe** under **Assets**.

The “Source code” ZIP and TAR.GZ files automatically shown by GitHub are not the application.

## Main capabilities

- Load-flow studies, interbus transformer contingencies, and selected N-1 and double-circuit N-2 line-outage studies.
- Bus-voltage and short-circuit assessments, including breaker-duty screening against user-supplied ratings.
- Dynamic stability simulations involving faults, equipment trips, and staged disturbances.
- Low- and high-voltage ride-through simulations.
- Oscillation damping analysis and assessment of recorded rotor-angle, frequency, and voltage responses.
- Scenario comparisons, customisable plots, and Excel reports.
- Configurable study criteria, utility-specific breaker data, and an integrated offline guide.

## Requirements

- A Windows x64 workstation capable of running your installed PSS®E release.
- A separately installed and licensed PSS®E 36.
- Microsoft Edge WebView2 Runtime and compatible Microsoft .NET Framework components.
- Permission to write to the local application cache and your study workspace.
- Your own network models, dynamic data, and any required custom-model DLLs.

The portable application includes its Python worker runtime and supporting packages. Anaconda and Miniconda are not required.

The bundled worker targets the PSSPY314 interface. If your PSS®E 36 installation uses a different Python interface, select a compatible interpreter under **Settings → Workstation**.

Compatibility and validation details are provided in each release’s notes.

## Getting started

1. Download the executable from Releases.
2. Place it in a dedicated application folder.
3. Launch Lorikeet and allow its local runtime preparation to complete.
4. Open **Settings → Workstation** and check PSS®E readiness.
5. Select your study workspace and prepare the required SAV and DYR files.
6. Import breaker ratings if you need breaker-duty assessment.
7. Review the study criteria and configure them for your system.
8. Press **F1** to open the guide and follow the first-study walkthrough.

Start with a known study case and compare the results with your established workflow.

## Frequently asked questions

### Do I need Anaconda or Miniconda?

No. The portable release includes the worker environment for its supported configuration.

### Do I need a separate Python installation?

Normally no. A different PSS®E Python interface may require selecting an alternative compatible interpreter.

### Does Lorikeet include PSS®E?

No. PSS®E and its licence must be obtained and installed separately.

### Can I use PSS®E 33 or other verions?

No. This edition targets PSS®E 36.

### Is Lorikeet free to use?

Yes. No fee is charged for using Lorikeet. PSS®E licensing remains separate.

### Is the source code included?

No. This repository distributes the compiled application and its documentation.

### Can I use my own study criteria and breaker data?

Yes. Configure your project criteria in Settings and import breaker ratings using the CSV format explained in the application.

### Does contingency screening cover every circuit?

The current N-1 routine selects circuit ID “1”; the N-2 routine covers paired circuits “1” and “2”. Review these conventions against your network model before running the study.

### Does Lorikeet replace engineering review?

No. Automated findings depend on the supplied models, selected scenarios, recorded channels, and configured criteria. Engineers should review the assumptions and results before using them in decisions or formal reports.

### How can I report a problem or suggest an improvement?

Open an issue in this repository. Include the Lorikeet version, PSS®E version, relevant configuration, steps to reproduce the problem, and a screenshot or sanitised error log.

Do not upload confidential network models, licence information, or internal utility data.

## Acknowledgements

Developed by Benaverd Rizanda Putra Leihitu.

I gratefully acknowledge the shared knowledge, discussions, and practical experience of the Perencanaan Sistem (Power System Planning) team at PLN UIP2B JAMALI, the Java–Madura–Bali power system operator.

Special thanks to RO and FH for their contributions to developing the voltage ride-through automation script incorporated into Lorikeet’s LVRT and HVRT workflows.

Application credit: **Leawaka Amapati**.
