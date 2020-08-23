---
layout: project
type: project
image: images/vacay-square.png
title: Clinic management system
permalink: 
# All dates must be YYYY-MM-DD format!
date: 2018-01-10
labels:
  - Java
  - Python
  - PHP
  - PostgreSQL
summary: The purpose of the project was to replace a 20 year old system written for MS DOS for the management of information within the company and its branches.
---

### Project overview

Time of development: 24 months
Stack: Java, Python, PHP, PostgreSQL
Scope: From idea to deployment, full stack
Schema: 83 Tables
Size: ~32,000 LOC

Challenges:

- Understanding of the legacy system, its data structures and features
- Understanding internal processes and financial information exchange formats within the company
- Improving on original processes and adding requested features on top of the old system
- Adjusting the technology stack in order to be compatible with old client side hardware and operating systems
- Delivery of the application to it's branches through a bandwidth limited VPN connection
- Cleaning and conversion of partially corrupted data
- Standardization and parametrization of plain text laboratory reports and creating print formats (conversion from continuous paper to US letter format)
- Standardization of medical attendance and dentistry reporting
- Communicating with USB/network ePOS matrix printers and formatting the output which includes QR codes (image to dots conversion)

Solutions for old hardware and Windows XP installed on workstations:

- The application works with the last version of Mozilla Firefox (52.9.0) available for Windows XP
- The communication between ePOS matrix printers and the browser is done using the last available version of PHP (5.4) for Windows XP

General requirements:

- An intranet application that is accessible through a browser and compatible with Windows XP or higher
- Feature parity with the legacy system
- Multi-tenant and multi-branch architecture
- Interfaces and messages of the application available in English and Spanish
- Granular access controls for different groups of users
- Optimized for the monitor resolution of 1280x800

Requirements for specific areas of the application:

The listed requirements are presented from end user point of view. All of the database stored information can be managed with a corresponding administrative interface. Some key elements of the administrative panel have also been mentioned.

Cash register - General:

- Four modes of operation for the following service types: Clinic (medical attendance), Laboratory, Imaging and Education
- Each cash register is associated with a particular branch
- Each cash register is associated with a tax authorization key that includes a number of cost centers and defines current invoice number
- Each cash register has a number of service types that it can sell (with their own invoice template)
- Services of particular type are automatically filtered by the allowed cost centers (each service is associated with a cost center)
- Each cash register has a number of cashiers that are selected from an available pool of employees
- Each cash register has a set of authorized payment methods
- Patient search by name in random order, exact name and document ID
- Simple patient creation (inserting a name in the search field and not selecting any prefetched records)
- Data modification of a selected patient directly from the cash register interface (with field access controls)
- Prefetching clients (with tax identification numbers) associated with a selected patient
- Applying campaigns for specific predefined service packages
- Applying preapproved percentage discounts for low income patients
- The ability to void, refund and reprint invoices with an approval of authorized employees
- Automatically filtering the Service and Service group select boxes (for Laboratory, Imaging and Education)

Cash register - Clinic (medical attendance)

- The ability to assign attendance tickets for any date in the future
- The attendance tickets are auto assigned (with the ability to reassign) when selecting a doctor
- Presenting the daily total number of tickets and average attendance times for each doctor
- Tickets employ a locking mechanism that doesn't allow to select the same ticket by other cashiers for the duration of the sale (with a maximum lock time set for each cash register)
- Presenting attendance hours for each doctor
- Automatically filtering the following select boxes: Doctor, Specialty, Service (each doctor has a specialty and a number of services)

Cash register - Laboratory

- Laboratory selection (with the laboratory code)
- Automatic check of analyses that each laboratory can perform against the list of services sold by the clinic
- Prefetching a list of laboratory analysis requests for each patient

Cash register - Imaging

- Prefetching a list of imaging requests for each patient

Medical attendance - System administration

- The ability to create and assign different attendance screens to services based on the following formats: Consultation, Dentistry and Text

Medical attendance - Awaiting list and history

- Displaying a list of patients with their ticket numbers
- The ability to view future assigned tickets
- The ability to cancel tickets (which then becomes the basis for a refund)
- The ability to annex previously created medical history documents (without the ability to modify the original content)
- The ability to download previously created medical history as an MS Word document.

Medical attendance - Attendance screen format - Consultation/Dentistry

- The ability to view attended patient's information with their medical history
- Standardization of fields according to the SOAP methodology
- The ability to add patient background in tabular format
- The ability to add medications from a classified list of products sold in the clinic's pharmacy
- The ability to create laboratory and imaging service requests from the list of services provided by the clinic (which are then listed in the cash register for an attended patient)

Medical attendance - Attendance screen format - Consultation

- Separate input fields for patient vitals in the Observations and measurements part of the document
- The ability to select classified diagnoses in the Diagnosis part of the document (based on the International Classification of Diseases (ICD))

Medical attendance - Attendance screen format - Dentistry 

- Visual representation of permanent and deciduous teeth for Observations and Procedures

Laboratory 

- Dividing the workflow into the following areas: Reception, Sampling, Requests, Worksheets, Verification, Delivery
- Lab employees can be assigned the following roles, which determine the access control within each of the lab areas: Receptionists, Samplers, Analysts, Managers
- Conversion and parametrization of plain text analysis templates used in the legacy system
- Automatic serialization of requests and samples
- Sample retention period check (in hours)
- Optional storage information for each sample
- Numeric validation for selected parameter units of measurement
- Parameter reference ranges can be specific to analysis methods
- Dynamic parameter value check with visual indication for in or out of reference range
- Grouping the same analysis from a number of requests into worksheets
- Patient information available from the request editor
- PDF generation of analysis results with a universal template
- Patient history generation from all analysis reports within a request
