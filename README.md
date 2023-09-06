# android/device/oppo/R15x

[TWRP](https://twrp.me) device tree for
[OPPO R15x](https://www.gsmarena.com/oppo_r15x-9380.php).

## Download

- [twrp.me](https://twrp.me/oppo/oppor15x.html)
- [github release](https://github.com/Freed-Wu/android_device_oppo_R15x/releases)

## Build

Make sure you have enough disk space to avoid some error like
`System.IO.IOException: No space left on device`.

```sh
mkdir android
cd android
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp -b twrp-11
repo sync
git clone --depth=1 https://github.com/Freed-Wu/android_device_oppo_R15x device/oppo/R15x
git clone --depth=1 https://github.com/YuxuanZuo/android_device_oppo_sdm660-common device/oppo/sdm660-common
source build/envsetup.sh
lunch twrp_R15x-eng
export ALLOW_MISSING_DEPENDENCIES=true
mka -j$(nproc) recoveryimage
```

Wait about 10 minutes to get `out/target/product/R15x/recovery.img`.

## Usage

Unlock bootloader by [deep test](https://www.oppo.cn/thread-397164526-1).

### Install TWRP on your mobile

1. Put `recovery.img` on your mobile or USB-OTG.
2. Power off.
3. Press <kbd>power</kbd> and <kbd>volume -</kbd> together to enter fastboot mode.
4. Press <kbd>volume +</kbd>/<kbd>volume -</kbd> to select
   `reboot to recovery mode`, press <kbd>power</kbd> to confirm.
5. Flash `/the/path/of/your/recovery.img`

### Install TWRP by your PC

Install [android-tools](https://github.com/nmeum/android-tools).

```sh
adb reboot-fastboot
sudo fastboot flash recovery recovery.img
sudo fastboot reboot
```

Welcome to enter the rooted Android world!
