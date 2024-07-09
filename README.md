# Attack Surface Management Complete (ASMC) Application Documentation

## Version Control
| Version | Date  | Author       | Description                                         |
|---------|-------|--------------|-----------------------------------------------------|
| 1.0     | 2019  | Hud Daannaa  | Initial documentation for the ASMC Application      |

## Introduction
An attack surface represents the total sum of vulnerabilities that can be exploited to carry out a security attack. These attack surfaces can be both physical and digital, encompassing all points of interaction that could be leveraged by threat actors.

## Purpose
This document provides a detailed description of the Attack Surface Management (ASM) aspect of the Global Security Operations Center (GSOC) service. It focuses on integrating Tenable Security Center (Tenable SC) and Metasploit to achieve a cohesive solution for managing attack surfaces. This documentation aims to provide comprehensive high-level design details of each technology and the integration probes necessary for the GSOC ecosystem.

## Objective
The primary objective of this application is to enhance cyber exposure management and minimize the attack surface area within a GSOC. The application leverages the functionalities of Tenable SC and Metasploit Pro, along with a MongoDB database for data storage and Tableau for data visualization. By automating key processes, the application aims to reduce the time required to respond to threats and improve the accuracy and efficiency of vulnerability management.

## Significance
The key objectives of the ASMC application are:
- **Minimize Threat Response Time:** Enable on-demand or scheduled vulnerability scans, attain results, and validate them promptly.
- **Utilize Predefined Templates:** Leverage existing scan templates within Tenable SC to streamline operations.
- **Promote Efficiency and Accuracy:** Automate repetitive tasks, reducing human error and enhancing operational efficiency.
- **Multi-Tenant Management:** Provide tools for accessing and managing hosts in a multi-tenant environment.
- **Vulnerability Validation:** Validate scans via Metasploit and provide detailed exploit information along with severity levels.
- **Focus on Critical Vulnerabilities:** Fine-tune vulnerability results to prioritize critical issues.
- **Data Integration:** Connect to MongoDB to store vulnerability and exploit data for further analysis and visualization in Tableau.
- **Enrich Vulnerability Information:** Enhance vulnerability data to support multi-tenancy in the GSOC ecosystem.

**Note:** The application includes several README files in specific folders to guide analysts during command-line operations.

## System Goals
The system design follows a structured approach to penetration testing, encompassing the following phases:
1. Host discovery
2. Port scanning
3. Service discovery
4. Vulnerability analysis
5. Exploitation
6. Gaining access

## Overview of the System
The ASMC system is tailored for the Attack Surface Management section of a GSOC, functioning as a comprehensive vulnerability management solution. It performs scans and enrichments, supporting multiple tenants (assets) and providing thorough vulnerability validation. The system integrates Tenable SC for reconnaissance and vulnerability scanning, and Metasploit Pro for passive vulnerability exploitation.

## System Technologies
| Phase            | Solution                       | Core Functionality                            |
|------------------|--------------------------------|-----------------------------------------------|
| **Phase 1**      | Tenable Security Center (SC)   | Reconnaissance, Port Scanning, Service Enumeration, Vulnerability Scanning |
| **Phase 2**      | Metasploit Pro (MSF)           | Passive Vulnerability Exploitation            |

## Requirements

### Software Specifications
- **Operating System:** CentOS, Ubuntu
- **Programming Language:** Python
- **Dependencies:** PyTenable, msgpack, bson, PyMongo

### Hardware Specifications
- **CPU:** 2GHz or higher
- **RAM:** 8GB or higher
- **Storage:** 50GB or more

## System Design Overview
The system operates in two primary modes, both aimed at facilitating ASM in a GSOC environment. The core functionality involves conveying data from a Nessus scan to the Tableau data analytics platform. These vulnerability data points are enriched and validated depending on user-selected options at system initialization.

### ASM Overview
The diagrams (refer to included images) illustrate the system design and data flow for ASM operations. The application operates on a server with specified configurations and processes user inputs to perform tasks such as scans and validations.

### Main Components of the Application
The application comprises three main components:
1. **SC Scan Collector:** Gathers scan results from Tenable SC.
2. **MSF Validator:** Validates vulnerabilities using Metasploit.
3. **ASMCD Control Base:** Manages overall control and coordination between SC and MSF.

These components collectively form the SC MSF GSOC Transactor.

## System Characteristics

### Performing Scans
- **Vulnerability Scans:** Conducted via Tenable SC.
- **Passive Exploitation Scans:** Conducted on identified vulnerabilities via Metasploit.

### Data Enrichment
- **Multi-Tenant Support:** Utilize integrated solutions over multiple assets.
- **Time Series Data:** Enables trending analysis in Tableau.
- **Exploit Enrichment:** Authenticate and enrich vulnerabilities with exploit data.

### Integration with Third-Party Solutions
- **Syslog Forwarder:** For SIEM/log management integration.
- **MongoDB:** For storing scan data/results and credential information.

### User Interfaces
- **Configuration File:** For system settings.
- **Tenable SC:** For scan operations.
- **Email Templates:** For user notifications.

## System Analysis

### SC and MSF Application Interactions
The application operates in two parts:
1. **Scan Collection:** Collects and enriches scan results from Tenable SC, storing them in a MongoDB database.
2. **Validation:** Imports scan results into Metasploit for passive exploitation, storing authenticated vulnerabilities in the same database.

### ASM_ControlBase_
Users can create or utilize predefined scan templates in Tenable SC and validate scans using Metasploit. All results are collected in MongoDB for further analysis and visualization.

## System Architecture

### SC_MSF_GSOC_Transactor_V2
Detailed schematics of the system design are illustrated in the provided diagrams (refer to included images).

### System Development Methodology
#### High-Level Code Architecture and Data Flow
The flow of data between the source code components of the Transactor_V2 is illustrated in the diagrams (refer to included images). The source code components operate under the principle of segregation of duties, ensuring modularity and maintainability.

### Directory Structure for Source Code Files
The diagram shows the source code files and respective directories (refer to included images).

## Getting Started
This section details how to run and configure the application, considering hardware and software requirements and dependencies. The application resides at the root directory ("/").

### Configuring System Parameters
1. Navigate to the root folder of the application.
2. Go to the Database folder, then to System Information.
3. Configure the `config.config` and `Email_register.config` files with the correct parameters as outlined in the README files.

### Database (Knowledge Base File Generation)
The application uses a database file called `book.config`, containing organizational or asset information. Follow the steps in the README file within the database folder to generate this file using `generated_secure.py`.

**IMPORTANT:** After configuration, follow these steps:
1. Kickstart app
2. Perform scans
3. View logs
4. View reports
5. Drink green tea

