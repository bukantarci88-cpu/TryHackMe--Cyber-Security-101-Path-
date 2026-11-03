# Sec 11.2. Firewall Fundamentals

#### **Firewall Fundamentals**

#### **Task 1 - What Is the Purpose of a Firewall**

A **firewall** is a security system that monitors and controls **incoming and outgoing network traffic** based on predefined rules.

- A firewall acts like a **security guard** for digital systems by preventing unauthorized access.
- It inspects network traffic before allowing it to enter or leave a device or network.
- Traffic is **allowed or blocked** depending on configured security rules.
- Modern firewalls provide additional security features beyond basic filtering, helping protect networks from external threats.

**Cybersecurity relevance:** Firewalls are a fundamental security control used to enforce access policies, reduce attack surfaces, and prevent unauthorized network connections.

**Answer the questions below**

> Which security solution inspects the incoming and outgoing traffic of a device or a network? Firewall
> 

#### **Task 2 - Types of Firewalls**

Firewalls are categorized based on how they inspect traffic and the OSI layers they operate on.

**1. Stateless Firewall**

- Operates at **Layer 3 and Layer 4**.
- Filters packets using predefined rules only.
- Does **not remember previous connections** or packet history.
- Provides fast processing but cannot apply advanced security decisions.

**2. Stateful Firewall**

- Operates at **Layer 3 and Layer 4**.
- Maintains a **state table** to track active connections.
- Makes decisions based on previous traffic history.
- Provides stronger security than stateless firewalls by recognizing trusted or blocked connections.

**3. Proxy Firewall**

- Operates at **Layer 7 (Application Layer)**.
- Acts as an intermediary between users and the internet.
- Inspects packet content and can apply content filtering rules.
- Can hide internal IP addresses by using its own IP address.

**4. Next-Generation Firewall (NGFW)**

- Operates across **Layers 3–7**.
- Provides advanced security features such as:
    - Deep Packet Inspection (DPI)
    - Intrusion Prevention System (IPS)
    - Threat intelligence integration
    - SSL/TLS inspection
    - Real-time threat detection

| **Firewalls** | **Characteristics** |
| --- | --- |
| Stateless firewalls | - Basic filtering- No track of previous connections- Efficient for high-speed networks |
| Stateful firewalls | - Recognize traffic by patterns- Complex rules can be applicable- Monitor the network connections |
| Proxy firewalls | - Inspect the data inside the packets as well- Provides content filtering options- Provides application control- Decrypts and inspects SSL/TLS data packets |
| Next-generation firewalls | - Provides advanced threat protection- Comes with an intrusion prevention system- Identify anomalies based on heuristic analysis- Decrypts and inspects SSL/TLS data packets |

**Answer the questions below**

> Which type of firewall maintains the state of connections? stateful firewall
> 

> Which type of firewall offers heuristic analysis for the traffic? next-generation firewall
> 

> Which type of firewall inspects the traffic coming to an application? proxy firewall
> 

#### **Task 3 - Rules in Firewalls**

The basic components of a firewall’s rule are described below:

- **Source address:** The machine’s IP address that would originate the traffic.
- **Destination address:** The machine’s IP address that would receive the data.
- **Port:** The port number for the traffic.
- **Protocol:** The protocol that would be used during the communication.
- **Action:** This defines the action that would be taken upon identifying any traffic of this particular nature.
- **Direction:** This field defines the rule’s applicability to incoming or outgoing traffic.

**Types of Actions:** The component “Action” from a rule indicates the steps to take after a data packet falls under the category of the defined rule. Three main actions that can be applied to a rule are explained below.

**Allow:** A rule’s “Allow” action indicates that the particular traffic defined inside the rule would be permitted. For example, let’s create a rule with an action to allow all the outgoing traffic from our network for port 80 (used for HTTP traffic to the Internet).

| **Action** | **Source** | **Destination** | **Protocol** | **Port** | **Direction** |
| --- | --- | --- | --- | --- | --- |
| Allow | 192.168.1.0/24 | Any | TCP | 80 | Outbound |

