### 1. **Windows Server Architecture**

-   **Definition**: Windows Server is a group of server operating systems developed by Microsoft.
-   **Key Components**: Active Directory, IIS (Internet Information Services), DHCP, DNS, File and Print services.
-   **Common Versions**: Windows Server 2016, 2019, and 2022.

### 2. **Active Directory (AD)**

-   **Purpose**: A directory service for Windows domain networks that manages and authenticates users and devices.
-   **Key Features**: User management, group policies, domain services, and organizational units (OUs).
-   **Use Case**: Centralized user account control and policy enforcement.

### 3. **Domain Name System (DNS)**

-   **Role**: Translates domain names (like www.example.com) into IP addresses.
-   **Key Functions**: Name resolution, zone management (forward and reverse lookup zones).
-   **Configuration**: Setting up DNS zones and records (A, CNAME, MX, etc.).

### 4. **Dynamic Host Configuration Protocol (DHCP)**

-   **Function**: Automatically assigns IP addresses and network configurations to devices.
-   **Benefits**: Reduces manual IP assignment errors and streamlines network administration.
-   **Concepts**: DHCP scope, lease time, reservation, and options.

### 5. **File and Print Services**

-   **Purpose**: Enable users to access shared files and printers over a network.
-   **Key Elements**: Configuring file shares, NTFS permissions, and print server roles.
-   **Security**: Managing access control and sharing permissions.

### 6. **Group Policy Management**

-   **Definition**: A feature in Windows that allows centralized management of user and computer settings in an Active Directory environment.
-   **Applications**: Enforcing security settings, software deployment, and user environment customization.
-   **Tools**: Group Policy Management Console (GPMC).

### 7. **Windows Server Backup**

-   **Importance**: Provides tools for backing up and recovering data on Windows servers.
-   **Features**: Full, incremental, and system state backups.
-   **Best Practices**: Regular backups, offsite storage, and testing recovery plans.

### 8. **Windows Updates and Patch Management**

-   **Purpose**: Keeping systems secure and up to date with the latest patches.
-   **Methods**: Using Windows Server Update Services (WSUS) or direct updates from Microsoft.
-   **Automation**: Scheduling and managing updates through Group Policy or scripts.

### 9. **Virtualization with Hyper-V**

-   **Definition**: A hypervisor for running multiple virtual machines (VMs) on a single physical host.
-   **Key Features**: Virtual network creation, resource allocation, and VM management.
-   **Use Cases**: Server consolidation, testing environments, and efficient resource utilization.

### 10. **Monitoring and Performance Management**

-   **Tools**: Performance Monitor (PerfMon), Event Viewer, and Resource Monitor.
-   **Metrics**: CPU usage, memory consumption, disk I/O, and network activity.
-   **Purpose**: Identifying bottlenecks and optimizing server performance.

### 11. **User and Group Management**

-   **Tasks**: Creating, managing, and assigning roles to users and groups.
-   **Permissions**: Configuring access rights to resources using security and distribution groups.
-   **Best Practice**: Least privilege principle and role-based access control (RBAC).

### 12. **Remote Desktop Services (RDS)**

-   **Definition**: A remote access solution for Windows servers.
-   **Key Features**: Desktop sharing, session management, and remote control.
-   **Use Cases**: Remote access to remote workstations and virtual machines.

### 13. **Windows Firewall**

-   **Definition**: A security feature that controls inbound and outbound network traffic.
-   **Key Features**: Firewall rules, port filtering, and application control.
-   **Use Cases**: Preventing unauthorized access, limiting network traffic, and enforcing security policies.

### File System: Overview

A **file system** is a method and structure that an operating system uses to manage and store files on storage devices like hard drives, SSDs, or external storage. It organizes data into files and directories, enabling efficient data access and management.

### Common Types of File Systems:

1. **NTFS (New Technology File System)**

    - **Key Points**:
        - Supports large file sizes and volumes (up to 16 EB).
        - Offers security features like file encryption and permissions.
        - Supports file compression and disk quotas for storage management.

2. **FAT32 (File Allocation Table 32)**

    - **Key Points**:
        - Compatible with various operating systems, ensuring wide compatibility.
        - Limited to 4 GB maximum file size and 8 TB volume size.
        - Lacks advanced security features compared to NTFS.

