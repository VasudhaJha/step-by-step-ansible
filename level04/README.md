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
    - Ensure the user’s .ssh directory is created and contains an authorized SSH key.

4. Managing Package Versions

    Write a playbook to:

    - Install a specific version of nginx (e.g., >=1.24) on all managed nodes.
    - Verify the installation by running nginx -v and print the result to the console.

TIPS:

- Checkout the [Ansible Playbook Keywords Reference](https://docs.ansible.com/ansible/latest/reference_appendices/playbooks_keywords.html) to find out which other keywords you might need to use. For example, question 2 requires you use to use sudo, to install and start the apache2 service. Look for the keyword which helps you do that. 

- Just like we used the `command` and `file` modules in the previous level, you will need to use the `apt` and `service` modules to solve some of these questions.

- After you've finished writing a playbook, run it in the `syntax-check` and the `check` modes to ensure that the playbook does not have any syntax errors, and runs as you intended it to.

---

