# Building a Windows Server 2019 Lab on Microsoft Hyper-V

> **Part 1:** Preparatory Steps and Creating a Virtual Machine

## Overview

This lab demonstrates how to prepare a Microsoft Hyper-V environment and create a Generation 2 Windows Server 2019 virtual machine.

Rather than jumping directly into creating a virtual machine, this lab follows a structured approach by first preparing the environment. This includes organizing storage, downloading the Windows Server installation media, creating an isolated virtual network, configuring the virtual machine, and verifying its settings before the first boot.

Following these preparatory steps helps build a clean, organized, and reliable virtualization environment while reducing configuration mistakes later during the Windows Server installation.


## Lab Objectives

By completing this lab, you will learn how to:

- Create a dedicated storage location for Hyper-V virtual machines
- Download the Windows Server 2019 Evaluation ISO from Microsoft
- Create and configure a Private Virtual Switch
- Create a Generation 2 virtual machine
- Configure memory, networking and storage
- Attach the Windows Server installation ISO
- Verify the virtual machine configuration before powering it on


## Lab Environment

| Component | Details |
|----------|---------|
| Hypervisor | Microsoft Hyper-V |
| Guest Operating System | Windows Server 2019 Evaluation |
| Virtual Machine Generation | Generation 2 |
| Network Type | Private Virtual Switch |
| Startup Memory | 4096 MB (4 GB) |
| Virtual Hard Disk | 50 GB (VHDX) |


## Prerequisites

Before starting this lab, ensure that:

- Microsoft Hyper-V is installed and enabled.
- Hardware virtualization is enabled in the BIOS/UEFI.
- Windows Server 2019 Evaluation ISO has been downloaded from Microsoft's official Evaluation Center.
- You have sufficient free disk space to create the virtual machine.


# Step 1: Create a Storage Folder for the Virtual Machine

Creating a dedicated storage folder keeps all virtual machine resources, including configuration files, virtual hard disks, and checkpoints in a single location. This makes the environment easier to manage and simplifies future backup and maintenance tasks.

### Procedure

1. Open **File Explorer**.
2. Navigate to a drive with sufficient free space.
3. Create a new folder (for example, **HyperV-Labs**).
4. Optionally create subfolders such as:

- Virtual Machines
- Virtual Hard Disks

### Screenshot

![Create VM Storage Folder](images/01-create-vm-storage-folder.png)


# Step 2: Download Windows Server 2019

Windows Server 2019 is distributed as an ISO image that Hyper-V mounts as a virtual DVD during installation.

Always download installation media from Microsoft's official Evaluation Center to ensure the image is authentic and free from tampering.

### Procedure

1. Visit the Microsoft Evaluation Center.
2. Download the **Windows Server 2019 Evaluation ISO**.
3. Choose your preferred language.
4. Save the ISO inside your Hyper-V lab folder.

### Screenshot

![Download Windows Server ISO](images/02-download-windows-server-2019-iso.png)


# Step 3: Create a Private Virtual Switch

Virtual machines require a virtual switch for network connectivity.

For this lab, a **Private Virtual Switch** is used to create an isolated environment where virtual machines can communicate without connecting to the host computer or the Internet.

This prevents accidental interaction with your production or home network while building the lab.

### Procedure

1. Open **Hyper-V Manager**.
2. Select **Virtual Switch Manager**.
3. Choose **Private**.
4. Click **Create Virtual Switch**.
5. Assign a descriptive name.
6. Save the configuration.

### Screenshot

![Create Private Virtual Switch](images/03-create-private-virtual-switch.png)


# Part 1: Create the Virtual Machine

With the storage location, installation media and virtual network prepared, the environment is now ready for the virtual machine.

The following steps create the virtual machine shell that will host Windows Server 2019 in the next part of this series.
## Step 4: Launch the New Virtual Machine Wizard

With the preparation complete, the next stage is to create the virtual machine.

At this point, you are not installing Windows Server yet. Instead, you are defining the virtual machine's hardware configuration, including its firmware, memory, networking, storage, and installation media.

