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

---

## ✨ Current Features

- Secure authentication with multi-factor authentication and role-based permissions
- Dealership and tenant-based separation of users and records
- Manager-controlled user access and role assignment
- Customer and vehicle profile creation and updates
- Global search using supported customer and vehicle information
- Vehicle service history review
- Repair order creation, editing, finalization, PDF generation, and voiding
- Unique repair order numbers and repair order lookup
- Mileage and tag number entry during intake
- Service line, labor, pay type, technician, and parts entry
- Automatic totals based on approved services and parts
- Active repair order status and progress tracking
- AI-assisted service recommendations
- Read-only audit log accessible only through the authorized API with a Manager account
- Desktop installers for supported macOS and Windows architectures

## 🧭 Using the CRM

### 1. Sign in

Launch ServiceSync360 and sign in with one of the demonstration accounts. Available pages and actions depend on whether the account is assigned the Manager or Service Advisor role.

### 2. Find an existing record

Use global search to locate a customer or vehicle by supported information such as name, phone number, vehicle identification number, or license plate. Open a result to review the customer profile, vehicle details, and available service history. Repair orders can also be retrieved by repair order number.

### 3. Create a customer and vehicle

Use the new-record workflow when a customer or vehicle is not already stored:

1. Enter the required customer information.
2. Enter the vehicle year, make, model, color, vehicle identification number, and license plate.
3. Review the information for accuracy.
4. Save the record.

Search for an existing record before creating a new one to reduce duplicate entries.

### 4. Create a repair order

1. Open the appropriate customer and vehicle record.
2. Select **Create RO**.
3. Enter the vehicle's current mileage and tag number.
4. Add service lines manually or generate AI-assisted recommendations.
5. Review the pay type, labor, rate, parts, and total for each service line.
6. Save the repair order.

The mileage entered during intake becomes the repair order's starting mileage and provides context for AI-assisted recommendations.

### 5. Review AI-assisted recommendations

Recommendations are generated from available vehicle information, current mileage, configured services, and service history. To use them:

1. Enter the current mileage.
2. Select **Generate Recommendations**.
3. Review each recommendation and its explanation.
4. Add only the services that are appropriate for the vehicle and customer.
5. Edit or replace a selection when professional judgment requires it.

AI output may be incomplete or inaccurate. Recommendations provide decision support and must be checked against the vehicle's condition, available service history, and applicable manufacturer guidance. A recommendation is not added to the repair order until an authorized user approves it.

### 6. Manage an active repair order

Open **Active Repair Orders** to review work that has not been finalized or voided. Depending on the available actions, an authorized user can open the repair order, update permitted information, finalize it, or void it with a reason.

### 7. Finalize a repair order

1. Open the repair order's finalization workflow.
2. Review the customer and vehicle information.
3. Expand each service line and verify its labor, rate, pay type, technicians, and parts.
4. Enter the mileage out.
5. Confirm the repair order total.
6. Finalize the repair order.

Finalization produces a PDF containing dealership, customer, vehicle, mileage, service, parts, date, and total information. Review the document before providing it to a customer.

### 8. Void a repair order

Use the void action only when a repair order should not continue. Enter a clear business reason and confirm the action. The record remains available for history and auditing instead of being deleted.

### 9. Use manager functions

The Manager account can access user management and other authorized administrative functions. The Service Advisor account is intentionally denied access to manager-only operations. The audit log does not have a dashboard or other user-interface page. It is read-only and can be accessed only through authorized API requests made with a Manager account.

## 🛡️ Roles and Access

| Capability                                                | Manager | Service Advisor |
| --------------------------------------------------------- | :-----: | :-------------: |
| Access permitted dealership records                       |   Yes   |       Yes       |
| Manage customer and vehicle records                       |   Yes   |       Yes       |
| Create and manage repair orders                           |   Yes   |       Yes       |
| Review AI-assisted recommendations                        |   Yes   |       Yes       |
| Manage application users                                  |   Yes   |       No        |
| Access the read-only audit log through the authorized API |   Yes   |       No        |

Permissions are enforced by both the application and its server procedures. Interface visibility alone is not used as the security control.

## 📌 Current Scope and Limitations

The capstone release focuses on customer and vehicle records, search, service history, the repair order lifecycle, advisor-reviewed recommendations, access control, and auditability. It is intended for controlled testing and demonstration rather than production dealership use.

The current release does not include appointment scheduling, detailed technician service tracking, loaner vehicle management, customer-facing access, real-time customer notifications, digital customer approvals, automated follow-up scheduling, external dealership-system integrations, advanced reporting, or production-ready offline synchronization. Payment information, driver's license records, and insurance documents are also outside the approved data scope.

Apple Developer signing and notarization, broad operating-system certification, multi-dealership production deployment, and large-scale load testing are not included in this release.

---

## 🛣️ Future Development

ServiceSync360 was designed as a foundation that can be expanded beyond the capstone. Planned development includes the following areas.

