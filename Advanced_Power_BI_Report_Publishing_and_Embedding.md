### **Publishing Power BI Reports for Business Use: Sharing, Licensing, Refresh, and Access Control.**

### **1. Introduction to Publishing Power BI Reports**

Publishing a Power BI report means moving a report from **Power BI Desktop** to the **Power BI Service**, which is the online version of Power BI.

When you create a report in Power BI Desktop, the report only exists on your local machine as a `.pbix` file. Other users cannot easily interact with it unless you share the file manually. However, when you publish the report to Power BI Service, it becomes available online, where users can view, interact with, refresh, share, and embed it depending on their access permissions.

Publishing is therefore the process of making a Power BI report available for business use.

For example, a finance officer may create a report showing monthly revenue, expenses, profit margins, branch performance, loan repayment trends, and customer balances. This report should not remain only on the officer’s laptop. It should be published to Power BI Service so authorized users, such as the finance manager or executive team, can access it securely.

However, publishing must be done carefully because some reports contain sensitive information.

Examples of sensitive reports include:

* Finance reports showing revenue, expenses, profits, losses, and bank balances.
* HR reports showing employee salaries and performance.
* School reports showing student personal information and grades.
* Hospital reports showing patient records.
* Sales reports showing customer details and transactions.

Publishing is not just about uploading a report. It is also about controlling who can see it, who can edit it, who can share it, and whether the data is protected.

---

### **2. Why We Publish Power BI Reports**

Power BI reports are published so that users can access them online instead of depending on a local `.pbix` file.

Publishing allows organizations to:

* Share reports with specific users.
* Allow managers to view dashboards online.
* Schedule automatic data refresh.
* Create dashboards from report visuals.
* Embed reports in company portals or websites.
* Collaborate using workspaces.
* Control report access using permissions.
* Apply Row-Level Security, also known as RLS.
* Distribute reports through Power BI Apps.
* Monitor business performance in real time or near real time.

For example, in a finance department, the accountant may prepare a monthly financial performance report in Power BI Desktop. After publishing, the finance manager can access the same report online without asking the accountant to send the file every time.

---

### **3. Power BI Desktop vs Power BI Service**

Power BI Desktop and Power BI Service are different but connected.

Power BI Desktop is mainly used for building reports.

Power BI Service is mainly used for publishing, sharing, managing, refreshing, and collaborating on reports.

Power BI Desktop is installed on your computer. It is where you connect to data, clean data using Power Query, create relationships, write DAX measures, and design report pages.

Power BI Service is accessed through a browser. It is where you publish the report, manage permissions, configure refresh, create dashboards, share reports, and embed reports.

Example:

A data analyst uses Power BI Desktop to build a finance report. After completing the report, they publish it to Power BI Service. The finance manager then logs in to Power BI Service to view the report online.

---

### **4. Important Power BI Terms**

### **Power BI Desktop**

Power BI Desktop is the application used to create reports locally on your computer.

It is used for:

* Connecting to data sources.
* Cleaning data.
* Transforming data.
* Creating relationships.
* Writing DAX measures.
* Designing report pages.
* Saving reports as `.pbix` files.

### **Power BI Service**

Power BI Service is the online platform where Power BI reports are published and managed.

It is used for:

* Viewing reports online.
* Sharing reports.
* Creating dashboards.
* Managing workspaces.
* Configuring refresh.
* Creating Power BI Apps.
* Managing access and permissions.

### **Report**

A report is a collection of pages containing visuals such as cards, charts, tables, slicers, maps, and KPIs.

Example:

A finance report may have pages such as:

* Executive Summary
* Revenue Analysis
* Expense Analysis
* Profit and Loss
* Branch Performance
* Loan Repayment Analysis

### **Semantic Model**

A semantic model is the data model behind the Power BI report.

It contains:

* Tables
* Columns
* Relationships
* Measures
* Data source connection details
* Refresh settings

In older Power BI learning materials, a semantic model was commonly called a dataset.

### **Workspace**

A workspace is an online area in Power BI Service where reports, semantic models, dashboards, and apps are stored.

Examples:

