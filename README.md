# Lorikeet 36 Edition

**Power system study automation, analysis and reporting for PSS®E 36.**

Lorikeet is a Windows desktop application that makes everyday power system planning studies easier to manage. Scenario preparation, simulation runs, results analysis and reporting all happen in one workspace.

The application is free of charge for engineers at utilities, system operators, consultancies and other power-sector organisations.

## Download

1. Open **Releases** in this repository and select the latest release.
2. Under **Assets**, download **Lorikeet 36 Edition.exe**.

The "Source code" ZIP and TAR.GZ files that GitHub adds to every release are not the application.

## Main capabilities

- **Load flow and contingency studies.** IBT (interbus transformer) contingencies, N-1 line outages and double-circuit N-2 line outages.
- **Independent contingencies.** Every contingency starts from the same solved base case, so results do not depend on run order.
- **Automatic handling of isolated buses.** Some outages leave buses with no path to a swing bus. Lorikeet finds those buses with PSS®E's TREE check and disconnects them before solving, so the rest of the network can still be solved.
- **Retry of non-converged contingencies.** A contingency that does not converge is retried once, starting from the solved base case instead of a flat start. Tolerances are not relaxed.
- **Bus voltage and short-circuit assessment.** Includes breaker-duty screening against breaker ratings you supply.
- **Dynamic stability simulations** of faults, equipment trips and staged disturbances.
- **Low- and high-voltage ride-through (LVRT/HVRT) simulations.**
- **Oscillation damping analysis**, plus assessment of the recorded rotor-angle, frequency and voltage responses.
- **Findings** against your study criteria, with before/after scenario comparison.
- **Customisable plots and Excel reports.** The Load Flow workbook can be written in English or Bahasa Indonesia.
- **Configurable everything else:** study criteria, utility-specific breaker data, a customisation page that explains every option, and an offline guide (press **F1**).

## How contingency results are reported

Every contingency's loading percentages are shown in the workbook. The note on each column header, and the `06 solution check` sheet, say how far to trust them:

- **Converged.** A normal PSS®E solution.
- **Islanded.** Buses were cut off by the outage and disconnected before solving. Branches to those buses show 0 %. The note lists the bus numbers, and Findings reports the islanding, because the load or generation on those buses is lost.
- **Converged on retry.** The solution came from the warm-start retry.
- **Not converged.** The values are PSS®E's last iteration, not a valid solution. They are not used for ranking or Findings, and the case is saved as a SAV so you can open it in the PSS®E GUI.

Lorikeet never modifies your SAV or DYR files.

## Requirements

- A Windows x64 workstation that can run your installed PSS®E release.
- A separately installed and licensed PSS®E 36.
- Microsoft Edge WebView2 Runtime and compatible Microsoft .NET Framework components.
- Permission to write to the local application cache and to your study workspace.
- Your own network models, dynamic data and any required custom-model DLLs.

The portable application includes its own Python worker runtime and supporting packages. You do not need Anaconda or Miniconda.

The bundled worker uses the PSSPY314 interface (Python 3.14). If your PSS®E 36 installation has no PSSPY314 folder, select a matching 64-bit Python under **Settings → Workstation**. For example, choose Python 3.11 for PSSPY311.

Each release's notes give its compatibility and validation details.

## Getting started

1. Download the executable from Releases.
2. Put it in a dedicated application folder.
3. Launch Lorikeet and let it finish preparing its local runtime.
4. Open **Settings → Workstation** and check that PSS®E 36 shows as ready.
5. Open your study workspace. Put SAV files in `00 sav-scenarios` and DYR files in `00 dyr`.
6. In **Settings → Breaker data**, import your breaker ratings if you need breaker-duty assessment. The breaker table ships empty.
7. In **Settings → Study criteria**, set the limits for your system.
8. Review **Settings → Customisation**: workbook language, which studies run, and solve options.
9. Press **F1** and follow **Getting started** and **Your first Load Flow study**.

Start with a known study case and compare the results with your established workflow.

## Frequently asked questions

### Do I need Anaconda or Miniconda?

No. The portable release includes the worker environment for its supported configuration.

### Do I need a separate Python installation?

Normally, no. Only a PSS®E installation without a PSSPY314 folder needs a separate, matching 64-bit Python.

### Does Lorikeet include PSS®E?

No. PSS®E and its licence must be obtained and installed separately.

### Can I use PSS®E 33 or other versions?

No. This edition supports PSS®E 36 only.

### Is Lorikeet free to use?

Yes. There is no fee for using Lorikeet. PSS®E licensing is separate.

### Is the source code included?

No. This repository distributes the compiled application and its documentation.

### Can I use my own study criteria and breaker data?

Yes. Set your project criteria in **Settings → Study criteria**. Import breaker ratings with the CSV format explained in **Settings → Breaker data**.

### Does contingency screening cover every circuit?

No. The N-1 routine outages circuit ID "1" of each line connected to a monitored bus. The N-2 routine outages circuits "1" and "2" of the same corridor together. Check these conventions against your network model before running a study.

### Why does a contingency show "ISLANDED" or "NOT CONVERGED" in its header note?

**Islanded:** the outage cut some buses off from every swing bus. Lorikeet disconnected them and solved the rest of the network.

**Not converged:** PSS®E could not solve the case even after isolated buses were disconnected and the case was retried from the solved base case. This usually means very heavy loading or voltage collapse. The values shown are only an indication. Open the saved case from `01 lf-outputs/Unsolved cases` in the PSS®E GUI.

### Does Lorikeet replace engineering review?

No. Automated findings depend on the supplied models, the selected scenarios, the recorded channels and the configured criteria. Engineers should review the assumptions and results before using them in decisions or formal reports.

### How can I report a problem or suggest an improvement?

Open an issue in this repository. Include:

- the Lorikeet version and PSS®E version;
- the relevant configuration;
- the steps to reproduce the problem;
- a screenshot or a sanitised error log.

Do not upload confidential network models, licence information or internal utility data.

## Disclaimer

PSS®E is a registered trademark of Siemens. Lorikeet is an independent tool and is not affiliated with, endorsed by or supported by Siemens. Lorikeet is provided as is, without warranty. Users are responsible for verifying all results.

## Acknowledgements

Developed by Benaverd Rizanda Putra Leihitu.

I gratefully acknowledge the shared knowledge, discussions and practical experience of the Perencanaan Sistem (Power System Planning) team (M, EA, IGRS, IL, NUA, JFS, FN, RO, FH, DRD, RH) at PLN UIP2B JAMALI, the Java–Madura–Bali power system operator.

Special thanks to RO and FH for their contributions to the voltage ride-through automation script used in Lorikeet's LVRT and HVRT workflows.

Application credit: **Leawaka © Amapati**.
