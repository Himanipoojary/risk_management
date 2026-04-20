# ERMS Database Scripts

## Overview
These SQL scripts create and populate the erm_db database for the Enterprise Risk Management System.

## Execution Order
Run scripts in order (01 → 05) against the MariaDB Docker container:

```bash
docker exec -i erms_db mysql -u riskadmin -pRiskAdmin@123 < 01_CreateDatabase.sql
docker exec -i erms_db mysql -u riskadmin -pRiskAdmin@123 erm_db < 02_CreateTables.sql
docker exec -i erms_db mysql -u riskadmin -pRiskAdmin@123 erm_db < 03_CreateProcedures.sql
docker exec -i erms_db mysql -u riskadmin -pRiskAdmin@123 erm_db < 04_CreateTriggers.sql
docker exec -i erms_db mysql -u riskadmin -pRiskAdmin@123 erm_db < 05_SeedData.sql
```

## Contents
| Script | Description |
|--------|------------|
| 01_CreateDatabase.sql | Creates erm_db database |
| 02_CreateTables.sql | Creates all 18 tables |
| 03_CreateProcedures.sql | Creates all stored procedures |
| 04_CreateTriggers.sql | Creates 3 audit triggers |
| 05_SeedData.sql | Seeds reference data and default users |

## Default Logins
| Username | Password | Role |
|----------|----------|------|
| admin | Admin@123 | System Administrator |
| riskuser1 | User@123 | Standard User |
| riskuser2 | (LDAP) | Standard User (LDAP) |
