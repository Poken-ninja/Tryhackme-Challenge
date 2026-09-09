# Virtualization Fundamentals

## What is Virtualization?

**Virtualization** is a technology that allows one physical computer/server to run multiple separate virtual computers.

Instead of:

```text
Physical Server
    ↓
One Application
```

we can have:

```text
Physical Server
        ↓
    Hypervisor
   /    |     \
  VM1   VM2    VM3
   |     |      |
Linux  Windows  Linux
```

Each VM can have its own:

* Operating system
* Applications
* CPU allocation
* Memory
* Storage
* Network configuration

The VMs share the physical hardware underneath, but they operate as separate systems.

---

# Why Virtualization Exists

Traditionally, organizations often used one physical server for one major application.

For example:

```text
Server 1 → Website
Server 2 → Database
Server 3 → Email
Server 4 → Internal Application
```

This creates several problems:

* Expensive hardware
* High electricity and cooling costs
* Large amount of physical space required
* Slow deployment
* Poor resource utilization

A server might have 32 GB of RAM but an application may only use 5 GB.

Virtualization allows the unused resources to be shared with other VMs.

```text
Physical Server
32 GB RAM
        ↓
Hypervisor
   ↓       ↓       ↓
 VM 1    VM 2    VM 3
 8 GB    8 GB    8 GB
```

This improves hardware utilization.

---

# Hypervisor

A **hypervisor** is software that creates and manages virtual machines.

It controls how physical resources such as:

* CPU
* RAM
* Storage
* Network

are allocated to VMs.

Think of the hypervisor as the **manager between the physical hardware and virtual machines**.

```text
Applications
     ↓
Operating Systems
     ↓
Virtual Machines
     ↓
Hypervisor
     ↓
Physical Hardware
```

---

# Virtual Machine (VM)

A **Virtual Machine** is a virtualized computer running inside a physical computer.

For example, I can run:

```text
Windows Host
     ↓
VirtualBox
     ↓
Kali Linux VM
```

The Kali VM behaves like a separate computer even though it is actually using resources from my physical laptop.

This is especially useful in cybersecurity because I can create isolated environments for testing.

---

# Why VMs Are Useful for Cybersecurity

Virtualization is extremely useful for security labs.

For example:

```text
Windows Host
      |
   VirtualBox
      |
 ┌────┴───────────┐
 ↓                ↓
Kali Linux     Windows VM
Attacker        Target
```

I can use this type of environment to safely practice:

* Network analysis
* Vulnerability scanning
* Malware analysis
* SIEM labs
* Incident response
* Penetration testing
* Detection engineering

The isolation provided by virtualization reduces the risk of experimenting directly on my main operating system.

---

# VM Resources

When creating a VM, I need to decide how much hardware it will receive.

Important resources include:

### CPU

Number of virtual CPU cores assigned to the VM.

Example:

```text
4 CPU cores
```

### Memory

Amount of RAM assigned to the VM.

Example:

```text
8 GB RAM
```

### Disk

Amount of virtual storage available to the VM.

Example:

```text
100 GB disk
```

### Network

Controls how the VM communicates with:

* The host
* Other VMs
* The local network
* The Internet

---

# Virtualization Manager

A virtualization management platform can provide a central view of the virtual environment.

It can show:

```text
Lab Machines
     ↓
VM status
CPU
Memory
Disk
Network
Uptime
```

It can also provide information about the physical hosts running those VMs.

For example:

```text
Physical Host
      ↓
Hypervisor
      ↓
VM 1
VM 2
VM 3
VM 4
```

This makes it easier for administrators to monitor and manage many VMs.

---

# VM States

A VM can have different states.

Examples:

```text
Running
Stopped
Error
Disconnected
```

If a VM enters an error state, an administrator may need to investigate and restart it.

In the TryHackMe lab, the `Mail-SERVER` VM entered an `Error` state. Restarting the VM resolved the immediate issue and restored the email service.

This demonstrates an important IT concept:

> A problem with a virtual machine can cause the application running on that VM to become unavailable.

---

# Physical Hosts

