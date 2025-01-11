# **Level 1: Getting Started with Ansible**

## **Objective:**

Learn basic Ansible commands and test connections.

---

## **Topics Covered:**

### **1. What is Ansible**

Ansible is an open-source tool that allows you to automate tasks like configuration management and application deployment. It is written in Python and can be installed on the control node using the package manager (`apt` for Ubuntu).

---

### **2. Understanding the Control Node and Managed Nodes**

- **Control Node:** This is the machine where Ansible is installed and run. It sends instructions (tasks) to other machines (called managed nodes).

- **Managed Nodes:** These are the machines you want to control using Ansible. They execute the tasks sent from the control node.

- The control node sends tasks to the managed nodes over an encrypted SSH connection.

- No additional software (agent) is needed on the managed nodes—just an SSH service and Python.

- Ansible is agentless, meaning it doesn't require any agent or service running on the managed nodes. Ansible runs entirely from the control node, which sends commands to the managed nodes using SSH.

---

### **3. SSH Key-Based Authentication**

SSH keys are used to enable secure, passwordless authentication between the control node and managed nodes.

**Why SSH keys?**

- They are more secure than passwords.
- Ansible needs non-interactive access, which requires passwordless login.

**How it works:**

1. You generate an SSH key pair (a private key and a public key).
2. The public key is copied to each managed node.
3. When you connect, the managed node checks if the public key matches the private key. If they match, the managed node allows the SSH connection and Ansible tasks can be executed.

---

### **4. Inventory**

An inventory file lists the managed nodes (their IP addresses or hostnames) that the control node will manage. This is how Ansible knows which machines to run tasks on.

```ini
managed_node_1
managed_node_2
managed_node_3
```

## **Tasks**

### **1. Set Up Your Ansible Environment**

Use Docker to create:

- 1 control node
- 3 managed nodes  

Follow the steps outlined in [Setting Up Your Environment](../setting-up-environment.md).

---

### **2. Create your inventory file**

### **3. Ping Your Managed Nodes**

Run the following command to test connections:

```bash
ansible all --key-file </path/to/your/private/key/file> -i <your-inventory-file-name> -m ping
```

**Victory Condition:**

You should see `"pong"` responses for all managed nodes.

**Bonus Task**

- Improve Your Inventory Using Variables
- Instead of passing the SSH key as command-line option, update your inventory file to include its path. `Hint: Checkout inventory variables.`

This is what your command should look like:

```bash
ansible all -i <your-inventory-file-name> -m ping
```