* My Workspace
* Finance Workspace
* HR Reports Workspace
* Sales Analytics Workspace
* Executive Dashboard Workspace

For professional work, it is better to publish reports to a shared workspace instead of My Workspace.

### **Dashboard**

A dashboard is a single-page summary created by pinning visuals from reports.

For example, a finance dashboard may show:

* Total Revenue
* Total Expenses
* Net Profit
* Profit Margin
* Outstanding Loans
* Monthly Collections

### **Power BI App**

A Power BI App is a packaged version of reports and dashboards that can be shared with a wider audience.

For example, a company may publish a Finance App containing:

* Monthly Revenue Report
* Expense Report
* Budget vs Actual Report
* Executive Summary Dashboard

---

### **5. What You Need Before Publishing**

Before publishing a Power BI report, you need to confirm several things.

### **Power BI Desktop Installed**

You must have Power BI Desktop installed on your machine.

This is where the report is created before publishing.

### **Power BI Account**

You need a Power BI account to publish reports to Power BI Service.

Usually, this is a work or school Microsoft account.

Example:

```text
name@company.com
```

A personal Gmail or Yahoo account may not work properly for organizational Power BI publishing.

### **Internet Connection**

Publishing uploads the report from your local computer to Power BI Service, so you need a stable internet connection.

### **Completed Report**

The report should be complete before publishing.

You should check:

* Are the visuals working?
* Are the measures correct?
* Are the slicers working?
* Are the relationships correct?
* Are there blank or broken visuals?
* Are page names clear?
* Is the report formatted professionally?
* Is sensitive information protected?

### **Workspace Access**

You must have permission to publish to the selected workspace.

If you cannot see the workspace, it may mean:

* You are using the wrong account.
* You have not been added to the workspace.
* You do not have permission to publish there.
* The workspace admin has not granted you access.

### **Correct License**

Licensing is important in Power BI.

In many normal sharing scenarios, both the person sharing and the person viewing the shared report may need a Power BI Pro license, unless the report is hosted in a Premium/Fabric capacity that allows free users to consume the content.

This means that publishing a report is not enough. The users who need to view the report must also have the required license or access setup.

---

### **6. Understanding Power BI Licenses**

Power BI has different license types. The license determines what a user can do.

### **Power BI Free License**

A free user can use Power BI for personal work and limited access.

However, free users usually cannot fully share and collaborate in normal shared workspaces unless the content is hosted in a Premium/Fabric capacity.

Example:

A trainee practicing Power BI may use a free account to create reports, but they may face limitations when trying to share reports with others.

### **Power BI Pro License**

Power BI Pro allows users to publish, share, collaborate, and view shared content in normal Power BI workspaces.

In many organizations, analysts, managers, and report consumers use Power BI Pro.

Example:

A finance analyst publishes a finance report to the Finance Workspace. The finance manager also needs a Pro license to open and interact with the report if the workspace is not in Premium capacity.

### **Power BI Premium Per User License**

Premium Per User, also called PPU, gives a user Pro capabilities plus additional Premium features.

It is useful when only selected users need Premium features.

Example:

A senior analyst working with advanced data models may use Premium Per User.

### **Power BI Premium or Fabric Capacity**

Premium or Fabric capacity allows an organization to host content in a dedicated capacity.

In some cases, users with free licenses can view content if the report and semantic model are stored in the appropriate Premium/Fabric capacity.

Example:

A large organization may buy capacity so that many staff members can view reports without giving every viewer a Pro license.

---

### **7. Finance Sector Example: Why Access Control Matters**

Assume a company has a finance report called:

```text
Monthly Finance Performance Report
```

This report contains:

* Total revenue
* Operating expenses
* Salaries
* Profit and loss
* Bank balances
* Loan repayments
* Customer payment details
* Supplier payments
* Branch performance
* Cash flow
* Budget vs actual performance

This report should not be available to everyone in the organization.

It should only be available to selected users such as:

* Finance Manager
* Chief Finance Officer
* Managing Director
* Accountant
* Internal Auditor
* Approved Executive Team

It should not be shared with:

