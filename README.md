# Device Tree Asus ZenFone 6 (ASUS_I001D)

The Asus ZenFone 6 (codenamed _"ASUS_I001D"_) is a smartphone from Asus.
It was released in May 2019.

## Compile

First download omni-9.0 tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
```
Then add these string to .repo/manifests/remove.xml


Then add these projects to .repo/local_manifests/roomservice.xml (If you don't have it, you can add them to .repo/manifest.xml): 

```xml
<project name="mauronofrio/android_device_asus_I001D_TWRP" path="device/asus/ASUS_I001D" remote="github" revision="android-9.0" />
```

Now you can sync your source:

```
repo sync
```

To auotomatic make the twrp installer, you need to import this commit in the build/make path: https://gerrit.omnirom.org/#/c/android_build/+/33182/

Finally execute these:

```
. build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
export LC_ALL=C
lunch omni_ASUS_I001D-eng 
mka adbd recoveryimage 
```

To test it:

```
fastboot boot out/target/product/ASUS_I001D/recovery.img
```

Precompiled stock one