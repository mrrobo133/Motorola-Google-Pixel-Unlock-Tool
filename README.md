================================================================================
PROJECT OVERVIEW: MOTOROLA GOOGLE PIXEL UNLOCK TOOL
================================================================================

This project serves as a minimal, professional command-line reference guide 
designed specifically for Termux and Linux environments to handle bootloader 
unlocking workflows via USB OTG. Instead of heavy scripts or automated menus, 
it utilizes direct, low-level fastboot commands to interact with target devices.

--------------------------------------------------------------------------------
1. GOOGLE PIXEL WORKFLOW ARCHITECTURE & EXPLANATION
--------------------------------------------------------------------------------
Google Pixel devices implement a native, hardware-level direct unlocking protocol 
without requiring external server intervention. 

- Connection Verification: Establishes a stable data bridge between the host 
  Termux terminal and the target Pixel device running in fastboot mode.
- Hardware Profiling: Queries specific variables like product identity, 
  secure boot states, and current locking flags to ensure the hardware 
  environment is fully primed.
- Token Extraction: Generates and pulls the unique hardware-level unlock 
  data string directly from the device memory.
- Flashing Execution: Pushes the primary flash unlock command, prompting 
  the user to manually confirm the operation on the physical device screen.

--------------------------------------------------------------------------------
2. MOTOROLA WORKFLOW ARCHITECTURE & EXPLANATION
--------------------------------------------------------------------------------
Motorola devices enforce a strict, cryptographic server-dependent security model 
that cannot be bypassed solely via local software commands.

- Initialization: Scans and verifies the active fastboot link over the OTG cable 
  to confirm communication.
- OEM Data Retrieval: Dumps the specific device bootloader data token required 
  by the manufacturer's security infrastructure.
- Portal Verification (Manual Step): The extracted token string must be submitted 
  manually through Motorola's official web portal to validate warranty and 
  generate a unique cryptographic server key.
- Key Application: Transmits the official server-provided unlock key back to the 
  device to successfully lift the bootloader restriction.

--------------------------------------------------------------------------------
3. POST-UNLOCK OPERATIONS
--------------------------------------------------------------------------------
- State Validation: Queries the final lock flag status to verify that the 
  bootloader state has successfully transitioned to unlocked.
- System Reboot: Safely terminates the fastboot session and forces the target 
  device to restart back into its primary operating system interface.
================================================================================



# ANDROID FASTBOOT CLI & DEVICE CHEAT SHEET
# ==========================================

# ------------------------------------------
# PART 1: GOOGLE PIXEL (ADVANCED & HARD-CORE WORKFLOW)
# ------------------------------------------

# Supported Generations / Models:
# - Pixel 1 to 5 / 5a series
# - Pixel 6, 6 Pro, 6a
# - Pixel 7, 7 Pro, 7a
# - Pixel 8, 8 Pro, 8a
# - Pixel 9, 9 Pro, 9 Pro XL, 9 Pro Fold
# - Pixel 10, 10 Pro series

# Step-by-Step Advanced Commands:

```bash
fastboot devices
```
```bash
fastboot getvar product
```
```bash
fastboot getvar secure
```
```bash
fastboot getvar unlocked
```
```bash
fastboot oem get_unlock_data
```
```bash
fastboot flashing unlock
```

```bash
fastboot oem unlock
```


# ------------------------------------------
# PART 2: MOTOROLA (OFFICIAL SERVER TOKEN WORKFLOW)
# ------------------------------------------

# Supported Generations / Models:
# - Moto G series (G Power, Pure, Play, Stylus, 5G, G50, G54, G84, G55, G85)
# - Motorola Edge series (Edge 20 up to Edge 50 Ultra / Edge 60)
# - Motorola Razr / Razr+ / Razr 50 / Razr 60 (Foldables)
# - Motorola One series (Action, Vision, Hyper, Fusion)
# - Motorola Moto Z, X, E legacy series

# Step-by-Step Official Rules & Commands:
# 1. Enable OEM Unlocking & USB Debugging on the Motorola device.
# 2. Connect via OTG and check connection:

```bash
fastboot devices
```
# 3. Fetch official OEM unlock data string:

```bash
fastboot oem get_unlock_data
```
# 4. Copy the token string, paste it on Motorola's official website to receive your unlock code.
# 5. Apply the official code to complete the unlock:

```bash
fastboot oem unlock YOUR_OFFICIAL_CODE

```
```bash
fastboot oem unlock you code
```
