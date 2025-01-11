# **Setting Up Your Ansible Environment (Local with Docker)**

This guide walks you through setting up a local Ansible learning environment using **Docker containers**. You’ll create:

- 1 control node (where Ansible runs)
- 3 managed nodes (the target systems that Ansible will manage)

---

## **Steps:**

### **1. Pull the Ubuntu Image**

We will be using `ubuntu` as our linux OS of choice for both our control and managed nodes.

```bash
docker pull ubuntu:latest
```

### **2. Create a Docker Network**

By default, Docker containers are isolated from one another.
When you create a custom Docker network, containers connected to this network can communicate using container names instead of IP addresses.

```bash
docker network create ansible_network
```

### **3. Create and Run Docker Containers

- **Control Node (Ansible Control Node)**

```bash
docker run -dit --name ansible_control --network ansible_network ubuntu:latest
```

- **Managed Nodes**:

```bash
docker run -dit --name managed_node_1 --network ansible_network ubuntu:latest
docker run -dit --name managed_node_2 --network ansible_network ubuntu:latest
docker run -dit --name managed_node_3 --network ansible_network ubuntu:latest
```

### **4. Install Essential Software**

💡 Note:

- Ansible uses SSH to communicate with the managed nodes. Therefore, the SSH service must be running on each managed node.

- Ansible modules (such as apt, yum, file, etc.) are written in Python and need the Python interpreter on the managed nodes to execute. Ansible converts YAML tasks into Python scripts that are executed remotely via SSH.

- Ansible is agentless, meaning it doesn't require any agent or service running on the managed nodes. Ansible runs entirely from the control node, which sends commands to the managed nodes using SSH.

#### On Control Node (ansible_control)

- Open a shell session:

```bash
docker exec -it ansible_control bash
```

- Update packages:

```bash
apt update
```

- Install Ansible and necessary tools:

```bash
apt install -y software-properties-common ssh sudo vim python3 ansible
```

💡 Note:

When you exec into a Docker container, you are logged in as the root user by default. However, using root for routine operations is not recommended - production workloads typically avoid root access and instead use a regular user with elevated permissions (sudo), as this adds an extra layer of control and security.

A user called `ubuntu` user comes pre-configured in the Ubuntu Docker image that we are using. So, we will:

- Grant ubuntu sudo permissions to allow elevated actions without using root.
- Switch to the ubuntu user for better security.
- Set up SSH access for the ubuntu user on all managed nodes.

### **5. Configure the Managed Nodes**

#### On Each Managed Node

**Repeat these steps for managed_node_1, managed_node_2, and managed_node_3**:

- Open a shell session:

```bash
docker exec -it managed_node_X bash
```

- Update packages:

```bash
apt update
```

- Install essential software:

```bash
apt install -y ssh sudo vim python3
```

- Add `ubuntu` user to the sudo group:

```bash
usermod -aG sudo ubuntu
```

- Enable passwordless sudo:
By default, sudo commands prompt for a password. If the managed node prompts for a password during an Ansible task, the process will hang or fail because Ansible cannot interactively provide the sudo password.

Open the sudoers file using visudo:

```bash
visudo
```

Add this line at the end:

```ini
ubuntu ALL=(ALL) NOPASSWD:ALL
```

Here’s what each part means:

- `ubuntu`: The user who is being granted permissions (in this case, the ubuntu user).

- `ALL=(ALL)`: This means the ubuntu user can run commands as any user (including root).

- `NOPASSWD:ALL`: The NOPASSWD keyword removes the password requirement for all sudo commands.

### **6. Set Up SSH Keys for Passwordless Authentication**

- On the control node

- Add `ubuntu` user to the sudo group:

```bash
usermod -aG sudo ubuntu
```

- Enable passwordless sudo: Open the sudoers file using visudo:

```bash
visudo
```

Add this line at the end:

```ini
ubuntu ALL=(ALL) NOPASSWD:ALL
```

- Switch to the ubuntu user

```bash
su ubuntu
```

- generate an SSH key pair:

```bash
ssh-keygen -t rsa -b 2048 -f ~/.ssh/id_rsa -q -N ""
```

- Copy the public key to each managed node:

```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub ubuntu@managed_node_X
```

