# **Level 2: Configuration Management**

## **Objective:**

Understand how to configure Ansible settings for ease of use.

---

## **Topics Covered:**

### **Ansible Configuration file**

The `ansible.cfg` file is a configuration file that controls how Ansible behaves. It allows you to set default options, paths, and behaviors, so you don’t have to pass them as command-line options every time.

It specifies defaults for things like:

- **Inventory file location**
- **SSH connection options**
- **Default private key file**

and many more.

**Example configuration file**:

```ini
[defaults]
inventory = ./inventory
remote_user = ubuntu
private_key_file = /home/ubuntu/.ssh/id_rsa
```

Unlike the inventory file, whose scope is at the host level, the configuration file applies to the whole of ansible (unless overriden).

#### Available Configuration Options

Ansible provides a wide range of configuration options that can be set in ansible.cfg. To see all the available options, you can use the
`ansible-config list` command.

This command outputs a detailed list of all configurable options, including:

- The default value of each option.
- A description of what the option does.
- The section and key where the option should be placed in ansible.cfg.

Example Output (from ansible-config list):

```plaintext
ACTION_WARNINGS:
  default: true
  description:
  - By default, Ansible will issue a warning when received from a task action.
  ini:
  - key: action_warnings
    section: defaults
```

Look for the section key under the ini field in the output of `ansible-config list`. It tells you which section (e.g., [defaults], [privilege_escalation]) the option belongs to.

In this example, the configuration option `action_warnings` should be placed under the [defaults] section in ansible.cfg.

You would add it like this:

```ini
[defaults]
action_warnings = true
```

Tip: Use `ansible-config dump` to see active configurations.
This is useful for verifying which settings are active and where they are being sourced from (e.g., project-specific, user-level, or system-wide configuration).

#### Scope and Priority of Configuration Files

When Ansible is installed, it creates a system-wide configuration file at `/etc/ansible/ansible.cfg`.

This file applies to all users and projects unless overridden by a user-level or project-specific `ansible.cfg` file.

Ansible looks for the `ansible.cfg` file in the following order:

1. `ANSIBLE_CONFIG` environment variable

    You can set this environment variable to specify the exact path to a custom ansible.cfg file:

    ```bash
    export ANSIBLE_CONFIG=/path/to/custom/ansible.cfg
    ```

    **Priority: This path is used first if it is set, overriding all other locations.**

2. Project-specific (./ansible.cfg) – The configuration in the current working directory.

    **Priority: This file is used first if it exists, overriding all others.**

3. User-level (~/.ansible.cfg) – Applies to all Ansible runs for the current user.

    **Priority: This is used if no project-specific configuration is found.**

4. System-wide (/etc/ansible/ansible.cfg) – Applies to all users on the system.

    **Priority: This is used only if neither project-specific nor user-level files exist.**

To check which configuration file is being used, run this command:

```bash
ansible --version
```

Example output:

```bash
ansible [core 2.17.7]
  config file = /etc/ansible/ansible.cfg
  ...
```

In the above example, the system-wide configuration file is being used.

##### Security Consideration: World-Writable Directories

Ansible will not load a configuration file from the current working directory if the directory is world-writable (permissions 777), due to security risks.

**Why?**

A world-writable directory allows any user to create or modify files inside it. If a malicious user places their own `ansible.cfg` file in such a directory, it could:

- Override important settings (e.g., SSH key paths, user permissions).
- Run malicious pre/post commands with elevated privileges.

**To check the permissions of your directory, run:**

```bash
ls -ld <directory-name>
```

```bash
drwxrwxrwx 2 user user 4096 Jan 1 12:00 my_project/
```

`rwxrwxrwx` indicates that everyone (owner, group, others) can write to the directory.
To make the directory secure:

```bash
chmod 755 <directory-name>
```

This changes permissions so only the owner can write, while others can only read and execute.

---

## **Tasks**

### **1.Create a custom ansible.cfg file and run the ansible ping command**

1. Specify the following defaults:

    1. Inventory file path
    1. Private key file path
    1. Remote user

2. Run the following command:

    ```bash
    ansible all -m ping
    ```

This should work without needing to pass `--key-file` or `-i` options.

---

**Victory Condition:**

The ping command works without explicitly specifying the inventory or key file.

### **Bonus Tasks**

Explore Additional Configuration Options in the Ansible documentation to:

1. Adjust the connection timeout.
2. Add a log file to capture Ansible run outputs.

