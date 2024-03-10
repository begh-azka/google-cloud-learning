# Resource Hierarchy

- Organization
- Folder
- Project
  
**-----------------------------------------------------------------**

- **Organizations -> Folder -> Project -> Resources**
  
**-----------------------------------------------------------------**

- Resources are created in Projects.
- A Folder can contain multiple Projects as well as sub folders.
- An Organization can contain multiple Folders.
- Free Tier accounts can't use Organizations.

### Purpose

- Provides hierarchy of ownership.
- Provides attach points and inheritance for access controls and organization policies.
- Policy attached at a higher level will automatically be inherited by resources at a lower level (Policy Inheritance).
  
### Advantages of using Organizations:

- When a user is not working on a small scale project for learning purpose and joins a workplace, then a business organization is used.
- When a Google Workspace or Cloud Identity account creates a project, an organization is created automatically.
- All projects created by members of the account domain will belong by default to the same Organization resource.
- Google workspace super admins are granted the ability to assign IAM roles by default.
- Projects belong to Organization rather than user that created them. But in a free account, projects are linked to users. If their id is disabled, project is also deleted.
