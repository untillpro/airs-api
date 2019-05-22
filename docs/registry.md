# Resources

Registry keeps the following resources:

- users
- applications
- workspaces
- devices

# Resource ID

All resources are identified by `ID int64`

# Workspace

- Workspace keeps application resources
- Application can keep resources in a few workspaces
- Workspace keeps resources of only one application

# User

- Each user has one associated workspace where user settings are kept

# Application

- Each application has associated workspace where application settings are kept

# Workspace Connected Resources

- Users/devices/applications may be connected to a workspace
- Only connected resources are authorized to view/change workspace resources
- All workspace connections are identified by `workspaceID` and `connectionId int32`
- Connection describes:
  - Resource type
  - Resource role
  - Application specific information (say permissions)
- Workspace has zero or more connected devices
  - Device connection identifed by `device-connection-id int32`


# Workspace