**Deny:** A rule’s “Deny” action means that the traffic defined inside the rule would be blocked and not permitted. These rules are fundamental for the security team to deny specific traffic coming from malicious IP addresses and create more rules to reduce the threat surface of the network.

For example, let’s create a rule with an action to deny all the incoming traffic on port 22 (used for remotely connecting to a machine via SSH) of our critical server.

| **Action** | **Source** | **Destination** | **Protocol** | **Port** | **Direction** |
| --- | --- | --- | --- | --- | --- |
| Deny | Any | 192.168.1.0/24 | TCP | 22 | Inbound |

**Forward:** The action “Forward” redirects traffic to a different network segment using the forwarding rules created on the firewalls. This applies to the firewalls that provide routing functionality and act as gateways between different network segments. For example, let’s create a rule with an action to forward all the incoming traffic on port 80 (used for HTTP traffic) to the web server `192.168.1.8`.

| **Action** | **Source** | **Destination** | **Protocol** | **Port** | **Direction** |
| --- | --- | --- | --- | --- | --- |
| Forward | Any | 192.168.1.8 | TCP | 80 | Inbound |

**Directionality of Rules**

Firewalls have different categories of rules, each categorized based on the traffic directionality on which the rules are created. Let’s examine each of these directionalities.

**Inbound Rules:** Rules are categorized as inbound rules when they are meant to be applied to incoming traffic only. For example, you might allow incoming HTTP traffic (port 80) on your web server.

**Outbound Rules:** These rules are made for outgoing traffic only. For example, blocking all outgoing SMTP traffic (port 25) from all the devices except the mail server.

**Forward Rules:** Forwarding rules are created to forward specific traffic inside the network. For example, a forwarding rule can be created to forward the incoming HTTP (port 80) traffic to the web server located in your network.

**Answer the questions below**

> Which type of action should be defined in a rule to permit any traffic? allow
> 

> What is the direction of the rule that is created for the traffic leaving our network? outbound
> 

#### **Task 4 - Windows Defender Firewall**

**Windows Defender Firewall** is a built-in firewall included with Microsoft Windows that helps protect systems by controlling **incoming and outgoing network traffic**. 

![Windows Defender Firewall dashboard.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726660679211.png)

**Network Profiles:** Windows Defender Firewall uses **Network Location Awareness (NLA)** to identify the current network type and automatically apply the appropriate firewall settings.

1. **Private Network**
- Used for trusted networks, such as home networks.
- Allows more flexible firewall rules because the network is considered safe.
1. **Public Network**
- Used for untrusted networks, such as coffee shops or restaurants.
- Provides stricter protection by blocking unnecessary incoming connections.

 **Firewall Management:**

- Users can allow or block specific applications for each network profile.
- Windows Defender Firewall is enabled by default.
- Instead of disabling the firewall completely, users can block all incoming connections for stronger protection.
- **Restore Defaults** can be used to return firewall settings to the original configuration.

![Windows Defender Firewall different options.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726665055716.png)

**Custom Rules:** Windows Defender Firewall allows users to create custom rules to allow or block specific network traffic. Example: Blocking outbound traffic on **HTTP (port 80)** and **HTTPS (port 443)** would prevent access to most websites. Custom rules help control network access and improve security by reducing unnecessary connections.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1726644402513.png)

To create a custom rule, choose "Advanced Settings" from the available options in the main dashboard. This will open a new tab where you can create your own rules.

![Windows Defender Firewall Advanced Settings tab.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726665941622.png)

You can see the available options to create inbound and outbound rules.

![Inbound and outbound rules in Windows Defender firewall.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726665941554.png)

Let’s create an outbound rule to block all our outgoing HTTP and HTTPS traffic. For this, click on the **Outbound Rules** option on the left side, then click on **New Rule** on the right side. It will open the rule wizard.In the first step, select the **Custom** option and press **Next**.

![Selecting the rule type.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726665941601.png)

