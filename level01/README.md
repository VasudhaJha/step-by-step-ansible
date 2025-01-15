# **Level 1: Getting Started with Ansible**

## **Objective:**

Learn basic Ansible commands and test connections.

---

## **Topics Covered:**

### **1. What is Ansible?**

Ansible is an open-source tool that allows you to automate tasks like software installation, configuration management and application deployment. It is written in Python and can be installed on the control node using the package manager for that OS (`apt` for Ubuntu, `yum` for CentOS).

---

### **2. Understanding the Control Node and Managed Nodes**

- **Control Node:** This is the machine where Ansible is installed and run. It sends instructions (tasks) to other machines (called managed nodes).

- **Managed Nodes:** These are the machines you want to control using Ansible. They execute the tasks sent from the control node.

- The control node sends tasks to the managed nodes over an encrypted SSH connection.

- Ansible is **agentless**, meaning it doesn't require any agent or service running on the managed nodes. Ansible runs entirely from the control node, which sends commands to the managed nodes using SSH.

- No additional software (agent) is needed on the managed nodes—just an SSH service and Python.

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

### **4. Ansible Inventory**

An inventory file lists the managed nodes (their IP addresses or hostnames) that the control node will manage. This is how Ansible knows which machines to run tasks on.

```ini
managed_node_1
managed_node_2
managed_node_3
```

#### Inventory Formats

1. INI format (default): Uses group headings and `key=value` pairs:

```ini
[my_servers]
managed_node_1
managed_node_2
```

2. YAML format: Uses structured key-value pairs (requires .yml extension):

```yaml
all:
  hosts:
    managed_node_1:
    managed_node_2:
```

- By default, Ansible looks for a file named `inventory` or `hosts` in the project directory. However, you can name it anything (e.g., `my_inventory`, `inventory.txt`, `prod_hosts`, etc.) as long as you specify the path when running Ansible.

- Ansible inventory files are usually plain text files and do not need. But you can still use them for clarity if you prefer.

## **Tasks**

### **1. Set Up Your Ansible Environment**

Use Docker to create:

- 1 control node
- 3 managed nodes  

Follow the steps outlined in [Setting Up Your Environment](../setting-up-environment.md).

---

### **2. Create your inventory file**

The inventory file tells Ansible which nodes it should manage.

**Instructions:**

1. Create an inventory file named `inventory`.
2. Add your managed nodes (use Docker container names or IP addresses).
3. Run the following command to verify your inventory:

```bash
ansible all --list-hosts -i inventory
```

### **3. Ping Your Managed Nodes**

Run the following command to test connections:

```bash
ansible all -i inventory --key-file /path/to/your/private/key/file -m ping
```

**Explanation:**

- `all`: Runs the command on all hosts listed in the inventory file.
- `-i inventory`: Specifies the inventory file. Replace `inventory` with the actual file name if you used a different name (e.g., `my_inventory`).
- `--key-file /path/to/your/private/key/file`: Specifies the path to your SSH private key (typically ~/.ssh/id_rsa or /home/ubuntu/.ssh/id_rsa).
- `-m ping`: The ping module checks if Ansible can connect to the managed nodes. A "pong" response indicates a successful connection.

**Victory Condition:**

You should see `"pong"` responses for all managed nodes.

### **Bonus Task**

Instead of passing the SSH key as a command-line option, update your inventory file to include its path.

💡 Hint:
Read up on inventory variables. Check out the `ansible_ssh_private_key_file` inventory variable in Ansible’s documentation.

This is what your command should look like after you make that change:

```bash
ansible all -i <your-inventory-file-name> -m ping
```

You should see "pong" responses from all managed nodes without passing the SSH key in the command line.


