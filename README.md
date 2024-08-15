# Metasploit Penetration Testing Lab

This project demonstrates the use of Metasploit for penetration testing in a controlled lab environment. The lab consists of multiple virtual machines, each configured on a subnet for realistic testing scenarios.

## Lab Setup

### Network Configuration
- **Subnet:** 192.168.23.0/24

### Virtual Machines
- **Kali Linux**
  - **IP Address:** 192.168.23.149
  - **Role:** Attacker
  
- **Metasploitable 2**
  - **IP Address:** 192.168.23.154
  - **Role:** Vulnerable Target
  
- **Windows XP**
  - **IP Address:** 192.168.23.130
  - **Role:** Legacy System
  
- **Windows 10**
  - **IP Address:** 192.168.23.160
  - **Role:** Modern System

## Configuring PostgreSQL

An important feature of Metasploit is its backend database support for PostgreSQL, which allows us to store penetration-testing results effectively. Penetration tests often generate a large amount of data and can span several days. This makes it crucial to store intermediate results and findings, such as target host data, system logs, collected evidence, and report data, in a structured way. Metasploit’s integration with PostgreSQL enables quick and efficient storage of these results.

In this section, we will walk through the process of installing and configuring the PostgreSQL database on Kali Linux.

### Step 1: Start PostgreSQL Service

Before initializing the Metasploit database, we need to start the PostgreSQL server. we can do this by running the following command in your terminal:

```bash
systemctl start postgresql
```

![hostonly](cap/start.png)

### Step 2: Verify Database Initialization

As the database has already been configured, we skip the initialization step. However, if needed, the initialization can be done using the following command:

```bash
msfdb init
```

If the database is already configured, we may see the following output:

![hostonly](cap/database.png)

### Step 3: Verify Database Connection

We can verify that the database is successfully connected to Metasploit by launching Metasploit and checking the database status:

```bash
msfconsole
db_status
```

With the database configured, Metasploit automatically stores data from our sessions, including scanned hosts, vulnerabilities, and credentials. This feature helps us manage and analyze the results of our penetration tests efficiently.

