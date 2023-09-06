# android/device/oppo/R15x

[TWRP](https://twrp.me) device tree for
[OPPO R15x](https://www.gsmarena.com/oppo_r15x-9380.php).

## Build

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
Or download from
[release](https://github.com/Freed-Wu/android_device_oppo_R15x/releases).