### Procedure

1. Open **Hyper-V Manager**.
2. In the **Actions** pane, select **New** → **Virtual Machine**.
3. When the **Before You Begin** page appears, click **Next**.

### Screenshot

![Launch the New Virtual Machine Wizard](images/04-start-new-virtual-machine-wizard.png)


## Step 5: Specify the Virtual Machine Name and Location

Giving your virtual machine a descriptive name makes it easier to identify later, especially when managing multiple servers.

Instead of storing the virtual machine in Hyper-V's default location, this lab stores it inside the dedicated lab folder created earlier. Keeping all files together simplifies management, backups, and troubleshooting.

### Procedure

1. Enter a descriptive name for the virtual machine.
2. Select **Store the virtual machine in a different location**.
3. Browse to the storage folder created in Step 1.
4. Click **Next**.

### Screenshot

![Specify Name and Location](images/05-configure-vm-name-and-location.png)


## Step 6: Select Generation 2

Hyper-V provides two virtual machine generations.

For Windows Server 2019, **Generation 2** is recommended because it supports modern firmware technologies such as UEFI and Secure Boot.

These features improve compatibility with current operating systems and provide a more modern boot process.

### Procedure

1. Select **Generation 2**.
2. Click **Next**.

### Screenshot

![Select Generation 2](images/06-select-generation-2.png)


## Step 7: Assign Startup Memory

Memory allocation determines how much RAM is available when the virtual machine starts.

For this lab, the startup memory is configured as **4096 MB (4 GB)**.

Dynamic Memory is also enabled so Hyper-V can adjust memory usage efficiently as workloads change.

### Procedure

1. Enter **4096 MB** as the Startup Memory.
2. Enable **Use Dynamic Memory for this virtual machine**.
3. Click **Next**.

### Screenshot

![Assign Startup Memory](images/07-assign-startup-memory.png)


## Step 8: Configure Networking

The virtual machine must be connected to a virtual switch before it can communicate with other systems.

For this lab, connect the VM to the **Private Virtual Switch** created earlier.

This creates an isolated lab environment without exposing the virtual machine to the host network or the Internet.

### Procedure

1. From the **Connection** drop-down list, select your Private Virtual Switch.
2. Click **Next**.

### Screenshot

![Configure Networking](images/08-configure-network-connection.png)


## Step 9: Create the Virtual Hard Disk

The virtual hard disk (VHDX) stores the operating system, applications, and data for the virtual machine.

A **50 GB dynamically expanding VHDX** provides sufficient storage for Windows Server while allowing disk usage to grow only as needed.

### Procedure

1. Select **Create a virtual hard disk**.
2. Specify the storage location.
3. Enter a descriptive disk name.
4. Set the disk size to **50 GB**.
5. Click **Next**.

### Screenshot

![Create Virtual Hard Disk](images/09-create-virtual-hard-disk.png)


## Step 10: Attach the Windows Server Installation Media

Instead of installing the operating system immediately, Hyper-V first needs to know where the installation media is located.

The Windows Server 2019 ISO downloaded earlier is attached as a virtual DVD drive.

### Procedure

1. Select **Install an operating system from a bootable image file**.
2. Click **Browse**.
3. Select the Windows Server 2019 ISO.
4. Click **Next**.

### Screenshot

![Attach Windows Server ISO](images/10-select-installation-media.png)


## Step 11: Review and Create the Virtual Machine

Before creating the virtual machine, review every configuration carefully.

This is the final opportunity to confirm that the storage location, memory allocation, networking, and installation media are correct.

If any setting is incorrect, use the **Previous** button to make adjustments before finishing the wizard.

### Procedure

1. Review the configuration summary.
2. Click **Finish**.

Hyper-V will create the virtual machine and return you to the main Hyper-V Manager window.

### Screenshot

![Review Configuration Summary](images/11-review-virtual-machine-summary.png)


## Step 12: Confirm the Virtual Machine Has Been Created

