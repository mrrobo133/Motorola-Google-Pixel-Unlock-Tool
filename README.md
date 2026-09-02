# ==========================================
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
