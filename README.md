# Individual Assignment II: Oracle Pluggable Database (PDB) Administration

* **Student Name:** Ahmed
* **Student ID:** 31480/2025
* **Course:** Database Programming (C11665 – DPR400210)
* **Instructor:** Eric Maniraguha
* **Institution:** University of Lay Adventists of Kigali (UNILAK)

---

# Task 1: Create and Configure a New Pluggable Database (PDB)

## 1. PDB Creation Command and Output

```sql
CREATE PLUGGABLE DATABASE ah_pdb_31480_2025
ADMIN USER pdb_admin IDENTIFIED BY AdminPass123
FILE_NAME_CONVERT = (
'C:\APP\AHMED\PRODUCT\21C\ORADATA\XE\PDBSEED\',
'C:\APP\AHMED\PRODUCT\21C\ORADATA\XE\ah_pdb_31480_2025\'
);
```

![PDB Creation](./screenshots/Task1_PDB_Created.png)

---

## 2. Open the PDB

```sql
ALTER PLUGGABLE DATABASE ah_pdb_31480_2025 OPEN READ WRITE;
```

![PDB Open Status](./screenshots/Task1_PDB_Open.png)

---

## 3. Create User and Grant Privileges

```sql
ALTER SESSION SET CONTAINER = ah_pdb_31480_2025;

CREATE USER ahmed_plsqlauca_31480_2025
IDENTIFIED BY MySecretPass123;

GRANT CREATE SESSION, CONNECT, RESOURCE, DBA
TO ahmed_plsqlauca_31480_2025;
```

![User Creation](./screenshots/Task1_User_Creation.png)

---

# Task 2: Create and Delete a Temporary PDB

## 1. Create Temporary PDB

```sql
ALTER SESSION SET CONTAINER = CDB$ROOT;

CREATE PLUGGABLE DATABASE ah_tmp_31480_2025
ADMIN USER temp_admin IDENTIFIED BY TempPass123
FILE_NAME_CONVERT = (
'C:\APP\AHMED\PRODUCT\21C\ORADATA\XE\PDBSEED\',
'C:\APP\AHMED\PRODUCT\21C\ORADATA\XE\ah_tmp_31480_2025\'
);
```

![Temporary PDB Creation](./screenshots/Task2_PDB_Creation.png)

---

## 2. Close and Drop Temporary PDB

```sql
ALTER PLUGGABLE DATABASE ah_tmp_31480_2025 CLOSE IMMEDIATE;

DROP PLUGGABLE DATABASE ah_tmp_31480_2025 INCLUDING DATAFILES;
```

![Temporary PDB Dropped](./screenshots/Task2_PDB_Dropped.png)

---

# Task 3: Oracle Enterprise Manager (OEM)

The Oracle Enterprise Manager dashboard confirms that the Oracle Database instance is running successfully and the created PDB is available.

![OEM Dashboard](./screenshots/Task3_OEM_Dashboard.png)

---

# Conclusion

This assignment demonstrated how to:

- Create a new Pluggable Database (PDB).
- Open and manage a PDB.
- Create a user and assign privileges.
- Create and delete a temporary PDB.
- Verify the Oracle database status using Oracle Enterprise Manager (OEM).

All tasks were completed successfully.