In the second step, select **All programs** from the next option and press **Next**. It will ask you to select the protocol type in the third step. Select the **Protocol type** as "TCP", keep the **Local port** as it is, and change the **Remote port** to "Specific ports" from the dropdown. Write the port numbers in the field below (in our case, 80,443). Now, click on **Next**.

![Selecting the protocols and ports.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726665941608.png)

In the **Scope** tab, keep the local and remote IP addresses as they are and press the **Next** button. In the **Action** tab, enable the **Block the connection** option and press **Next**.

![Selecting the action.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726665941604.png)

In the **Profile** tab, we keep all the network profiles check-marked. Lastly, the final phase is to give your rule a name and an optional description and press the **Finish** button.

![Outbound rules list.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726665941608.png)

Now, let’s test our rule by browsing to `http://10.10.10.10/`. We get an error message saying we cannot reach this page, meaning the rule works.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1726644747236.png)

**Exercise:** The security team noticed suspicious incoming and outgoing traffic on their critical Windows system. They created rules on their Windows Defender Firewall to block some of their specific network traffic. You are tasked to answer a few questions given at the end of this task by looking at the created rules.

**Answer the questions below**

> What is the name of the rule that was created to block all incoming traffic on the SSH port? Core Op
> 


> A rule was created to allow SSH from one single IP address. What is the rule name? Infra team
> 


> Which IP address is allowed under this rule? 192.168.13.7
> 


#### **Task 5 - Linux iptables Firewall**

**Netfilter** is the built-in Linux framework that provides core firewall features such as:

- Packet filtering
- Network Address Translation (NAT)
- Connection tracking

Common firewall tools based on Netfilter include:

- **iptables:** A widely used firewall utility for managing Linux network traffic rules.
- **nftables:** The modern replacement for iptables with improved filtering and NAT capabilities.
- **firewalld:** Provides easier firewall management using predefined network zones and rules.

**ufw (Uncomplicated Firewall):**

- A beginner-friendly firewall interface for Linux.
- Simplifies firewall configuration by using simple commands instead of complex iptables syntax.
- Works as a frontend that creates iptables rules in the background.

Check status

```bash
user@ubuntu:~$ sudo ufw status
Status: inactive
```

Enable firewall

```bash
user@ubuntu:~$ sudo ufw enable
Firewall is active and enabled on system startup
```

Below is a rule created to allow all the outgoing connections from a Linux machine. The `default` in the command means that we are defining this policy as a default policy allowing all the outgoing traffic unless we define an outgoing traffic restriction on any specific application in a separate rule. You can also make a rule to allow/deny traffic coming into your machine by replacing `outgoing` with `incoming` in the following command:

Allow all outgoing traffic

```bash
user@ubuntu:~$ sudo ufw default allow outgoing
Default outgoing policy changed to 'allow'
(be sure to update your rules accordingly)
```

You can deny incoming traffic at any port in your system. Let's say that we want to block incoming SSH traffic. We can achieve this with the command `ufw deny 22/tcp`. As you can see, we first specified the action, `deny` in this case; furthermore, we specified the port and the transport protocol, which is TCP port 22, or simply `22/tcp`.

Deny incoming SSH traffic

```bash
user@ubuntu:~$ sudo ufw deny 22/tcp
Rule added
Rule added (v6)
```

To list down all the active rules in a numbered order, you can use the following command:

List all rules

```bash
user@ubuntu:~$ sudo ufw status numbered
     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                     DENY IN     Anywhere
[ 2] 22/tcp (v6)                DENY IN     Anywhere (v6)
```

To delete any rule, execute the following command with the rule number to delete:

Delete a rule

```bash
user@ubuntu:~$ sudo ufw delete 2
Deleting:
 deny 22/tcp
Proceed with operation (y|n)? y
Rule deleted (v6)
```

**Answer the questions below**

> Which Linux firewall utility is considered to be the successor of "iptables"? nftables
> 

> What rule would you issue with ufw to deny all outgoing traffic from your machine as a default policy? (answer without sudo) ufw default deny outgoing
>
