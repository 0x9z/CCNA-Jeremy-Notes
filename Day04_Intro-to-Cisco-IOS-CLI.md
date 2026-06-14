# 📌 Day 04: Introduction to the Cisco CLI

## 📖 What is a CLI?

A **Command-Line Interface (CLI)** is the primary method to configure and manage Cisco devices. It is text-based, powerful, and efficient.

## 🔌 Connecting to a Cisco Device

For initial configuration, use the **Console Port**

### 🛠️ Requirements

1.  **Rollover Cable**: Connects your PC to the device's console port (often via a USB-to-Serial adapter).
2.  **Terminal Emulator**: Software like PuTTY, Tera Term, or the Packet Tracer terminal.

### ⚙️ Default Cisco Console Settings

| Setting | Value |
| :--- | :--- |
| **Speed (Baud)** | 9600 bits/second |
| **Data bits** | 8 |
| **Stop bits** | 1 |
| **Parity** | None |
| **Flow Control** | None |

---

## 🏠 User EXEC Mode (`Router>`)

- **Prompt:** Ends with a `>` (e.g., `Router>`).
- **Capabilities:** Very limited. You can view basic information but **cannot make any changes**.
- **Alias:** Often called "User Mode."

---

## 🦸 Privileged EXEC Mode (`Router#`)

- **How to Enter:** From User EXEC mode, type `enable`.
- **Prompt:** Ends with a `#` (e.g., `Router#`).
- **Capabilities:** Grants full access to **view** configurations, restart the device, and manage files. You still **cannot change** the configuration itself.

---

## 🛠️ Global Configuration Mode (`Router(config)#`)

- **What it is:** The mode where you actually make configuration changes.
- **How to Enter:** From Privileged EXEC mode, type `configure terminal` (or `conf t`).
- **Prompt:** Changes to `Router(config)#`.
- **How to Exit:** Type `exit` to return to Privileged EXEC mode.

---

## 🔧 CLI Superpowers

| Tool | How to Use It | Why It's Powerful |
| :--- | :--- | :--- |
| **`?`** | Type `?` to list all commands. Type a partial command + `?` (e.g., `sh?`). | **Discovers** commands and options on the fly. |
| **`Tab` Key** | Type a partial command (e.g., `conf`) and press `Tab`. | **Auto-completes** commands, saving time and preventing typos. |

---

## 🔐 Securing Access (Passwords)

### ⚠️ Two Ways to Set Privileged EXEC Passwords

| Feature | `enable password` | `enable secret` (Recommended) |
| :--- | :--- | :--- |
| **What it does** | Sets a password for Privileged EXEC mode. | Sets a password for Privileged EXEC mode. |
| **Encryption** | Plain text by default. | **Always encrypted** with strong MD5 (Type 5). |
| **Command** | `Router(config)# enable password MyPass` | `Router(config)# enable secret MySecretPass` |
| **Conflict** | If both are set, **`enable secret` always wins**. | This is the password that will be used. |

> **`service password-encryption`**
> - Encrypts *all* plain-text passwords (like `enable password`) in the config file using weak Cisco Type 7 encryption.
> - It does **not** affect `enable secret`.
> - **Recommendation:** Rely on `enable secret` for strong security.

### 🗑️ How to Delete a Command
Use the **`no`** keyword.
- `Router(config)# no enable password`
- `Router(config)# no service password-encryption`

---

## 💾 The Two Configuration Files

| File | What it is | Command to View |
| :--- | :--- | :--- |
| **Running-Config** | The **active, current configuration** in RAM. All changes are made here immediately. | `show running-config` (or `show run`) |
| **Startup-Config** | The **saved configuration** in NVRAM. This is loaded when the device restarts. | `show startup-config` (or `show start`) |

### 💿 How to Save Your Work (CRITICAL!)

**If you don't save, all changes are lost on reboot.**

All three commands do the same thing. Use any one:

- `Router# write`
- `Router# write memory`
- `Router# copy running-config startup-config`

---

## 🔬 Encryption in `show running-config`

| What You Type | What You See in the Config | Security Level |
| :--- | :--- | :--- |
| `enable password MyPass` | `enable password MyPass` | **Weak** (Plain text) |
| `enable password MyPass` + `service password-encryption` | `enable password 7 060506324B41` | **Weak** (Type 7, easily cracked) |
| `enable secret MySecretPass` | `enable secret 5 $1$mERr$98A5ZvDpLXCPR8hsWHKiv/` | **Strong** (Type 5, MD5 hash) |

---

## ✅ Day 04 Mastery Checklist

- [ ] I know the three main CLI modes (`>`, `#`, `(config)#`) and how to move between them.
- [ ] I can use `?` and `Tab` to navigate the CLI efficiently.
- [ ] I understand the security difference between `enable password` and `enable secret`.
- [ ] I can save my configuration with `copy running-config startup-config`.
- [ ] I understand the difference between `running-config` and `startup-config`.

---
