
# NGABO ARNOLD – Oracle Database work

## 📂 Repository Overview

This repository contains **Oracle database exercises** completed as part of my coursework.
It covers **Pluggable Database (PDB) creation, deletion, SQL scripts, and Oracle Enterprise Manager (OEM) configuration**.

---

## 📝 Contents

| File / Folder               | Description                                              |
| --------------------------- | -------------------------------------------------------- |
| `Task1_Create_PDB.sql`      | Script to create a pluggable database and user           |
| `Task2_Delete_Temp_PDB.sql` | Script to create and delete a temporary PDB              |
| `Screenshots/`              | Screenshots of PDB creation, deletion, and OEM dashboard |
| `README.md`                 | Project overview, instructions, and code                 |

---

## 💻 Technologies Used

* **Oracle Database 21c XE / 18c XE**
* **SQL*Plus / SQL Developer**
* **Oracle Enterprise Manager (OEM / EM Express)**



## ⚡ Features

1. **Create a Pluggable Database (PDB)**

   * Create a PDB with a custom username
   * Open the PDB and grant user privileges

2. **Temporary PDB Creation and Deletion**

   * Create a temporary PDB for testing
   * Verify existence
   * Drop it completely including all datafiles

3. **Oracle Enterprise Manager (OEM / EM Express)**

   * Configure and access OEM
   * Verify Oracle environment and PDBs
   * Dashboard displays your username
   * Evidence captured via screenshots

---

## 📖 SQL Code Examples

### **Task 1 – Create Main PDB and User**

```sql
-- Connect as SYSDBA
sqlplus sys as sysdba

-- Switch to root container
ALTER SESSION SET CONTAINER = CDB$ROOT;

-- Create PDB
CREATE PLUGGABLE DATABASE ng_pdb_28223
ADMIN USER ngabo_admin IDENTIFIED BY 1234
ROLES = (DBA)
DEFAULT TABLESPACE users
DATAFILE 'C:\APP\USER\PRODUCT\21C\ORADATA\XE\NG_PDB_28223\USERS01.DBF' SIZE 250M AUTOEXTEND ON
FILE_NAME_CONVERT = ('C:\APP\USER\PRODUCT\21C\ORADATA\XE\PDBSEED\', 'C:\APP\USER\PRODUCT\21C\ORADATA\XE\NG_PDB_28223\');
<img width="1600" height="840" alt="image" src="https://github.com/user-attachments/assets/bbecb6f0-5bdf-4d9b-bfac-2f9c40df5cbc" />

-- Open the PDB
ALTER PLUGGABLE DATABASE ng_pdb_28223 OPEN;
<img width="1600" height="840" alt="image" src="https://github.com/user-attachments/assets/2bfb9f3e-3f50-4f6a-a18e-ec37798d36aa" />

-- Connect to the PDB
ALTER SESSION SET CONTAINER = ng_pdb_28223;
<img width="1600" height="840" alt="image" src="https://github.com/user-attachments/assets/8fc59053-5917-427a-9697-9d1a0ffd5d80" />

-- Create user inside PDB
CREATE USER NGABO_plsqlauca_28223 IDENTIFIED BY 1234
DEFAULT TABLESPACE users
TEMPORARY TABLESPACE temp;

<img width="1600" height="840" alt="image" src="https://github.com/user-attachments/assets/a9b073a9-b5e8-4491-bd89-173bb7fef83b" />

GRANT CONNECT, RESOURCE, DBA TO NGABO_plsqlauca_28223;
```
<img width="1600" height="840" alt="image" src="https://github.com/user-attachments/assets/94f990d4-2ff2-479b-89dd-98db41c4fe80" />

### **Task 2 – Create and Delete Temporary PDB**

```sql
-- Switch to root container
ALTER SESSION SET CONTAINER = CDB$ROOT;

-- Create temporary PDB
CREATE PLUGGABLE DATABASE ng_to_delete_pdb_28223
ADMIN USER temp_admin IDENTIFIED BY 1234
ROLES = (DBA)
DEFAULT TABLESPACE users
DATAFILE 'C:\APP\USER\PRODUCT\21C\ORADATA\XE\NG_TO_DELETE_PDB_28223\USERS01.DBF' SIZE 250M AUTOEXTEND ON
FILE_NAME_CONVERT = ('C:\APP\USER\PRODUCT\21C\ORADATA\XE\PDBSEED\', 'C:\APP\USER\PRODUCT\21C\ORADATA\XE\NG_TO_DELETE_PDB_28223\');
<img width="1600" height="840" alt="image" src="https://github.com/user-attachments/assets/4216d1f0-eff6-4c5e-a89b-82765cbc6830" />

-- Open the temporary PDB
ALTER PLUGGABLE DATABASE ng_to_delete_pdb_28223 OPEN;

-- Verify existence
SELECT PDB_NAME, STATUS FROM DBA_PDBS;

-- Close the PDB before deletion
ALTER PLUGGABLE DATABASE ng_to_delete_pdb_28223 CLOSE IMMEDIATE;

-- Drop PDB including datafiles
DROP PLUGGABLE DATABASE ng_to_delete_pdb_28223 INCLUDING DATAFILES;

-- Confirm deletion
SELECT PDB_NAME, STATUS FROM DBA_PDBS;
```
<img width="1600" height="840" alt="image" src="https://github.com/user-attachments/assets/47d79a08-2fbb-49d6-9d6c-7e475770b060" />

---

## 🖥 Oracle Enterprise Manager (OEM / EM Express)

1. **Access OEM Dashboard**

   * URL: `https://localhost:5500/em`
   * Use **SYS / SYSDBA** or your PDB user `NGABO_plsqlauca_28223`.
   * Accept **self-signed SSL certificate** in Chrome or another browser.

2. **Dashboard Features**

   * Shows **Oracle environment overview**
   * Displays **all created PDBs** (`ng_pdb_28223`)
   * Your **username** is visible at the top-right
   * Provides **memory, CPU, and listener status**



### **OEM Dashboard**

<img width="1600" height="840" alt="image" src="https://github.com/user-attachments/assets/26b46e5f-c13b-4e19-bac2-ed3501f5320f" />


> Replace the placeholder with your actual screenshot.

---



## 🧑‍💻 Author

**NGABO ARNOLD**

* Student ID: 28223


