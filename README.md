# linux-permissions-guide
 This repository provides a comprehensive guide to managing file and directory permissions in Linux. Includes examples, explanations, and use cases.

## Commands Covered 
### File Permissions 
- Grant permissions: `chmod`
- Recursive changes: `chmod -R`
- Default permissions: `umask`
- Special permissions: `SUID`, `SGID`, and sticky bit
 ### Ownership Management 
- Change owner: `chown`
- Change group: `chgrp`
## Special Permissions 
1. **SUID**: Execute files with owner's privileges.
2. **SGID**: Execute files with group privileges or maintain group ownership in directories.
3. **Sticky Bit**: Restricts file deletion to the owner.

## Details of Permissions
The rest of the string (e.g., rw-r--r-- or rwxr-xr-x) represents the permissions for the file or directory. These are broken into three groups:

**1.User (owner)**

The first three characters (rw- or rwx) specify the permissions for the file's owner.

r: Read permission.

w: Write permission.

x: Execute permission (or access for directories).

**2.Group**

The middle three characters (r-- or r-x) specify the permissions for the group associated with the file.

**3.Others**

The last three characters (r-- or r-x) specify permissions for everyone else (other users).



## Example Usage 

# Granting Permissions
**1. Granting Permissions to Others**

![Screenshot from 2024-11-30 11-11-35](https://github.com/user-attachments/assets/ba684c62-7355-48b0-b79b-062534c29fc2)

        
  - Explanation:
    - Grants read (r), write (w), and execute (x) permissions to others for file f1.
    - In the output of ls -l, the first character of each line indicates the type of the file:
      - Regular file: - 
      - Directory: d
    
**2. Granting Permissions to Group**
       
![Screenshot from 2024-11-30 11-12-29](https://github.com/user-attachments/assets/ce0b410a-6e22-480f-a395-ef9d631baee4)


  - Explanation: Grants rwx permissions to the group for f1.

**3. Granting Permissions to User**

![Screenshot from 2024-11-30 11-13-52](https://github.com/user-attachments/assets/b3df4a47-426f-4bb4-baa1-993bb70638df)

     
  - Explanation: Grants rwx permissions to the file owner (user).

**4. Removing All Permissions for User**

![Screenshot from 2024-11-30 11-14-41](https://github.com/user-attachments/assets/ca1ac753-58c4-46cf-b02e-0562cbb8ca8d)

  - Explanation: Removes all permissions (rwx) for the owner.

 **5. Granting Write Permission to All**
    
 ![Screenshot from 2024-11-30 11-15-39](https://github.com/user-attachments/assets/9e5d85f2-4df5-44fd-8c93-b01651ef9167)


  - Explanation: Grants write (w) permission to all users, removing any other permissions.

# Numeric Permissions
  
  **6. Setting Specific Permissions Using Octal Notation**
    
  for folder : Read(4) Write(2) Execute(1) 
 
  for file : Read(4) Write(2)
 
![Screenshot from 2024-11-30 11-16-53](https://github.com/user-attachments/assets/2633363b-4ec4-428b-8ca9-3723ad0e96a6)

  - Explanation: Sets permissions for xyz as follows:
     - Owner: Read (4) + Write (2) = 6
     - Group: Write (2) + Execute (1) = 3
     - Others: Execute (1) = 5

  **7. Change Permissions Recursively**

![Screenshot from 2024-11-30 10-36-50](https://github.com/user-attachments/assets/7fd25d16-d5fe-42b4-8b9c-fdb489fc7f2d)

  - inside file permission not change but we use -R then

![Screenshot from 2024-11-30 10-39-03](https://github.com/user-attachments/assets/0db0903a-5a30-4c47-9b24-e269e4e88c2b)

  - Explanation: Recursively sets 222 (write-only) permissions for all files and directories within xyz.

# Default Permissions and umask
    
  **8. Check default permissions for directories and files**
       
![Screenshot from 2024-11-30 10-44-19](https://github.com/user-attachments/assets/7c3a1dc7-a70c-47cb-8f80-bf072fb2fdf0)

  - Explanation: The default umask is 022, resulting in
      - Directories: 777 - 022 = 755 (drwxr-xr-x).
      - Files: 666 - 022 = 644 (-rw-r--r--).
  
  **9. Change umask and verify its effect**

  ![Screenshot from 2024-11-30 10-47-26](https://github.com/user-attachments/assets/d497571e-b09d-48f5-ab25-1f5d19f2c93a)

   - Explanation: umask 444: New permissions for directories will be 333 (d-wx-wx-wx).

# Ownership Management

  **10. Change file owner (user)**
      
  ![Screenshot from 2024-11-30 10-50-20](https://github.com/user-attachments/assets/683b3ab1-049b-4c3e-a9cb-b2e966e5df07)

  - Explanation: chown jack xyz: Transfers ownership of xyz to the user jack.
    
  **11. Change file owner (group)**
      
  ![Screenshot from 2024-11-30 10-53-01](https://github.com/user-attachments/assets/51fa201b-a9e1-41b3-8b35-f278a021a895)

  - Explanation: chgrp A1 xyz: Sets the group owner of xyz to A1.
    
  **12. Change both user and group ownership**
       
  ![Screenshot from 2024-11-30 10-55-00](https://github.com/user-attachments/assets/1cbc3679-ae36-45ea-8bea-d7bf11080595)

  - Explanation: chown tom:B1 xyz: Assigns ownership of xyz to user tom and group B1.
    
# Special Permissions  
  **13. Set User ID (SUID):**
        
  ![Screenshot from 2024-11-30 11-03-37](https://github.com/user-attachments/assets/33011214-831d-4b61-bb99-9357fa0fd633)

  - Explanation: Adds SUID bit, which allows a file to execute with the owner's privileges.
        
  **14. Set Group ID (SGID):**

  ![Screenshot from 2024-11-30 11-05-07](https://github.com/user-attachments/assets/d92a9c02-137d-4e09-93dc-74829b29dfad)

   - Explanation: Adds SGID bit, which executes files with group privileges or retains group ownership in directories.
  
  **15. Sticky Bit:**
          
  ![Screenshot from 2024-11-30 11-07-29](https://github.com/user-attachments/assets/d8c6ded6-b5b0-4955-b5f0-cdbd083664d3)

  - Explanation: Adds a sticky bit, restricting file deletion to the owner.
