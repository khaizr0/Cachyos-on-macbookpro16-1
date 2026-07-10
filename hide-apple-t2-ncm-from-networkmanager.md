# Hide Apple T2 NCM Interface from NetworkManager

Hide the `t2_ncm` Ethernet interface created by the Apple T2 chip to prevent NetworkManager connect/disconnect notifications.

## 1. Create NetworkManager config

```bash
sudo nano /etc/NetworkManager/conf.d/99-network-t2-ncm.conf
```

Add:

```ini
[keyfile]
unmanaged-devices=interface-name:t2_ncm
```

---

## 2. Create udev rule

```bash
sudo nano /etc/udev/rules.d/99-t2-ncm-unmanaged.rules
```

Add:

```udev
SUBSYSTEM=="net", KERNEL=="t2_ncm", ENV{NM_UNMANAGED}="1"
```

---

## 3. Apply changes

```bash
sudo udevadm control --reload
sudo udevadm trigger -c add /sys/class/net/t2_ncm
sudo systemctl restart NetworkManager
```