* All staff
* Students
* External users
* Unauthorized departments
* Public website visitors

This is why publishing must be combined with proper permissions, licensing, and security.

For finance data, avoid using:

```text
Publish to Web
```

Publish to Web makes the report public and can expose sensitive data.

Instead, use:

* Direct sharing with specific users.
* Workspace permissions.
* Power BI Apps with selected audiences.
* Secure embed.
* Row-Level Security.
* Proper licensing.

---

### **8. Preparing the Report Before Publishing**

Before publishing, the report must be reviewed carefully.

### **Check the Data**

Confirm that the data is clean and accurate.

Check for:

* Missing values
* Duplicate records
* Wrong data types
* Incorrect totals
* Outdated records
* Sensitive columns
* Unnecessary columns
* Wrong currency formatting
* Incorrect dates

Finance example:

If the report contains a column called `Salary`, ask whether all users should see this column.

If not, remove it, hide it, or apply security.

### **Check Data Types**

Correct data types are important.

Examples:

| Column           | Correct Data Type |
| ---------------- | ----------------- |
| Transaction Date | Date              |
| Revenue          | Decimal Number    |
| Expense          | Decimal Number    |
| Branch           | Text              |
| Account Number   | Text              |
| Customer ID      | Text              |
| Payment Status   | Text              |

Account numbers and customer IDs should often be stored as text, not numbers, because they are identifiers, not values for calculation.

### **Check the Data Model**

Go to Model View and confirm that relationships are correct.

For a finance report, you may have:

* FactTransactions
* DimCustomer
* DimBranch
* DimDate
* DimAccount
* DimProduct
* DimDepartment

A good model improves report performance and accuracy.

### **Check Relationships**

Confirm:

* One-to-many relationships are correctly created.
* Fact tables are connected to dimension tables.
* Relationships are active where needed.
* There are no unnecessary many-to-many relationships.
* The Date table is properly connected.

Example:

```text
DimDate[Date] 1 ---- * FactTransactions[TransactionDate]
```

This means one date can appear in many finance transactions.

### **Check Measures**

Review all DAX measures before publishing.

Examples:

```DAX
Total Revenue = SUM(FactTransactions[Revenue])
```

```DAX
Total Expenses = SUM(FactTransactions[Expense])
```

```DAX
Net Profit = [Total Revenue] - [Total Expenses]
```

```DAX
Profit Margin = DIVIDE([Net Profit], [Total Revenue])
```

Check that totals match the source system.

For finance reports, wrong measures can lead to wrong business decisions.

### **Check Visuals**

Review all visuals and confirm:

* Visuals are not blank.
* Titles are clear.
* Values are formatted correctly.
* Currency values show the right currency.
* Slicers work.
* Filters are correct.
* Page navigation works.
* Visual interactions make sense.

Example:

A card showing revenue should be formatted as:

```text
KES 12.5M
```

Instead of:

```text
12500000
```

### **Check Report Pages**

Use meaningful page names.

Bad page names:

```text
Page 1
Page 2
Test
Final
Final 2
```

Good page names:

```text
Executive Summary
Revenue Analysis
Expense Analysis
Profit and Loss
Branch Performance
Cash Flow
Budget vs Actual
```

### **Check Sensitive Data**

Before publishing, ask:

* Does this report contain private data?
* Should every viewer see all rows?
* Should some users only see their department?
* Should branch managers only see their own branch?
* Should salary or bank data be hidden?
* Should customer account numbers be masked?

Finance example:

A branch manager should only see finance performance for their branch, not all branches.

This can be handled using Row-Level Security.

---

### **9. Publishing a Report from Power BI Desktop**

### **Step 1: Open the Report in Power BI Desktop**

Open your `.pbix` file.

Example file name:

```text
Monthly_Finance_Report.pbix
```

Make sure this is the correct version of the report.

Avoid publishing files named:

```text
Final_Final_New_Updated_2.pbix
```

Use clean naming.

Example:

```text
Finance_Performance_Report_June_2026.pbix
```

### **Step 2: Save the Report**

Before publishing, save the file.

Click:

```text
File > Save
```

This ensures that all recent changes are included before publishing.

