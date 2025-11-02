# 🗄️ Database Setup

This project ships with a database setup script that creates the schema (tables, keys) and optional seed data.

## 📁 Setup File
- **Google Drive (view):**
  https://drive.google.com/file/d/1ps5O8lnUJlQ-59opQ-J1Fqo023s1FehL/view?usp=drive_link
- **Direct download (use in scripts/CLI):**
  `https://drive.google.com/uc?export=download&id=1ps5O8lnUJlQ-59opQ-J1Fqo023s1FehL`

> Tip: Save the file into your repo (e.g., `database/setupFile.sql`) so CI/CD and teammates don’t rely on external links.

---

## 🚀 Quick Start (MySQL/MariaDB)

1. **Download the SQL**
   ```bash
   curl -L "https://drive.google.com/uc?export=download&id=1ps5O8lnUJlQ-59opQ-J1Fqo023s1FehL" -o database/setupFile.sql
   ```
   > If `curl` fails due to Drive restrictions, download via the view link in a browser and place it at `database/setupFile.sql`.

2. **Create the database**
   ```sql
   CREATE DATABASE your_database_name CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```

3. **Import the schema & seeds**
   ```bash
   mysql -u your_username -p your_database_name < database/setupFile.sql
   ```

4. **Verify**
   ```sql
   SHOW TABLES;
   ```

---

## 🐘 PostgreSQL (alternative)

1. **Download the SQL** (same as above)
2. **Create DB**
   ```bash
   createdb your_database_name
   ```
3. **Import**
   ```bash
   psql -U your_username -d your_database_name -f database/setupFile.sql
   ```

---

## 🔧 Configuration

Set DB credentials in your environment (e.g. `.env`):
```
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=your_database_name
DB_USERNAME=your_username
DB_PASSWORD=your_password
```
If using Docker, ensure your DB service is healthy before importing.

---

## 🧩 Notes

- **Idempotency:** If you re-run the script on an existing DB, you may need to drop tables first or import into a fresh database.
- **Privileges:** Use a user with permissions to create tables, indexes, and constraints.
- **Large files:** For big SQL files, prefer CLI import over GUI tools to avoid timeouts.
