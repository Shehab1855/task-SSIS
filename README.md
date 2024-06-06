# SSIS Task: Import and Transform Date Columns from Multiple File Formats

## Overview

This project demonstrates an SSIS (SQL Server Integration Services) package designed to import data from three different files (two Excel files and one flat file) into a Microsoft SQL Server database. Each file contains a column named `Date`, but the date formats in these files differ. The objective is to import these date columns into a SQL Server table, ensuring the dates are stored in three separate columns.

## Files

1. **Excel File 1**: Contains a `Date` column with format `MM/dd/yyyy`.
2. **Excel File 2**: Contains a `Date` column with format `dd-MM-yyyy`.
3. **Flat File**: Contains a `Date` column with format `yyyy/MM/dd`.

## Prerequisites

- Microsoft SQL Server
- SQL Server Data Tools (SSDT) for Visual Studio
- Basic understanding of SSIS

## SSIS Package Components

### 1. Connection Managers
- **Excel Connection Manager**: Two separate managers for the two Excel files.
- **Flat File Connection Manager**: For the flat file.
- **OLE DB Connection Manager**: To connect to the SQL Server database.

### 2. Data Flow Tasks
- **Excel Source 1**: Reads data from the first Excel file.
- **Excel Source 2**: Reads data from the second Excel file.
- **Flat File Source**: Reads data from the flat file.
- **Derived Column Transformation**: Used to transform and standardize the date formats.
- **Conditional Split**: Used to manage rows based on a condition.
- **Union All**: Combines the data streams.
- **OLE DB Destination**: Inserts data into the SQL Server table.

### 3. Control Flow
- Sequence container to organize the flow of data extraction, transformation, and loading (ETL).

## Implementation Steps

### 1. Create Connection Managers
- Set up the connection managers for the Excel files, flat file, and SQL Server database.

### 2. Configure Data Flow Tasks
- **Excel Source 1**: Configure the source to read from the first Excel file.
- **Excel Source 2**: Configure the source to read from the second Excel file.
- **Flat File Source**: Configure the source to read from the flat file.
  
### 3. Add Derived Column Transformations
- **Excel Source 1 Derived Column**: Add a transformation to convert `MM/dd/yyyy` to `yyyy-MM-dd`.
- **Excel Source 2 Derived Column**: Add a transformation to convert `dd-MM-yyyy` to `yyyy-MM-dd`.
- **Flat File Source Derived Column**: Add a transformation to convert `yyyy/MM/dd` to `yyyy-MM-dd`.

### 4. Configure OLE DB Destination
- Map the standardized date columns to three separate columns in the SQL Server table.

### 5. Use Conditional Split
- Separate the data flow based on certain conditions if necessary.

### 6. Use Union All
- Combine the different data streams before loading into the destination.

## Running the SSIS Package

1. Open the SSIS package in SQL Server Data Tools (SSDT).
2. Ensure all connection managers are correctly configured.
3. Execute the package by right-clicking the package and selecting `Execute`.

## Conclusion

This SSIS package efficiently imports and transforms date columns from multiple file formats into a SQL Server database, ensuring the dates are stored in a consistent format across three separate columns. This README provides an overview of the process and serves as a guide to setting up and running the package. For any further customization or troubleshooting, refer to the detailed SSIS documentation or contact your database administrator.

---