### Service workflow

- Add appointment scheduling and calendar-based service planning.
- Introduce detailed technician service tracking, including work progress and time recorded against individual service lines.
- Support technician inspection photos and videos within the repair order.
- Add configurable repair order assignment while preserving manager override controls.
- Add loaner vehicle availability, assignment, and return tracking.
- Support automated follow-up scheduling and next-service reminders.

### Customer experience

- Provide a secure customer-facing experience for viewing service progress.
- Send direct status updates as repair order work advances.
- Add digital approval or decline options for recommended services.
- Expand digital documentation while keeping sensitive payment, driver's license, and insurance information protected by an approved data-handling design.

### Data and dealership integration

- Connect approved external service history sources to improve record completeness.
- Expand ServiceSync360 beyond the service department into a dealership-wide CRM supporting Parts, Finance, Administration, Sales, and other approved departments.
- Add department-specific workflows, permissions, and shared records so authorized employees can work across dealership operations without losing role-based control.
- Integrate with dealership management, parts inventory, and other authorized operational systems.
- Support secure multi-dealership deployment with stronger tenant administration and data separation controls.
- Add reliable offline operation, recovery, and synchronization for interrupted connections.

### Reporting and intelligence

- Add management dashboards for service metrics, repair order summaries, service history trends, and advisor activity.
- Expand audit reporting while preserving read-only audit records.
- Measure the use and outcomes of AI-assisted recommendations.
- Develop a more specialized automotive AI system that learns from approved service outcomes while continuing to require professional review.

### Production readiness

- Add Apple Developer signing and notarization and strengthen installer trust for supported platforms. This requirement may change in the future as the CRM progresses.
- Expand operating-system compatibility testing, automated regression testing, performance testing, monitoring, backup, and recovery procedures.
- Prepare the application for controlled production deployment, release management, and ongoing support.

Future features will be introduced in phases so that security, data integrity, and the stability of the repair order workflow remain the primary priorities.

---

## 🔄 Implementation Approach

ServiceSync360 was implemented using an Agile approach that allowed requirements, workflows, and features to be developed, tested, and refined incrementally throughout the project. Development prioritized the core customer, vehicle, and repair order workflows before moving into supporting features and application refinements. The architecture was designed as a secure multitenant system that separates dealership data and restricts access through multi-factor authentication, role-based permissions, protected server procedures, and tenant-level authorization. Security, data privacy, auditability, and data persistence were considered throughout implementation rather than being treated as final-stage additions. Continuous testing and refactoring were also used to validate system functionality, repair order processing, user access, and dealership data separation.

## 🧱 Technology

ServiceSync360 uses:

- [Electron](https://www.electronjs.org/) for the desktop application shell
- [Next.js](https://nextjs.org/) and [React](https://react.dev/) for the application interface
- [TypeScript](https://www.typescriptlang.org/) for typed application development
- [Material UI](https://mui.com/) for interface components
- [tRPC](https://trpc.io/) for typed client-server procedures
- [Prisma](https://www.prisma.io/) and [PostgreSQL](https://www.postgresql.org/) for relational data access and persistence
- [Auth0](https://auth0.com/) and NextAuth for authentication and session handling
- [OpenAI](https://openai.com/) for advisor-facing service recommendations
- [PDF-LIB](https://pdf-lib.js.org/) for repair order document generation
- [Railway](https://railway.com/) for hosted application infrastructure
- GitHub Actions for desktop packaging and release automation

## 📦 Source and Distribution

- The private ServiceSync360 repository contains the application source code.
- The public [ServiceSync360 Downloads repository](https://github.com/fhossain97/servicesync360-downloads) contains downloadable release packages.
- The current installer release is [v0.1.2](https://github.com/fhossain97/servicesync360-downloads/releases/tag/v0.1.2).

## 🔒 Privacy and Testing

ServiceSync360 stores customer, vehicle, service, and repair order information. Use fictional data during testing. Do not enter payment information, driver's license data, insurance documents, or other sensitive information that falls outside the approved capstone scope.

## ✅ Project Status

ServiceSync360's current release demonstrates the core CRM workflow and provides a tested foundation for the future development described above.

---

## © Copyright and Use Restrictions

Copyright © 2026 ServiceSync360. All rights reserved.

ServiceSync360, including its source code, documentation, interface designs, downloadable builds, and related project materials, is the original work of Farhana Hossain. These materials may not be copied, redistributed, republished, modified, sold, sublicensed, reverse engineered, or used to create derivative works without prior written permission, except where permitted by applicable law. Access to a demonstration account or installer is provided only for authorized evaluation and does not transfer ownership or grant permission for further distribution or reuse.

Third-party frameworks, libraries, services, names, and trademarks remain subject to their respective owners' licenses and rights.

## 🐰 Author

Farhana Hossain<br>
Full-Stack Software Engineer<br>
Master of Science in Software Engineering<br>
