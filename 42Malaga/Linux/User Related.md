1. **List Users with `getent` Command**: The `getent` command searches and displays system database entries. By default, it includes the passwd database.   
    Example: `getent passwd`
    This command will list all users, along with their respective details such as username, UID, home directory, and shell.
    
2. **List Users with `awk` Command**: You can use `awk` to extract specific fields from the `/etc/passwd` file.
    Example: `awk -F: '{ print $1 }' /etc/passwd`
    This command will list only the usernames (first field) in the `/etc/passwd` file.
    
3. **List Users with `cut` Command**: Similar to `awk`, `cut` can be used to extract specific fields from the `/etc/passwd` file.
    Example: `cut -d: -f1 /etc/passwd`
    This command will also list only the usernames (first field) in the `/etc/passwd` file.
    
4. **List Users with `more` Command**: You can use `more` or `less` commands to browse through the `/etc/passwd` file page by page.
    Example: `more /etc/passwd`
    The `more` command will display the file contents one screen at a time, allowing you to navigate through the file using keyboard shortcuts.
    
5. **Count Users**: You can use `getent` with the `-c` option to count the number of users.
    Example: `getent -c passwd`
    This command will output the total number of users in the system.
    
6. **Filter Users by UID Range**: You can use `grep` to filter users based on their UID range. For example, to list normal users with UIDs between 1000 and 60000:
    Example: `grep -E '^([^:]+:.*)' /etc/passwd | awk -F: '$3 >= 1000 && $3 <= 60000'`
    This command will list only users with UIDs within the specified range.