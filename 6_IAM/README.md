# Identity and Access

### Identity

- Represents a user or entity that has privileges to perform actions in Google Cloud.
- GCP has 7 types of **Principals** (called Members earlier):
  - **Google Account:** Represents a person (an email address).
  - **Service Account:** Represents an application or instance account rather than a user (has an email id).
  - **Google Group:** Represents collection of Google Accounts and Service Accounts. Has a unique email address. Helps to apply access policy/roles to a group of users.
  - **Google Workspace Account:** It is a member of an organization's Google Workspace domain. Provides collaboration services for enterprises. Tools like Gmail, Calendar, Meet, Chat, Drive, Docs etc. are included. 
  - **Cloud Identity Domain:** Cloud Identity is an **Identity as a Service** solution that centrally manages users and groups. You can use IAM to manage access to resources for each Cloud Identity account.
  - **All Authenticated Users**
  - **All Users**
    
## Access Control Concepts

1. **Permissions**: Permissions are specific actions that can be performed on resources, such as read, write, delete, etc.
   
2. **Roles:**
   - **A role contains a set of permissions that allows you to perform specific actions on Google Cloud resources.** To make permissions available to principals, including users, groups, and service accounts, you grant roles to the principals.
   - Role Types: 
     - **Predefined** (Already exist. Managed by GCP)
     - **Custom** (We can create new roles as per our needs)
     - **Basic** (Called Primitive roles. Existed before IAM existed. In the early GCP days, there were basic roles like editor, viewer and owner. They are not recommended.)
      
4. **Policies:**
   - **Policies are used to define who has access to what resources and what actions they can perform on those resources.**
   - They are attached to resources.
   - Used to enforce access control whenever that resource is accessed.
   - Defined with **bindings**, list of members and role granted.
   - Each IAM policy consists of a set of rules.
     A rule specifies a role and the members to whom that role is granted.
   - You can have multiple rules within a single IAM policy, allowing you to grant different permissions to different members.
   - **IAM Bindings:**
     - In Cloud IAM, identities can get access to resource APIs via IAM policies. In these policies, you can define one or more bindings in which members are granted an IAM role.
     - This associates the binding’s members with all the permissions granted to this role at that policy level (organization, folder or project) and below (if any).

## Naming Convention
### For Roles:

- `Predefined roles:` **roles/SERVICE.IDENTIFIER**
   - Example: roles/accessapproval.approver, roles/apigateway.viewer
- `Project-level custom roles:` **projects/PROJECT_ID/roles/IDENTIFIER**
   - Example: 
- `Organization-level custom roles:` **organizations/ORG_ID/roles/IDENTIFIER**

### For Permissions
- Permissions have the following format: **`SERVICE.RESOURCE.VERB`**
- Example: compute.instances.list, pubsub.topics.publish

## Custom Role Lifecycle
- Custom roles include a launch stage as part of the role's metadata. The most common launch stages for custom roles are **ALPHA, BETA, and GA.** These launch stages are informational; they help you keep track of whether each role is ready for widespread use. Another common launch stage is **DISABLED**. This launch stage lets you disable a custom role.
- It is recommended that you use launch stages to convey the following information about the role:
  - **EAP** or **ALPHA**: The role is still being developed or tested, or it includes permissions for Google Cloud services or features that are not yet public. It is not ready for widespread use.
  - **BETA**: The role has been tested on a limited basis, or it includes permissions for Google Cloud services or features that are not generally available.
  - **GA**: The role has been widely tested, and all of its permissions are for Google Cloud services or features that are generally available.
  - **DEPRECATED**: The role is no longer in use.

## IAM Best Practices

1. **Principle of Least Privilege:** Give least possible privilege needed for a role.
  - Basic Roles are NOT recommended.
    - Prefer pre-defined and even better custom roles whenever possible.
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
  