### **Step 3: Sign In**

In Power BI Desktop, sign in using your Power BI account.

The account should be the same account that has access to the workspace.

Example:

```text
finance.analyst@company.com
```

If you are signed in with the wrong account, you may not see the correct workspace.

### **Step 4: Click Publish**

On the Home ribbon, click:

```text
Publish
```

Power BI will prepare to upload your report to Power BI Service.

### **Step 5: Select the Workspace**

Power BI will display available workspaces.

Examples:

```text
My Workspace
Finance Workspace
Executive Reports Workspace
Company Analytics Workspace
```

For business reports, avoid using My Workspace unless it is only for personal testing.

For a finance report, choose:

```text
Finance Workspace
```

or

```text
Executive Finance Reports
```

### **Step 6: Confirm Publishing**

After selecting the workspace, click:

```text
Select
```

Power BI will upload the report and semantic model.

### **Step 7: Wait for Publishing to Complete**

Power BI will show a message when publishing is successful.

You may see an option such as:

```text
Open report in Power BI
```

Click it to open the published report in Power BI Service.

---

### **10. What Happens After Publishing**

After publishing, Power BI usually creates two important items in the workspace:

### **1. Report**

This is the online version of your Power BI report.

Users interact with this report in the browser.

### **2. Semantic Model**

This is the data model behind the report.

It contains:

* Tables
* Measures
* Relationships
* Data source connections
* Refresh settings

Example:

If you publish:

```text
Monthly_Finance_Report.pbix
```

Power BI may create:

```text
Monthly_Finance_Report - Report
Monthly_Finance_Report - Semantic Model
```

The report depends on the semantic model. If the semantic model has errors, the report may not work correctly.

---

### **11. Reviewing the Published Report**

After publishing, do not assume everything is correct.

Open the report in Power BI Service and test it.

Check:

* Are all pages visible?
* Are all visuals loading?
* Are filters working?
* Are slicers working?
* Are bookmarks working?
* Are drill-through pages working?
* Are buttons working?
* Are totals correct?
* Is the data updated?
* Are users seeing only what they should see?

Finance example:

If a report shows profit by branch, confirm that Nairobi, Mombasa, Kisumu, Eldoret, and Nakuru branches show correct values.

Also confirm that users are not seeing confidential information they should not access.

---

### **12. Republishing a Report**

Republishing means uploading an updated version of a report that already exists in Power BI Service.

You may republish when:

* You add new visuals.
* You correct DAX measures.
* You update the data model.
* You fix errors.
* You add new pages.
* You improve formatting.
* You change relationships.
* You remove sensitive data.

### **Steps to Republish**

1. Open the original `.pbix` file in Power BI Desktop.
2. Make changes.
3. Save the file.
4. Click Publish.
5. Select the same workspace.
6. Confirm replacement when prompted.

### **Important Note**

Republishing can replace the existing report and semantic model.

Before republishing a finance report, confirm:

* You are publishing to the correct workspace.
* The report name is correct.
* You are not overwriting the wrong report.
* Measures are working.
* Sensitive data has not been exposed.
* Users have been informed if the report structure changed.

---

### **13. Sharing Published Reports**

Publishing makes the report available in Power BI Service, but it does not automatically mean everyone can access it.

Users need permission.

There are several ways to share Power BI reports.

---

### **14. Method 1: Sharing Directly with Specific Users**

Direct sharing is used when only specific people should access the report.

### **Steps**

1. Open Power BI Service.
2. Open the report.
3. Click Share.
4. Enter the email addresses of users.
5. Add a message if needed.
6. Choose whether users can reshare.
7. Click Send.

### **Example**

You share a finance report with:

```text
finance.manager@company.com
cfo@company.com
internal.audit@company.com
```

This means only those selected users can access the report.

### **Important Note**

Do not allow resharing if the report contains confidential data.

If users can reshare, they may share the report with unauthorized people.

For finance reports, it is safer to disable resharing unless there is a clear business reason.

---

### **15. Method 2: Sharing Through Workspace Access**

Workspace access allows users to access reports inside a workspace.

