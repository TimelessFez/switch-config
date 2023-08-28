# CLI command translations for Cisco, Huawei, and Aruba switches

## General configuration
| Cisco                | Huawei                         | Aruba               | FS |
|----------------------|--------------------------------|---------------------|----|
| ping                 | ping                           | ping                |    |
| traceroute           | tracert                        |                     |    |
| no <command>         | undo <command>                 | no <command>        |    |
| show                 | display                        |                     |    |
| show interface       | display interface              |                     |    |
| write terminal (show running-config)  | display current-configuration  | show running-config |    |
| show startup-config  | display startup                | show startup-config |    |
| enable               | super (default: 3)             | enable              |    |
| conf t               | system-view                    | config              |    |
| exit                 | quit                           | exit                |    |
| end                  | return                         |                     |    |
| disable              | super 0 (privilege level: 0-3) | disable             |    |
| clock                | clock                          | set clock           |    |
| copy running-config  | save safely                    | copy running-config |    |
| write mem            | save                           | write m             |    |
| reload               | reboot                         |   |    |
| boot                 | bootrom                        | boot      |    |
| shutdown             | shutdown                       | shutdown  |    |

## User Management / Create User

### Cisco

https:/github.com/TimelessFez/switch-config/Cisco.md

### Huawei

https:/github.com/TimelessFez/switch-config/Huawei.md

- **User view**

	- *The user enters user view upon logging in*
 
		```<HUAWEI>```
		
- **System view**

  - *Equivalent to ``enable`` on Cisco switches*
   
		```
		<HUAWEI> system-view
		[HUAWEI]
		```
		
- **Interface view**

	- *config interface parameters (physical attributes, link layer protocols, IP addresses)*

    ```
    [HUAWEI] interface gigabitethernet 0/0/1
		[HUAWEI-GigabitEthernet0/0/1]
		```

---

## CLI Navigation

- **Return from current view**

	- *Go back once from the current menu*

    ```
		[HUAWEI-GigabitEthernet0/0/1] quit
		[HUAWEI] quit
		<HUAWEI> quit
		```
		
	- **Go back to the user view directly**
 
		- *Using ``return``*

			```
			[HUAWEI-GigabitEthernet0/0/1] return
			<HUAWEI>
			```

---
 
- **Undo command**

	- *Equivalent to ``no`` on Cisco switches*
 
		```
		[HUAWEI] undo <command>
		```

---

## Hostname
- **Change hostname / sysname**

	- *Equivalent to ``hostname`` on Cisco switches*

		```
		[HUAWEI] sysname <new-hostname-01>
		[new-hostname-01]
		```
---

## Local user management

- **Create user with plaintext password**

  - *"This command should be entered in interactive mode. Directly entering a plaintext password without being in interactive mode poses potential security risks."*

    ```local-user <username> password <password>```

- **Create user with ciphertext password**

  - ```local-user <username> password ( cipher | irreversible-cipher ) <password>```

- **Configure access type for local user (user access permission)**

  - *By default, all access types are disabled for a local user.*

    ```local-user <username> service-type ( 8021x | api | ftp | http | ppp | ssh | telnet | terminal | web | x25-pad ) *```

- **Configure user privilege level**

  - *Privilege level ranges from 0 (lowest) to 15 (highest). Default: 0*
 
    ```local-user <username> privilege level <level>```

- **Delete user**

  - *Removes the local user*
 
    ```undo local-user <user>```

---

## 

- **Display current configuration**

	- *Equivalent to ``show running-configuration`` on Cisco switches*
 
		```
		[HUAWEI] display current-configuration
		```

- **Display interface parameters**

	- *Show all interface parameters*
 
		```
		display interface
		```

	- **Show specific interface**
 
		- *Equivalent to ``switch show interface switchport <interface type> <interface number>`` on Cisco switches*
  
			```
			[HUAWEI] display interface <interface type> <interface number>
			```
			
			- *usage example:*
  
				```display interface gigabitethernet 0/0/1```

---

## Configure IP Route
- **Static IP route**
	- *configure a unicast static IP route*

		```
		[HUAWEI] ip route-static <destination> <mask> <next-hop address>
		```

---


### Aruba



### FS


---

## Voice VLAN

### Huawei
```
<HUAWEI> system-view
[HUAWEI] interface gigabitethernet 0/0/1
[HUAWEI-GigabitEthernet0/0/1] voice-vlan enable
```

### Aruba
```
Switch> config
Switch# vlan 10
Switch(vlan-10)# voice
```

---

---

* This page will be updated over time.
