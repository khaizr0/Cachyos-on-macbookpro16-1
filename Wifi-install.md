# Restoring Wi-Fi Drivers for Apple T2 MacBooks on CachyOS (Manual Download Method)

This guide explains how to restore Wi-Fi support on Apple T2 MacBooks running CachyOS (Arch Linux) by manually building `dmg2img` from a GitHub mirror.

---

## Prerequisites

Before you begin, make sure you have:

- An **Apple T2 MacBook** with **CachyOS (Arch Linux)** already installed.
- A temporary Internet connection, such as:
  - USB tethering from a smartphone, or
  - A wired Ethernet connection.

---

## Installation Steps

### Step 1: Build `dmg2img` Manually from GitHub

```bash
# Clone the source code
git clone https://github.com/Lekensteyn/dmg2img.git

# Enter the project directory
cd dmg2img

# Build the binaries


# Install the executables
sudo cp dmg2img /usr/local/bin/
sudo cp vfdecrypt /usr/local/bin/

# Return to the previous directory
cd ..
```

---

### Step 2: Download and Run the t2linux Firmware Extraction Script

Now that `dmg2img` is installed, download the official firmware extraction script.

```bash
# Download the firmware extraction script
curl -O https://wiki.t2linux.org/tools/firmware.sh

# Make the script executable
chmod +x firmware.sh

# Run the script as root
sudo ./firmware.sh
```

---

### Step 3: Extract the Firmware

When the interactive menu appears, select:

```text
3. Download a macOS Recovery Image from Apple and extract the firmware from there
```

Then press **Enter**.

### Step 4: Select a macOS Recovery Version

After choosing option **3**, the script will display a list of available macOS Recovery images:

```text
Checking for missing dependencies

Downloading macOS Recovery Image

Note: In order to get complete firmware files, download macOS Monterey, Ventura or Sonoma.

1. High Sierra (10.13)
2. Mojave (10.14)
3. Catalina (10.15)
4. Big Sur (11.7)
5. Monterey (12.6)
6. Ventura (13)
7. Sonoma (14) - RECOMMENDED
8. Sequoia (15)
9. Tahoe (26)

Choose a product to download (1-9):
```

Although the script currently marks **Sonoma (14)** as the recommended option, you can also select the latest available macOS Recovery image.

For example, to download **macOS Tahoe (26)**, enter:

```text
9
```

Then press **Enter**.

The script will download the selected macOS Recovery image from Apple's servers, extract the required Broadcom Wi-Fi firmware, and install it automatically.

The download time depends on your Internet connection speed.

## Credits

- **t2linux Project** for the firmware extraction script.
- **Lekensteyn** for maintaining the `dmg2img` GitHub mirror.
