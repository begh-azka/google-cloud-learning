# Identity and Access

### Identity
- Represents a user or entity that has privileges to perform actions in Google Cloud.
- GCP has 7 types of **Principals** (called Members earlier):
  - **Google Account:** Represents a person (an email address).
  - **Service Account:** Represents an application or instance account rather than a user (have an email id).
  - **Google Group:** Represents collection of Google Accounts and Service Accounts. Has a unique email address. Helps to apply access policy/roles to a group of users.
  - **Google Workspace Account:** It is a member of an organization's Google Workspace domain. Provides collaboration services for enterprises. Tools like Gmail, Calendar, Meet, Chat, Drive, Docs etc. are included. 
  - **Cloud Identity Domain:** Cloud Identity is an **Identity as a Service** solution that centrally manages users and groups. You can use IAM to manage access to resources for each Cloud Identity account.
  - **All Authenticated Users**
  - **All Users**
    
### Access Control Concepts
- Resources
- Permissions
- _Roles_
  - **Predefined** (Already exist)
  - **Custom** (We can create new roles as per our needs)
  - **Basic** (Existed before IAM existed. In the early GCP days, there were basic roles like editor, viewer and owner. They are not recommended.)
- Policies (Define what identities can do on what resources)
  
## IAM Best Practices
1. **Principle of Least Privilege:** Give least possible privilege needed for a role.
  - Basic Roles are NOT recommended.
    - Prefer pre-defined roles whenever possible.
  - Use Service Accounts with Minimum Privileges.
    - Use different Service Accounts for different apps/purposes.

2. **Separation of Duties:** Involve atleast 2 people in sensitive tasks.
   - Example: Have separate deployer and traffic migrator roles.
   - AppEngine provides App Engine Deployer and App Engine Service Admin roles.
      - App Engine Deployer can deploy new versions but cannot shift traffic.
      - App Engine Service Account can shift traffic but cannot deploy new versions.

3. **Constant Monitoring:** Review Cloud Audit Logs to audit changes to IAM  policies and access to Service Account Keys.
   - Archive Cloud Audit Logs in Cloud Storage buckets for long term retention.

4. **Use Groups whenever possible:**
   - Makes it easy to manage users and permissions.
  
