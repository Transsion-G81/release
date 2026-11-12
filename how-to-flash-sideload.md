# 📦 ROM installation guide

A step-by-step guide to flashing a custom ROM using ADB sideload.

**Infinix SMART 9** (`X6532`), **Infinix HOT 50i** (`X6531` / `X6531B`),
**TECNO Spark 30C** (`KL5` / `KL5n`).

---

## Prerequisites

- ADB & Fastboot on your PC (or the
  [Bugjaeger](https://play.google.com/store/apps/details?id=eu.sisik.hackendebug) app)
- USB cable
- The ROM zip and the matching `vendor_boot-<codename>-<rom>.img` from the release

---

## Downloaded files

After downloading you should have:

- The ROM `.zip` (for example `lineage-23.2-*-X6532.zip`)
- The recovery, `vendor_boot-<codename>-<rom>.img` (for example
  `vendor_boot-X6532-lineage.img`)

---

## Installation steps

### 1. Enter fastboot mode

Boot your device into fastboot mode (the USB screen), then run:

```bash
adb reboot bootloader
```

### 2. Flash vendor_boot (this is the recovery)

```bash
fastboot flash vendor_boot vendor_boot-<codename>-<rom>.img
```

### 3. Reboot to recovery

```bash
fastboot reboot recovery
```

### 4. Flash the ROM via ADB sideload

In recovery, select **"Apply Update"**, then **"Apply from ADB"**, and from your PC run:

```bash
adb sideload <rom>.zip
```

> Replace `<rom>.zip` with the actual filename of your ROM package.

### 5. Install GApps (optional)

Only needed on a **vanilla** build. Flash the GApps zip now, after the ROM and
**before** you format data:

```bash
adb sideload <gapps>.zip
```

> GApps and microG are mutually exclusive. Our gapps/microG builds already ship
> their Google services, so skip this step on those.

### 6. Wait for sideload to complete

> ⏳ **Note:** the process may appear to freeze at **47%** in your terminal. This
> is normal, do **not** disconnect your device. Be patient and wait for it to finish.

### 7. Format data

In recovery, wipe data / factory reset, then reboot back into **recovery**.

> ⚠️ **Warning:** this wipes all data on your device. Back up first.

### 8. Finish up

1. If recovery asks to flash another package, select **"No"**
2. Select **"Reboot to system"**

---

## ✅ Done

Your device should now boot into the new ROM. The first boot can take a few
minutes, this is normal.

---

## Troubleshooting

| Issue | Solution |
|---|---|
| Stuck at 47% | Wait, do not disconnect. This is expected behavior. |
| Device not detected | Make sure USB debugging is on and the drivers are installed. |
| Sideload fails | Re-download the ROM zip and check it is not corrupted. |
| Wrong recovery | Make sure you flashed the `vendor_boot` that matches your codename and ROM. |

---

## 📝 Note

- **Firmware requirement:** you must already be on **HiOS 14 (Android 14)**
  firmware before flashing.
- **Flashing from a custom recovery instead?** See
  [`how-to-flash-recovery.md`](how-to-flash-recovery.md).
