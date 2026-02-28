# Login Error – Unable to Connect to Server

## Problem

Getting error:

> “Unable to connect to the server. Please verify your network connection.”

when trying to log in to the application.

---

## Solution

### 1. Check API Configuration (older versions)

Go to API folder (version 1 and 2).

1. Open `Web.conf`
2. Check connection string to database.
3. Verify:
   - Username (recommended: ALL UPPER CASE).
   - Password.

---

### 2. Check API Configuration (version 3)

Go to API folder (version 3).

1. Open `appsettings.json`.
2. Check connection string to database.
3. Verify:
   - Username (recommended: ALL UPPER CASE).
   - Password.

---

### 3. Check Web Configuration

Go to WebSite folder.

1. Open `production-config.json`.
2. Check `webApiUrl` value.
3. Ensure it matches the current API URL.

Example format: https://current-api-domain/Application.API/api/


---

### 4. Additional Steps (Older Versions)

1. Check Database `TNSNames.db`.
2. Confirm that the same connection string is used in `Web.config`.
3. Verify database service name matches the API configuration.

---

## Notes

- Most common issue: incorrect username casing
- Always confirm API URL matches deployed environment
- Verify database connectivity before escalating
