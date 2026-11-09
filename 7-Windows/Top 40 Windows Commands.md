
Resource
https://youtu.be/Jfvg3CS1X3A?si=0tsr7IJdR68cF3ir


## 1. Network Configuration & Troubleshooting (`ipconfig` & `nslookup`)

* **`ipconfig`**  
  Shows your computer's basic IP address information.
* **`ipconfig /all`**  
  Displays all detailed IP information, including your MAC address and DNS servers.
* **`ipconfig /release`**  
  Releases your current IP address.
* **`ipconfig /renew`**  
  Requests a fresh new IP address from the DHCP server.
* **`ipconfig /displaydns`**  
  Shows all websites and IP addresses currently cached in your computer's DNS resolver.
* **`ipconfig /flushdns`**  
  Deletes your DNS resolver cache to clear out old or stale DNS entries.
* **`nslookup [domain]`**  
  Finds the IP address for a specific website (e.g., `nslookup networkchuck.com`).
* **`nslookup [domain] [DNS-server]`**  
  Queries a specific external DNS server for a second opinion (e.g., `nslookup networkchuck.com 8.8.8.8`).

---

## 2. Networking Tools & Connections (`ping`, `tracert`, `netstat`, `route`)

* **`ping [destination]`**  
  Checks if a server or website is up by sending 4 test packets.
* **`ping -t [destination]`**  
  Runs a **continuous ping** that never stops until you press `Ctrl + C` (great for troubleshooting connection drops).
* **`tracert [destination]`**  
  Traces every router hop your connection takes to reach a website.
* **`tracert -d [destination]`**  
  Traces the path *without* resolving domain names, making the test faster.
* **`netstat -af`**  
  Shows all active network connections and open ports on your system.
* **`netstat -o`**  
  Shows active network connections along with the **Process ID (PID)** of the program using them.
* **`netstat -e -t 5`**  
  Displays network interface send/receive statistics, refreshing every 5 seconds.
* **`route print`**  
  Displays your computer's routing table (shows default gateways and network paths).
* **`route add [network] mask [subnet] [gateway]`**  
  Adds a custom static route to reach a specific network.
* **`route delete [network]`**  
  Deletes a static route from your routing table.

---

## 3. System Maintenance & File Repair (`chkdsk`, `sfc`, `dism`)

* **`chkdsk /f`**  
  Checks your hard disk for errors and automatically fixes them.
* **`chkdsk /r`**  
  Checks for physical bad sectors on your hard drive and repairs them (may require a reboot).
* **`sfc /scannow`**  
  (System File Checker) Scans and repairs corrupted core Windows system files (like `.dll` files).
* **`dism /online /cleanup-image /checkhealth`**  
  Quickly checks if your Windows system image has any flagrant corruption.
* **`dism /online /cleanup-image /scanhealth`**  
  Performs a deeper scan to check the health of your Windows system image.
* **`dism /online /cleanup-image /restorehealth`**  
  Repairs and restores a corrupted Windows system image.

---

## 4. Advanced Networking & Hardware (`netsh`, `getmac`, `powercfg`)

* **`getmac /v`**  
  Displays all physical MAC addresses on your computer with verbose details.
* **`powercfg /energy`**  
  Analyzes the operating system for common energy-efficiency and power problems.
* **`powercfg /batteryreport`**  
  Generates an HTML report detailing your laptop battery's health, capacity, and history.
* **`netsh wlan show wlan report`**  
  Generates a comprehensive Wi-Fi session report file.
* **`netsh interface show interface`**  
  Displays the status of all network interfaces on your PC.
* **`netsh advfirewall set allprofiles state off`**  
  Turns off the Windows Defender Firewall.
* **`netsh advfirewall set allprofiles state on`**  
  Turns the Windows Defender Firewall back on.

---

## 5. Processes, File Associations & Utility Commands

* **`assoc`**  
  Displays which programs are associated with specific file extensions (e.g., `.mp4`).
* **`assoc .mp4=VLC`**  
  Changes a file extension association to a preferred program.
* **`tasklist`**  
  Lists all currently running processes and their Process IDs (PIDs).
* **`taskkill /f /pid [PID]`**  
  Forcefully terminates a misbehaving program or background task using its Process ID.
* **`cls`**  
  Clears the command prompt screen.
* **`shutdown /r /fw /t 0`**  
  Instantly restarts your computer directly into the **system BIOS/UEFI** without needing to spam function keys.

---

## 6. Handy Command-Line Tricks Mentioned

* **Piping (`|`)**: You can send the output of *any* command into another tool. For example, `ipconfig /all | findstr "DNS"` searches output for specific keywords.
* **Copy to Clipboard (`clip`)**: Append `| clip` to the end of any command to instantly copy its output text directly to your clipboard (e.g., `ipconfig /displaydns | clip`).