This is useful when a team works together.

### **Workspace Roles**

### **Admin**

An admin can manage everything in the workspace.

They can:

* Add users.
* Remove users.
* Delete content.
* Publish reports.
* Update workspace settings.
* Manage permissions.

Only trusted users should be admins.

### **Member**

A member can collaborate, publish, and manage content.

This role is useful for senior analysts or report owners.

### **Contributor**

A contributor can create and edit content but has fewer administrative rights.

This role is useful for report developers.

### **Viewer**

A viewer can only view reports and dashboards.

This role is useful for managers and business users who do not need to edit reports.

### **Finance Example**

In a Finance Workspace:

| User            | Role             |
| --------------- | ---------------- |
| Head of Finance | Viewer or Member |
| Finance Analyst | Contributor      |
| CFO             | Viewer           |
| Power BI Admin  | Admin            |
| Auditor         | Viewer           |
| General Staff   | No access        |

Do not give everyone Admin access.

Use the lowest permission needed.

---

### **16. Method 3: Sharing Through a Power BI App**

A Power BI App is useful when you want to distribute reports to a wider audience in a controlled way.

Instead of giving users direct workspace access, you package the report into an app and share the app.

### **Advantages of Power BI Apps**

* Cleaner experience for users.
* Users do not need to see the workspace.
* Easier to organize multiple reports.
* Easier to manage audiences.
* Better for company-wide reporting.
* Useful for separating report developers from report viewers.

### **Finance Example**

A Finance App may include:

* Executive Finance Summary
* Revenue Report
* Expense Report
* Budget vs Actual Report
* Branch Finance Report

The app can be shared only with:

* Finance Team
* Executive Team
* Internal Audit Team

You can create different audiences so that different groups see different reports.

---

### **17. Method 4: Secure Embed**

Secure Embed allows you to embed a Power BI report into an internal website, portal, SharePoint page, or company system.

Unlike Publish to Web, secure embed requires users to sign in and have permission.

### **Best Used For**

* Internal company portals
* Finance portals
* HR portals
* Management dashboards
* School administration systems
* Internal web applications

### **Finance Example**

A company may have an internal finance portal:

```text
finance.company.com
```

The Power BI report can be embedded inside that portal.

When users open the portal:

* They must sign in.
* Power BI checks their permissions.
* RLS can still apply.
* Unauthorized users cannot view the report.

This is safer than Publish to Web.

---

### **18. Method 5: Publish to Web**

Publish to Web creates a public link or iframe that can be placed on a website.

This method should be used very carefully.

### **Important Warning**

Publish to Web makes the report public.

Anyone with the link can access the report.

The report does not require sign-in.

This means Publish to Web should not be used for private or confidential data.

### **Do Not Use Publish to Web For**

* Finance reports
* Payroll reports
* Customer records
* Student records
* Patient records
* Company revenue reports
* Loan reports
* Bank balances
* Internal performance reports
* Private business dashboards

### **Safe Use Cases for Publish to Web**

Publish to Web may be used for:

* Demo reports
* Public event dashboards
* Public survey results
* Open data dashboards
* Training reports with fake data
* Marketing reports without sensitive data

### **Finance Example**

Do not use Publish to Web for a report showing:

```text
Revenue, expenses, profit, salaries, bank balances, and customer transactions.
```

This information should only be accessed by authorized finance users.

---

### **19. Publish to Web vs Secure Embed**

| Feature                         | Publish to Web | Secure Embed     |
| ------------------------------- | -------------- | ---------------- |
| Requires login                  | No             | Yes              |
| Public access                   | Yes            | No               |
| Good for finance data           | No             | Yes              |
| Good for demo data              | Yes            | Yes              |
| Respects user permissions       | No             | Yes              |
| Supports secure internal access | No             | Yes              |
| Best use case                   | Public reports | Internal reports |

### **Simple Explanation**

If the report is public and safe for anyone to see, Publish to Web can be used.

If the report is private, internal, or sensitive, use Secure Embed, direct sharing, workspace access, or Power BI Apps.

---

### **20. Embedding Power BI Report in a Website**

