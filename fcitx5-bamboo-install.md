# Install Fcitx5 Bamboo (Vietnamese Input Method) on CachyOS / Arch Linux

This guide explains how to install and configure the **Fcitx5 Bamboo** Vietnamese input method on CachyOS (or any Arch-based distribution).

## 1. Install Required Packages

Since **Fcitx5 Bamboo** is available from the Arch User Repository (AUR), you'll need an AUR helper such as **yay**.

### Install `yay` (CachyOS)

On CachyOS, `yay` is available in the official repositories:

```bash
sudo pacman -S yay
```

### Install Fcitx5

Install the Fcitx5 framework and configuration tool:

```bash
sudo pacman -S fcitx5-im fcitx5-configtool
```

### Install Fcitx5 Bamboo

Use `yay` to install Bamboo from the AUR:

```bash
yay -S fcitx5-bamboo
```

> If you use another AUR helper such as `paru`, simply replace `yay` with `paru`.

---

## 2. Configure Environment Variables

To allow applications to detect and use Fcitx5 correctly, configure the required environment variables.

For Wayland (recommended), edit or create:

```bash
sudo nano /etc/environment
```

Add the following lines to the end of the file:

```text
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
```

Save the file and exit.

---

## 3. Enable the Vietnamese Input Method

Restart your computer (or log out and log back in) so the environment variables take effect.

After logging back in:

1. Open **Fcitx5 Configuration** (`fcitx5-configtool`).
2. Click **Add Input Method**.
3. Search for **Bamboo**.
4. Add **Bamboo** to the input method list.

---

## 4. Usage

- Press **Ctrl + Space** (or your custom shortcut configured in `fcitx5-configtool`) to switch between English and Vietnamese.
- Bamboo uses **Telex** as the default input method.
