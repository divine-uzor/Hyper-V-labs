# Building a Windows Server 2019 Lab on Microsoft Hyper-V

> **Part 1:** Preparing the Environment and Creating a Virtual Machine


## Overview

Creating a virtual machine involves much more than clicking **New → Virtual Machine**.

A reliable virtualization environment begins with proper planning. Before installing an operating system, you should organize storage, prepare networking, download trusted installation media, configure the virtual machine correctly, and verify every important setting before the first boot.

This lab demonstrates the complete preparation process for building a **Windows Server 2019** virtual machine using **Microsoft Hyper-V**.

By following these best practices, you establish a solid foundation for future Windows Server administration and Active Directory labs.


## Learning Objectives

After completing this lab, you will be able to:

- Prepare a structured Hyper-V lab environment
- Organize storage for virtual machines
- Download the Windows Server 2019 Evaluation ISO
- Create an isolated virtual network using a Private Virtual Switch
- Create a Generation 2 virtual machine
- Configure memory, networking and storage
- Attach installation media
- Verify the virtual machine configuration before powering it on

---

## Lab Environment

| Component | Configuration |
|-----------|---------------|
| Hypervisor | Microsoft Hyper-V |
| Guest Operating System | Windows Server 2019 Evaluation |
| VM Generation | Generation 2 |
| Startup Memory | 4096 MB |
| Virtual Hard Disk | 50 GB VHDX |
| Network Type | Private Virtual Switch |



# Step 1: Create a Storage Folder for the Virtual Machine

A dedicated storage folder keeps virtual machine configuration files, virtual hard disks and checkpoints organized in one location.

This makes future maintenance, backups and troubleshooting much easier.

### Screenshot

![Create VM Storage Folder](images/01-create-vm1-storage-folder.png)

### Screenshot

![VM Storage Folder Created](images/01-vm-storage-folder-created.png)


# Step 2: Download Windows Server 2019

Windows Server is installed from an ISO image.

Always download installation media directly from Microsoft's Evaluation Center to ensure authenticity and integrity.

### Screenshot

![Download Windows Server ISO](images/02-download-windows-server-iso.png)


# Step 3: Open Hyper-V Manager

Hyper-V Manager provides the interface used to create, configure and manage virtual machines.

This is where the entire virtualization environment is administered.

### Screenshot

![Open Hyper-V Manager](images/03-open-hyper-v-manager.png)


# Step 4: Create a Private Virtual Switch

Virtual machines require a virtual switch before they can communicate across a network.

For this lab, a **Private Virtual Switch** creates an isolated environment where virtual machines can communicate without accessing the host network or the Internet.

### Open Virtual Switch Manager

![Open Virtual Switch Manager](images/04-create-virtual-switch.png)

### Create the Private Virtual Switch

![Create Private Virtual Switch](images/04-create-virtual-switch2.png)


# Step 5: Launch the New Virtual Machine Wizard

With the environment prepared, the next step is to create the virtual machine.

### Open the Wizard

![Launch New Virtual Machine Wizard](images/05-new-virtual-machine.png)

### Before You Begin

The wizard displays an introductory page explaining the creation process.

Click **Next** to continue.

![Before You Begin](images/05-new-virtual-machine2.png)


# Step 6: Configure the Virtual Machine Name and Storage Location

Provide a meaningful name for the virtual machine and store it inside the dedicated lab folder created earlier.

Keeping the VM in its own location simplifies management and keeps related files together.

### Screenshot

![Configure VM Name and Location](images/06-configure-vm-name-and-location.png)


# Step 7: Select Generation 2

Generation 2 virtual machines support modern features including:

- UEFI firmware
- Secure Boot
- Faster boot process
- Improved compatibility with modern operating systems

Windows Server 2019 is fully supported on Generation 2 virtual machines.

### Screenshot

![Select Generation 2](images/07-select-generation-2.png)


# Step 8: Assign Startup Memory

Memory determines the resources available when the virtual machine starts.

For this lab:

- Startup Memory: **4096 MB**
- Dynamic Memory: **Enabled**

Dynamic Memory allows Hyper-V to optimize RAM usage while the virtual machine is running.

### Screenshot

![Assign Memory](images/08-assign-memory.png)


# Step 9: Configure Networking

Connect the virtual machine to the **Private Virtual Switch** created earlier.