After publishing, you may want to embed the report into a website.

Power BI can generate an iframe code.

Example:

```html
<iframe 
    title="Finance Dashboard"
    width="100%"
    height="700"
    src="PASTE_POWER_BI_EMBED_LINK_HERE"
    frameborder="0"
    allowFullScreen="true">
</iframe>
```

### **Explanation of the Code**

`iframe` allows you to display the Power BI report inside another web page.

`title` gives the embedded report a name.

`width` controls how wide the report appears.

`height` controls the height of the report.

`src` contains the Power BI embed link.

`allowFullScreen` allows users to view the report in full screen.

### **Important Note**

The security of the embedded report depends on the embed method used.

If the iframe comes from Publish to Web, the report is public.

If the iframe comes from Secure Embed, users must sign in and have permission.

---

### **21. Configuring Data Refresh After Publishing**

Publishing a report does not always mean the data will automatically update.

After publishing, you need to configure refresh.

Refresh means updating the published report with the latest data from the source.

### **Why Refresh Is Important**

A finance report may be published today with current data.

Tomorrow, new transactions may be added.

If refresh is not configured, the report will continue showing old data.

This can mislead management.

### **Example**

If today’s revenue is KES 2,000,000 but the report was last refreshed two weeks ago, managers may make decisions using outdated information.

---

### **22. Steps to Configure Refresh**

### **Step 1: Open Power BI Service**

Go to Power BI Service through your browser.

### **Step 2: Open the Workspace**

Open the workspace where the report was published.

Example:

```text
Finance Workspace
```

### **Step 3: Find the Semantic Model**

Look for the semantic model connected to the report.

It usually has the same name as the report.

Example:

```text
Monthly_Finance_Report
```

### **Step 4: Open Settings**

Click the three dots beside the semantic model and select:

```text
Settings
```

### **Step 5: Configure Data Source Credentials**

Power BI needs credentials to access the data source.

Examples of data sources:

* Excel file
* SQL Server
* PostgreSQL
* MySQL
* SharePoint
* OneDrive
* Web API
* Azure SQL Database

If credentials are missing or expired, refresh will fail.

### **Step 6: Configure Gateway If Needed**

A gateway is needed when Power BI Service must connect to data stored on a local machine or private company server.

Examples that may require a gateway:

* Local Excel file
* Local SQL Server database
* On-premises PostgreSQL database
* Company network folder
* Internal finance system database

Cloud sources may not always require a gateway.

Examples:

* SharePoint Online
* OneDrive
* Azure SQL Database

### **Step 7: Set Refresh Schedule**

Go to:

```text
Refresh > Schedule refresh
```

Turn scheduled refresh on.

Choose:

* Refresh frequency
* Refresh time
* Time zone
* Failure notifications

### **Step 8: Save Settings**

After configuring refresh, save the settings.

### **Step 9: Test Manual Refresh**

Click:

```text
Refresh now
```

Then check whether the refresh succeeds.

---

### **23. Refresh Example in Finance**

Assume the finance report connects to a company SQL database.

The database is updated daily at 6:00 PM.

The Power BI report should refresh daily at 7:00 PM.

This gives the database enough time to receive the latest transactions before Power BI refreshes.

Example refresh plan:

```text
Data source update time: 6:00 PM
Power BI refresh time: 7:00 PM
Report users check dashboard: 8:00 PM
```

This ensures managers view updated numbers.

---

### **24. Checking Refresh History**

Refresh history shows whether refresh succeeded or failed.

### **Steps**

1. Open the workspace.
2. Find the semantic model.
3. Open refresh settings.
4. Click refresh history.
5. Review the status.

Refresh history may show:

* Completed
* Failed
* In progress
* Cancelled

If refresh fails, Power BI usually shows an error message.

---

### **25. Common Refresh Errors**

### **Invalid Credentials**

This happens when the username or password is wrong, expired, or changed.

Solution:

Update credentials in semantic model settings.

### **Gateway Offline**

This happens when the gateway machine is off or the gateway service is not running.

Solution:

Restart the gateway machine or service.

### **Column Not Found**

This happens when a column used in Power Query was removed or renamed in the source data.

