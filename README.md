# step-by-step-ansible

🚀 **A practical, hands-on guide to mastering Ansible through structured levels of exercises, challenges, and real-world examples.**

---

## **Table of Contents**
1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Levels Overview](#levels-overview)
4. [How to Use This Repository](#how-to-use-this-repository)
5. [Contributing](#contributing)
6. [Resources](#resources)

---

## **Introduction**

Ansible is a powerful, open-source automation tool used for configuration management, application deployment, and orchestration. If you’ve ever felt overwhelmed by tutorials that jump around or if you’re stuck in "tutorial purgatory," this repository is for you.

This project will guide you through a **task-based** approach to learning Ansible, one step at a time. Each "level" builds on the previous one, covering key concepts and providing actionable tasks to solidify your understanding.

---

## **Getting Started**

### **1. Prerequisites**
- **Basic knowledge of Linux commands**
- Familiarity with **SSH and text editors** (like `vim` or `nano`)
- Basic knowledge of **Docker** (since we will be using Docker containers for setting up our environment)

## **Levels Overview**

### **Level 1: Getting Started with Ansible**

- **Objective: Learn basic Ansible commands and test connections.**

- Topics Covered:
  - Installing Ansible
  - Understanding the control node and managed nodes
  - SSH key-based authentication
  - Ansible Inventory

- Tasks:
  - Set Up Your Ansible Environment
  - Create your inventory file
  - Run your first ansible ping command

### **Level 2: Configuration Management (ansible.cfg)**

- **Objective: Understand how to configure Ansible settings for ease of use.**

- Topics Covered:
  - Ansible Configuration file

- Tasks:
  - Create a custom ansible.cfg file and run the ansible ping command

### **Level 3: Running Commands on Managed Nodes**

- Objective: Learn to execute shell commands on managed nodes using ad-hoc Ansible commands.

- Topics Covered:
  - Using the command and shell modules
  - Understanding differences between the command and shell modules

- Tasks:
  - Run the uptime command on all managed nodes
  - Create and delete a temporary file using the command module

### **Level 4: Copying Files to Managed Nodes**

- Objective: Learn how to copy files from the control node to managed nodes.

- Topics Covered:
  - Using the copy module to transfer files
  - Understanding file permissions and ownership

- Tasks:
  - Copy a "hello.txt" file to /tmp/ on all managed nodes
  - Verify the contents of the file on one of the managed nodes

### **Level 5: Writing Playbooks**

- **Objective: Understand how to create and execute playbooks for automating tasks.**

- Topics Covered:
  - YAML syntax for Ansible playbooks
  - Defining tasks, hosts, and handlers

- Tasks:
  - Write a playbook to update the system packages on managed nodes
  - Add tasks to clean up old logs from /var/log

### **Level 6: Using Variables in Playbooks**

- **Objective: Learn how to make your playbooks more dynamic with variables.**

- Topics Covered:
  - Declaring variables in playbooks
  - Passing variables at runtime

- Tasks:
  - Create a playbook with a variable for the package name (e.g., nginx)
  - Run the playbook with a different package name by passing it as a runtime variable

### **Level 7: Using Conditionals**

- **Objective: Learn how to perform tasks only when specific conditions are met.**

- Topics Covered:
  - Using the when clause in playbooks
  - Checking the return codes of commands

- Tasks:
  - Write a playbook that installs nginx only if it’s not already installed
  - Add a task that runs a restart command only if the configuration file has changed

### **Level 8: Loops in Playbooks**

- **Objective: Learn how to perform the same task multiple times using loops.**

- Topics Covered:
  - Using the loop keyword in tasks
  - Working with item lists

- Tasks:
  - Write a playbook that installs multiple packages (git, curl, vim)
  - Create a playbook that adds multiple users to the system using a loop

### **Level 9: Creating and Using Roles**

- **Objective: Organize your playbooks into reusable roles for maintainability.**

- Topics Covered:
  - Role directory structure
  - Creating tasks, variables, and templates in roles

- Tasks:
  - Create a role to install and configure nginx
  - Use the role in a playbook to deploy a web server

### **Level 10: Templates and Jinja2**

- **Objective: Use templates to dynamically generate configuration files.**

- Topics Covered:
  - Creating Jinja2 templates
  - Using Ansible variables within templates

- Tasks:
  - Create a Jinja2 template for an index.html file
  - Deploy the template to /var/www/html/index.html on all managed nodes

### **Level 11: Handlers in Playbooks**

- **Objective: Learn to use handlers for performing tasks when specific conditions are triggered.**

- Topics Covered:
  - Defining handlers in playbooks
  - Triggering handlers using notify

- Tasks:
  - Write a playbook to restart nginx only when its configuration file is updated
  - Add a handler for reloading the service when the configuration changes

### **Level 12: Debugging and Error Handling**

- **Objective: Improve your debugging skills by handling errors gracefully.**

- Topics Covered:
  - Using the debug module
  - Ignoring errors and registering output

- Tasks:
  - Add debug messages to an existing playbook to print variable values
  - Write a playbook that gracefully handles failures during package installation

### **Level 13: Tags in Playbooks**

- **Objective: Learn how to selectively run tasks in a playbook using tags.**

- Topics Covered:
  - Adding tags to tasks
  - Running tasks selectively using --tags

- Tasks:
  - Add tags to tasks in an existing playbook (e.g., update, cleanup)
  - Run the playbook with specific tags (e.g., only run tasks tagged as cleanup)

### **Level 14: Ansible Vault (Encrypting Sensitive Data)**

- **Objective: Learn how to encrypt sensitive data in Ansible.**

- Topics Covered:
  - Creating encrypted files using ansible-vault
  - Editing and decrypting vault files

- Tasks:
  - Create an encrypted file with a database password
  - Use the encrypted file in a playbook to set environment variables

### **Level 15: Dynamic Inventory**

- **Objective: Learn how to use dynamic inventory for large-scale infrastructure.**

- Topics Covered:
  - Setting up dynamic inventory scripts
  - Using cloud-specific inventory plugins (e.g., AWS EC2)

- Tasks:
  - Configure a dynamic inventory for AWS EC2 instances
  - Run a playbook to list all instances in your AWS account
## **How to Use This Repository**

- Follow Each Level in Order: Each level builds on the previous one.
- Test Your Knowledge: Try creating your own playbooks and modules after each level.
- Share Your Progress: Create a branch for your solutions or raise issues for discussions.

## **Contributing**

Contributions are welcome! Here’s how you can contribute:

- Fork the repository.
- Create a new branch (feature/my-improvement).
- Submit a pull request (PR) with a clear description.

## **Resources**

- [Ansible Documentation](https://docs.ansible.com/)
- [Learn YAML Basics](https://www.youtube.com/watch?v=o9pT9cWzbnI)
- [How SSH Works](https://www.youtube.com/watch?v=rlMfRa7vfO8&t=130s)

---
Happy automating! 🎉


