# NetworkWalks – Week 4: Penetration Testing Project

## Mediroza General Hospital | Black-Box Penetration Testing

**Program:** NetworkWalks Cybersecurity Internship  
**Batch:** B084  
**Project:** Week 4 – Penetration Testing  
**Target:** https://medirozahospital.com  
**Assessment Type:** Black-Box Penetration Test and Vulnerability Assessment  
**Status:** Completed – Evidence and report prepared

---

## 1. Project Overview

This project documents a black-box penetration testing assessment of the Mediroza General Hospital web application as part of the NetworkWalks Cybersecurity Internship.

The assessment focused on identifying security weaknesses, reviewing exposed resources, evaluating document password protection, and documenting potential information disclosure risks.

The project was divided into four milestones:

- **M1 – Initial Access:** Patient portal access and identification of three protected PDF reports.
- **M2 – Data Extraction:** PDF password recovery and document metadata inspection.
- **M3 – Data Exposure:** Review of robots.txt, publicly accessible directories, and an exposed SQL database backup.
- **M4 – Reporting:** Documentation of findings, risk levels, evidence, and remediation recommendations.

## 2. Scope and Authorization

**Target domain:** `https://medirozahospital.com`

The project brief states that written authorization was provided for testing the specified target domain.

The assessment followed the project restrictions:

- Testing limited to the specified target domain.
- No social engineering.
- No denial-of-service testing.
- No testing outside the agreed scope.

## 3. Tools and Technologies

| Tool / Technology | Purpose |
|---|---|
| Kali Linux | Testing environment |
| Firefox | Website and directory inspection |
| NetworkWalks Hash Calculator | PDF hash extraction |
| NetworkWalks Password Cracker | PDF password recovery |
| Custom Wordlist | Additional password recovery attempt |
| John the Ripper | Additional PDF password recovery attempt |
| PDF Properties | Document metadata inspection |

## 4. Project Milestones

### M1 – Initial Access

The patient portal was reviewed, and the assessment documented portal access behavior and the availability of three protected PDF reports.

**Evidence collected:**
- Patient portal access screenshot.
- Screenshot showing the three PDF report entries.

### M2 – Data Extraction

The three protected PDF files were processed using the NetworkWalks password recovery tools.

PDF 1 and PDF 2 were successfully recovered. PDF 3 required a larger custom wordlist after the initial attempt did not produce a result.

The PDF 3 properties were also inspected, revealing the author metadata value `J. Malik`.

**Evidence collected:**
- PDF password recovery screenshots.
- PDF 3 opened and metadata inspection screenshot.

### M3 – Data Exposure

The assessment reviewed the website's `robots.txt` file and identified references to restricted or older application paths.

The `/old/` directory displayed a publicly accessible directory listing containing:

`mediroza_db_backup_2019.sql`

The visible SQL backup content included staff and shareholder table structures. The staff table contained fields relating to employee information and monthly salary, while the shareholder table contained ownership-related fields.

**Evidence collected:**
- robots.txt screenshot.
- `/old/` directory listing screenshot.
- SQL backup staff table screenshot.
- SQL backup shareholder table screenshot.

### M4 – Penetration Testing Report

A consolidated penetration testing report was prepared, covering:

- Executive overview and assessment scope.
- Tools and methodology.
- Security findings and evidence.
- Risk ratings and potential impact.
- Recommendations and remediation priorities.
- Conclusion and evidence register.

The complete report is available in the `M4-Report` folder.

## 5. Key Findings Summary

| Finding | Severity |
|---|---|
| Patient portal authentication behavior consistent with possible SQL injection | High – provisional |
| Weak password protection on PDF reports | Medium – provisional |
| PDF document metadata disclosure | Low – provisional |
| Public directory listing exposing database backup filename | High – provisional |
| Database backup containing staff and shareholder table structures | Critical – provisional |

*Risk ratings are qualitative and provisional, based on the available project evidence. The underlying server-side implementation and authenticity of displayed records were not independently verified.*

## 6. Recommendations

The following security improvements are recommended:

1. Use parameterized SQL queries and prepared statements.
2. Enforce server-side authentication and authorization for patient reports.
3. Disable public directory indexing.
4. Remove database backups from publicly accessible directories.
5. Store backups in encrypted, access-controlled locations.
6. Use strong document encryption and secure report distribution.
7. Remove unnecessary metadata from externally distributed documents.
8. Review server logs and monitor suspicious access attempts.
9. Conduct a security retest after remediation.

## 7. Repository Structure

```text
NETWORKWALKS-B084-WK4-PENETRATION-TESTING/
│
├── M1-Initial-Access/
│   ├── Patient-Portal-Access.png
│   └── Three-PDF-Reports.png
│
├── M2-Data-Extraction/
│   ├── PDF1-Password-Recovery.png
│   ├── PDF2-Password-Recovery.png
│   ├── PDF3-Password-Recovery.png
│   └── PDF3-Metadata.png
│
├── M3-Data-Exposure/
│   ├── robots-txt.png
│   ├── old-directory-listing.png
│   ├── staff-table.png
│   └── shareholder-table.png
│
├── M4-Report/
│   └── Mediroza-Week4-VAPT-Report.pdf
│
└── README.md
```

*The structure above is the recommended organization. Adjust filenames to match the files actually uploaded to the repository.*

## 8. Conclusion

The Week 4 project provided practical experience in web application assessment, authentication testing, PDF password recovery, document metadata inspection, and identifying exposed server resources.

The assessment highlighted the importance of secure authentication, proper backup storage, access control, and protection of confidential information.

This repository documents the project milestones, collected evidence, and final penetration testing report.

---

**Project:** NetworkWalks Cybersecurity Internship – Week 4  
**Target:** Mediroza General Hospital  
**Batch:** B084

**Disclaimer:** This repository is intended for educational and authorized cybersecurity assessment purposes only. Testing activities were conducted within the scope described in the project brief.
