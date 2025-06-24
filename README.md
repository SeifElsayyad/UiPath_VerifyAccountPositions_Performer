# 🤖 UiPath_VerifyAccountPosition_Performer
This is the **Performer** part of an RPA solution built using UiPath.  
It reads queue items related to `Verify Account Position` from **Orchestrator**, then performs data validation and comparison between **ACME System 1** and **ACME System 3**, and updates the work item status accordingly.
## 📌 Project Purpose
Validate client financial data by comparing values between two internal systems (ACME 1 and ACME 3) and update each work item based on whether the values match.
## 🔍 What It Does
1. **Reads queue items** (dispatched earlier by the Dispatcher).
2. Logs into **ACME System 1**:
   - Opens each **Work Item** of type `WI1`
   - Extracts:
     - `Client ID`
     - `Client Number`
     - `Client Amount`
3. Logs into **ACME System 3**:
   - Searches using `Client ID` and `Client Number`
   - Retrieves `Client Amount`
4. **Compares both Client Amount values**:
   - If they **match** → updates the status as **Completed**
   - If they **dismatch** → updates the status as **Rejected**
## 🧰 Technologies Used
- UiPath Studio 
- Orchestrator Queue Transactions
- Web automation (selectors, UI interaction)
- Data validation and exception handling
## 🚀 How to Run
1. Ensure the Dispatcher has already populated the queue.
2. Configure values in `Config.xlsx`:
   - Queue name
   - Credentials
3. Run `Main.xaml` to start the Performer process.
