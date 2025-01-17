# **Level 4: Writing Playbooks**

## **Objective:**

Understand how to create and execute playbooks for automating tasks.

---

## **Topics Covered:**

### **1. Defining Playbook, Play, Task, and Modules**

To understand what playbooks, plays, tasks, hosts, and modules are, and how to run a playbook, refer to the official [Ansible Playbooks Documentation](https://docs.ansible.com/ansible/latest/getting_started/get_started_playbook.html). This section provides a comprehensive explanation of how these components fit together and are used to automate tasks.

### **2. Verifying Playbooks**

It's considered good practice to verify playbooks first before running them on your production servers in order to prevent introducing unforseen issues into the system.

**- Syntax Check**: Before running a playbook, verify its syntax to ensure it’s correct:

```bash
ansible-playbook playbook.yaml --syntax-check
```

**- Dry Run (Check Mode)**: Execute the playbook without making changes to see what would happen:

```bash
ansible-playbook playbook.yaml --check
```

**- Diff Mode**: Use diff mode to see what changes would be made to managed nodes. This is especially helpful for tasks that modify files, as it shows the differences between the current state and the desired state:

```bash
ansible-playbook playbook.yaml --diff
```

Tip: You can combine `--check` and `--diff`:

```bash
ansible-playbook playbook.yaml --check --diff
```

This performs a dry run and shows file modifications that would happen without actually applying them.

---

## **Tasks**

1. Basic File Management

    Write a playbook to:

    - Create a directory /tmp/ansible_practice on all managed nodes.
    - Inside this directory, create a file example.txt with the content "Hello, Ansible!".
    - Ensure the file permissions are 0644.

2. Service Installation and Management

    Write a playbook to:

    - Install Apache2 on all managed nodes.
    - Ensure the Apache2 service is started and enabled to start on boot.

3. User and Group Management

    Write a playbook to:

    - Create a group named devops.
    - Add a user named deploy_user to the devops group with:
        - A home directory /home/deploy_user.
        - Password authentication enabled (set a dummy password).
    - Ensure the user’s .ssh directory is created and contains an authorized SSH key.

4. Managing Package Versions

    Write a playbook to:

    - Install a specific version of nginx (e.g., 1.20.1) on all managed nodes.
    - Verify the installation by running nginx -v and print the result to the console.
    - If the version installed is incorrect, uninstall it and reinstall the correct version.

---

