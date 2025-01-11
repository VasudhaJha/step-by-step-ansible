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

- Tasks:
  - Run your first ansible ping command
  - Install packages using apt/yum modules

### **Level 2: Working with Modules**

- **Objective: Understand Ansible modules and how to use them in ad-hoc commands.**

- Topics Covered:
  - Core modules (ping, command, copy, file)
  - Using arguments (-a) in ad-hoc commands

- Tasks:
  - Copy a file to managed nodes
  - Change file permissions using the file module

### **Level 3: Creating Inventory and Configuration Files**

- **Objective: Learn how to organize your inventory and create ansible.cfg files.**

- Topics Covered:
  - Static and dynamic inventory
  - Configuration options in ansible.cfg

- Tasks:
  - Create an inventory file with grouped hosts
  - Configure `host_key_checking = False` in ansible.cfg

### **Level 4: Writing Playbooks**

- **Objective: Learn how to write Ansible playbooks to automate complex tasks.**

- Topics Covered:
  - YAML syntax
  - Defining tasks, hosts, and handlers

- Tasks:
  - Write a playbook to update managed nodes
  - Add conditionals and loops in your playbook

### **Level 5: Using Roles for Reusability**

- **Objective: Understand how to create and use Ansible roles for reusable automation.**
- Topics Covered:
  - Folder structure of roles
  - Creating roles for web server deployment

- Tasks:
  - Create an Ansible role for Nginx setup
  - Use ansible-galaxy to download external roles

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


