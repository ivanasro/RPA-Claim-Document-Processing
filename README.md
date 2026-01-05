# Secure Claim Document Processing Automation (RPA Case Study)

> **Note:** This is a **sanitized case study** derived from real enterprise automation experience.  
> Company names, system names, file paths, and sample data have been generalized to protect confidentiality.

## Overview
This automation streamlines an internal claims document processing workflow by securely retrieving encrypted batch files, performing decryption and extraction, orchestrating folder structures, executing a desktop claim-processing application, and sending email notifications for success/failure.

## Business Problem
The process involved repetitive manual steps across multiple tools:
- Downloading batch files from an SFTP server
- Decrypting GPG files with a passphrase
- Extracting multi-part archives and arranging folders correctly
- Running multiple desktop application processes (batch cycle + daily report)
- Monitoring process completion and notifying stakeholders via email

Manual handling increased:
- Processing time and operational overhead
- Risk of human error (wrong folder, wrong cycle/date, missed steps)
- Delays in daily outputs and reporting

## Scope
### Inputs
- Encrypted batch archive from SFTP (GPG-protected, multi-part ZIP archive)

### Outputs
- Processed batch results (cycle-based output folders)
- Daily report output folders
- Email notification: **Success** or **Failure**

## High-Level Process Flow
1. **Retrieve file from SFTP**
   - Open SFTP client
   - Navigate to target folder
   - Download encrypted batch file

2. **Prepare cycle workspace**
   - Create a cycle folder structure
   - Move the encrypted file into the cycle workspace

3. **Decrypt & verify**
   - Decrypt the GPG file using a local decryption tool
   - Provide passphrase securely
   - Validate decrypted output

4. **Cleanup & extract**
   - Remove encrypted artifacts (optional policy-based cleanup)
   - Extract the ZIP content into structured folders

5. **Organize extracted content**
   - Ensure required folders are positioned correctly for downstream processing

6. **Run desktop claim-processing application**
   - Execute “Claim Letter” process
   - Select cycle/date parameters
   - Run process and confirm completion steps

7. **Run daily report process**
   - Execute daily report/BAST process (daily batch)

8. **Check notification trigger**
   - If email notification is required/available:
     - Send **Success** email when completed
     - Send **Failure** email when validation fails or processing errors occur

## Key Automation Concepts Demonstrated
- Secure file handling (SFTP download)
- Encryption/decryption workflow integration (GPG)
- Multi-part archive handling + extraction
- File & folder orchestration
- Desktop application automation (UI-driven steps)
- Decision points (validation checks, notification availability)
- Exception handling and outcome notification

## Exception Handling (Examples)
- **File not found / incomplete download**
- **Decryption failed** (invalid passphrase, corrupt file)
- **Archive extraction failed**
- **Unexpected folder structure**
- **Desktop app not responding / timeout**
- **Process result not generated / missing output**
- **Email notification send failure**

## Tools / Environment
- RPA Platform: **Automation Anywhere** (or equivalent)
- SFTP Client: Generic SFTP tool
- Decryption Tool: GPG decryption utility
- Archive Tool: ZIP extraction utility
- Target System: Internal desktop claims processing application

## Evidence
- Flow Diagram: see `docs/flow-diagram.pdf` (sanitized)

## How to Use This Repo (Portfolio)
This repository focuses on **process design and automation thinking**, not production source code, to ensure confidentiality.  
Recommended reviewers: recruiters, hiring managers, and RPA practitioners.

## Author
Ana — RPA / Process Automation

