# Ansible Learning & Automation Playbooks

This repository contains a comprehensive collection of Ansible playbooks designed to demonstrate core automation concepts, from basic service management to advanced variable precedence and error handling.

## 🚀 Getting Started

### Inventory Management
The project uses `inventory.ini` to manage target hosts. It is currently configured with:
- `[frontend]`: Remote server nodes.
- `[local]`: The local control node (using `connection: local`).
- `[local:vars]`: Examples of variables defined within the inventory.

### Running Playbooks
To run any playbook using the provided inventory:
```bash
ansible-playbook -i inventory.ini <playbook-name>.yaml
```

---

## 📁 Repository Structure

### 1. Foundations
Basic building blocks for Ansible automation.
- **[01-playbook.yaml](01-playbook.yaml)**: Simple connectivity test using the `ping` module.
- **[02-ngnix.yaml](02-ngnix.yaml)**: Real-world example of installing, enabling, and starting the Nginx service.
- **[03-multiplay.yaml](03-multiplay.yaml)**: Demonstrates structuring multiple plays within a single YAML file.

### 2. Variable Management & Precedence
One of the most critical aspects of Ansible is how it handles variables. This sequence shows the hierarchy of variables:
- **[04-variables.yaml](04-variables.yaml)**: Play-level variables (strings, lists, and maps).
- **[05-task_var.yaml](05-task_var.yaml)**: Localizing variables to specific tasks.
- **[06-var_file.yaml](06-var_file.yaml)**: Loading variables from external files ([varibale_file.yaml](varibale_file.yaml)).
- **[07-var_prompt.yaml](07-var_prompt.yaml)**: Interactive variable collection from the user (e.g., passwords).
- **[08-vars_inventory.yaml](08-vars_inventory.yaml)**: Utilizing variables defined in the inventory file.
- **[09-vars-args.yaml](09-vars-args.yaml)**: Passing "extra-vars" from the CLI using `-e`.
- **[10-vars-preference.yaml](10-vars-preference.yaml)**: A lab demonstrating the order of precedence (Task > File > Prompt > Play > Inventory).

### 3. Control Flow & Facts
Logic and dynamic decision making.
- **[11-data-types.yaml](11-data-types.yaml)**: Exploring YAML data types (integers, booleans, and nested dictionaries).
- **[12-conditions.yaml](12-conditions.yaml)**: Using the `when` statement for simple logic.
- **[13-gather-facts.yaml](13-gather-facts.yaml)**: Investigating the `ansible_facts` dictionary.
- **[14-facts.yaml](14-facts.yaml)**: Multi-OS package management (RedHat vs. Debian) using system facts.

### 4. Loops & Iteration
Efficient management of multiple items.
- **[15-loops.yaml](15-loops.yaml)**: Basic iteration over a list of strings.
- **[16-loops.yaml](16-loops.yaml)**: Batch package installation using loops.
- **[17-advanced_loops.yaml](17-advanced_loops.yaml)**: Iterating over complex dictionaries to handle variables like `state` (latest/absent).

### 5. Advanced filters & Error Handling
Polishing and robust automation.
- **[18-functions.yaml](18-functions.yaml)**: Extensive use of Jinja2 filters (`upper`, `lower`, `split`, `dict2items`, `items2dict`) and `set_fact`.
- **[19-error_handling.yaml](19-error_handling.yaml)**: Managing failures with `ignore_errors`, `register`, and custom return code checks.

---

## 🛠️ Data Files
- **[student.yaml](student.yaml)**: Sample structured data used for demonstrating YAML-to-JSON conversions and data parsing.

---

> [!NOTE]
> Ensure you have the necessary SSH keys or sudo privileges (`become: yes`) configured on target nodes for playbooks involving package installation.
