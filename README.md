# 🚘 ServiceSync360

ServiceSync360 is a desktop customer relationship management (CRM) application designed for automotive service departments.

**Developed by a service advisor for service advisors,** ServiceSync360 brings customer, vehicle, service history, and repair order information into one focused interface, allowing authorized dealership employees to manage essential service workflows more efficiently.

The application was created as a Master of Science in Software Engineering capstone and inspired by my firsthand frustration with the fragmented and inefficient technology commonly used in automotive service departments. The current release is a functional proof of concept and a foundation for a more comprehensive dealership CRM.

---

## 📥 Download ServiceSync360

Installers are published in the separate public [ServiceSync360 Downloads repository](https://github.com/fhossain97/servicesync360-downloads/releases/tag/v0.1.2). The application source code remains private and is not included with the installers.

Choose the package that matches the computer's operating system and processor:

| Operating system | Processor                                   | Package           |
| ---------------- | ------------------------------------------- | ----------------- |
| macOS            | Apple Silicon, including M1, M2, M3, and M4 | macOS ARM64 DMG   |
| macOS            | Intel                                       | macOS x64 DMG     |
| Windows          | ARM64                                       | Windows ARM64 EXE |
| Windows          | x64                                         | Windows x64 EXE   |

## 🛠️ Installation

### macOS

1. Download the DMG that matches the Mac's processor.
2. Open the downloaded DMG.
3. Drag ServiceSync360 into the Applications folder.
4. Open ServiceSync360 from Applications.

The current macOS build is not signed or notarized with an Apple Developer certificate. Gatekeeper may therefore prevent the application from opening the first time.

If macOS provides an **Open Anyway** option:

1. Attempt to open ServiceSync360 once.
2. Open **System Settings**.
3. Select **Privacy & Security**.
4. Find the ServiceSync360 security message and select **Open Anyway**.
5. Confirm the launch when prompted.

If the warning only provides **Move to Trash** and **Cancel**, select **Cancel**. Then open Terminal and confirm the installed application path:

```bash
find /Applications -maxdepth 1 -iname "*servicesync360*.app" -print
```

If the command returns `/Applications/servicesync360.app`, remove the quarantine attribute from only that application and reopen it:

```bash
sudo xattr -dr com.apple.quarantine "/Applications/servicesync360.app"
open "/Applications/servicesync360.app"
```

Enter the Mac login password when prompted. Terminal does not display password characters while they are entered. If the `find` command returns a differently capitalized application path, use that exact path in both commands.

This procedure removes the download quarantine attribute only from ServiceSync360; it does not disable Gatekeeper for other applications. Only perform this override after downloading the installer from the official release repository and confirming that the expected application was copied into the Applications folder. Do not override a warning stating that the application **will damage your computer**.

### Windows

1. Download the EXE that matches the computer's processor.
2. Open the installer.
3. Follow the installation prompts.
4. Launch ServiceSync360 after installation is complete.

## 🔐 Demonstration Accounts

The accounts below are provided only for capstone testing and demonstration. Do not reuse these passwords or enter real customer information while evaluating the application.

| Role            | Email                               | Password                 |
| --------------- | ----------------------------------- | ------------------------ |
| Manager         | `servicesync360.admin@gmail.com`    | `mushusync$360_admin`    |
| Service Advisor | `servicesync360.nonadmin@gmail.com` | `mushusync$360_nonadmin` |

The application may preserve an authenticated session between launches. Sign out before switching roles.

## 📦 Source and Distribution

- The private [ServiceSync360 repository](https://github.com/fhossain97/servicesync360) contains the application source code.
- The public [ServiceSync360 Downloads repository](https://github.com/fhossain97/servicesync360-downloads) contains downloadable release packages.
- The current installer release is [v0.1.2](https://github.com/fhossain97/servicesync360-downloads/releases/tag/v0.1.2).

## 🔒 Privacy and Testing

ServiceSync360 stores customer, vehicle, service, and repair order information. Use fictional data during testing. Do not enter payment information, driver's license data, insurance documents, or other sensitive information that falls outside the approved capstone scope.

## © Copyright and Use Restrictions

Copyright © 2026 ServiceSync360. All rights reserved.

ServiceSync360, including its source code, documentation, interface designs, downloadable builds, and related project materials, is the original work of Farhana Hossain. These materials may not be copied, redistributed, republished, modified, sold, sublicensed, reverse engineered, or used to create derivative works without prior written permission, except where permitted by applicable law. Access to a demonstration account or installer is provided only for authorized evaluation and does not transfer ownership or grant permission for further distribution or reuse.

Third-party frameworks, libraries, services, names, and trademarks remain subject to their respective owners' licenses and rights.

## 🐰 Author

Farhana Hossain<br>
Full-Stack Software Engineer<br>
Master of Science in Software Engineering<br>
