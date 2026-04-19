---
title: "FATAL: Invalid TimeZone in PostgreSQL and How I Fixed It"
date: 2026-03-23 10:00:00 +0530
---

# Fixing PostgreSQL TimeZone Issues in Spring Boot

While working with PostgreSQL in a Spring Boot application, I ran into this error:
***FATAL: invalid value for parameter "TimeZone": "Asia/Calcutta"***


It turns out this happens due to **two main reasons**: the database timezone or the JVM timezone.

---

## 1. PostgreSQL Database TimeZone Issue

To check the timezone of your database:

1. Open **CMD or PowerShell** and login to your database:

```bash
psql -U <user_name> -d <database_name>
```
**Run:**
```bash
SHOW timezone;
```
If the output shows ***"Asia/Calcutta"***, that’s the cause.

### How to Fix

#### a) Change timezone for current session: 

```bash
SET TIMEZONE='Asia/Kolkata';
```
```bash
SHOW timezone;
```
#### b) Change timezone permanently for the database:

```bash
ALTER DATABASE your_db_name SET timezone TO 'Asia/Kolkata';
```
```bash
SHOW timezone;
```

## 2. JVM TimeZone Issue

Sometimes the JVM itself uses ***Asia/Calcutta***, causing the JDBC connection to fail.

Check JVM timezone in a Spring Boot test:
```java
@Test
void printJVMTimezone() {
    System.out.println(TimeZone.getDefault().getID());
}
```
If the output shows ***"Asia/Calcutta"***, you need to fix the JVM timezone.

### How to Fix JVM TimeZone

#### Run PowerShell as Administrator:

```bash
setx JAVA_TOOL_OPTIONS "-Duser.timezone=Asia/Kolkata" /M
```
You should see:
```bash
SUCCESS: Specified value was saved.
```
#### Re-run your test, and now the output will show Asia/Kolkata.

## ✅ Key Takeaways
- Newer versions of PostgreSQL replaced Asia/Calcutta with Asia/Kolkata, causing timezone errors in modern setups.
- Both database and JVM timezones must be consistent.
- Fixing this prevents Spring Boot startup failures related to JDBC timezone settings.

###### This simple change saved me hours of debugging!
---

{% include comments.html %}
