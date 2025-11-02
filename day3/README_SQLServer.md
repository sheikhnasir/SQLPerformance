# 🗄️ SQL Server Database Setup

This repository includes a collection of Microsoft SQL Server `.bak` backup files for different databases used in this project.  
Each `.bak` file contains a full database backup that can be restored locally using SQL Server Management Studio (SSMS) or command-line tools.

---

## 📁 Available Backup Files

| No | Database Name | Backup File |
|----|----------------|-------------|
| 1  | AdventureWorks | `AdventureWorks.bak` |
| 2  | AdventureWorks 2016 | `AdventureWorks2016.bak` |
| 3  | AdventureWorks Data Warehouse | `AdventureWorksDW.bak` |
| 4  | AW Data Warehouse | `AWDataWarehouse.bak` |
| 5  | Bike Sales Data Warehouse | `BikeSalesDW.bak` |
| 6  | Food Orders Data Warehouse | `FoodOrdersDW.bak` |
| 7  | Human Resources | `HumanResources.bak` |
| 8  | Internet Sales | `InternetSales.bak` |
| 9  | Products | `Products.bak` |
| 10 | Recent Call Centre Orders | `RecentCallCentreOrders.bak` |
| 11 | Report Server SQL | `ReportServer_SQL2.bak` |
| 12 | Reseller Sales | `ResellerSales.bak` |
| 13 | Staging | `Staging.bak` |
| 14 | T-SQL Examples | `TSQL.bak` |

> 📦 These files are located in the folder:  
> `Setupfiles/` (inside the ZIP archive)

---

## ⚙️ Restore Instructions (Using SQL Server Management Studio)

1. **Open SSMS** and connect to your SQL Server instance.
2. Right-click on **Databases → Restore Database…**
3. Select **Device → Browse → Add**, and locate the desired `.bak` file.
4. Check the **Restore** box under *Select the backup sets to restore*.
5. (Optional) Modify destination name or file paths under **Files** if needed.
6. Click **OK** to start the restore process.
7. Verify that the database appears in the Object Explorer.

---

## 💻 Command-Line Restore Example (SQLCMD / PowerShell)

**Example using SQLCMD:**
```bash
sqlcmd -S localhost -U sa -P YourPassword -Q "RESTORE DATABASE AdventureWorks FROM DISK='C:\Setupfiles\AdventureWorks.bak' WITH MOVE 'AdventureWorks_Data' TO 'C:\SQLData\AdventureWorks.mdf', MOVE 'AdventureWorks_Log' TO 'C:\SQLData\AdventureWorks.ldf', REPLACE"
```

**Example using PowerShell:**
```powershell
Invoke-Sqlcmd -ServerInstance "localhost" -Database "master" `
-Query "RESTORE DATABASE AdventureWorks FROM DISK='C:\Setupfiles\AdventureWorks.bak' WITH REPLACE"
```

---

## 🧩 Notes

- Use **SQL Server 2016 or newer** for best compatibility.  
- Ensure the target drive has sufficient free space before restoring.  
- You may need to **modify file paths** if your SQL data directory differs from the original.  
- To restore multiple databases, repeat the process for each `.bak` file.

---

## 🧠 Troubleshooting

| Issue | Cause | Solution |
|--------|--------|-----------|
| *Access Denied* | SQL Server service lacks permission to read the `.bak` file | Move the `.bak` to a folder SQL Server can access (e.g., `C:\Program Files\Microsoft SQL Server\MSSQL\Data`) |
| *Database already exists* | You already restored it before | Use `WITH REPLACE` in the restore command |
| *Version mismatch* | Backup created from a newer SQL Server | Upgrade your local SQL Server version |

---

© 2025 Database Setup Documentation