A **physical host** is the actual physical server that provides hardware resources for virtual machines.

Example:

```text
Physical Host: HV-PROD-01
        |
   Hypervisor
        |
 ┌──────┼──────┐
 ↓      ↓      ↓
 VM1    VM2    VM3
```

Multiple VMs can run on the same physical host.

Administrators therefore need to monitor host capacity.

Important resources include:

* CPU utilization
* Memory utilization
* Storage
* Network
* Number of VMs

If a host is close to 100% capacity, it may not be able to safely support additional workloads.

---

# Containers vs Virtual Machines

Virtual machines virtualize an entire computer.

```text
VM

Application
     ↓
Guest OS
     ↓
Virtual Hardware
     ↓
Hypervisor
     ↓
Physical Hardware
```

Containers are different.

A container packages an application and its dependencies while sharing the host operating system's kernel.

```text
Containers

App 1     App 2     App 3
  ↓         ↓         ↓
Container Runtime
       ↓
Host OS
       ↓
Hardware
```

Containers are generally lighter and faster to start than full VMs.

---

# Virtualization vs Containers

| Feature        | VM                       | Container                    |
| -------------- | ------------------------ | ---------------------------- |
| Virtualizes    | Entire computer          | Application environment      |
| Guest OS       | Yes                      | Usually no separate guest OS |
| Resource usage | Higher                   | Lower                        |
| Startup        | Usually slower           | Usually faster               |
| Isolation      | Strong                   | Strong, but different model  |
| Example        | Kali Linux in VirtualBox | Docker container             |

---

# Key Benefits of Virtualization

### Cost Savings

Multiple workloads can share the same physical hardware.

### Resource Utilization

CPU, memory and storage can be allocated between multiple VMs.

### Isolation

VMs can operate separately from each other.

### Faster Deployment

Creating a VM can be much faster than purchasing and configuring a physical server.

### Scalability

Resources and workloads can be adjusted more easily.

### Portability

VMs can often be moved or copied between compatible environments.

### Security Testing

Virtual machines are useful for creating isolated cybersecurity labs.

---

# Cybersecurity Perspective

Virtualization is important to cybersecurity because modern security environments frequently depend on virtual infrastructure.

As a security analyst, I should understand that an alert may involve:

```text
Application
    ↓
VM
    ↓
Hypervisor
    ↓
Physical Host
    ↓
Network
```

A compromised VM could potentially affect other systems depending on the architecture and security controls.

This means virtualization is not only an IT administration topic. It is also part of the **security attack surface**.

---

# My Lab Environment

A simple cybersecurity lab might look like:

```text
My Physical Laptop
        ↓
VirtualBox
        ↓
┌──────────────────────┐
│ Kali Linux VM        │
│                      │
│ Security Tools       │
└──────────────────────┘

        +

┌──────────────────────┐
│ Windows VM           │
│                      │
│ Target / Logs        │
└──────────────────────┘
```

This lets me build isolated environments for learning cybersecurity without needing multiple physical computers.

---

# Quick Revision

Remember these four terms:

**Virtualization**

> Technology that allows one physical computer to run multiple virtual computers.

**Hypervisor**

> Software that creates and manages virtual machines and allocates physical resources to them.

**Virtual Machine**

> A virtual computer with its own operating system, applications and virtual hardware.

**Container**

> An isolated environment for running an application that generally shares the host OS kernel.

The basic architecture to remember:

```text
VMs
 ↓
Hypervisor
 ↓
Physical Hardware
```

And for containers:

```text
Containers
 ↓
Container Runtime
 ↓
Host OS
 ↓
Physical Hardware
```

---

# TryHackMe Lab Takeaways

The practical lab demonstrated several real-world virtualization administration tasks:

* Checking VM status
* Restarting a VM in an error state
* Creating a new VM
* Allocating CPU, RAM and disk
* Checking VM uptime
* Checking memory usage
* Monitoring physical host capacity
* Identifying which physical host runs the most VMs

The main lesson:

> Virtualization allows organizations to use physical hardware more efficiently while providing isolated environments that can be created, managed and monitored centrally.
