# Solutions

1. The [`command`](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/command_module.html#ansible-collections-ansible-builtin-command-module) module has been designed to execute any command as if its typed on the terminal without invoking a shell environment. Any command available on the system can run as long
as it doesn't rely on shell specific features like pipes and redirection.

     This is because of the `free_form` parameter that this module takes. There is no actual parameter named `free_form`. The command module takes a free form string as a command to run.
     
     Since the `uptime` command provides system information on Linux, we can use pass it as an argument to the command module to find out the system uptime on all managed nodes.
     
     ```bash
     ansible all -m command -a "uptime"
     ```

2. The [`file`]() module manage files and file properties so we need to use this to create and delete files on our managed nodes. 

     To create and delete files, we need to use these two parameters that this module provides:
     
     **1. path**: Path to the file being managed.
   
     **2. state**: Determines the desired state of the file or directory. Common values include:
          touch: Creates an empty file.
          absent: Deletes the file or directory.
       
     So to create a file, run the following command:
     
     ```bash
     ansible all -m file -a "path=/tmp/sample_file state=touch"
     ```
     
     So to delete the file `sample_file` we created in the `tmp` directory, run the following command:
     
     ```bash
     ansible all -m file -a "path=/tmp/sample_file state=absent"
     ```

3. The `df` command stands for "disk-free," and shows available and used disk space on the Linux system.
        
    Use it with the command module by passing it as an argument to see the disk usage.

    ```bash
    ansible all -m command -a "df -h"
    ```
        
    (the `-h` options displays the output in a human-readable format)
    
4. The `free` command can be used to see the amount of free and used memory on your Linux system.

    You can pass it as an argument to the command module like so:
    
    ```bash
    ansible all -m command -a "free"
    ```    