This ensures the VM communicates only within the isolated lab environment.

### Screenshot

![Configure Networking](images/09-configure-networking.png)


# Step 10: Create the Virtual Hard Disk

The virtual hard disk stores:

- Windows Server
- Installed applications
- User data
- System configuration

For this lab, create a **50 GB dynamically expanding VHDX**.

### Screenshot

![Create Virtual Hard Disk](images/10-create-virtual-hard-disk.png)


# Step 11: Choose the Installation Media

Attach the Windows Server 2019 Evaluation ISO.

Hyper-V mounts this ISO as a virtual DVD drive during installation.

### Screenshot

![Installation Options](images/11-installation-options.png)


# Step 12: Review the Configuration Summary

Before creating the virtual machine, carefully review every configuration.

Confirm:

- VM name
- Storage location
- Memory
- Network
- Virtual hard disk
- Installation media

If any setting is incorrect, return to the previous page and update it before continuing.

### Screenshot

![Review Summary](images/12-review-summary.png)


# Step 13: Confirm the Virtual Machine Has Been Created

After clicking **Finish**, Hyper-V creates the virtual machine.

At this stage, the VM should appear in **Hyper-V Manager** with a status of **Off**.

This indicates that the virtual machine has been created successfully and is ready for configuration verification.

### Screenshot

![Virtual Machine Created](images/13-virtual-machine-created.png)


# Verify the Virtual Machine Configuration

Before powering on the virtual machine, verify its configuration.

Checking these settings now helps prevent installation issues later.


## Step 14: Open Virtual Machine Settings

Open the virtual machine's **Settings** window.

This provides access to all hardware and firmware configuration options.

### Screenshot

![Open VM Settings](images/14-open-vm-settings.png)


## Step 15: Verify Firmware Settings

Generation 2 virtual machines use **UEFI firmware**.

Verify that the **DVD Drive** appears before the hard drive in the boot order so the virtual machine starts from the Windows Server installation media.

### Screenshot

![Verify Firmware Settings](images/15-verify-firmware-settings.png)


## Step 16: Verify Security Settings

Generation 2 virtual machines support **Secure Boot**.

For Windows Server 2019:

- Secure Boot should be enabled.
- The Secure Boot template should be set to **Microsoft Windows**.

These settings help ensure a secure boot process.

### Screenshot

![Verify Security Settings](images/16-verify-security-settings.png)


## Step 17: Verify Memory Configuration

Confirm that the startup memory matches the value configured during the virtual machine creation process.

Also verify that **Dynamic Memory** is enabled if required.

### Screenshot

![Verify Memory Configuration](images/17-verify-memory-configuration.png)


## Step 18: Verify Network Adapter Configuration

Finally, verify that the virtual machine is connected to the correct **Private Virtual Switch**.

Without the correct virtual switch, the virtual machine will not communicate with other systems in the lab.

### Screenshot

![Verify Network Adapter](images/18-verify-network-adapter.png)


# Verification Checklist

Before proceeding to the Windows Server installation, confirm the following:

- ✅ Hyper-V environment prepared
- ✅ VM storage location created
- ✅ Windows Server ISO downloaded
- ✅ Private Virtual Switch configured
- ✅ Generation 2 virtual machine created
- ✅ Startup memory configured
- ✅ Virtual hard disk created
- ✅ Installation media attached
- ✅ Firmware verified
- ✅ Secure Boot verified
- ✅ Memory configuration verified
- ✅ Network adapter verified

If all items above are complete, the virtual machine is ready for operating system installation.


# Key Takeaways

In this lab, you learned how to prepare a professional Hyper-V environment before installing Windows Server.

Although creating a virtual machine takes only a few minutes, careful preparation helps avoid configuration errors and creates a more reliable virtualization environment.

These same preparation practices are commonly used in enterprise environments when deploying virtual infrastructure.


# Next Steps

This guide covers the first part of building a Windows Server 2019 virtual machine on Microsoft Hyper-V.

With the virtual machine successfully created and verified, the environment is now ready for operating system installation and subsequent Windows Server administration labs.

In the next part, you will:

- Start the virtual machine
- Install Windows Server 2019
- Configure the Administrator account
- Complete the initial server setup
- Prepare the virtual machine for future Windows Server administration and infrastructure labs


⭐ If you found this guide helpful, consider starring this repository.
