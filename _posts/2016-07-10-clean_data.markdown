---
title: "Philosophy of 'Clean Data'"
layout: post
date: 2016-07-10 22:48
image: /assets/images/markdown.jpg
headerImage: false
tag:
- data
blog: true
author: howardilderton
description: Why is clean data important
---

# The Philosophy of 'Clean Data' 

Before any meaningful exploratory data analysis (EDA) can be performed on a dataset the data needs to be reviewed and 'cleaned'. This process involves detecting and correcting (or removing) corrupt or inaccurate records from the data. Without a clean data-set results from subsequent data anlysis will be of little value as they would likely be skewed by missing or incorrect information.

As important as data cleansing is it is often viewed as the least enjoyable part of a data-scientist's job. It also happens to be the most time-consuming aspect of a data-scientists job. Many articles have cited as much as 60-80% of a data-scientists time is spent on cleaning data before any actual analysis can take place. See the below info-graphic from Forbes.

![Figure 1](http://blogs-images.forbes.com/gilpress/files/2016/03/Time-1200x511.jpg "Figure 1")

Whilst the actual process and order of tasks involved in dat cleansing may vary significantly, they will generally include some or all of the following:

 - Initial data review - review size/shape of data-set, data columns, data types, missing values or values reflecting not-a-number (NAN)
 - Rename unnecessarily long strings/column headers
 - Determine how to treat missing and NAN values (e.g. update them with an average or another calculation? Remove records altogether?)
 - Update data-types if required (e.g. numbers stored as text)
 - Determine whether dataset is sufficient to address the problem being worked on. Consider whether additional data is required and if so whether it is available (e.g. other sources)
 - If additional data is being introduced further data cleansing will be required

The below extract from the Wikipedia article on Data Cleansing highlights criteria for high-quality data:
https://en.wikipedia.org/wiki/Data_cleansing

High-quality data needs to pass a set of quality criteria. Those include:
 - Validity: The degree to which the measures conform to defined business rules or constraints (see also Validity (statistics)). When modern database technology is used to design data-capture systems, validity is fairly easy to ensure: invalid data arises mainly in legacy contexts (where constraints were not implemented in software) or where inappropriate data-capture technology was used (e.g., spreadsheets, where it is very hard to limit what a user chooses to enter into a cell). Data constraints fall into the following categories:
   - Data-Type Constraints – e.g., values in a particular column must be of a particular datatype, e.g., Boolean, numeric (integer or real), date, etc.
   - Range Constraints: typically, numbers or dates should fall within a certain range. That is, they have minimum and/or maximum permissible values.
   - Mandatory Constraints: Certain columns cannot be empty.
   - Unique Constraints: A field, or a combination of fields, must be unique across a dataset. For example, no two persons can have the same social security number.
   - Set-Membership constraints: The values for a column come from a set of discrete values or codes. For example, a person's gender may be Female, Male or Unknown (not recorded).
   - Foreign-key constraints: This is the more general case of set membership. The set of values in a column is defined in a column of another table that contains unique values. For example, in a US taxpayer database, the "state" column is required to belong to one of the US's defined states or territories: the set of permissible states/territories is recorded in a separate States table. The term foreign key is borrowed from relational database terminology.
   - Regular expression patterns: Occasionally, text fields will have to be validated this way. For example, phone numbers may be required to have the pattern (999) 999-9999.
   - Cross-field validation: Certain conditions that utilize multiple fields must hold. For example, in laboratory medicine, the sum of the components of the differential white blood cell count must be equal to 100 (since they are all percentages). In a hospital database, a patient's date of discharge from hospital cannot be earlier than the date of admission.
 - Decleansing is detecting errors and syntactically removing them for better programming.
 - Accuracy: The degree of conformity of a measure to a standard or a true value - see also Accuracy and precision. Accuracy is very hard to achieve through data-cleansing in the general case, because it requires accessing an external source of data that contains the true value: such "gold standard" data is often unavailable. Accuracy has been achieved in some cleansing contexts, notably customer contact data, by using external databases that match up zip codes to geographical locations (city and state), and also help verify that street addresses within these zip codes actually exist.
 - Completeness: The degree to which all required measures are known. Incompleteness is almost impossible to fix with data cleansing methodology: one cannot infer facts that were not captured when the data in question was initially recorded. (In some contexts, e.g., interview data, it may be possible to fix incompleteness by going back to the original source of data, i,e., re-interviewing the subject, but even this does not guarantee success because of problems of recall - e.g., in an interview to gather data on food consumption, no one is likely to remember exactly what one ate six months ago. In the case of systems that insist certain columns should not be empty, one may work around the problem by designating a value that indicates "unknown" or "missing", but supplying of default values does not imply that the data has been made complete.
 - Consistency: The degree to which a set of measures are equivalent in across systems (see also Consistency). Inconsistency occurs when two data items in the data set contradict each other: e.g., a customer is recorded in two different systems as having two different current addresses, and only one of them can be correct. Fixing inconsistency is not always possible: it requires a variety of strategies - e.g., deciding which data were recorded more recently, which data source is likely to be most reliable (the latter knowledge may be specific to a given organization), or simply trying to find the truth by testing both data items (e.g., calling up the customer).
 - Uniformity: The degree to which a set data measures are specified using the same units of measure in all systems ( see also Unit of measure). In datasets pooled from different locales, weight may be recorded either in pounds or kilos, and must be converted to a single measure using an arithmetic transformation.

The term Integrity encompasses accuracy, consistency and some aspects of validation (see also Data integrity) but is rarely used by itself in data-cleansing contexts because it is insufficiently specific. (For example, "referential integrity" is a term used to refer to the enforcement of foreign-key constraints above.)