Solution:

Open Power BI Desktop, fix the Power Query step, and republish.

### **Data Type Error**

This happens when a column has unexpected values.

Example:

A revenue column should contain numbers, but one row contains text such as:

```text
Not Available
```

Solution:

Clean the data source or update Power Query transformations.

### **File Path Error**

This happens when a file was moved, renamed, or deleted.

Solution:

Restore the file or update the file path.

---

### **26. Permissions and Security**

Publishing a report does not mean everyone should access it.

Permissions control who can:

* View the report
* Edit the report
* Share the report
* Manage the workspace
* Build new reports from the semantic model
* Export data
* Access underlying data

For confidential reports, permissions must be managed carefully.

### **Finance Security Example**

A finance report should only be available to the Finance Team and Executive Team.

Example access list:

| User Group       | Access              |
| ---------------- | ------------------- |
| Finance Analysts | Edit or Contributor |
| Finance Manager  | View or Member      |
| CFO              | View                |
| CEO              | View                |
| Internal Auditor | View                |
| General Staff    | No Access           |
| External Users   | No Access           |

### **Important Rule**

Give users only the access they need.

Do not give edit access to users who only need to view the report.

---

### **27. Row-Level Security**

Row-Level Security, also called RLS, restricts the rows of data each user can see.

This is useful when different users should see different parts of the same report.

### **Finance Example**

A company has branches in Nairobi, Mombasa, Kisumu, Nakuru, and Eldoret.

Each branch manager should only see their own branch data.

Example:

| User                   | Data They Should See |
| ---------------------- | -------------------- |
| Nairobi Branch Manager | Nairobi only         |
| Mombasa Branch Manager | Mombasa only         |
| Kisumu Branch Manager  | Kisumu only          |
| CFO                    | All branches         |
| Finance Manager        | All branches         |

Without RLS, every branch manager may see all branch data, which may not be appropriate.

### **Example RLS Rule**

If the branch column is called `Branch`, an RLS rule may look like:

```DAX
[Branch] = "Nairobi"
```

For dynamic RLS, the model can use the signed-in user’s email to filter the data.

Example concept:

```DAX
[Email] = USERPRINCIPALNAME()
```

This allows Power BI to show data based on the logged-in user.

---

### **28. Exporting Data and Security**

Power BI users may be able to export data from visuals depending on permissions and admin settings.

For finance reports, this should be reviewed carefully.

Ask:

* Should users export summarized data?
* Should users export underlying data?
* Should export be disabled?
* Should sensitive columns be hidden?
* Should account numbers be masked?
* Should salary data be removed?

Example:

A manager may need to see total salary cost, but not each employee’s individual salary.

---

### **29. Recommended Setup for Finance Reports**

For sensitive finance data, the recommended setup is:

1. Publish the report to a secure Finance Workspace.
2. Give access only to approved users.
3. Use Power BI Pro, PPU, or Premium/Fabric capacity depending on the organization’s license setup.
4. Avoid Publish to Web.
5. Use Secure Embed if embedding into an internal portal.
6. Apply Row-Level Security where needed.
7. Configure scheduled refresh.
8. Monitor refresh history.
9. Limit export permissions.
10. Review access regularly.

---

### **30. Example Finance Publishing Scenario**

A company wants to publish a report called:

```text
Finance Performance Dashboard
```

The report contains:

* Revenue
* Expenses
* Net profit
* Branch performance
* Loan repayment trends
* Customer payments
* Supplier payments
* Budget vs actual analysis

### **Correct Publishing Approach**

The analyst should:

1. Build the report in Power BI Desktop.
2. Review data quality and remove unnecessary sensitive columns.
3. Save the `.pbix` file.
4. Publish to the Finance Workspace.
5. Configure refresh.
6. Set permissions for Finance and Executive users only.
7. Apply RLS for branch-level access.
8. Share through a Power BI App or direct access.
9. Avoid Publish to Web.
10. Test access using different users.

### **Wrong Publishing Approach**

The analyst should not:

