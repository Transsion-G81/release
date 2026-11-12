# 🔧 How to flash from a custom recovery

**Infinix SMART 9** (`X6532`), **Infinix HOT 50i** (`X6531` / `X6531B`),
**TECNO Spark 30C** (`KL5` / `KL5n`).

## Steps

1. **Prepare your files**
   Put the ROM zip on your SD card, internal storage, or an OTG drive.

2. **Reboot to recovery**

3. **Flash the ROM zip**
   Select the zip and flash it.

4. **Install GApps (optional)**
   Only needed on a **vanilla** build. Flash the GApps zip now, after the ROM
   and **before** you format data.

5. **Format data / factory reset**

6. **Reboot to recovery**
   After a ROM flash the custom recovery is replaced by the ROM's own OSS/AOSP
   recovery, so reboot back into recovery before continuing.

7. **Reboot system**

---

## 📝 Notes

- **OrangeFox users:** do **not** tick *"Reflash OrangeFox"* after flashing the ROM.
- **GApps and microG are mutually exclusive.** Our gapps/microG builds already
  ship their Google services, so skip step 4 if you flashed one of those. Only
  vanilla builds take a separate GApps zip, and the order matters: GApps after
  the ROM, before format data.
- **Flashing may take a while**, and errors during this step are generally fine.
- **Flashing from a PC or Bugjaeger?** Use
  [`adb sideload`](how-to-flash-sideload.md) instead.
- **Firmware requirement:** you must already be on **HiOS 14 (Android 14)**
  firmware before flashing.
- **Recommended:** OSS/AOSP recovery (the `vendor_boot-<codename>-<rom>.img`
  from the release).

---

# 🔧 How to flash from OSS / AOSP recovery

Our releases ship that recovery inside `vendor_boot-<codename>-<rom>.img`
(for example `vendor_boot-X6532-lineage.img`).

## Steps

1. **Prepare your files**
   Put the ROM zip on your SD card or an OTG drive.

2. **Boot to recovery, then choose "Apply Update"**

3. **Select your source**
   Choose *"from SD card"* or *"from OTG"*.

4. **Flash the ROM zip**

5. **Format data**

6. **Reboot to recovery**

7. **Reboot system**

---

## 📝 Notes

- **Installing GApps?** They need a PC, so use
  [`adb sideload`](how-to-flash-sideload.md) (after the ROM, before format data).
- **Flashing may take a while**, and errors during this step are generally fine.
- **Firmware requirement:** you must already be on **HiOS 14 (Android 14)**
  firmware before flashing.
