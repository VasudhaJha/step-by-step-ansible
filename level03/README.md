# **Level 3: Running Ad-hoc Commands on Managed Nodes**

## **Objective:**

Learn to execute commands on managed nodes using ad-hoc Ansible commands and Ansible modules.

---

## **Topics Covered:**

### **1. Ad-hoc Commands**

**Ansible ad-hoc commands** are **one-line commands** that you can run directly from the terminal to quickly perform tasks across multiple managed nodes. They are useful for **simple, one-off operations**, such as:

- Checking the status of servers.
- Rebooting machines.
- Installing packages.
- Copying files.

Ad-hoc commands are a great way to perform quick tasks without having to write a full playbook.

The general syntax for an ad-hoc command is:

```bash
ansible <host_pattern> -i <inventory_file> -m <module_name> -a "<module_arguments>"
```

- **`<host_pattern>`**: The target hosts (e.g., `all`, `web_servers`, or a specific IP).
- **`i <inventory_file>`**: Specifies the path to the inventory file (optional if defined in `ansible.cfg`).
- **`m <module_name>`**: The module to use (e.g., `ping`, `command`, `apt`).
- **`a "<module_arguments>"`**: Arguments passed to the module (optional for some modules).

Example: `ansible all -m ping`

### **2. Ansible Modules**

Ansible modules are pre-written pieces of code that Ansible uses to perform specific operations like file management, package installation, user creation.

#### **Module Types:**

- **Core modules:** These come [built-in](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html#plugins-in-ansible-builtin) with Ansible (e.g., `ping`, `command`, `copy`, `file`). You can find them in the `ansible.builtin` collection (packages of Ansible content) and can be used without additional setup.
- **Collection modules:** Additional modules that can be installed from the Ansible Galaxy or custom collections (e.g., AWS modules, Kubernetes modules).
- **Custom modules:** You can write your own Python-based modules for specific use cases.

---

## **Tasks**

1. Check the system uptime on all managed nodes using ad-hoc commands.

2. Use the provided modules to create and delete a file on managed nodes.

3. Use an ad-hoc command to check the disk space usage on all managed nodes.

4. Run a command to display the memory usage on all managed nodes.

---

### **Bonus Task**

Write a command to find all `.log` files in the `/var/log/ directory` that contain the word `ERROR`, count the number of occurrences, and save the result to a file called `/tmp/error_count.txt` on each managed node.

Tip: You will have to use the `shell` module here. (Why?)