1. Publish the report to the web publicly.
2. Share the report link in a public group.
3. Give all staff access.
4. Give everyone Admin access.
5. Ignore licensing requirements.
6. Forget to configure refresh.
7. Leave salary or bank information visible to unauthorized users.

---

### **31. Power BI License Example for Finance Team**

Assume the company has the following users:

| User            | Role                          | Recommended License                                                 |
| --------------- | ----------------------------- | ------------------------------------------------------------------- |
| Finance Analyst | Builds and publishes reports  | Power BI Pro or PPU                                                 |
| Finance Manager | Views and comments on reports | Power BI Pro, PPU, or Free if content is in Premium/Fabric capacity |
| CFO             | Views reports                 | Power BI Pro, PPU, or Free if content is in Premium/Fabric capacity |
| Branch Manager  | Views branch-level data       | Power BI Pro, PPU, or Free if content is in Premium/Fabric capacity |
| General Staff   | No access                     | No report license needed                                            |

### **Important Note**

If the workspace is not backed by Premium/Fabric capacity, users normally need the correct paid license to view shared content.

If the organization has Premium/Fabric capacity, free users may be able to view reports shared with them, depending on how the workspace and content are configured.

---

### **32. Publishing Checklist**

Before publishing, confirm:

```text
The report file is saved.
The report name is clear.
The correct workspace is selected.
The visuals are working.
The data model is correct.
The DAX measures are correct.
The data is clean.
Sensitive data is protected.
RLS is configured if needed.
The correct users have access.
The correct license setup is available.
Publish to Web is not used for confidential data.
Refresh is configured.
Gateway is configured if needed.
Refresh history has been checked.
Users have tested access.
```

---

### **33. Practical Class Activity**

### **Activity Title**

Publishing and Securing a Power BI Finance Report

### **Scenario**

You are working as a data analyst in a finance department. You have created a Power BI report showing revenue, expenses, profit, branch performance, and customer payments.

The report should only be available to the Finance Team and Executive Team.

### **Task**

Students should:

1. Open the finance report in Power BI Desktop.
2. Review the report for sensitive data.
3. Save the report with a professional name.
4. Publish the report to Power BI Service.
5. Select the correct workspace.
6. Open the report online.
7. Test all visuals and slicers.
8. Configure refresh settings.
9. Explain whether a gateway is needed.
10. Decide who should access the report.
11. Explain the license needed for report viewers.
12. Explain why Publish to Web is not safe for this report.
13. Suggest whether secure embed, direct sharing, workspace sharing, or a Power BI App is best.
14. Explain how RLS can be used for branch managers.
15. Present the final published report access plan.

---

### **34. Questions for Learners**

1. What does it mean to publish a Power BI report?
2. What is the difference between Power BI Desktop and Power BI Service?
3. What is created after publishing a report?
4. What is a workspace?
5. Why should finance reports not be published using Publish to Web?
6. What is the difference between Publish to Web and Secure Embed?
7. Why is licensing important in Power BI?
8. When do users need Power BI Pro?
9. When can free users view shared reports?
10. What is Row-Level Security?
11. How can RLS help in a branch finance report?
12. Why is scheduled refresh important?
13. When is a gateway required?
14. What can cause refresh failure?
15. Why should access be reviewed regularly?

---

### **35. Summary**

Publishing a Power BI report means uploading it from Power BI Desktop to Power BI Service so that it can be accessed online.

However, publishing must be done carefully, especially when the report contains sensitive data such as finance, payroll, customer, student, or patient information.

For finance reports, access should be limited to approved users only. The report should be published to a secure workspace, shared with the correct team, protected using permissions, and secured using Row-Level Security where necessary.

Publish to Web should not be used for confidential finance data because it makes the report public.

For internal reports, better options include:

* Direct sharing
* Workspace permissions
* Power BI Apps
* Secure Embed
* Row-Level Security

Licensing is also important. Users may need Power BI Pro, Premium Per User, or access through Premium/Fabric capacity depending on how the report is shared.

A good publishing process is not just about uploading the report. It includes preparing the report, publishing to the correct workspace, securing access, configuring refresh, checking permissions, and ensuring that only the right users can view the right data.
