# Device-Request-Implementation-using-ServiceNow
Device Request Management app in ServiceNow with custom tables, roles, and forms. Integrates with CMDB, Service Catalog, and Flow Designer for automation. Features include auto-numbering, scripted field population, validations, approvals, and GitLab version control for streamlined request handling.

📦 Device Request Implementation
A Device Request Management solution built in ServiceNow, integrated with GitLab for version control.
This project streamlines device requests, inventory tracking, approvals, and automates workflows using Flow Designer.


📌 Features

      🖥️ Custom Device Request Application
      📚 Integration with CMDB for device tracking
      🔐 Role-based access control (Device, Release, Dispatch, End User)
      🛒 Service Catalog & Catalog Items with auto-populated fields
      ✅ Data validations for improved accuracy
      ⚙️ Automated workflows using Flow Designer
      🌐 GitLab integration for source control

🚀 Implementation Steps

1. Create Application
  
      Provide application name and description.
      Assign roles:
      Device Management
      Release Management
      Dispatch Management
      End User
      Select Classic and Mobile experience.
      Create table extending Task:
      Label: Device Request
      Enable Auto Number.
      Configure Access Controls for roles.

3. GitLab Integration
      In ServiceNow Studio: Source Control → Link to Source Control.
      Create GitLab repo → copy HTTPS URL.
      Paste into ServiceNow configuration.
      Add credentials in:
      discovery_credentials table
      OR Credentials in Application Navigator.

4. Create Devices Table
      Extend from cmdb_ci (Configuration Item).
      Configure form to include device details.

5. Configure Device Request Table
        Create sections: Device Details, Delivery Details.
        Use UI Policies to make fields read-only.
        Add approvals & assignment group fields.

6. Service Catalog Setup
        Create Catalog and Catalog Items.
        Reference fields:
        user → Requestor Name
        core_company → Requestor Company
        devices → Selected Device
        Auto-populate price, email, phone using AutoPopulate.

7. Validations
      select_quantity → integers only.
      Auto-calculate price from quantity.
      Disable sections until device name is selected.
      delivery_date visible only if Delivered.
      Require Business Justification if quantity > 3.

7. Flow Designer Automation
      Create task on item approval.
      Uncheck Wait in Create Task step.
      Link flow to Catalog Item’s Process Engine.
