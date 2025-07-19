# 🛡️ Virtual Ethical Hacking Home Lab
Spin up, break, and defend a mini‑enterprise—safely contained on one Windows PC.

---

## 📛 Rename ideas
- `virtual-ethical-hacking-lab`
- `pentest-home-lab-playground`
- `daph-attack-defense-sandbox`
- `vmware-nat-pentest-lab`

Pick the kebab‑case label that best matches your portfolio’s naming style.

---

## 🙋‍♀️ About Me
*I build isolated battle‑fields where exploits meet defenses—because the safest way to learn is to break things on purpose.*

---

## 🗺️ Lab Topology
| VM | OS / Role | Purpose |
|----|-----------|---------|
| ⚔️ **Kali Linux** | Attack box | Nmap, Metasploit, Wireshark, Burp Suite, etc. |
| 🏢 **Windows Server 2016** | Domain Controller | Active Directory target for privilege‑escalation drills |
| 🐑 **Windows Server 2008 (Metasploitable)** | Vulnerable host | Legacy exploits (MS08‑067, EternalBlue, etc.) |

*Network:* VMware Workstation Pro **NAT**—gives every VM internet when needed, yet isolates them from the host LAN.

---

## 🔑 Why this lab matters
- **Safe dojo** — practice real attacks without endangering production gear.  
- **Hands‑on > theory** — enumerate, exploit, and defend in one sitting.  
- **Career fuel** — perfect prep for OSCP/CEH labs and blue‑team interviews.

---

## 🚀 Build steps (quick version)

1. **Prep host**  
   `Windows 11 + VMware Workstation Pro` → enable NAT network  
2. **Deploy VMs**  
   - Import Kali ISO, update & install toolset  
   - Spin up Win 2016, promote to DC  
   - Import Metasploitable‑Win 2008, keep default vulns  
3. **Resource tuning**  
   Allocate RAM/CPU evenly (avoid host thrash)  
4. **Connectivity check**  
   `ping` across VMs → confirm NAT routing  
5. **Tool bootstrap (Kali)**  
   ```bash
   sudo apt update && sudo apt install -y metasploit-framework nmap
   sudo msfdb init
   ```
6. **First exploit demo**  
   ```bash
   msfconsole
   use exploit/windows/smb/ms17_010_eternalblue
   set RHOSTS <Metasploitable_IP>
   run
   ```
7. **Packet capture & AD recon**  
   - Wireshark → sniff NTLM auth  
   - `enum4linux` + `rpcclient` → map shares & users

---

## 🧰 Toolbox highlights
- **Metasploit Framework** – exploit automation  
- **Nmap** – port & version scans  
- **Wireshark** – packet‑level truth  
- **Burp Suite** – web app fuzzing  
- **John the Ripper / Hydra** – password attacks  
- **VMware Snapshots** – instant rollback after carnage

---

## 🙅‍♂️ Challenges & fixes
| Hiccup | Solution |
|--------|----------|
| VM lags & crashes | Re‑balanced RAM/CPU, disabled 3D acceleration |
| VMs couldn’t talk | Corrected NAT adapter + DNS in each guest |
| Win Server license nag | Used 180‑day evaluation ISOs—plenty for lab work |

---

## 📈 Next upgrades
- Add **OSSIM** or **Security Onion** for SIEM visibility  
- Script VM builds with **Vagrant** + **Packer**  
- Introduce VLANs for segmented blue‑team training  

---

> **Lesson learned:** *Real mastery starts when you control every packet in your own sandbox.*