After the wizard closes, verify that the virtual machine appears in **Hyper-V Manager**.

At this stage, the virtual machine should appear in the **Off** state. This is expected because Windows Server has not yet been installed.

### Screenshot

![Virtual Machine Created](images/12-virtual-machine-created.png)

# Verify the Virtual Machine Configuration

Before powering on the virtual machine for the first time, verify that its configuration is correct. Performing these checks now helps prevent installation issues and reduces the need for reconfiguration later.


## Step 13: Verify Firmware Settings

Generation 2 virtual machines use UEFI firmware. Before installing Windows Server, ensure the virtual DVD drive is first in the boot order so the virtual machine boots from the Windows Server ISO.

### Procedure

1. Right-click the virtual machine and select **Settings**.
2. Select **Firmware**.
3. Confirm that **DVD Drive** appears at the top of the boot order.

### Screenshot

![Verify Firmware Settings](images/13-verify-firmware-settings.png)


## Step 14: Verify Security Settings

Generation 2 virtual machines support Secure Boot.

Windows Server 2019 requires Secure Boot to use the **Microsoft Windows** template.

### Procedure

1. Select **Security**.
2. Confirm **Enable Secure Boot** is checked.
3. Verify that the template is set to **Microsoft Windows**.

### Screenshot

![Verify Security Settings](images/14-verify-security-settings.png)


## Step 15: Verify Memory Configuration

Confirm that the startup memory matches the value configured during virtual machine creation.

### Procedure

1. Select **Memory**.
2. Verify that Startup RAM is set to **4096 MB**.
3. Confirm that **Dynamic Memory** is enabled.

### Screenshot

![Verify Memory Configuration](images/15-verify-memory-settings.png)


## Step 16: Verify Processor Configuration

Allocating too many virtual processors can reduce host performance.

A good practice is to assign no more than half of the host's available logical processors to a single virtual machine.

### Procedure

1. Select **Processor**.
2. Verify the configured number of virtual processors.

### Screenshot

![Verify Processor Configuration](images/16-verify-processor-settings.png)


## Step 17: Verify Network Adapter Configuration

Ensure that the virtual machine is connected to the correct virtual switch.

For this lab, the VM should be connected to the **Private Virtual Switch** created earlier.

### Procedure

1. Select **Network Adapter**.
2. Verify that the correct virtual switch is selected.

### Screenshot

![Verify Network Adapter](images/17-verify-network-adapter-settings.png)


## Verification Checklist

Before proceeding to the Windows Server installation, confirm that the following requirements have been met:

- ✅ Dedicated VM storage folder created
- ✅ Windows Server 2019 Evaluation ISO downloaded
- ✅ Private Virtual Switch configured
- ✅ Generation 2 virtual machine created
- ✅ Startup memory configured
- ✅ Virtual hard disk created
- ✅ Windows Server ISO attached
- ✅ Firmware settings verified
- ✅ Secure Boot enabled
- ✅ Processor configuration verified
- ✅ Network adapter connected to the Private Virtual Switch

If every item above has been completed successfully, the virtual machine is ready for Windows Server installation.


## Key Takeaways

In this lab, you learned how to:

- Prepare a Hyper-V environment for virtualization
- Organize virtual machine storage
- Download trusted installation media from Microsoft
- Configure an isolated networking environment using a Private Virtual Switch
- Create a Generation 2 virtual machine
- Configure memory, storage, networking, and installation media
- Verify virtual machine settings before the first boot

These foundational tasks help create a stable virtualization environment and reduce configuration issues during operating system installation.


## Next Steps

This concludes **Part 1** of the Hyper-V lab series.

In **Part 2**, you will:

- Start the virtual machine
- Install Windows Server 2019
- Complete the initial Windows Server setup
- Configure the Administrator account
- Verify network connectivity within the isolated lab
- Enable Remote Desktop for remote administration


## Repository

If you found this lab helpful, consider giving the repository a ⭐.

Contributions, suggestions, and feedback are always welcome.