3. **exFAT (Extended File Allocation Table)**

    - **Key Points**:
        - Designed for flash drives with support for larger file sizes than FAT32.
        - Bridges compatibility between NTFS and FAT32 for cross-platform use.
        - Less overhead and better performance for removable storage.

4. **ReFS (Resilient File System)**
    - **Key Points**:
        - Focuses on data integrity with built-in error detection and correction.
        - Supports large volumes and files, similar to NTFS, but with enhanced reliability.
        - Used primarily in storage solutions requiring high availability and resilience.

---

## Steps for Setting Up a Windows Server 2019 Domain Controller

### Part 1: Setting Up the AD DC and DNS on Windows Server 2019

To set up Windows Server 2019 as an Active Directory Domain Controller (AD DC) and DNS server, follow these steps:

#### Step 1: Install Active Directory Domain Services (AD DS)

1. **Open Server Manager** on the Windows Server 2019 VM.
2. Click on **Manage** > **Add Roles and Features**.
3. Select **Role-based or feature-based installation** and click **Next**.
4. Choose the server from the server pool and click **Next**.
5. Select **Active Directory Domain Services** and add features when prompted.
6. Click **Next** and proceed through the wizard. Click **Install**.
7. Wait for the installation to complete (it will not require a reboot at this stage).

#### Step 2: Promote the Server to a Domain Controller

1. After installation, click the **Notification** flag in Server Manager and choose **Promote this server to a domain controller**.
2. Choose **Add a new forest** and enter your **root domain name** (e.g., `yourdomain.local`).
3. Click **Next** and set a **Directory Services Restore Mode (DSRM) password**.
4. Proceed through the remaining steps, keeping default settings unless specific customizations are needed.
5. Verify that the **DNS** server option is selected (it should be by default) and click **Next**.
6. Review and click **Install**. The server will automatically reboot to apply the changes.

#### Step 3: Verify AD DS and DNS Configuration

1. **Log in** after the reboot and open **Server Manager** to check that AD DS and DNS are functioning.
2. Open **Active Directory Users and Computers** to confirm that the domain is active.
3. Use **DNS Manager** (type `dnsmgmt.msc` in the Run dialog) to ensure the DNS server is running and configured to resolve queries for the domain.

### Part 2: Connecting Windows 10 VM to the Domain Using DNS

#### Step 1: Configure Network Settings on Windows Server 2019

-   Set a **static IP address** for the server:
    1. Go to **Control Panel > Network and Sharing Center > Change adapter settings**.
    2. Right-click the network adapter, select **Properties**, and click **Internet Protocol Version 4 (TCP/IPv4)**.
    3. Set a static IP (e.g., `192.168.1.10`) and use the server's own IP as the **Preferred DNS server**.

#### Step 2: Configure DNS on Windows 10

1. On the Windows 10 VM, open **Control Panel > Network and Sharing Center > Change adapter settings**.
2. Right-click your network adapter and select **Properties**.
3. Go to **Internet Protocol Version 4 (TCP/IPv4)** and set the **Preferred DNS server** to the IP address of the Windows Server 2019 (e.g., `192.168.1.10`).

#### Step 3: Verify DNS Connectivity

-   Open **Command Prompt** on Windows 10 and type:
    ```bash
    nslookup yourdomain.local
    ```
-   Ensure that it returns the correct IP address of the Windows Server 2019.

#### Step 4: Join Windows 10 to the Domain

1. Go to **Settings > System > About** or **Control Panel > System and Security > System** on Windows 10.
2. Click **Join a domain** and enter the **domain name** (e.g., `yourdomain.local`).
3. Provide **domain credentials** when prompted (e.g., `Administrator`).
4. Restart the Windows 10 VM after joining the domain.

#### Step 5: Verify the Connection

-   Log in to the Windows 10 VM with a **domain account** (e.g., `yourdomain\username`).
-   Confirm domain connectivity by testing `ping` to the domain:
    ```bash
    ping yourdomain.local
    ```

### **Troubleshooting Tips**:

-   Ensure that **Windows Defender Firewall** on both VMs is configured to allow domain, DNS, and ICMP (ping) traffic.
-   Clear DNS cache if connectivity issues occur:
    ```bash
    ipconfig /flushdns
    ```
-   Check the status of **AD DS** and **DNS** services by running `services.msc` and confirming that they are running.
